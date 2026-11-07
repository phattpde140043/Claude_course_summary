# Claude Platform 101 — Tóm tắt khóa học

> **Nguồn & phương pháp** (11/2026): tải **raw HTML** 13 bài tại [academy.claude.com/courses/claude-platform-101](https://academy.claude.com/courses/claude-platform-101) → đọc trọn → tóm tắt **giữ nguyên code samples**. Refer links (2) + media đã phân tích ở Phần B / phụ lục.
> ℹ️ Không có YouTube link. Media = **PNG diagrams** (3-layer stack, model tiers, agent loop, terminal screenshots) — không có text trích được; nội dung tương ứng đã mô tả trong từng phần.

## Mục lục

| Phần | Nội dung |
| :--- | :--- |
| **A** | 13 bài học (API → model → agent loop → tools → thinking → built-in → skills → MCP → context → managed agents → Claude Code) |
| **B** | Refer links: Fable/Mythos 5.1 (blog) + Managed Agents events-and-streaming (docs) |

---

# PHẦN A — 13 bài học

## Bài 1: What is the Claude Platform? (6′)

### Định nghĩa
**Claude Platform** = hạ tầng của Anthropic để build với Claude **programmatically**: thay vì chat trong browser, bạn gửi **structured requests** từ code và nhận structured responses — kiểm soát mọi chi tiết: model nào, bao nhiêu tokens, tools gì, system instructions nào.

Cấu thành: **REST API** (gọi từ mọi ngôn ngữ) · **SDKs** · **CLIs** · **Console** (quản lý API keys, monitor usage, deploy managed agents, test prompts).

### 3 lớp của platform
1. **Primitives** — building blocks gọi từ code: Messages API, tool use, files, web search, code execution, MCP servers, skills
2. **Infrastructure** — để scale agentic systems qua prototype: managed agents, retries, queues, observability
3. **Controls** — chạy production: dashboards, evals

> Shorthand: *"build with primitives, scale on infrastructure, run with control."*

### Ví dụ: draft help desk replies
Wire nút UI → Messages API (Python):
```python
client = anthropic.Anthropic()
response = client.messages.create(
    model="claude-haiku-4-5",   # Haiku: hợp cho drafting đơn giản
    max_tokens=1024,
    system=TONE_AND_GUIDELINES,
    messages=[{"role": "user", "content": ticket_content}],
)
draft = response.content
```
- `model` — model xử lý (Haiku vì task đơn giản) · `max_tokens` — cap độ dài response · `system` — system prompt định nghĩa role (tone + guidelines vào đây) · `messages` — array objects với role `user`/`assistant`
- Flow: define client → retrieve ticket → `messages.create` → trả response cho button render
- Ý nghĩa cốt lõi: không build chatbot từ đầu — **nhét Claude vào sản phẩm đã có**, API là cách wire nó in. Cần agents? Platform **chạy giúp** (managed agents)

## Bài 2: Your first API call (5′)

### Setup
1. Lấy **API key** từ platform.claude.com (tài khoản mới có credit miễn phí; nạp thêm trong Console)
2. Lưu vào **`.env.local`** — *hardcode key trong source là cách chúng lộ trên GitHub*
3. `npm install @anthropic-ai/sdk`

### Giải phẫu request
Mọi call qua `messages.create` với 3 thứ: **model** · **max_tokens** (cap response) · **messages** (objects role `user`/`assistant`).

### Ví dụ thật: review code có bug (~20 dòng)
```typescript
import Anthropic from "@anthropic-ai/sdk";
const client = new Anthropic();
const buggyCode = `
function add(a, b) {
  return a - b;
}
`;
const response = await client.messages.create({
  model: "claude-sonnet-5",
  max_tokens: 2048,
  system: "You are a terse senior code reviewer. Give feedback in one paragraph.",
  messages: [
    { role: "user", content: `Review this code:\n${buggyCode}` },
  ],
});
for (const block of response.content) {
  if (block.type === "text") {
    console.log(block.text);
  }
}
```
2 điều đáng chú ý:
- **System prompt là chỗ shape persona** — muốn terse senior reviewer thì nói vậy
- ⚠️ `response.content` là **array of blocks, không phải string** — text thường 1 block, nhưng Claude có thể trả nhiều loại (text, tool calls, thinking) → **luôn loop và check `type`**

Chạy → Claude phát hiện `add` đang trừ. **Từ script đến product**: cùng shape `messages.create` làm engine cho endpoint summarize (pull transcript từ DB → system "extract insights and risks" → save vào row → return UI) — cùng một call, bọc trong route handler.

## Bài 3: Choosing the right model (5′)

### 4 model tiers (param `model`)
> Ghi chú của bài: Fable 5.1 GA từ **1/9/2026** (video quay trước đó với Opus 4.7/Sonnet 4.6; code dùng model IDs hiện tại).

| Tier | Định vị | Model hiện tại |
| :--- | :--- | :--- |
| **Fable** | Capable nhất — tier mới **trên Opus**, đắt nhất; dành cho thử thách khó nhất | `claude-fable-5-1` |
| **Opus** | Mạnh nhất trong 3 core families nhưng chậm + đắt nhất — deep reasoning, phân tích phức tạp, multi-step coding, viết tinh tế | `claude-opus-5-5` |
| **Haiku** | Nhanh nhất + rẻ nhất — tối ưu speed/cost; high-volume low-complexity (classification, extraction, routing) | `claude-haiku-4-5` |
| **Sonnet** | **Sweet spot**: cân bằng intelligence/speed/cost cho đa số production work | `claude-sonnet-5` |

### Đánh giá trước khi viết production code
Setup **eval đơn giản**: 20–30 representative examples từ workload thật, chạy qua từng model, chấm theo "good output" của use case. Rồi **đi lên từ dưới**: Haiku trước → chất lượng giữ được thì xong (tiết kiệm tiền); không → Sonnet; chỉ với Opus khi task cần.

### So sánh trực tiếp
```python
models = ["claude-haiku-4-5", "claude-sonnet-5", "claude-opus-5-5"]
for model in models:
    response = client.messages.create(
        model=model, max_tokens=300,
        messages=[{"role": "user", "content": prompt}],
    )
    print(model, response.usage)
```
- Loop chỉ đổi `model` — cùng prompt, cùng max_tokens; **`response.usage` trả input/output tokens = cái hóa đơn tính trên đó**
- Quan sát: Opus chậm nhất + polished nhất (lãng phí cho định nghĩa 2 câu); Sonnet tight hơn; Haiku về trong <1s với câu trả lời rất competent
> Nguyên tắc chốt: *"The right model is the cheapest one whose output you'd actually ship."*

### Routing trong production
Một endpoint — nhiều models theo loại việc: file vào → **Haiku classify** · client updates → **Sonnet draft** · chỉ RFP responses → **Opus**. *One queue, three models, picked per task.*

## Bài 4: The agent loop explained (7′)

### Agent là gì
**Agent = Claude chạy cả 2 phía của messaging loop không cần người ở giữa** — nhận task, chọn tool, execute code trong loop cho đến khi Claude quyết định xong.

**Loop tối thiểu:**
1. Gửi message cho Claude kèm tools
2. Claude trả **final answer** hoặc **request dùng tool** bạn định nghĩa
3. Code bạn **execute tool đó**
4. Gửi kết quả lại cho Claude
5. Lặp tới khi `stop_reason` = `end_turn`

### Ví dụ đầy đủ: get_weather + Austin
```python
import anthropic
client = anthropic.Anthropic()

# tools array nói cho Claude có gì: name, description, JSON schema cho inputs
tools = [{
    "name": "get_weather",
    "description": "Get the current weather for a city.",
    "input_schema": {
        "type": "object",
        "properties": {"city": {"type": "string", "description": "The city to get weather for"}},
        "required": ["city"],
    },
}]

def run_tool(name, tool_input):
    if name == "get_weather":
        return f"Weather in {tool_input['city']}: 95F, sunny"
    raise ValueError(f"Unknown tool: {name}")

messages = [{"role": "user", "content": "What should I wear in Austin today?"}]

while True:
    response = client.messages.create(
        model="claude-sonnet-5", max_tokens=1024,
        tools=tools, messages=messages,
    )
    if response.stop_reason == "end_turn":
        for block in response.content:
            if block.type == "text":
                print(block.text)
        break
    if response.stop_reason == "tool_use":
        tool_results = []
        for block in response.content:
            if block.type == "tool_use":
                result = run_tool(block.name, block.input)
                tool_results.append({
                    "type": "tool_result",
                    "tool_use_id": block.id,
                    "content": result,
                })
        messages.append({"role": "assistant", "content": response.content})
        messages.append({"role": "user", "content": tool_results})
```
Chạy thấy 2 turns: turn 1 `stop_reason: tool_use` (Claude xin get_weather Austin) → turn 2 `end_turn` (*"wear something light and breathable"*). **2 API calls, 1 tool execution, 1 final answer.**

### Trong production
Cùng loop đó làm **auto-review endpoint**: compliance agent đọc structural report → look up building codes qua tool → viết risk findings vào DB từng cái. Khác biệt chỉ: tools thật thay mock, results **stream về UI dạng server-sent events**, findings persist vào bảng.

> *"You own the loop and the tools. Claude owns the reasoning."* — Không muốn own loop? **Managed agents** chạy đúng loop này trên hạ tầng Anthropic.

## Bài 5: What is tool use? (8′)

### Tool là gì
**Tool = function bạn định nghĩa và expose cho Claude.** Điều cần nội hóa: **Claude không execute tool — code bạn execute.** Flow: Claude *requests* tool call → code bạn *executes* → result *trở lại* Claude → tiếp tục.

### Định nghĩa tool
**JSON schema 3 phần**: `name` · `description` · `input_schema` — truyền trong request body qua array `tools`. ⚠️ **`description` là thứ Claude đọc để quyết định gọi hay không — viết mơ hồ = tool use tệ; đây là lý do #1 agents misfire.**

```json
{
  "name": "lookup_building_code",
  "description": "Look up a specific building code section by its identifier. Returns the full text of that code section.",
  "input_schema": {
    "type": "object",
    "properties": {"section": {"type": "string", "description": "The building code section to look up"}},
    "required": ["section"]
  }
}
```
Gửi compliance report → turn 1 Claude trả `stop_reason: "tool_use"` → loop gọi tool với param Claude xin → feed lại **tool result** (user message chứa `tool_result` block gắn với `tool_use_id`) → Claude tiếp tục.

### Nhiều tools: Claude tự chọn
Scenario Denver 3 ngày → khai báo `get_weather` + `get_forecast`; loop y hệt, chỉ thêm `runTool` **dispatch theo tên bằng switch**:
```typescript
function runTool(name, input) {
  switch (name) {
    case "get_weather":  return getWeather(input.city);
    case "get_forecast": return getForecast(input.city);
  }
}
while (true) {
  const response = await client.messages.create({
    model: "claude-sonnet-5", max_tokens: 1024, messages, tools,
  });
  if (response.stop_reason !== "tool_use") break;  // final answer
  messages.push({ role: "assistant", content: response.content });
  const toolResults = response.content
    .filter((block) => block.type === "tool_use")
    .map((block) => ({
      type: "tool_result",
      tool_use_id: block.id,
      content: runTool(block.name, block.input),
    }));
  messages.push({ role: "user", content: toolResults });
}
```
Claude gọi cả 2 tools (đôi khi cùng turn, đôi khi tuần tự) rồi trả lời *"pack layers, expect snow flurries today, warming through the week"* — nó **đọc descriptions**, map "today" → get_weather, "next few days" → get_forecast. Thêm tool thứ 3 = thêm vào array + thêm case.

### Tool runner — bỏ boilerplate
2 red flags của cách trên: code nhiều cho 2 lookups; không ai muốn **handwrite JSON schemas** cho mọi function. → **Tool runner** (beta trong SDKs: TypeScript, Python, Ruby, C#, Go, Java, PHP): define tool một lần, runner xử toàn bộ loop nội bộ. TypeScript dùng helper **`betaZodTool()`** với **Zod ≥ 3.25.0** (`npm install zod`):
```typescript
import { betaZodTool } from "@anthropic-ai/sdk/helpers/beta/zod";
import { z } from "zod";

const weatherTool = betaZodTool({
  name: "get_weather",
  description: "Get today's current weather for a city.",
  inputSchema: z.object({ city: z.string().describe("The city to check") }),
  run: async ({ city }) => getWeather(city),
});
const forecastTool = betaZodTool({ /* ... tương tự ... */ });

const runner = client.beta.messages.toolRunner({
  model: "claude-sonnet-5", max_tokens: 1024,
  messages: [{ role: "user", content: "I'm packing for a three-day trip to Denver. What's the weather today and over the next few days?" }],
  tools: [weatherTool, forecastTool],
});
const finalMessage = await runner;  // final message sau khi tool ping-pong settle
```
Không while loop, không stop-reason switch, không push tool results tay; **Zod schema còn validate input Claude gửi**; `await runner` = final assistant message.

### Tools thật
Tools thật = **thin wrappers quanh functions có sẵn trong codebase** (compliance agent bọc `lookup_building_code` + `search_building_code` sẵn có — mỗi finding cite section cụ thể). Phổ: bạn tự chạy loop → tool runner → (cuối phổ) **managed agents delegate cả agent**.

## Bài 6: What is thinking? (5′)

### Extended thinking là gì
Claude **reason step-by-step trước khi trả lời**: sinh **reasoning tokens** (chain of thought) rồi mới đưa answer. Trên Opus 5, thinking text **ẩn** trừ khi request có `thinking` gồm `"display": "summarized"` — khi đó **summary reasoning** quay về cùng final text. Failure mode tránh: hỏi multi-step và bắt trả ngay → *confidently wrong*.

### Adaptive thinking trên Opus 5
Trên Opus 5, thinking **adaptive + bật mặc định** — không cần chọn token budget: Claude tự quyết khi nào nghĩ và nghĩ bao nhiêu. Điều khiển độ sâu bằng **`effort`** — ⚠️ **gotcha: nằm trong `output_config`, không phải cạnh block `thinking`**. Levels: `low` · `medium` · `high` (default) · `xhigh` · `max`.

### Khi nào dùng / bỏ
✅ Math + multi-step logic · code debugging · regulatory analysis · mọi thứ có **trade-offs/so sánh options**. ❌ Classification, extraction, boilerplate đơn giản — chỉ thêm **latency + cost** không cải thiện.

### Trong action — road trip từ SF
```python
response = client.messages.create(
    model="claude-opus-5",
    max_tokens=16000,
    thinking={"type": "adaptive", "display": "summarized"},  # summarized = trả reasoning text
    output_config={"effort": "high"},  # low | medium | high | xhigh | max
    tools=[weather_tool],
    messages=[{"role": "user", "content": "Plan a road trip out of San Francisco with two stops, weighing weather and drive time."}],
)
```
Output: **thinking blocks** (Claude cân trade-offs) → tool calls check từng city → text block recommendation. *The reasoning is visible — that's the whole point.*

### Trong production
Khác biệt giữa agent tìm lỗi **từng cái một** và agent **nối chúng lại**: bật adaptive thinking cho auto-review → compliance agent reason **across** report sections — bắt được wind load spec ở section 3 mâu thuẫn material spec chỗ khác trong document.

## Bài 7: Built-in tools (6′)

### Server tools — bạn khai báo, Anthropic chạy
Chạy trên hạ tầng Anthropic → **không cần agent loop**: Claude tự gọi, result về **trong cùng một response**. Ba cái chính:
- **Web search** — search internet, trả kết quả kèm citations
- **Code execution** — viết + chạy Python trong sandbox
- **Web fetch** — lấy full content từ URLs

```python
# Call 1: web search — Anthropic chạy search server-side
search_response = client.messages.create(
    model="claude-opus-5", max_tokens=1024,
    tools=[{"type": "web_search_20260209", "name": "web_search"}],
    messages=[{"role": "user", "content": "What is Anthropic's latest model release? Answer in one sentence."}],
)
for block in search_response.content:
    if block.type == "server_tool_use":
        print(f"Tool call: {block.name} — {block.input}")
    elif block.type == "text":
        print(block.text)

# Call 2: code execution — Claude viết + chạy Python trong sandbox
code_response = client.messages.create(
    model="claude-opus-5", max_tokens=1024,
    tools=[{"type": "code_execution_20260120", "name": "code_execution"}],
    messages=[{"role": "user", "content": "Calculate the mean and standard deviation of [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]"}],
)
for block in code_response.content:
    if block.type == "server_tool_use":
        print(f"Tool call: {block.name} — {block.input}")
    elif block.type == "bash_code_execution_tool_result":
        print(f"stdout: {block.content.stdout}")
    elif block.type == "text":
        print(block.text)
```
Điểm mới: **không switch stop_reason, không push tool results** — response có sẵn block types mới: `server_tool_use` (tool call) + code execution result block (stdout) + `text` bình thường. Chạy thấy: Python Claude thật sự viết, stdout sandbox, câu trả lời cuối.

### Client tools
Chạy **nơi code bạn chạy** — Anthropic publish schemas + train Claude sẵn (khỏi tự định nghĩa):
- **Memory** — Claude đọc/ghi memory xuyên sessions (4 SDKs có helper xử lý calls against storage bạn cung cấp)
- **Bash** — persistent bash shell để Claude chạy commands (app bạn chạy shell)

### Production + lưu ý
Đường ngắn nhất tới features mất hàng tuần nếu tự làm — VD web search làm **fact-check endpoint** kiểm mọi claim số liệu/regulatory trong draft với live web. ⚠️ *"Just because something is validated on the internet doesn't mean it's true. Always double-check Claude's work."*

## Bài 8: Skills (6′)

### Skill là gì
**Folders of instructions, scripts, resources Claude load dynamically** cho task chuyên biệt. Lõi = **`SKILL.md`** — package instructions upload **một lần**, attach vào bất kỳ `messages.create` nào. Bạn dạy Claude cách **LÀM** việc: format status report, review checklist, release notes.

### Skills vs Tools
- **Tools** kết nối Claude với data + actions (*"look up this code section"*) — Claude gọi, thứ khác chạy
- **Skills** dạy Claude một **procedure** (*"generate daily status report theo template này"*) — playbook Claude đọc và theo, đôi khi chạy cả bundled scripts

> *Tools = **what** Claude can do. Skills = **how** you want it done.*
> Skills **load progressively**: khởi động chỉ load name + description; agent quyết định relevant mới load full → context lean.

### Upload + Attach
```python
# Upload một lần (hoặc upload trực tiếp trên Claude Platform)
skill = client.skills.create(
    display_name="Status Report Generator",
    files=files_from_dir("status-report-skill"),  # folder chứa SKILL.md
)
print(skill.id)  # reference ID này cho các request sau

# Attach qua container config
response = client.messages.create(
    model="claude-opus-5",
    max_tokens=4096,
    container={
        "skills": [
            {"type": "custom", "skill_id": skill.id, "version": "latest"}
        ]
    },
    tools=[{"type": "code_execution_20250825", "name": "code_execution"}],
    messages=[{"role": "user", "content": f"Generate the daily status report from this activity log:\n\n{activity_log}"}],
)
```
Điểm đáng chú ý:
- Skills **GA** trên Claude API — beta header `skills-2025-10-02` **không còn cần** (gửi vẫn chạy bình thường)
- `container.skills` là **list** → layer nhiều Skills lên một call
- **Code execution bật kèm là bắt buộc**: trên API, Skills chạy trong container của code execution tool — điều cho Skill procedures làm việc thật (chạy scripts)

Output = status report đúng format SKILL.md quy định (sections, tone, blocker handling); user prompt chỉ 1 dòng — **procedure nằm trong Skill**. Production: chuẩn hóa output cả feature — mọi PM nhận cùng cấu trúc không ai copy-paste template vào prompt.

## Bài 9: MCP (6′)

### Vấn đề maintenance
Agent cần pull tasks Asana + check Google Calendar + search Slack → custom tools = **bạn viết 3 integrations** rồi **maintain mãi** mỗi khi service đổi API. MCP **đẩy maintenance cho provider**: Asana/Slack/Google tự publish MCP server, expose tools (descriptions + schemas + auth) qua standard protocol — API đổi, họ update server, **bạn không đổi gì**.

### Tools vs Skills vs MCP
| | Dùng cho | Ai maintain |
| :--- | :--- | :--- |
| **Tools** | Systems **của bạn** (DB, project tracker, proprietary APIs) | Bạn |
| **Skills** | **Process** của bạn (report template, review checklist) — instructions, không hẳn integration | Bạn |
| **MCP** | **Third-party services** | Provider |

> *Tools = your stuff · Skills = your processes · MCP = everyone else's stuff.*

### Connect tới MCP server (Linear)
Hai mảnh trong request: `mcp_servers` khai connection (type, URL, name, optional auth token) + tool type `mcp_toolset` cấp quyền dùng tools của server đó (default = tất cả):
```python
response = client.beta.messages.create(
    model="claude-opus-5",
    max_tokens=1024,
    messages=[{"role": "user", "content": "What tools do you have available?"}],
    mcp_servers=[{
        "type": "url",
        "url": "https://mcp.linear.app/mcp",
        "name": "linear",
        "authorization_token": os.environ["LINEAR_MCP_TOKEN"],
    }],
    tools=[{"type": "mcp_toolset", "mcp_server_name": "linear"}],
    betas=["mcp-client-2025-11-20"],  # MCP connector đang beta
)
```
**Không viết một dòng schema nào** — Claude **introspect** server, nhận list tools + schemas, tự chọn đúng tool cho prompt. Chạy → Claude list tools của Linear rồi gọi một cái.

### Filter tools Claude được dùng
Server thường expose rất nhiều tools (ngốn context, hoặc không muốn write):
```python
tools=[{
    "type": "mcp_toolset",
    "mcp_server_name": "slack",
    "default_config": {"enabled": False},
    "configs": {
        "search_messages": {"enabled": True},
        "list_channels": {"enabled": True},
    },
}]
```
→ Claude search Slack + list channels được, **không post/delete** — hợp khi tin service cho đọc nhưng không muốn Claude viết hộ. Thêm: **modelcontextprotocol.io** cho danh sách servers + tài liệu protocol.

## Bài 10: Context management (6′)

### Context là gì
**Mọi thứ Claude thấy trong một turn**: system prompt · message history · tool definitions + results · attached files + skills · thinking blocks. Là input của mọi API call — **trả tiền lúc vào lẫn lúc ra**; window đầy → **request fail**. Mục tiêu không phải nhét tất cả vào, mà *fit đúng những thứ cần vào*.

### 4 patterns (3 là API features, 1 là design pattern)
1. **Just-in-time context** *(design pattern)* — đừng load tất cả upfront; load cái agent cần **ngay lúc này**, cho nó tự pull thêm qua tools. Compliance agent không nhét cả building code book vào system prompt — gọi `lookup_building_code` khi cần section cụ thể
2. **Server-side compaction** — conversation dài → Anthropic auto-summarize các turn cũ thành 1 block; opt-in bằng `context_management`:
```python
response = client.beta.messages.create(
    betas=["compact-2026-01-12"],
    model="claude-opus-5",
    max_tokens=1024,
    context_management={"edits": [{"type": "compact_20260112"}]},
    messages=messages,
)
```
   API tự summarize khi input vượt trigger threshold — khỏi tự theo dõi độ dài
3. **Prompt caching** — mark phần **stable** của request (system prompt, tool definitions, document dài) và **reuse across calls** với giá rẻ hơn nhiều. Toán học: system prompt 4.000 tokens × 100 calls/giờ — *"caching là khác biệt giữa bill dùng được và điện thoại từ phòng tài chính"*
4. **Memory tool** — context cần sống **xuyên sessions** (preferences, running notes, quyết định tuần trước). Claude đọc/ghi **memory directory qua tool calls**; bạn implement **storage backend client-side** (file system, DB, encrypted store...); Anthropic **auto-inject system instruction** bảo Claude check memory directory trước khi bắt đầu

### Layer cả 4
Production thường layer tất cả (compliance agent: cache system prompt + tool defs, JIT pull code sections). Mỗi pattern xử một failure mode: **cost** · **window size** · **statelessness** — chọn theo cái đang hỏng của bạn. (Managed agents có sẵn caching + compaction bật mặc định.)

## Bài 11: What are managed agents? (7′)

### Định nghĩa
**Claude Managed Agents** = suite APIs build + deploy **agents at scale**: define agents (tools, personas, capabilities) → configure sandbox environments (packages, network controls) → fire sessions từ app mình — Claude làm việc trong **isolated container** với full file system access, bash execution, web search. Bản chất: **agent loop được host giúp** (Console có section riêng).

### Ví dụ 1: Kanban board tự làm việc
Kéo ticket vào "in progress" → **tự động fire session**. Ticket "optimize website performance":
1. Back end tạo session → trỏ **environment** cấu hình sẵn **Lighthouse + Puppeteer** → **GitHub repo mount vào container**
2. Claude có codebase + tools + **rubric** định nghĩa done: *Lighthouse > 90 · no render-blocking resources · all images lazy loaded*
3. Claude chạy audit → nén images, inline CSS, defer scripts — **mọi tool call stream về board real-time** qua event stream
4. **Rubric kick in**: một **grader riêng** (context window riêng) đánh giá output theo criteria → Claude đọc feedback, quay vào sửa cái miss, resubmit → demo đưa Lighthouse lên **96**
5. Kéo ticket thứ 2 trong khi cái đầu còn chạy — **2 sessions, 2 containers, song song**

### Ví dụ 2: recurring research agent + memory
Agent theo dõi giá + plan changes của mọi SaaS tool công ty trả tiền, report trước stand-up. Mỗi run: search web pricing pages + flag tier changes/features ảnh hưởng hợp đồng → chạy **cost analysis Python trong sandbox** → dùng **Excel skill** viết executive summary → post link Slack + tạo review task Asana (qua **MCP servers**). Đồng thời **đọc/ghi memory store**: check kết quả tuần trước trước khi bắt đầu, lưu thay đổi sau khi xong → report thứ Hai nói được *"compute costs are 15% lower since last week"* thay vì listing pricing tĩnh.

### Ví dụ 3: incident response đa agent
Alert từ monitoring → back end nhận payload → gửi vào session mới dạng user message. Agent cần thêm từ monitoring stack → gọi **custom tool** (back end bạn chạy, trả result về cùng session). Session dùng **multi-agent coordination**: **coordinator** nhận alert, delegate cho **3 specialists** (mỗi cái context window riêng, cùng **shared file system**) → specialists báo lại → coordinator synthesize thành incident summary. Trước khi summary lên Slack: **permission policy** bật — bạn thấy draft, approve, message mới đi (*sensitive actions chờ human*). Memory khép vòng: coordinator check incidents cũ → *"this looks like the DNS resolution issue from two weeks ago caused by a misconfigured TTL"* — lần sau alert tương tự, agent khởi động với context đó thay vì chẩn đoán từ đầu.

### Building blocks
**Agents** (definitions) · **Sessions** (từng runs) · **Environments** (sandboxes) · **Tools** (kể cả custom trên back end bạn) · **MCP** (Slack, Asana...) · **Memory** · **Outcomes** (rubrics + graders định nghĩa và check "done") · **Multi-agent coordination**.

> *"You define what done looks like. Claude works until it gets there."*

## Bài 12: Building your first managed agent (8′)

### Vì sao delegate
Loop tự viết ổn cho nhiều features — nhưng khi loop chạy **phút đến giờ**, nhiều tools, có state giữ, files viết, resume sau mạng giật → không muốn chạy trên server mình. **Managed agent = agent loop chạy trên hạ tầng Anthropic**: describe agent một lần, cho environment, start session — Anthropic chạy loop, bạn **stream events** ra. **Enabled mặc định cho mọi API account.**

### 4 primitives (theo thứ tự)
1. **Agent** — persona: model + system prompt + toolset; **reusable** qua nhiều runs
2. **Environment** — nơi agent chạy: cloud/self-hosted, networking config
3. **Session** — một run của agent trong environment; **đơn vị công việc**
4. **Events** — mọi thứ chảy qua: actions, tool calls, results, replies

Dịch chuyển tư duy: **không chạy while loop — gửi events và đọc events.**

### 5 bước — managed agent nhỏ nhất (tạo file, đếm dòng, báo lại)
Dùng **agent toolset** (`agent_toolset_20260401`) — bộ file/bash/web tools có sẵn của Anthropic, khỏi tự define:

**1. Create the agent** (reusable):
```python
agent = client.beta.agents.create(
    name="Line Counter",
    model="claude-opus-5",
    system="You are a helpful agent that completes small file tasks.",
    tools=[{"type": "agent_toolset_20260401", "default_config": {"enabled": True}}],
)
```
**2. Create the environment** — sandbox: cloud + networking `limited` (sandbox & web tools chỉ với tới hosts trong `allowed_hosts`; task này không cần network → list rỗng; `unrestricted` chỉ khi agent phải với tới sites không list trước được). Mỗi session sandbox riêng — file viết vào đó:
```python
environment = client.beta.environments.create(
    name="line-counter-env",
    config={"type": "cloud", "networking": {"type": "limited"}},
)
```
**3. Create the session** (unit of work):
```python
session = client.beta.sessions.create(
    agent=agent.id,
    environment_id=environment.id,
    title="Count lines demo",
)
```
**4. Mở stream TRƯỚC, rồi gửi kickoff** — ⚠️ stream **chỉ deliver events xảy ra sau khi mở** → luôn mở trước khi gửi message:
```python
with client.beta.sessions.events.stream(session_id=session.id) as stream:
    # Stream đã mở — giờ mới gửi kickoff
    client.beta.sessions.events.send(
        session_id=session.id,
        events=[{
            "type": "user.message",
            "content": [{"type": "text", "text": "Create a file in the temp directory, count its lines, and report back."}],
        }],
    )
```
(Lưu ý `events` — số nhiều: events là cách mọi thứ chảy trong API này.)
**5. Consume stream** — 3 event types chính cho demo này:
```python
for event in stream:
    if event.type == "agent.message":          # text của Claude
        for block in event.content:
            if block.type == "text":
                print(block.text, end="", flush=True)
    elif event.type == "agent.tool_use":       # tool Claude chọn
        print(f"\n[tool] {event.name}")
    elif event.type == "session.status_idle":  # agent dừng, chờ input
        print("\n--- Agent done ---")
        break
```
⚠️ Trong app thật, check **`event.stop_reason.type`** trước khi coi là xong: `end_turn` = agent hết turn hoặc bạn interrupt; `requires_action` = tool call cần bạn trả lời.

### The trade + reconnect
Bạn delegate **loop + sandbox + resumability**, chỉ consume event stream. **Event history lưu server-side** → kết nối đứt: mở stream mới, **list past events** xem thiếu gì, skip event trùng (chi tiết code ở B.2). Production shape cho việc **dài, chạm files, "go organize this for me"** — VD fileshare cleanup: agent đọc spec cấu trúc thư mục, walk folder bừa bộn, move đúng chỗ, archive trùng + zero-byte, flag cái không chắc — session chạy **phút tỷ lệ nghìn files**.

## Bài 13: Building with Claude Code (5′)

### Ý tưởng
Viết code gọi Claude API tay được — nhưng nhanh hơn: **để Claude Code viết**. Project: file TypeScript lấy weather với 2 stubs — `getWeather` (nhận city, trả nhiệt độ + conditions) và `run` (dùng **tool runner** + Claude TS SDK). Tool runner là mảnh xử tool calling + agent loop giúp bạn.

### Claude API skill
Claude Code có built-in skill **Claude API**: invoke bằng **`/claude-api`**, hoặc Claude Code **tự động invoke khi phát hiện bạn dùng TypeScript SDK**.

### Một prompt = code chạy được
Mở project trong terminal, chạy Claude Code. Prompt tốt làm 3 việc: **nêu file** cần đổi · **nêu pattern** muốn dùng · **nêu end state** kỳ vọng. Claude Code điền `getWeather` + `run` theo types, append call cuối file, **chạy script, báo output**; lỗi thì **đọc error và patch code tại chỗ**.

### Kết quả & pattern
Lần chạy này: Claude Code tạo **Zod tool** parse input + return output theo city type, tạo tool runner + hàm `run`, in kết quả cuối của agent loop.

> Pattern cần nhớ — code Claude API luôn có hình quen thuộc: **Define a tool → Hand it to a runner → Return the result.** Không cần gõ từ memory mỗi lần: **stub the file, hand it to Claude Code, review the diff.**

---

# PHẦN B — Refer links đã quét

## B.1 — Claude Fable 5.1 & Mythos 5.1 (blog)
> Nguồn: anthropic.com/claude-fable-and-mythos-5-1 — được link từ Bài 3.

- **Cùng một model, mức safeguard khác nhau**: **Fable 5.1** GA; **Mythos 5.1** giới hạn cho trusted access programs (cybersecurity + life sciences)
- Định vị: "world's most advanced models for coding and knowledge work"; hệ thống **effort setting** mới (mặc định **High trong Claude Code, Medium ở nơi khác**)
- Benchmarks vượt Fable 5/Opus 5: agentic coding (Terminal-Bench 4.0: 55.8–60.9%) · scientific research (TB-Science: 52.6% vs 24.7%) · computer use (OSWorld 2.0: 77.9% partial) · multidisciplinary reasoning (HLE: 65.0% with tools). Khoa học: protein binders (~50% hit rate), bản đồ độ cao Venus độ phân giải cao hơn, tối ưu GPU tăng tốc bio models open-source tới 2.5×
- Safety: cyber safeguards giảm ~60% false positives; biology safeguards giảm 85% trên benign queries; **cho phép vulnerability discovery (không cho exploit development)**; **Enterprise Frontier Safeguards (EFS)** — privacy kiểu ZDR, data nằm hạ tầng khách; anti-distillation; watermark tuân thủ EU AI Act; Mythos 5.1 vẫn dưới risk tier kế tiếp trong Responsible Scaling Policy
- Availability: Fable 5.1 trên AWS, Google Cloud, Azure, Claude API (`claude-fable-5-1`); Mythos 5.1 qua Cyber/Life Sciences Verification Program (phát triển cùng chính phủ Mỹ, hiện giới hạn tổ chức Mỹ)
- Pricing: giữ nguyên Fable 5 — **$10/M input, $50/M output**; **cache reads giảm 75% còn $0.25/M** → workload điển hình rẻ ~25%, agentic cao tới ~45%

## B.2 — Managed Agents: events & streaming (docs)
> Nguồn: platform.claude.com/docs/en/managed-agents/events-and-streaming — được link từ Bài 12 (reconnect pattern). Beta header: `managed-agents-2026-04-01`.

- Mô hình **event-based 2 chiều**: bạn gửi `user.*` events (khởi động + steer session) và `system.message` (append system-level context); nhận về **session events** (trạng thái) + **span events** + **agent events** (tiến độ)
- ⚠️ **ZDR not eligible**: sessions là **stateful resources — transcripts persist tới khi bạn delete** (áp dụng mọi sub-feature kể cả self-hosted sandboxes)
- Models hỗ trợ (snapshot): `claude-fable-5-1`, `claude-mythos-5-1`, fable/mythos 5, opus 5.5/5, sonnet 5.5/5, haiku 5.5/4.5, opus 4.x, sonnet 4.x — qua Claude API + AWS + Google Cloud (đều beta)
- **Reconnect không sót event** (pattern bài 12 dẫn tới):
  1. Mở stream mới (buffering ngay)
  2. **List full event history** → seed set `seen_event_ids`
  3. Tail live stream, **skip mọi event ID đã có trong history**
  ```python
  with client.beta.sessions.events.stream(session.id) as stream:
      history = client.beta.sessions.events.list(session.id)
      seen_event_ids = {past_event.id for past_event in history}
      for event in stream:
          if event.type in ("event_start", "event_delta"):  # preview events — bỏ qua
              continue
          if event.id in seen_event_ids:
              continue
          seen_event_ids.add(event.id)
          match event.type:
              case "agent.message":
                  for block in event.content:
                      if block.type == "text":
                          print(block.text, end="")
              case "session.status_idle":
                  break
  ```
  (TypeScript tương tự với `Set<string>` + labeled `break tail`.) Lưu ý: `event_start`/`event_delta` là **delta previews không có top-level `id`** — skip.
- Khi reconnect vào session đang pause: `stop_reason.event_ids` trên `session.status_idle` mới nhất **liệt kê các calls đang chờ bạn trả lời**

---

# Phụ lục: Nguồn & media đã phân tích

| Nhóm | Chi tiết |
| :--- | :--- |
| **Khóa chính (raw HTML, 13 bài)** | `/courses/claude-platform-101/` — what-is-the-claude-platform · your-first-api-call · choosing-the-right-model · the-agent-loop-explained · what-is-tool-use · what-is-thinking · built-in-tools · skills · mcp · context-management · what-are-managed-agents · building-your-first-managed-agent · building-with-claude-code |
| **Refer links (2)** | [Fable & Mythos 5.1](https://www.anthropic.com/claude-fable-and-mythos-5-1) (B.1) · [Managed Agents events-and-streaming](https://platform.claude.com/docs/en/managed-agents/events-and-streaming) (B.2) |
| **Links trong code samples** | `https://mcp.linear.app/mcp` (endpoint MCP Linear, Bài 9) · `modelcontextprotocol.io` (Bài 9 nhắc) — không phải trang nội dung |
| **Media (PNG, không có YouTube)** | Diagrams: 3-layer platform stack (Bài 1) · model tier cards (Bài 3) · agent loop + session lifecycle (Bài 4/12) · terminal screenshots (Bài 3/12) · Kanban/fileshare demo GIF (Bài 11/12) — **ảnh minh họa, không chứa text bổ sung cần trích**; nội dung tương ứng đã diễn đạt trong tóm tắt |

> ✅ **Độ phủ:** 13/13 bài đọc từ raw HTML gốc, **giữ nguyên toàn bộ code samples** (Python + TypeScript + JSON) — đây là khóa nặng code nhất trong 5 khóa đã quét. 2/2 refer links quét trọn. Duration mỗi bài: 6-5-5-7-8-5-6-6-6-6-7-8-5′.
