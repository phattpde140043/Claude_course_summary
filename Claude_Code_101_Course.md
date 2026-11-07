# Claude Code 101 — Tóm tắt khóa học

> **Nguồn quét** (11/2026): 12 bài của khóa [Claude Code 101](https://academy.claude.com/courses/claude-code-101) + mở rộng toàn bộ **sub links** trong nội dung:
> - 2 trang docs chính thức: [Code Review](https://code.claude.com/docs/en/code-review) và [Hooks](https://code.claude.com/docs/en/hooks)
> - 2 khóa con liên quan: [Introduction to subagents](https://academy.claude.com/courses/introduction-to-subagents) (4 bài) và [Introduction to agent skills](https://academy.claude.com/courses/introduction-to-agent-skills) (6 bài)
> - ℹ️ Không có YouTube link nào trong nội dung các bài (video đều là player nội bộ của Academy)

## Mục lục

| Phần | Nội dung |
| :--- | :--- |
| **A** | Claude Code 101 — 12 bài chính |
| **B** | Docs tham chiếu: Code Review (GitHub PRs) + Hooks reference |
| **C** | Khóa con: Introduction to subagents (4 bài) |
| **D** | Khóa con: Introduction to agent skills (6 bài) |

---

# PHẦN A — Claude Code 101 (12 bài)

## Bài 1: What is Claude Code? (5′)

### Khác biệt so với Claude.ai
- Claude Code có **truy cập trực tiếp** vào files, terminal và toàn bộ codebase của bạn
- Không còn workflow copy/paste — tool "vào và tự làm việc"
- Điểm mấu chốt: Claude Code vận hành như một **AI Agent**

### Agent là gì?
- Định nghĩa: *"software that can interact with its environment and perform actions to complete a defined goal"*
- Cơ chế: LLM chạy trong một **loop, theo thời gian thực**; có thể dùng tools, services ngoài, thậm chí AI agents khác

### 4 năng lực cốt lõi
1. **Đọc và hiểu codebase** — giải thích feature, trace bug qua code
2. **Edit files** toàn project — refactor một hàm và cập nhật mọi file tham chiếu
3. **Chạy terminal commands** — build scripts, tests, installs; dùng output để quyết định bước tiếp theo
4. **Search web** — tra documentation, API references mới nhất

### 3 khái niệm để dùng hiệu quả
1. **Context window** = "working memory" của Claude — chứa nhiều nhưng không phải tất cả; Claude **định vị chiến lược** câu trả lời thay vì nạp cả codebase
2. **Bạn kiểm soát permissions** — hands-on (duyệt từng lệnh) hoặc auto mode (background safety check sàng lọc hầu hết hành động)
3. **Claude có thể sai** — hiểu nhầm ý định, tạo bugs, over-engineer → stay in the loop để bắt lỗi sớm

> Claude Code có mặt tại: **terminal, VS Code, JetBrains IDEs, Claude Desktop app, và web**.

## Bài 2: How Claude Code works (5′)

### Agentic loop (5 bước)
1. User nhập prompt
2. Claude **gather context** — model trả về text hoặc tool call khả thi
3. Claude **take action** — edit file, chạy command
4. Claude **verify results** so với mục tiêu của prompt
5. Đạt mục tiêu → kết thúc, chờ prompt tiếp; không → **loop lại** đến khi "complete and verifiable"

Trong suốt loop, bạn có thể thêm context, interrupt, hoặc steer.

### Context
- **Context window** giới hạn lượng conversation history + file contents + command output
- Gần đầy → Claude Code tự **compact**: quyết định bỏ/tóm tắt gì để lấy lại không gian

### Tools
- *"The backbone of how agents work"* — khác assistant chỉ biến đổi text, tools cho Claude Code quyết định **khi nào** thực thi code
- VD: file-reading tool, web search tool; chọn tool bằng **semantic understanding**

### Permissions — 4 chế độ

| Mode | Hành vi |
| :--- | :--- |
| **Manual** | Xin duyệt rõ ràng trước mỗi edit file / shell command |
| **Auto-accept** | Edits tự chạy; các lệnh filesystem phổ biến (`mkdir`, `mv`, `rm`) cũng tự do; lệnh khác vẫn hỏi |
| **Plan mode** | Đọc files + chạy exploratory commands, **không đụng source files**, rồi tổng hợp plan trước khi làm |
| **Auto mode** | Bỏ qua prompt thường; background classifier chặn hành động *"irreversible, destructive, hoặc nhắm ngoài môi trường"* — khi bị chặn, Claude tìm đường an toàn hơn hoặc hỏi |

> ⚠️ Mode khởi động tùy version và settings. Cảnh báo: trao "free rein" nghĩa là một sai lầm có thể khó bắt trước khi xảy ra.

## Bài 3: Installing Claude Code (6′)

### 5 cách cài/đặt

| Cách | Chi tiết |
| :--- | :--- |
| **Terminal** | macOS/Linux/WSL: `curl` một bước, hoặc `brew install` (không auto-update). Windows: PowerShell `Invoke-RestMethod`, CMD `curl`, hoặc `winget`. Chạy lệnh `claude`; nếu fail → restart terminal, `cd` vào project, chạy lại |
| **VS Code** | Extensions panel → tìm "Claude Code" → cài bản của Anthropic (**blue verification check**). `Ctrl/Cmd+Shift+P` → "Claude Code Open in New Tab" hoặc icon sidebar |
| **JetBrains** | Plugin từ Marketplace → restart IDE → logo Claude mở pane terminal cạnh editor |
| **Desktop** | Sau khi đăng nhập Claude Desktop → tab **"Code"**: làm việc trong folder cụ thể, đổi permissions, hoặc chạy **cloud environment** |
| **Web** | `claude.ai/code` — như desktop nhưng **giới hạn GitHub repositories** |

**First-run:** chọn theme → đăng nhập bằng Claude account (Pro/Max/Team/Enterprise) hoặc API key; org có Claude Enterprise thì chọn option đó.

> ⚠️ **Scope:** chạy `claude` từ thư mục nào thì nó có quyền truy cập **thư mục đó + toàn bộ subfolders**.

### Chọn cách nào?

| Option | Best for |
| :--- | :--- |
| Terminal | Cutting edge — tính năng về đây trước nhất |
| IDE (VS Code/JetBrains) | Trải nghiệm gần như giống hệt, tích hợp editor |
| Desktop | Claude chạy nền trong khi bạn làm việc khác |
| Web | Làm việc từ xa qua GitHub repo |

## Bài 4: Your First Prompt (6′)

### Chọn permission mode
Nhấn **`Shift + Tab`** để vòng qua các mode: Manual → Auto-accept → Auto. *"There's no right or wrong answer — it's whatever you're comfortable with."*

### Plan Mode
- Nằm trong menu `Shift + Tab`
- Nhận prompt → đọc files + chạy shell commands để phân tích codebase và research hướng implement — **không edit source files**
- Hỏi clarifying questions dọc đường → trả về **plan chi tiết** có thể thực thi
- Best for: lên kế hoạch thay đổi phức tạp, code review an toàn, multi-step features

### Ví dụ: thêm dark mode toggle
1. Mở thư mục root của project → chạy `claude`
2. `Shift + Tab` tới khi status bar hiện **"plan mode on"**
3. Viết prompt descriptive: *"My app needs a dark mode implemented across the entire app"* + yêu cầu toggle switch trên header + nhờ Claude *"find a good contrast color that works"* từ light theme hiện có
4. Review plan → accept → Claude execute (tùy permission mode có thể check-in từng bước)
5. Cuối cùng xem chính xác Claude đã làm gì và cách nó suy luận

> Recap: prompt càng **descriptive** càng tốt; có thể stay in the loop ở mọi bước; dùng Plan Mode để đào chi tiết **trước khi code chạy**.

## Bài 5: Explore → Plan → Code → Commit (8′)

> *"Nếu chỉ mang về một điều từ khóa này, hãy là workflow này."* — Hầu hết mọi người nhảy thẳng đến việc nhờ Claude viết code, dẫn phải course-correct nhiều về sau.

### 1. Explore + Plan (qua Plan Mode)
- Plan mode: Claude **không thể edit files** — chỉ đọc và chạy shell commands để khám phá
- Prompt mẫu: *"I need to add WebP conversion to our image upload pipeline"* + nhờ Claude tự tìm: vị trí chèn trong pipeline? dependency mới cần? cách tiếp cận?
- Claude đọc files liên quan, chạy web searches, trả về **plan of action** — review, yêu cầu sửa từng phần nếu chưa đạt
- *"Đây là nơi course-correct tốt nhất — vì chưa có dòng code nào được viết"*
- Thay thế: chạy **explore subagent** (ngoài plan mode) khi chỉ cần tóm tắt codebase chung, không định thay đổi

### 2. Code
- Approve plan → Claude thực hiện từng item; permission mode quyết định mức can thiệp
- Claude tự troubleshoot trước khi tuyên bố xong — nhưng bạn vẫn có thể phải bước vào; lợi thế Plan Mode: bạn giữ **context của cả hành trình**

**3 tips cho session mượt:**
1. **Define success criteria** — nêu rõ "đúng" trông như thế nào ngay trong plan
2. **Add tools** — VD cài extension **Claude in Chrome** khi build web UI để Claude Code điều khiển browser tab và test UI trực tiếp
3. **Include a test suite** — cho Claude bộ test để tự validate liên tục (Claude viết test được); đảm bảo tests là **reliable source of truth** trước để tránh false positives

> 💡 Claude lặp lại cùng một lỗi? Nhờ nó **lưu solution vào CLAUDE.md**.

### 3. Commit
- Tự test changes trước khi push
- Chạy **subagent code reviewer** trước khi commit — "fresh pair of eyes" không mang bias của main agent sau cả session
- Nhờ Claude generate **commit message** theo style của bạn → lặp lại cycle

## Bài 6: Context Management (7′)

### Context window là gì?
- "Working memory" của Claude; mọi thứ chiếm chỗ: prompts, files Claude đọc, tool calls và kết quả của chúng

### Khi đầy thì sao?
- Gần limit → tự động **compact**: tóm tắt chi tiết quan trọng, bỏ tool call results không cần — *có thể mất chi tiết trong quá trình này*

### 3 lệnh quản lý

| Lệnh | Công dụng |
| :--- | :--- |
| `/compact` | Tóm tắt thủ công mọi thứ đến giờ → giải phóng chỗ, vẫn nhớ việc đã làm |
| `/clear` | Xóa sạch — hoàn toàn khởi động lại |
| `/context` | Xem kích thước context, các nhóm chiếm nhiều nhất, biểu đồ phân tích |

**Khi nào dùng gì:** `/compact` khi sắp đầy mà vẫn đang làm feature hiện tại · `/clear` trước khi bắt đầu feature mới (tránh old conversation làm lệch công việc mới).

> 💡 Cross-session knowledge → lưu vào **CLAUDE.md** để Claude không phải học lại mỗi lần.

### 3 cách tiết kiệm context
1. **Prompt cụ thể** — prompt mơ hồ phản tác dụng: Claude phải tự explore + suy luận, tốn context hơn prompt chi tiết
2. **Quản lý MCP servers** — mặc định servers chỉ load tên + instructions tool, chi tiết load theo nhu cầu; **tắt servers không liên quan** đến project hiện tại
3. **Dùng subagents** — chạy song song với **context window riêng**; VD hỏi *"authentication endpoints ở đâu?"* → subagent trả về đúng summary, main context sạch

## Bài 7: Code Review (10′)

> Summary sau task của Claude có thể che giấu edits từ nhỏ đến lớn. Session viết ra đoạn code *"không phải là thẩm phán chất lượng cao nhất"* cho chính nó.

### Xem thay đổi thực tế
- `/diff` — viewer tương tác của uncommitted changes; xem được **mỗi turn của Claude đổi gì**; phím mũi tên chuyển file, `Enter` mở
- ⚠️ Cần project là **git repo** (không thì nhờ Claude setup + commit trước; VCS khác thì `/diff`, `/code-review` không thấy changes, nhưng `/rewind` vẫn chạy vì Claude tự track edits của nó)

**Check mỗi lần:**
- Thay đổi **bạn không yêu cầu** (config bị edit, helper bị viết lại)
- **Tests yếu đi** — bị skip, delete, hoặc nới lỏng đến khi pass
- **Packages mới + giá trị hard-code** (dependency cho một hàm; URL/key viết cứng vào code)

- Nếu cả change sai hướng: **`/rewind`** (hoặc `Esc` ×2 trên prompt trống) → chọn prompt → **Restore code and conversation**. Giới hạn: files bị đổi bởi shell commands (như package installs) **không** được rollback.

### Xin ý kiến thứ hai
- Session dài mang toàn bộ history — điều reviewer không nên có. **`/code-review`** review trong **clean context**, *"không edit gì trừ khi bạn yêu cầu"*
- Chạy background (vài giây – vài phút); **tính vào usage** — dành cho changes xứng đáng scrutiny
- Prompt gợi ý: *"Review the changes you just made. Report problems; don't fix anything yet."*
- Effort levels: `/code-review low` (chỉ high-confidence, ít false alarm) · `/code-review high` (lưới rộng, cả findings kém chắc chắn) — level giữ nguyên đến khi đổi

### Xử lý từng finding — 3 nhóm
1. **Fix now** — vấn đề thật, quan trọng
2. **Ask why** — không verify được hoặc có vẻ sai (reviewer cũng có thể miss)
3. **Leave it** — thật nhưng nhỏ; gom cho session sau

- Challenge finding bằng cách quote lại: *"You reported that isValidEmail doesn't trim spaces, but line 4 calls trim(). Check again."*
- Yêu cầu evidence kèm fix: *"Fix the first finding: don't skip the empty-email test and restore the original assertion"* → chạy tests, hiện output
- Fix lớn hóa ra thành change lớn → chạy review lại lần nữa

### Khi nào cần review kỹ
- Change quá lớn để giữ trong đầu · chạm code nhạy cảm · làm việc destructive · trước khi bàn giao cho teammate
- One-line change: liếc diff là đủ

> ⚠️ Đây **không phải** "Claude Code Review" — product riêng của team (Owner bật trên GitHub repos, post findings lên pull requests) — xem Phần B.

## Bài 8: The CLAUDE.md file (10′)

### Vấn đề nó giải quyết
- Không có CLAUDE.md → Claude Code **bắt đầu fresh mỗi lần**: re-explore codebase, tìm dependencies, khám phá features; đôi khi **tự giả định sai** → khó steer
- Giải pháp: file Markdown tên `CLAUDE.md` ở **project root** — Claude Code đọc tự động mỗi session; như *"onboarding script cho codebase"*; nội dung được **append vào prompt** của bạn

### Ví dụ cấu trúc
```markdown
# Project
This is a Next.js 15 app using the App Router, Tailwind, and Drizzle ORM.

# Commands
- Dev server: `pnpm dev`
- Run tests: `pnpm test`
- Lint: `pnpm lint`

# Code Style
- Use 2-space indentation
- Prefer named exports
- All API routes go in app/api/
- Use server actions instead of API routes where possible
```
→ Nhờ viết React component, Claude đã tự dùng Tailwind + theo conventions của bạn.

### CLAUDE.md dành cho teams
- **Commit vào version control** để cả team hưởng
- Hierarchy: **Project-level** (project root, share cả team) · **User-level** (config folder, cá nhân, áp dụng cho mọi projects của bạn — hợp cho preferences riêng)

### 3 pro tips
1. **Save corrections to memory** — cứ phải sửa Claude cùng một điều (VD: luôn dùng server actions thay API routes)? Nhờ nó lưu rule đó vào memory — persists qua sessions
2. **Reference project docs** bằng ký hiệu `@` + path:
   ```markdown
   ## README.md
   Please read if you need more info: @README.md
   ```
3. **Start without one** — khởi động project *chưa có* CLAUDE.md để thấy mình hay course-correct ở đâu; nhờ Claude generate bằng **`/init`** khi cần. Giữ file **compact**, chỉ thông tin cần thiết

## Bài 9: Subagents (6′)

### Ý tưởng
- Claude **delegate** tasks cho subagents: bẻ task ra, chạy song song, cải thiện context management
- Mỗi subagent chạy trong **context window riêng, isolated**; xong việc trả về **summary** cho main thread — *"bạn có câu trả lời mà không phải cả hành trình tới nó"*

### Tạo subagent của riêng bạn
- Subagent = **Markdown file + YAML frontmatter**
- Dễ nhất: **nhờ Claude tạo** — mô tả subagent + nơi lưu. Prompt mẫu:
  > *"Create a code-reviewer subagent in .claude/agents/ that reviews code for bugs and readability. Make it read-only."*
- Vị trí: `.claude/agents/` (project hiện tại) · `~/.claude/agents/` (mọi projects của bạn)
- Folder chưa tồn tại lúc session bắt đầu → **restart Claude Code** để load subagent mới
- Claude tự sinh name, description, prompt — các thứ này cũng quyết định **khi nào** Claude invoke subagent theo prompt của bạn

### Tùy biến sâu
- **Persistent memory**: subagent giữ memory xuyên conversations — hợp khi dùng nhất quán trên cùng projects
- **Preloaded skills**: thêm key `skills`, liệt kê theo tên — khác skills trong conversation chính, **toàn bộ skill được load full** vào context subagent

→ Đào sâu: Phần C (khóa Introduction to subagents).

## Bài 10: Skills (3′)

### Skills là gì?
- **Markdown file dạy Claude một lần** — Claude tự áp dụng khi liên quan
- *"Folders of instructions, scripts, and resources that agents can discover and use"* để làm việc chính xác và hiệu quả hơn
- Động cơ: đỡ phải lặp lại giải thích coding standards, PR review formats, commit conventions mỗi lần

### SKILL.md hoạt động thế nào?
- Trong Claude Code, file skill là **`SKILL.md`**
- **Description chính là cơ chế trigger**: bạn yêu cầu (VD "review this PR") → Claude so với các skill descriptions → kích hoạt cái khớp
- Ban đầu **chỉ name + description được load** → không ăn hết context window; nội dung load **on demand** khi request khớp

### Skills sống ở đâu?
- **Personal**: `~/.claude/skills` — theo bạn Across mọi projects (commit style, doc format, giải thích code)
- **Project**: `.claude/skills` trong repo root — ai clone repo cũng có (team standards, brand guidelines, fonts/colors)

### Skills vs các hình thức tùy biến khác
- **CLAUDE.md**: load vào **mọi** conversation — hợp rules always-on (VD TypeScript strict mode)
- **Slash commands**: phải gõ tay
- **Skills**: **automatic + task-specific** — kích hoạt khi khớp

> Rule of thumb: *"If you find yourself explaining the same thing to Claude repeatedly — that's a skill waiting to be written."*

→ Đào sâu: Phần D (khóa Introduction to agent skills).

## Bài 11: MCP (6′)

### MCP là gì?
- **Model Context Protocol** — open standard cho Claude Code kết nối **tools và data sources ngoài**
- Insight then chốt: phần lớn context hữu ích nằm **ngoài codebase** (databases, productivity apps, public repos) — MCP bắc cầu nối này
- Claude **tự quyết định** khi nào dùng tool nào theo query của bạn

### Làm được gì?
- **Linear MCP server** (project management): pull chi tiết ticket cụ thể (VD truy vấn MEN-12)
- **Context7** (docs MCP server): documentation dependencies luôn mới (VD pull docs shadcn/ui mới nhất)

### Thêm MCP server
- Lệnh: **`claude mcp add`**
- 2 loại server: **HTTP** (remote, provider host, kết nối qua mạng) · **Stdio** (process local trên máy bạn, VD Python script)
- Quản lý: lệnh **`/mcp`** trong session — xem servers kết nối, status, **disable** server không cần

### Scoping servers — 3 phạm vi
1. **Local** — chỉ project hiện tại, chỉ bạn
2. **User** — mọi projects của bạn
3. **Project** — dùng file **`.mcp.json`** commit vào version control → *"ai trên codebase cũng có đúng các servers đó tự động"*

### Context costs (chi phí context)
- Mỗi server kết nối thêm tool names + instructions vào context window **kể cả khi idle**
- Chạy `/mcp` audit và **disable servers không dùng**
- **Ưu tiên CLI** nếu có tương đương (`gh` cho GitHub, `aws` cho AWS) — hiệu quả hơn context vì không register listing từng tool
- **Skills pairing**: kết hợp MCP server với Skill dạy Claude dùng tools của nó tốt — chỉ name + description của Skill ở trong context
- **Tool search**: bật mặc định — full MCP tool definitions chỉ vào context khi Claude cần

## Bài 12: Hooks (6′)

### Vì sao dùng hooks?
- Đặc tính định nghĩa: hooks **deterministic — luôn luôn chạy**
- Đối lập với instructions trong CLAUDE.md: nhờ Claude chạy Prettier sau edits *"works most of the time"* nhưng không đảm bảo — hook loại bỏ ngoại lệ
- Use cases: auto-format sau file edits · log mọi command (compliance) · **chặn thao tác nguy hiểm** (sửa production files) · notification khi Claude xong task

### Cách hoạt động
- Cấu hình trong **`settings.json`**: chọn **event** → thêm **matcher** (tool nào) → cung cấp **command**
- Events phổ biến: `PreToolUse` (trước tool call) · `PostToolUse` (sau khi hoàn tất) · `UserPromptSubmit` (khi submit prompt, trước Claude xử lý) · `Stop` (Claude trả lời xong) · `Notification`
- Lệnh **`/hooks`** trong Claude Code: xem danh sách read-only để xác nhận hook đã register

### Ví dụ thực tế: auto-format
- Hook **PostToolUse** với matcher **`"Edit|Write"`** — trigger sau khi Claude dùng Edit/Write
- Command kiểm tra extension file và chạy formatter đúng: Prettier cho TypeScript, gofmt cho Go...

### Chặn bằng PreToolUse
- Hook nhận tool name + input dạng **JSON trên stdin**
- Exit codes: **0** = tiến hành · **2** = **block** — stderr được feed lại Claude như feedback để nó hiểu lý do và điều chỉnh · **khác** = non-blocking error (hiện cho user)
- VD enforcement: chặn writes vào production config directory · chặn bash chứa `rm -rf` · chặn commits vào main
- Nguyên tắc: dùng hooks cho những gì phải **"guaranteed, not suggested"**

### Chia sẻ với team
- Hooks trong `.claude/settings.json` là project-level, **commit vào repo** → cả team kế thừa
- Dùng biến môi trường **`CLAUDE_PROJECT_DIR`** trong commands để tham chiếu project scripts — paths đúng bất kể cwd của Claude

> Chốt: *"If something needs to happen every time without fail, don't put it in a prompt. Put it in a hook."*

---

# PHẦN B — Docs tham chiếu

## B.1 — Code Review (product GitHub PRs)

> Trang docs được link từ Bài 7. Lưu ý: đây là **product riêng** "Code Review" (Team/Enterprise), khác lệnh `/code-review` chạy trong session.

### Tổng quan
- Claude review **pull requests** trong GitHub repositories: nhiều agents đọc từng change cùng code xung quanh, tìm **logic errors, security vulnerabilities, broken edge cases**; bước **verify** kiểm tra findings trước khi báo cáo
- Findings là **inline comments** trên các dòng liên quan, xếp theo severity, kèm summary + **check run** trên PR. Review **không approve/block PR** — quyết định merge thuộc team
- Availability: **Team và Enterprise**; GitHub (kể cả Enterprise Server/Cloud); không khả dụng với Zero Data Retention, HIPAA config, CMEK

### Review chạy thế nào — 4 stages (trên Anthropic infrastructure)
1. **Find** — nhiều agents xem diff + code xung quanh song song
2. **Verify** — kiểm candidate findings với code, lọc false positives
3. **Rank** — dedupe + xếp severity
4. **Post** — đăng kết quả lên PR

- Mặc định tập trung **correctness** (bugs phá production), không phải formatting hay test coverage; tùy chỉnh bằng files **`REVIEW.md`** + `CLAUDE.md` trong repo
- Trong review: repo access **read-only**, không push commits; review đọc diff chứ **không build/run code**
- Review level: **Quick** (nhẹ, rẻ nhất) · **Standard** (mặc định) · **Deep** (kỹ nhất, đắt nhất) — Owner chọn cho org, từng repo có thể khác
- Trigger: theo setting từng repo (PR mở / mỗi push / on request); comment **`@claude review`** để chủ động (người có write access)

### So sánh các cách review

| Option | Khởi phát | Chạy ở đâu | Ai dùng được |
| :--- | :--- | :--- | :--- |
| **Code Review** | PR activity hoặc `@claude review` | Anthropic infrastructure | Team/Enterprise + GitHub, Owner bật |
| **`/code-review`** | Bạn chạy trên branch | Claude Code session | Mọi người, mọi plan |
| **Ultrareview** | Khởi từ Claude Code | Cloud sandbox | Đăng nhập claude.ai |
| **CI của bạn** (GitHub Actions / GitLab CI/CD) | Pipeline events | CI runners của bạn | Ai có API key |
| **Tự viết** (subagent/skill) | Invoke trong session | Nơi bạn chạy Claude Code | Ai viết được |

## B.2 — Hooks reference (docs chi tiết — đã đọc trọn 284K ký tự)

> Trang docs được link từ Bài 12. Đây là tài liệu tham khảo đầy đủ của hooks system.

### Định nghĩa đầy đủ
- Hooks là **shell command, HTTP endpoint, MCP tool call, LLM prompt, hoặc subagent** do bạn định nghĩa, chạy **tự động** tại các điểm trong lifecycle Claude Code — chạy giống hệt across terminal, IDE, Desktop, cloud sessions
- 3 nhịp hoạt động: **per session** (`SessionStart`, `SessionEnd`) · **per turn** (`UserPromptSubmit`, `Stop`, `StopFailure`) · **per tool call** (`PreToolUse`, `PostToolUse` + Failure/Batch)

### Đầy đủ hook events
- **Session:** `SessionStart`, `SessionEnd`
- **Turn:** `UserPromptSubmit`, `UserPromptExpansion`, `Stop`, `StopFailure`, `MessageDisplay`
- **Tool call:** `PreToolUse` (block được), `PostToolUse`, `PostToolUseFailure`, `PostToolBatch`
- **Permissions:** `PermissionRequest`, `PermissionDenied`
- **Subagent/team:** `SubagentStart`, `SubagentStop`, `TeammateIdle`, `TaskCreated`, `TaskCompleted`
- **MCP:** `Elicitation`, `ElicitationResult`
- **Cấu hình/môi trường:** `InstructionsLoaded`, `ConfigChange`, `CwdChanged`, `DirectoryAdded`, `FileChanged`, `Setup`
- **Worktree:** `WorktreeCreate`, `WorktreeRemove`
- **Compact/model:** `PreCompact`, `PostCompact`, `PreModelSwitch` (block được), `PostModelSwitch`
- **Khác:** `Notification`

### Vị trí cấu hình (merge với nhau, không thay thế)

| Location | Scope | Share được? |
| :--- | :--- | :--- |
| `~/.claude/settings.json` | Mọi projects | Không |
| `.claude/settings.json` | Một project | Có (commit) |
| `.claude/settings.local.json` | Một project | Không (gitignore) |
| Managed policy settings | Toàn org | Admin quản (không tắt được bởi `disableAllHooks`) |
| Plugin `hooks/hooks.json` | Khi plugin bật | Theo plugin |
| Skill frontmatter | Phần còn lại của session sau khi invoke | Trong skill file (giới hạn: 1.024 hooks / 16.384 matcher chars mỗi skill) |
| Subagent frontmatter | Khi subagent đó chạy | Trong agent file |

### 5 handler types
1. **Command** (`type: "command"`) — JSON qua **stdin**; 2 dạng: **exec form** (có `args`, spawn trực tiếp không shell — an toàn nhất cho path placeholders) và **shell form** (không `args`, `sh -c`/Git Bash/PowerShell — hỗ trợ pipes, `&&`, globs). Windows: `.cmd`/`.bat` không chạy được exec form → dùng `node <script.js>`
2. **HTTP** (`type: "http"`) — POST JSON tới `url`; response body dùng cùng JSON output schema; `headers` hỗ trợ env var interpolation; có HTTP allowlists (`allowedHttpHookUrls`)
3. **MCP tool** (`type: "mcp_tool"`) — gọi tool của server (`server`, `tool`, `input` hỗ trợ `${tool_input.file_path}`); không chạy trên `SessionStart`/`Setup` lúc launch
4. **Prompt** (`type: "prompt"`) — LLM đánh giá single-turn (xem riêng bên dưới)
5. **Agent** (`type: "agent"`) — experimental; subagent có tools (Read/Grep/Glob) verify điều kiện (xem riêng)

- Field chung: `if` (permission-rule filter, VD `"Bash(git *)"`), `timeout` (mặc định 600s command/http/mcp_tool; 30s prompt; 60s agent), `statusMessage`, `once`
- Placeholders: `${CLAUDE_PROJECT_DIR}` (giữ nguyên trong worktrees), `${CLAUDE_PLUGIN_ROOT}`, `${CLAUDE_PLUGIN_DATA}`

### Matchers
- `"*"`/rỗng/bỏ trống = match tất cả · chỉ chữ/số/`_`/`-`/space/`,`/`|` = exact string hoặc list (`Bash`, `Edit|Write`) · ký tự khác = **unanchored JavaScript regex** (`^Notebook`, `mcp__memory__.*`)
- MCP tools hiện diện là `mcp__<server>__<tool>` — match cả server **phải** có hậu tố `.*` (chỉ `mcp__memory` là exact-match, không bao giờ chạy). Plugin servers: `mcp__plugin_<plugin>_<server>__<tool>`
- Mỗi event match một field khác nhau: tool events → `tool_name`; `SessionStart` → source; `SubagentStart/Stop` → agent type; `PreModelSwitch` → canonical model name...

### Input (JSON trên stdin / POST body)
- Fields chung: `session_id`, `prompt_id`, `transcript_path`, `cwd`, `scratchpad_dir`, `permission_mode` (`default`/`plan`/`acceptEdits`/`auto`/`dontAsk`/`bypassPermissions`), `hook_event_name`, `agent_id`/`agent_type` (subagents)
- Tool events thêm: `tool_name`, `tool_input`, `tool_use_id`. **Không** có biến `$CLAUDE_MODEL`

### Output — exit codes & JSON

| Stdout | Exit 0 | Exit 2 | Khác |
| :--- | :--- | :--- | :--- |
| JSON hợp lệ | Success, fields áp dụng | **Blocking** | Non-blocking; chỉ fields quyết định |
| JSON không parse được | Non-blocking error | Blocking; stderr là reason | Non-blocking error |
| Text thường / rỗng | Success | Blocking; stderr là reason | Non-blocking error |

- **Exit 2** = block; hiệu lực tùy event (chặn `PreToolUse`, `UserPromptSubmit`, `Stop`, `PreCompact`, `PreModelSwitch`...; bị bỏ qua trên `PermissionRequest`, `Setup`...). ⚠️ Policy enforcement phải dùng **exit 2**, không dùng exit 1
- JSON fields phổ biến: `continue: false` (dừng Claude hẳn — override mọi thứ), `stopReason`, `systemMessage`, `suppressOutput`, `terminalSequence` (OSC allowlisted cho desktop notifications)
- **`additionalContext`** (trong `hookSpecificOutput`): inject system-reminder vào context Claude — viết câu **trần thuật factual**, không phải mệnh lệnh (tránh prompt-injection defenses). Mọi string giới hạn **10.000 ký tự**
- **`onFailure: "block"`** (v2.1.295+): block action khi hook không start được / crash / timeout / output lỗi
- Background processes hook khởi động phải redirect stdout/stderr, không thì quyết định bị từ chối

### Quyết định theo từng nhóm event

| Events | Pattern | Fields chính |
| :--- | :--- | :--- |
| UserPromptSubmit, Stop, SubagentStop, Pre/PostToolUse, ConfigChange... | Top-level | `decision: "block"` + `reason` |
| **PreToolUse** | `hookSpecificOutput` | `permissionDecision` **allow/deny/ask/defer** (thứ tự ưu tiên deny > defer > ask > allow), `permissionDecisionReason`, `updatedInput` (**thay thế toàn bộ input**, được đánh giá lại theo rules) |
| PermissionRequest | `hookSpecificOutput` | `decision.behavior` (allow/deny), `updatedInput`, `updatedPermissions` (`addRules`/`setMode`/`addDirectories`...) |
| PermissionDenied | `hookSpecificOutput` | `retry: true` (thêm thông điệp "may retry", không đảo ngược denial) |
| PreModelSwitch | Cả hai | `permissionDecision` allow/deny/ask (không nhận defer/updatedInput) |
| Elicitation(+Result) | `hookSpecificOutput` | `action` accept/decline/cancel + `content` |
| MessageDisplay | `hookSpecificOutput` | `displayContent` (viết lại chỉ để hiển thị) |
| SessionStart | Context only | `additionalContext`, `initialUserMessage`, `sessionTitle`, `watchPaths`, `reloadSkills` |

### Deep-dive các event quan trọng

**SessionStart** — chạy nền lúc startup/`--continue`/`--resume`/`/clear`; `source`: `startup|resume|clear|compact|fork`. Khi resume/fork có phản hồi trước đó: nhận thêm `seconds_since_last_response`, `context_tokens`, `prompt_cache_likely_expired`, `estimated_cache_write_usd` (chi phí ước tính viết lại cache). `reloadSkills: true` rescan skills (hữu ích sau khi `git pull` skills repo của team).

**Setup** — chỉ chạy với `--init-only` hoặc `-p --init`/`--maintenance` (CI prep); không block được, mọi JSON output bị bỏ; chỉ hooks `command` chạy.

**UserPromptSubmit** — cũng fire trên scheduled tasks/`/loop`, background subagent reports. Slash commands đến **như đã gõ** (chưa expand) — muốn match theo tên command dùng `UserPromptExpansion`. Block: `decision: "block"` + `reason` + tùy chọn `suppressOriginalPrompt`.

**PreToolUse** — khớp mọi tool trừ `EndConversation`; **`@`-file mentions không fire** event này (dùng Read deny rules hoặc `CLAUDE_CODE_DISABLE_FILE_MENTIONS=1`). ⚠️ `file_path` của file-tools luôn **absolute với native separators** — Windows dùng backslash kể cả Git Bash → normalize (`${FILE_PATH//\\//}`) và match theo segment, đừng match `^/src/`. Tool input có `mcp_server: {name, source}` (v2.1.274+) — tin vào `source` (`plugin`, `user`, `project`...), không tin prefix `mcp__`. **Defer** (chỉ `-p` non-interactive): turn kết thúc với `stop_reason: "tool_deferred"`, resume bằng `claude -p --resume <id>`; chỉ hoạt động cho single tool call/turn.

**PermissionRequest** — chạy khi permission prompt sắp hiện (nhanh hơn `Notification` ~6s); cũng chạy trong session không prompt được (background subagents dưới `-p`) — không quyết định = auto-deny. Có thể trả về `updatedPermissions`: `addRules/replaceRules/removeRules` (`{rules, behavior, destination}`), `setMode` (default/auto/acceptEdits/dontAsk/bypassPermissions/plan), `addDirectories`; destinations: `session`, `localSettings`, `projectSettings`, `userSettings`.

**PostToolUse** — nhận `duration_ms` (không tính permission prompts); có thể `updatedToolOutput` (**phải đúng shape output của tool** — Bash `{stdout, stderr, interrupted, isImage}`; MCP output không validate), `classifierContext` (≤2.000 chars, v2.1.236+). Bash edit/diff recording (`bashEditDiffEnabled`): PostToolUse nhận `tool_response.bashEditDiff` với `changedFiles` (≤200), diffs (≤5 files).

**Stop / StopFailure** — Stop chạy khi Claude trả lời xong (interrupt của user không fire; API error → `StopFailure` với `error`: `rate_limit`, `overloaded`, `authentication_failed`...). Stop nhận `stop_hook_active` (kiểm tra để tránh vòng lặp vô hạn), `last_assistant_message`, `background_tasks` + `session_crons` (phân biệt "session xong" với "đang chờ background"). **Cap 8 lần continue liên tiếp** — sau 8 lần Claude Code buộc kết thúc turn (nâng bằng `CLAUDE_CODE_STOP_HOOK_BLOCK_CAP`). `decision: "block"` + `reason` buộc Claude tiếp tục; `additionalContext` = feedback không lỗi. Tip: lệnh `/goal` là shortcut cho session-scoped prompt-based Stop hook.

**TaskCreated / TaskCompleted** — TaskCreated block được (exit 2 → task bị xóa, message thành tool error; VD script ép subject có `[TICKET-123]`). TaskCompleted: chặn khi task không đạt tiêu chí (VD script chạy `npm test`, fail → exit 2 "Tests not passing..."); `continue: false` chỉ dừng teammate, bị bỏ qua khi TaskUpdate trigger.

**TeammateIdle** — teammate sắp idle; exit 2 = nhận feedback và tiếp tục làm; `continue: false` = dừng hẳn teammate.

**ConfigChange** — matcher theo source: `user_settings` / `project_settings` / `local_settings` / `policy_settings` / `skills`; block được (trừ `policy_settings` — enterprise policy luôn có hiệu lực).

**CwdChanged / FileChanged / DirectoryAdded** — CwdChanged: khi `cd` trong shell; có quyền truy cập `CLAUDE_ENV_FILE`; trả `watchPaths` cập nhật danh sách theo dõi. FileChanged: filesystem watcher (bắt mọi thay đổi — Edit/Write/Bash/process ngoài Claude Code); matcher vừa build watch list (split theo `|`, **không** dùng regex ở đây) vừa filter hooks chạy; trả được `watchPaths` động. DirectoryAdded: sau `/add-dir` hoặc SDK `register_repo_root`; chạy nền, không block được.

**WorktreeCreate / WorktreeRemove** — WorktreeCreate **thay thế hành vi mặc định** (`git worktree`) → cho dùng VCS khác (SVN, Perforce, Mercurial): hook checkout và **in ra path worktree** (dòng cuối stdout; HTTP hooks trả `worktreePath`); `.worktreeinclude` không được xử lý — copy `.env` thủ công trong hook. WorktreeRemove: exit 0 = coi như đã xóa (hook phải tự xóa directory); non-zero mà directory còn → removal fail, worktree ở lại.

**PreCompact / PostCompact** — matcher `manual` (`/compact`) / `auto` (auto-compact + idle compaction); PreCompact block được (block auto-compact chủ động = bỏ qua; block compact phục hồi lỗi = request hiện tại fail); PostCompact nhận `compact_summary`.

**PreModelSwitch / PostModelSwitch** (v2.1.251+) — Pre chạy cho `/model`, picker, fast mode, SDK `set_model`; **không** chạy với fallback tự động (những cái đó chỉ đến Post). Matcher so với **canonical name** (alias/dated ID/Bedrock ID đều về một tên; không xác định được canonical → chạy mọi hook). Input gồm field chi phí: `context_tokens`, `prompt_cache_warm`, `cache_ttl`, `estimated_cache_write_usd`, `pricing` — hook có thể hiện giá trước khi đổi model. Quyết định: `allow` (bỏ confirm), `deny` (hủy), `ask` (confirm — chỉ hiện trên `/model` interactive, nơi khác = refuse); ưu tiên deny > ask > allow. Timeout mặc định 30s — timeout = block switch. PostModelSwitch: không block; stdout/`additionalContext` được gửi cho Claude với request kế tiếp (hữu ích: guidance theo model, VD matcher `.*opus.*` → "delegate implementation to subagents").

**Elicitation / ElicitationResult** — khi MCP server yêu cầu user input: hook có thể **trả lời thay** (`action: accept` + `content` — keys theo `requested_schema.properties`), decline, cancel, hoặc bỏ qua (dialog hiện). URL-mode: accept = không mở URL. ElicitationResult: sửa giá trị user submit (VD thêm `@example.com`), block (`decline`), hoặc để nguyên — `content` **thay thế toàn bộ** object của user.

### CLAUDE_ENV_FILE (biến môi trường persistent)
- Có trên `SessionStart`, `Setup`, `CwdChanged`, `FileChanged`: hook ghi các dòng `export` vào file path này; **mọi Bash command sau đó execute nội dung file trước tiên**
- Dùng `>>` để không ghi đè biến của hooks khác; cleared ở `CwdChanged` kế tiếp
- **PowerShell** (v2.1.296+): file được *parse* chứ không source — mọi dòng phải là `export NAME=value` đơn giản; nếu không thì **không** biến nào được áp dụng

### Timeouts đáng nhớ
- 600s (command/http/mcp_tool mặc định) · **30s UserPromptSubmit** (timeout → hủy hook, output discarded, prompt vẫn đến Claude) · **10s MessageDisplay** · 30s PreModelSwitch · **SessionEnd: 1.5s** (nâng bằng per-hook `timeout` hoặc `CLAUDE_CODE_SESSIONEND_HOOKS_TIMEOUT_MS`, tối đa 60s)

### Prompt-based hooks (LLM đánh giá)
- Gửi hook input + prompt của bạn tới một model; LLM trả JSON quyết định; dùng `$ARGUMENTS` làm placeholder cho input JSON
- Response schema: `{ "ok": true|false, "reason": "...", "impossible": true|false }` — `impossible: true` (chỉ Stop/SubagentStop): Claude Code cho phép dừng thay vì quay vòng vô hạn
- Hành vi `ok: false` theo event: Stop/SubagentStop → reason thành instruction tiếp, Claude tiếp tục; PreToolUse → deny (mặc định kết thúc turn; `continueOnBlock: true` = trả reason như tool error để Claude điều chỉnh); PostToolUse → warning line hoặc feedback với `continueOnBlock`; PermissionRequest/PermissionDenied → không hiệu lực (dùng command hook)
- VD Stop hook kiểm 3 điều kiện: "1. All user-requested tasks complete 2. Errors need addressing 3. Follow-up needed → Respond {\"ok\": true} to allow..."

### Agent-based hooks (experimental)
- Như prompt hook nhưng subagent có **Read/Grep/Glob**, tối đa **50 turns**, timeout mặc định 60s; hữu ích khi verify cần đọc file/test output thật
- Không hỗ trợ `continueOnBlock` và `impossible`; `ok: false` xử lý như prompt hook với continueOnBlock: true

### Async hooks (chạy nền)
- `"async": true` (chỉ command hooks): Claude tiếp tục làm việc, không chờ; **không thể block** — `decision`/`permissionDecision`/`continue` vô hiệu vì action đã xong
- Output (`additionalContext`/`systemMessage`) delivered ở **turn kế tiếp**; session idle thì chờ user tương tác tiếp (ngoại lệ: `asyncRewake` exit 2 đánh thức Claude ngay)
- `-p` mode: async hooks còn chạy bị kill khi teardown (outcome `cancelled`) — việc phải sống lâu hơn session → spawn process detached hoàn toàn
- VD kinh điển: `PostToolUse` matcher `Write|Edit` chạy test suite nền, trả kết quả qua `additionalContext`

### Security
- ⚠️ Command hooks chạy với **đầy đủ quyền user của bạn** — review + test mọi hook command trước khi thêm vào config
- **Workspace trust:** interactive session giữ lại hooks (kể cả từ `~/.claude/settings.json`) tới khi bạn accept trust dialog; **`-p`/SDK session coi folder là trusted** → hooks commit trong `.claude/settings.json` của repo lạ vẫn chạy — review `.claude/` trước khi script `claude -p`, dùng `--bare`, hoặc `--settings '{"disableAllHooks": true}'`
- Best practices: validate input; **luôn quote** `"$VAR"`; chặn path traversal (`..`); dùng absolute paths; tránh đụng `.env`, `.git/`, keys

### Windows PowerShell
- `"shell": "powershell"` trên command hook (auto-detect `pwsh.exe`, fallback `powershell.exe`)
- Placeholder viết `${CLAUDE_PROJECT_DIR}` hoặc `$env:CLAUDE_PROJECT_DIR` — **không** viết bare `$CLAUDE_PROJECT_DIR` (PowerShell parse thành `$null`)

### Debug hooks
- `claude --debug-file <path>` hoặc `claude --debug` (log ở `~/.claude/debug/<session-id>.txt`)
- Tìm hook chậm: grep dòng `Hooks:` trong log — VD `Hooks: PostToolUse:Write [.claude/hooks/log-write.sh] finished with status 0 (31ms)`; các kết thúc khác: `timed out`, `cancelled`, `moved to the background`, `failed to start`
- `CLAUDE_CODE_DEBUG_LOG_LEVEL=verbose` → thêm chi tiết matcher counts

### Event × handler type (ai hỗ trợ gì)
- **Đủ 5 types**: PreToolUse, PostToolUse (+Failure/Batch), UserPromptSubmit (+Expansion), Stop, SubagentStop, TaskCreated/Completed, TeammateIdle, PermissionDenied
- **4 types** (không agent): PermissionRequest
- **3 types** (command/http/mcp_tool, không prompt/agent): ConfigChange, CwdChanged, DirectoryAdded, Elicitation(+Result), FileChanged, InstructionsLoaded, MessageDisplay, Notification, PostCompact, PostModelSwitch, PreCompact, PreModelSwitch, SessionEnd, StopFailure, SubagentStart, Worktree*
- **Chỉ command + mcp_tool**: SessionStart, Setup

### Ví dụ: chặn `rm -rf`
```json
{
  "hooks": {
    "PreToolUse": [{
      "matcher": "Bash",
      "hooks": [{
        "type": "command",
        "if": "Bash(rm *)",
        "command": "${CLAUDE_PROJECT_DIR}/.claude/hooks/block-rm.sh"
      }]
    }]
  }
}
```
Script đọc JSON stdin, grep `rm -rf` → trả JSON `permissionDecision: "deny"` + reason; ngược lại `exit 0`.

## B.3 — `/code-review` local (docs đầy đủ của lệnh trong Bài 7)

> Trang docs: [code.claude.com/docs/en/code-review-local](https://code.claude.com/docs/en/code-review-local). `/review` là alias. Chạy được trên **mọi plan**; tính vào usage như phần còn lại của session.

### Cách chạy & targets
Không có target → review commits của branch hiện tại (so với upstream; không có upstream thì so `main`) + uncommitted changes:

| Muốn review | Gõ |
| :--- | :--- |
| Branch hiện tại + uncommitted | `/code-review` |
| 15 commits cuối | `/code-review HEAD~15..HEAD` |
| Branch này so branch kia | `/code-review main...my-feature` |
| Một commit `abc1234` | `/code-review abc1234^..abc1234` |
| Pull request theo số | `/code-review 1234` |
| File/thư mục | `/code-review src/auth` |

### Flags
- **`--fix`**: sau review, Claude **áp dụng các findings** vào working tree (edits qua permission mode như thường)
- **`--comment`**: post findings lên GitHub PR dạng **inline comments**, hoặc GitLab merge request dạng single note (qua `glab` CLI — thiếu CLI thì in ra terminal; GitLab self-managed phải truyền URL hoặc `!123`)
- **`--post`** (v2.1.227+): với `ultra` review PR github.com, preselect post findings lên PR
- **`--max-findings <n>|all|default`** (v2.1.288+): giới hạn số findings (findings tool limit 32); nhớ giá trị tới khi truyền `default`
- **Effort level** (`low` → `max`): `low` = chỉ findings tự tin cao (ít false positives); `medium`→`max` mở rộng coverage. Không gõ level → **dùng level lần gõ trước** (kể cả session trước — có notice "Reusing high effort..."); `-p` run không cập nhật level nhớ; `ultra` không dùng cũng không cập nhật

### Cơ chế & lưu ý quan trọng
- Review chạy là **background subagent với context window riêng** → không đầy conversation; findings về tới nơi trong hội thoại
- **/rewind caveat**: `--fix` chạy nền edit **ngoài checkpoints của session** — `/rewind` chỉ restore files Claude đã edit trong conversation; edits của review phải revert bằng git. Review chạy foreground (chạy lại `/code-review` khi đang có review, hoặc `-p`) thì `/rewind` hoạt động bình thường
- Đọc **`CLAUDE.md`** của bạn (kể cả `-p` run); **không đọc `REVIEW.md`** (file đó chỉ configure Code Review product trên GitHub)
- Trong desktop app: findings qua `ReportFindings` tool — list có file location, summary 1 câu, category tag (VD `correctness`); khi Claude fix sau đó, findings được đánh dấu fixed/skipped/no_change_needed
- **Claude tự start được review** khi bạn nhờ bằng lời thường, hoặc qua scheduled task; chặn điều này (giữ lệnh cho người gõ): `skillOverrides: {"code-review": "user-invocable-only"}` trong settings
- Foreground: chạy trong `-p`/SDK, hoặc `CLAUDE_CODE_DISABLE_BACKGROUND_TASKS=1`

### Escalate lên ultrareview
- `/code-review ultra --fix` → chạy **ultrareview** (cloud sandbox), findings về session rồi Claude apply
- Scope: branch hiện tại so default branch + uncommitted/staged; file nhạy cảm (`.env`, `*.tfvars`) theo quy tắc upload local repo lên cloud
- **Yêu cầu đăng nhập claude.ai** — không có trên Bedrock/Vertex/Foundry, Zero Data Retention, HIPAA, CMEK (những trường hợp đó `ultra` chạy local thay thế)
- CI/script: `claude ultrareview` subcommand chờ findings và in ra stdout

### Thay thế / mở rộng
- `/code-review` là **bundled skill** (không có SKILL.md trên đĩa) — muốn rule riêng cho mọi review → thêm vào `CLAUDE.md`
- **Thay lệnh**: skill cá nhân/project đặt tên `code-review` chạy thay bundled (alias `/review` vẫn chạy bản bundled)
- Lệnh láng giềng: **`/simplify`** (chỉ review cleanup + auto-fix; trước v2.1.147 từng là tên của /code-review) · **`/verify`** (chạy app xác nhận change hoạt động)

---

# PHẦN C — Introduction to subagents (4 bài, 45′)

## C.1 — What are subagents? (5′)
- Subagents = *"specialized assistants that Claude Code can delegate tasks to"* — mỗi cái chạy trong **conversation context window riêng**, trả **summary** cho main thread; các bước trung gian (file reads, searches, tool calls) bị **isolated**
- **Vì sao cần:** mọi tương tác tích lũy trong main context window; đầy → Claude *"mất dấu các phần trước của conversation"*. Subagent sinh context riêng với 2 input: (1) **custom system prompt** từ config file, (2) **task description** do parent agent viết theo request của bạn
- Phần còn lại của conversation subagent lưu trong **transcript file riêng**; tradeoff: main không thấy subagent kết luận bằng cách nào
- **Ví dụ thực tế** — tìm service xử lý refunds trong codebase lạ: không subagent → Claude đọc ~15 files, nhiều searches, trace calls — tất cả đầy context window cho **một fact**; có subagent (Explore) → việc đào nằm trong context của nó, main chỉ giữ câu hỏi + câu trả lời
- **Built-in subagents:**

| Subagent | Mục đích |
| :--- | :--- |
| **General purpose** | Task đa bước, cần cả exploration lẫn action |
| **Explore** | Search nhanh + điều hướng codebase |
| **Plan** | Dùng trong plan mode để research/analysis trước khi đưa plan |

- 3 lợi ích: **Focus** (bẻ việc, mỗi subagent một việc) · **Clean context** (isolated intermediate work) · **Concise output** (chỉ trả thông tin cần)

## C.2 — Creating a subagent (10′)
- Cách dễ nhất: **nhờ Claude viết file subagent** — mô tả agent + nơi lưu (wizard `/agents` đã bị xóa từ v2.1.198 nhưng format không đổi)
- **Scope:** `.claude/agents/` (project) · `~/.claude/agents/` (mọi projects trên máy)
- **Tùy chỉnh tools theo nhóm:** Read-only / Edit / Execution / MCP / Other — khớp tools với mục đích (code reviewer **không nên có** edit tools; giữ execution tools để thấy pending changes)
- **Chọn model:** Haiku (nhanh, nhẹ) · Sonnet (cân bằng) · Opus (phân tích phức tạp) · **Inherit** (theo main conversation) · **Color** nhận diện trong UI khi chạy nhiều subagents
- Field `model` nhận: alias (`sonnet`, `opus`, `haiku`, `fable`), **full model ID** (VD `claude-sonnet-5`), hoặc `inherit`; `description` bắt buộc **một dòng duy nhất** (dùng `\n` nếu cần xuống dòng)

**Config mẫu:**
```markdown
---
name: code-quality-reviewer
description: Use this agent when you need to review recently written or modified code for quality, security, and best practice compliance.
tools: Bash, Glob, Grep, Read, WebFetch, WebSearch
model: sonnet
color: purple
---

You are an expert code reviewer specializing in quality assurance, security best
practices, and adherence to project standards...
```

- **Fields:** `name` (tham chiếu bằng `@agent-name`) · `description` — quyết định **khi nào** Claude delegate, phải 1 dòng; thêm **"proactively"** để auto-delegation; thêm **example conversations** vào description để Claude delegate chuẩn hơn · `tools` · `model` · `color`
- Body markdown dưới frontmatter = **system prompt** — chất lượng prompt quyết định độ hữu ích
- **Testing:** restart nếu folder `agents` mới tạo; delegation không trigger → refine description với trigger scenarios cụ thể hơn

## C.3 — Designing effective subagents (10′)

### Config data được dùng thế nào
- **Name + description của mọi subagent được inject vào system prompt của main agent** → quyết định subagent nào chạy, khi nào
- Vai trò thứ hai: description còn **định hình input prompt** main agent viết cho subagent — *"doesn't just control when a subagent runs — it shapes what the subagent is told to do"*

### Viết description định hình input prompt
- Bad: description generic → prompt mơ hồ *"use git diff to find the current changes"* → subagent phải đoán file nào quan trọng
- Fix: thêm guidance vào description — *"You must tell the agent precisely which files you want it to review"* → main agent liệt kê files thật khi delegate

### Định nghĩa output format — *"cải thiện quan trọng nhất"*
1. **Natural stopping points** — subagent biết xong khi đủ các section
2. **Chặn overlong runs** — không có output định nghĩa, subagent không biết research bao nhiêu là đủ

VD template code review 6 sections: Summary · Critical Issues · Major Issues · Minor Issues · Recommendations · **Approval Status** (quyết định merge/deploy rõ ràng)

### Báo cáo obstacles
- Workarounds phát hiện giữa chừng (fix dependency, flag đặc biệt) **phải xuất hiện trong summary** — không thì main thread tốn thời gian + tokens khám phá lại
- Cần surface: setup/env quirks · workarounds · commands cần flags đặc biệt · dependencies/imports rắc rối → thêm section **"Obstacles Encountered"** vào template

### Giới hạn tool access

| Loại subagent | Tools | Lý do |
| :--- | :--- | :--- |
| Research / read-only | `Glob`, `Grep`, `Read` | Không thể sửa file nhầm |
| Code reviewer | `Bash` (cho `git diff`), **không** `Edit`/`Write` | Thấy changes mà không edit |
| Styling / sửa code | `Edit`, `Write` | Việc của nó là đổi code |

> Chốt: 4 đặc tính — description cụ thể + output có cấu trúc + obstacle reporting + tool giới hạn = subagent từ *"vaguely tries to help"* thành *"focused, predictable worker that finishes on time and reports back clearly"*.

## C.4 — Using subagents effectively (10′)
> Câu hỏi trung tâm: **"intermediate work có quan trọng với main thread của bạn không?"**

### Khi subagents tỏa sáng
- Cần **kết quả**, không cần tường thuật từng bước
- Exploratory work làm bẩn main context
- Task hưởng lợi từ **fresh perspective** hoặc custom system prompt
- **Research là classic use case:** tìm JWT validation trong codebase lạ → subagent đọc nhiều files, trace calls — main nhận summary sạch (*"middleware/auth.js line 42, gọi từ Express router trong route/api.js"*)
- **Code reviews:** Claude review code chính nó viết trong cùng thread thì feedback yếu; reviewer subagent thấy changes trong context riêng + encode team review standards trong system prompt để **tiêu chuẩn nhất quán toàn team**
- **Custom system prompts** thật sự cải thiện: copywriting (tone/audience/style — default prompt quá technical); styling (đọc design system files trước khi viết CSS)

### Khi subagents phản tác dụng — 3 anti-patterns
1. **Expert claims** — persona kiểu *"you are a Python expert"* vô giá trị; Claude đã có knowledge đó, main thread tự làm được
2. **Sequential pipelines** — chuỗi reproduce → debug → fix thất bại vì các bước phụ thuộc phát hiện trước đó; *"information gets lost in the handoff"*
3. **Test runners** — ẩn thông tin cần thiết; chỉ trả *"tests failed"* buộc thêm debug scripts để lấy output vốn hiện trực tiếp — *"performed worst among all configurations"*

### Bảng quyết định

| Dùng subagent cho | Tránh subagent cho |
| :--- | :--- |
| Research và exploration | "Expert" personas không thêm năng lực thật |
| Code reviews | Pipelines nhiều bước phụ thuộc nhau |
| Task cần custom system prompt | Chạy tests cần full output để debug |

---

# PHẦN D — Introduction to agent skills (6 bài, ~1h)

## D.1 — What are skills? (9′)
- Skills = **reusable markdown files** dạy Claude Code xử lý task cụ thể **tự động** — viết một lần, Claude áp dụng khi task xuất hiện
- Mỗi skill nằm trong file **`SKILL.md`** với **name + description** trong frontmatter; **matching dựa trên description** (Claude so request với các descriptions, kích hoạt cái khớp)
- **On-demand loading:** khác CLAUDE.md (luôn trong context) và slash commands (gõ tay), skills **tự kích hoạt khi liên quan** — ban đầu chỉ name + description trong context

| Loại | Vị trí | Scope |
| :--- | :--- | :--- |
| Personal | `~/.claude/skills` | Theo bạn mọi projects — commit style, doc format |
| Project | `.claude/skills` (repo root) | Ai clone repo cũng có — team standards, brand guidelines |

- Frontmatter mẫu:
  ```yaml
  ---
  name: pr-review
  description: Reviews pull requests for code quality. Use when reviewing PRs or checking code changes.
  ---
  ```
- Use cases: team code review standards · commit message formats · brand guidelines · documentation templates · framework debugging checklists

## D.2 — Creating your first skill (10′)
**VD skill `pr-description` (personal):**
```bash
mkdir -p ~/.claude/skills/pr-description
```
```markdown
---
name: pr-description
description: Writes pull request descriptions. Use when creating a PR, writing a PR, or when the user asks to summarize changes for a pull request.
---

When writing a PR description:
1. Run `git diff main...HEAD` to see all changes on this branch
2. Write a description following this format:

## What
One sentence explaining what this PR does.

## Why
Brief context on why this change is needed

## Changes
- Bullet points of specific changes made
```

- **Test:** Claude Code watch skills directories — skill mới dùng được **không cần restart**; nếu `~/.claude/skills` chưa tồn tại lúc đầu session → chạy `/reload-skills`. Test prompt: *"write a PR description for my changes"*
- **Matching:** startup load names + descriptions → so **semantic** (VD "explain this function" khớp skill "explain code with visual diagrams") → khớp thì đọc full SKILL.md; skills đơn giản auto-load (v2.1.19 bỏ approval step)
- **Priority khi trùng tên:** **Enterprise → Personal → Project** (org enforce standards, cá nhân vẫn customize); plugin skills đứng ngoài — namespaced `/plugin-name:skill-name`, cả hai cùng load
- Best practice: tên descriptive (`frontend-review`, `backend-review`) thay vì generic (`review`)
- **Update:** sửa SKILL.md · **Remove:** xóa directory — có hiệu lực ngay session hiện tại

## D.3 — Configuration and multi-file skills (10′)

### Metadata fields

| Field | Trạng thái | Ghi chú |
| :--- | :--- | :--- |
| `name` | Optional | Mặc định theo tên directory; lowercase/số/gạch ngang, ≤64 chars |
| `description` | **Recommended** | Quan trọng nhất — dùng để matching; ≤1.024 chars trên Claude.ai/API |
| `allowed-tools` | Optional | **Pre-approve** các tools liệt kê khi skill active — KHÔNG chặn tools khác |
| `model` | Optional | Chọn model cho skill |

### Viết description hiệu quả
- Trả lời 2 câu hỏi: skill làm **gì** + dùng **khi nào**
- Trigger không ổn định → thêm keywords trùng cách bạn hay diễn đạt request

### `allowed-tools` — cẩn thận
- `Bash` trần approve shell commands quá rộng → dùng pattern hẹp: `Bash(git status *)`
- Field bổ trợ `disallowed-tools`: gỡ tools khi skill active

### Progressive disclosure (tiết lộ dần)
- SKILL.md giữ **dưới 500 dòng**; dài hơn thì tách theo cấu trúc open standard:
  - `scripts/` — code chạy được · `references/` — tài liệu bổ sung · `assets/` — images, templates, data
- Link sang files phụ kèm chỉ dẫn rõ **khi nào** đọc (VD: đọc `architecture-guide.md` chỉ khi hỏi system-design)
- **Scripts hiệu quả:** code script KHÔNG vào context — chỉ **output** tốn tokens; instructed Claude *chạy* script chứ không đọc script

## D.4 — Skills vs. other Claude Code features (6′)

| So với | Phân biệt | Skills hợp cho |
| :--- | :--- | :--- |
| **CLAUDE.md** | CLAUDE.md load **mọi** conversation (TypeScript strict mode); skills load **on demand** | Knowledge task-specific, thỉnh thoảng mới dùng — PR checklist không cần nằm trong context khi đang code |
| **Subagents** | Subagents nhận task, làm việc **context riêng độc lập**, trả kết quả; skills làm giàu conversation **hiện tại** | Nâng knowledge cho task trước mắt, áp dụng xuyên suốt conversation |
| **Hooks** | Hooks **event-driven** (mỗi lần save, trước tool call); skills **request-driven** | Knowledge định hình cách xử lý request; hooks cho side effects tự động |
| **MCP servers** | Cung cấp **external tools/integrations** — category khác hẳn | — |

> Setup điển hình kết hợp tất cả: **CLAUDE.md** = standards always-on · **Skills** = expertise on-demand · **Hooks** = thao tác event-triggered · **Subagents** = delegated work isolated · **MCP** = external tools. Đừng ép mọi thứ vào skills khi feature khác hợp hơn.

## D.5 — Sharing skills (15′)

### 3 cách phân phối
1. **Git repository** — skills trong `.claude/skills` + commit → ai clone repo tự có, không cần install; updates propagate qua pull. Hợp: team coding standards, workflows gắn với codebase
2. **Plugins + marketplaces** — trong plugin project, tạo directory `skills/` mirror cấu trúc `.claude`; publish lên marketplace để cộng đồng discover + install. Hợp: skills không gắn project cụ thể
3. **Enterprise managed settings** — admins deploy org-wide (skills vào `.claude/skills/` của managed settings dir, VD `/etc/claude-code/.claude/skills/`); **priority cao nhất** (override personal/project cùng tên); kiểm cả marketplaces qua `strictKnownMarketplaces`:
   ```json
   "strictKnownMarketplaces": [
     { "source": "github", "repo": "acme-corp/approved-plugins" },
     { "source": "url", "url": "https://plugins.example.com/marketplace.json" }
   ]
   ```
   Hợp: standards bắt buộc, security, compliance

### Skills & subagents — gotcha quan trọng
- Subagents **KHÔNG inherit** skills bạn đã invoke trong main (context fresh, sạch) — trừ **fork** (copy conversation)
- Subagent có **Skill tool** thì vẫn tự find + invoke skills
- Built-in agents (Explore, Plan) **không preload skills**; chỉ **custom subagents** preload qua field `skills` — và preload là load **FULL lúc startup** (không on-demand như main):

```yaml
---
name: frontend-security-accessibility-reviewer
description: "Use this agent when you need to review frontend code for accessibility..."
tools: Bash, Glob, Grep, Read, WebFetch, WebSearch, Skill
model: sonnet
skills: accessibility-audit, performance-check
---
```
- Pattern hợp: delegation cần expertise riêng; các subagent khác nhau cần skills khác (frontend vs backend reviewer); enforce standards không phụ thuộc prompt

## D.6 — Troubleshooting skills (8′)

### Chạy validator trước tiên (v2.1.233+)
```bash
claude plugin validate ~/.claude/skills   # personal
claude plugin validate .claude/skills     # project
```
→ Bắt lỗi frontmatter không parse được trước khi debug gì khác.

### Bảng triệu chứng → fix

| Triệu chứng | Nguyên nhân | Fix |
| :--- | :--- | :--- |
| **Không trigger** | Description problem (gần như luôn) | So description với cách bạn thật sự diễn đạt; thêm trigger phrases; test các biến thể ("help me profile this", "why is this slow?") rồi thêm keywords cho biến thể fail |
| **Không load** | Sai cấu trúc | `SKILL.md` phải nằm trong **named directory** (không nằm trực tiếp ở skills root); tên file đúng chính xác `SKILL.md`; chạy `claude --debug` để tìm message naming skill của bạn |
| **Chọn nhầm skill** | Descriptions quá giống nhau | Viết description phân biệt, cụ thể |
| **Bị shadow** | Priority conflict | Enterprise shadow personal cùng tên → rename cho khác biệt hơn, hoặc hỏi admin |
| **Plugin skills thiếu** | Install/loading | `/plugin` → tab Installed + **Errors**; vừa cài thì `/reload-plugins`; skills phải ở `skills/` **plugin root** (không trong `.claude-plugin/`) |
| **Runtime errors** | Môi trường | Dependencies phải installed (**document chúng trong description** để Claude biết); scripts cần `chmod +x`; paths dùng **forward slashes** kể cả Windows |

> Lời khuyên chốt của khóa: *"The best skills address real pain points — start with the instructions you find yourself repeating most often."*

---

# Phụ lục: Tổng hợp nguồn đã quét

| Nhóm | URLs |
| :--- | :--- |
| **Khóa chính** | `/courses/claude-code-101/` — what-is-claude-code · how-claude-code-works · installing-claude-code · your-first-prompt · the-explore-plan-code-commit-workflow · context-management · code-review · the-claude-md-file · subagents · skills · mcp · hooks |
| **Docs** | [code-review](https://code.claude.com/docs/en/code-review) (landing, đầy đủ tổng quan) · [code-review-local](https://code.claude.com/docs/en/code-review-local) (`/code-review` command — mục B.3) · [hooks](https://code.claude.com/docs/en/hooks) (**đọc trọn 284K ký tự, 3 chunk** — mục B.2) |
| **Khóa con 1** | `/courses/introduction-to-subagents/` — what-are-subagents · creating-a-subagent · designing-effective-subagents · using-subagents-effectively |
| **Khóa con 2** | `/courses/introduction-to-agent-skills/` — what-are-skills · creating-your-first-skill · configuration-and-multi-file-skills · skills-vs-other-claude-code-features · sharing-skills · troubleshooting-skills |
| **Được nhắc trong docs** (tham chiếu thêm, ngoài phạm vi khóa học) | `code.claude.com/docs/en/` — code-review-setup · code-review-customize · code-review-pull-requests · code-review-costs · code-review-troubleshooting · ultrareview · hooks-guide · skills · sub-agents · permissions · settings-reference |

> ℹ️ **YouTube:** không có YouTube link nào xuất hiện trong nội dung 22 bài đã quét — các video trong bài là embed nội bộ của Academy (không có URL công khai riêng).
>
> ✅ **Độ phủ:** 22/22 bài Academy đã được đối chiếu với **HTML gốc** (prerendered) — Phần A, C, D phản ánh trọn nội dung từng trang. 2 trang docs reference (hooks + code-review-local) đọc trọn. 6 trang docs con của Code Review product (setup/customize/costs...) là tài liệu vận hành admin, ngoài phạm vi khóa học — tổng quan đã có ở B.1.
