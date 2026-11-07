# Khóa học Claude Code in Action — Tóm tắt chi tiết

> **Nguồn:** Claude Academy — *Claude Code in action* (9 bài học + Course quiz + Completion badge, tổng ~55 phút)
> **URL gốc:** `https://academy.claude.com/courses/claude-code-in-action` (các bài tại `.../lessons/<slug>`)
> **Ngày tóm tắt:** 2026-11-07
> **Phạm vi quét:** Full raw text 9/9 bài học.
> Đã rà soát sub-links bằng 2 lượt grep (kể cả pattern nhận diện URL escape JSON `https:\/\/`)
> — khóa học **không chứa link tài liệu/YouTube/GitHub nào** ngoài footer legal, nội dung tự chứa hoàn toàn.

## Mục lục

- [Tổng quan khóa học](#tổng-quan-khóa-học)
- [Phần 1 — Steer the work](#phần-1--steer-the-work)
  - [Bài 1: Steering long sessions](#bài-1-steering-long-sessions)
- [Phần 2 — Configure Claude](#phần-2--configure-claude)
  - [Bài 2: A CLAUDE.md that follows](#bài-2-a-claudemd-that-follows)
  - [Bài 3: Verification skills](#bài-3-verification-skills)
  - [Bài 4: Permission modes](#bài-4-permission-modes)
  - [Bài 5: Hooks](#bài-5-hooks)
- [Phần 3 — Automate repeat work](#phần-3--automate-repeat-work)
  - [Bài 6: Scheduled tasks and headless](#bài-6-scheduled-tasks-and-headless)
  - [Bài 7: GitHub Actions and Code Review](#bài-7-github-actions-and-code-review)
- [Phần 4 — Verify and share](#phần-4--verify-and-share)
  - [Bài 8: Trust it — Verifying unsupervised runs](#bài-8-trust-it--verifying-unsupervised-runs)
  - [Bài 9: Plugins](#bài-9-plugins)
- [Tổng kết toàn khóa](#tổng-kết-toàn-khóa)

---

## Tổng quan khóa học

Khóa học thực chiến về việc **dùng Claude Code trong dự án thật**:

- Điều khiển session dài.
- Cấu hình CLAUDE.md/skills/permission modes/hooks.
- Tự động hóa công việc lặp lại (scheduled tasks, headless, GitHub Actions).
- Xác minh kết quả chạy không giám sát.
- Đóng gói chia sẻ setup qua plugins.

Cấu trúc 4 nhóm bài theo sidebar của khóa:

| Nhóm | Bài | Thời lượng |
|---|---|---|
| Steer the work | 1. Steering long sessions | 6 min |
| Configure Claude | 2. A CLAUDE.md that follows · 3. Verification skills · 4. Permission modes · 5. Hooks | 7 + 5 + 5 + 7 min |
| Automate repeat work | 6. Scheduled tasks and headless · 7. GitHub Actions and Code Review | 7 + 6 min |
| Verify and share | 8. Trust it: Verifying unsupervised runs · 9. Plugins | 5 + 7 min |

---

## Phần 1 — Steer the work

### Bài 1: Steering long sessions

*(Lesson 1 of 9 · 6 min · slug: `steering-long-sessions`)*

**Vấn đề:** Prompt Claude làm task nhanh thì dễ — bạn hỏi, nó làm, bạn kiểm tra.

Nhưng task dài (refactor chục file, build feature mới mất nhiều giờ) là chuyện khác: càng phải "lái" Claude nhiều giữa chừng, việc càng kéo dài.

**Nguyên tắc cốt lõi — 2 thói quen:** (1) xác định phạm vi công việc **trước khi** Claude bắt đầu; (2) lái nó **trong lúc** nó chạy.

#### Scope the work first with plan mode

- Trước khi Claude viết dòng nào, cho nó lập plan. Ở **plan mode**, Claude research mà **không sửa** source files — đọc code, xác định cái gì cần đổi, đưa plan cho bạn review.
- Khi nhận plan: **đọc thật**, đừng lướt.
  - Plan càng kỹ càng ít surprise khi chạy.
  - Thiếu sót gì thì yêu cầu Claude bổ sung ngay — **iterate trên plan nhanh hơn** nhiều so với để Claude chạy rồi dọn dệp đống mess.

#### Steer while Claude works — Compact

- **`/compact`** tóm tắt conversation, dùng summary đó làm context mới và xóa messages cũ → giải phóng context window để Claude chạy tiếp.
- **Rủi ro:** thứ quan trọng bị rơi khỏi summary → Claude lạc hướng (drift).
- **Đừng chạy `/compact` trơn** — thêm instruction sau lệnh để chỉ dẫn cách tóm tắt. Ví dụ đã xong debug từ lâu, giờ chỉ quan tâm API changes:

```
/compact Focus on the --version flag implementation
```

- Mọi thứ viết sau lệnh sẽ định hình summary giữ lại gì — đó là **vô lăng điều khiển context** của bạn.

#### Rewind

- Khi Claude đi sai hướng, không cần prompt để kéo lại. **Rewind** đưa bạn về checkpoint gần nhất — **mỗi user prompt tạo một checkpoint** có thể revert.
- Mở menu: **double-tap Escape** trên prompt trống. Các tùy chọn:
  - **Restore code and conversation** — rollback cả hai cùng lúc.
  - **Restore conversation** — chỉ rollback chat.
  - **Restore code** — chỉ rollback files.
  - **Summarize from here** — tóm tắt mọi thứ *sau* checkpoint (hữu ích khi có side conversation, muốn giải phóng không gian).
  - **Summarize up to here** — tóm tắt mọi thứ *trước* checkpoint (hữu ích khi phase setup dài muốn nén lại nhưng giữ nguyên phần implementation).

#### Let Claude run more autonomously — Goal

- **`/goal`** đặt điều kiện hoàn thành: bạn mô tả "done" trông thế nào,
  Claude làm việc qua nhiều turn cho đến khi một **fast evaluator** xác nhận điều kiện đạt — nó không dừng chỉ vì *nghĩ* là xong. Ví dụ:

```
/goal all tests in src/billing pass, and the type checker reports zero errors
```

- Hủy: `/goal clear`.
- **Ràng buộc quan trọng:** evaluator chỉ đọc transcript → điều kiện phải **check được từ output Claude thực sự tạo ra** (như kết quả chạy test).

#### Loop

- **`/loop`** chạy một prompt theo interval giữa các turn — cố định hoặc tự phân nhịp (self-paced). Dùng để poll thứ bên ngoài (CI run, deploy) và hành động khi state đổi.
- Dừng loop self-paced đang chờ lượt chạy kế: nhấn **Escape**. Loop theo interval cố định chạy đến khi bạn yêu cầu hủy hoặc **7 ngày** trôi qua.

#### Run parallel work with worktrees

- Ẩn dụ: nhiều agents trên cùng codebase = nhiều vô lăng trong một xe → không an toàn, hai session Claude giành cùng file dẫn đến conflict.
- **Worktrees:** mỗi session có **file tree độc lập riêng** → không ai đè thay đổi của ai. Session thoát mà worktree sạch thì **tự động bị xóa**.
- File cần biết: **`.worktreeinclude`** đặt ở repo root — liệt kê các git-ignored files cần copy vào mỗi worktree (ví dụ file env variables hay local config cần ở mọi worktree nhưng không muốn commit).

#### Putting it together (tóm tắt bài)

1. Scope work trước, rồi steer.
2. Direct compaction để summary giữ thứ quan trọng.
3. Dùng rewind menu để hiệu chỉnh khi Claude drift.
4. Đặt goal khi mô tả được "done" tốt hơn mô tả các bước.
5. Chạy song song trong worktrees.

→ Làm vậy thì tin được một long run mà không phải trông nom từng bước.

---

## Phần 2 — Configure Claude

### Bài 2: A CLAUDE.md that follows

*(Lesson 2 of 9 · 7 min · slug: `a-claude-md-that-follows`)*

**Cái bẫy ai cũng dính:** CLAUDE.md cứ dài ra — gặp vấn đề thì thêm rule, lại gặp thì thêm nữa — thành một file khổng lồ và Claude bắt đầu **bỏ qua một phần** của nó.

Đây không phải bug của Claude; đó là cách file này hoạt động.

**Điểm mấu chốt:** CLAUDE.md **không phải enforced configuration — nó là guidance**. Mỗi dòng cạnh tranh với các dòng khác cho sự chú ý của Claude.

File càng dài càng tự cạnh tranh với chính nó, Claude càng khó theo bất kỳ rule đơn lẻ nào.

**Mục tiêu không phải ghi lại mọi thứ — mục tiêu là giữ file gọn. File càng gọn, Claude theo được càng nhiều.**

#### Trước tiên, tự hỏi CLAUDE.md có phải công cụ đúng không

- Có rule là **guidance**, có rule là **hard line** không bao giờ được phép vượt — hai việc khác nhau.
- Ví dụ "never push to main": đặt trong CLAUDE.md thì bạn chỉ *hy vọng* Claude đọc và tôn trọng.
  Đa số thời gian là có — nhưng "đa số" không đủ cho thứ nguy hiểm vậy. Rule cứng như vậy thuộc về **pre-tool-use hook**.
- Hook là code chạy **trước** khi Claude hành động và có thể **chặn** hành động đó — kể cả khi Claude cố push to main, hook chặn lại.
  Đó là enforcement thật, không phải lời đề nghị lịch sự. **Hard rules → hooks; soft conventions → CLAUDE.md.**

#### The four locations — 4 vị trí của CLAUDE.md

Claude load **tất cả cùng lúc** khi khởi động; không gì bị drop, chúng **stack** lên nhau:

| Vị trí | Mục đích |
|---|---|
| **Managed policy** | File cấp org do platform team kiểm soát. Không thể exclude → org policy luôn có hiệu lực. |
| **User** | Sở thích cá nhân, theo bạn qua mọi project trên máy. |
| **Project** | File chia sẻ với team, commit vào repo. |
| **Local** | Bị git ignore. Ghi chú cá nhân chỉ cho repo này. |

- **Local** hay bị bỏ qua nhưng rất hữu ích: ví dụ bạn đang refactor ở branch riêng và muốn Claude giữ trong đầu vài architectural decision
  — không nên đặt vào project file (ảnh hưởng cả team), mà để vào local, chỉ của riêng bạn cho repo này.

#### Split up a big file with imports

Khi project file dài, tách bằng path-to-file import syntax:

```
@.claude/conventions/code-style.md
@.claude/conventions/testing.md
@.claude/conventions/workflow.md
```

- **Hiểu đúng nó mua được gì:** khi Claude khởi động, nó **expand inline** các file import ngay tại chỗ tham chiếu.
  Imports giúp gọn gàng, nhưng **mọi thứ vẫn load up front** — chúng **không giảm** lượng context Claude phải đọc. **Dùng imports để tổ chức, không phải để giảm tải.**

#### Phrasing is what makes rules stick

Rule có được tuân thủ hay không nằm ở cách diễn đạt. Đa số rule thất bại vì **vague**.

**1. Be specific and checkable** — đừng viết "follow best practices" (bạn có chắc đó là gì không? Nếu bạn không check được nó có được tuân thủ, Claude cũng không):

- Vague: `"Follow best practices for API routes."`
- Specific: `"Put new API routes in src/api/handlers, one per file."` ← nhìn kết quả là biết ngay đúng/sai. Đó là chuẩn mỗi rule phải đạt.

**2. Name the replacement, don't just ban** — khi cấm điều gì, nói rõ làm gì thay thế, không thì cửa vẫn mở:

- Còn mở: `"Don't use default exports."` — rồi thì gì?
- Khép kín: `"Use named exports, not default exports."` ← nêu rõ replacement, không còn gì để hiểu lầm.

**3. Emphasis is a budget** — từ như "IMPORTANT", "YOU MUST" có nâng priority của rule, nhưng chỉ **tương đối** so với những gì yên tĩnh xung quanh.

Nếu rule nào cũng gào thì không gì nổi bật. Chi tiêu emphasis như ngân sách: dành cho 2–3 rule thật đau khi bị phá, còn lại để âm lượng bình thường.

#### Keep the file under revision

- CLAUDE.md **không bao giờ "xong"** — đối xử như living code liên tục được sửa.
- Khi Claude làm sai, đừng thở dài rồi sửa tay — hãy coi đó là **bug report cho CLAUDE.md**.
  Thậm chí bảo thẳng Claude: *"add that to the CLAUDE.md file"* — nó sẽ tự viết rule. File tốt dần lên mỗi lần có chuyện sai.

#### The bottom line

Đối xử với CLAUDE.md như **production code** — không justify được dòng nào thì xóa. Để file lean và followable:

1. Hard rules → hooks (nơi thực sự enforced).
2. Organize file dài bằng imports (nhớ: không giảm context).
3. Mọi rule specific + checkable, và nêu rõ replacement.
4. Chi tiêu emphasis budget cho vài rule quan trọng nhất.
5. Sửa file mỗi khi Claude làm sai.

**Ý chính: file càng lean, Claude theo càng nhiều.**

### Bài 3: Verification skills

*(Lesson 3 of 9 · 5 min · slug: `verification-skills`)*

Skills là cách tự động hóa việc lặp lại. Bài này tập trung một việc skills cực hợp: **verify chính công việc của Claude** — nếu chỉ xây được một skill, hãy xây skill này trước tiên.

#### Why a verification skill is the one to build first

- Cách kiểm tra bình thường: nhờ Claude refactor, xong, rồi bạn phải **nhớ** hỏi nó double-check — chạy tests, đọc diff.
  Vấn đề: việc kiểm tra phụ thuộc vào việc bạn nhớ yêu cầu. Quên một lần là code lỗi lọt qua.
- **Verification skill gỡ bỏ phụ thuộc đó.** Dạng của nó: bạn nhờ Claude refactor → nó xong → thay đổi khớp description của skill → **skill tự kích hoạt**, rồi nó:
  1. Chạy test suite.
  2. Đọc diff.
  3. Check rằng **không test nào bị nới lỏng** chỉ để cho pass.
  4. Báo cáo pass/fail kèm evidence.
- Toàn bộ flow chạy **không cần bạn yêu cầu** — description của skill là thứ trigger nó, và đã trigger thì luôn đi đúng các bước đó.
- Điểm check cuối đáng chú ý: chạy tests thấy xanh chưa đủ — test có thể bị **lặng lẽ nới lỏng** để pass vô điều kiện, nên skill đọc diff xác nhận tests không bị yếu đi.
  **"Done" không phải "code nhìn đúng" từ diff — done là các gate được chạy và quan sát, kết quả được nêu rõ ràng.**
- Dạng này áp dụng cho mọi procedure team lặp lại: release checklist, migration recipe, pre-PR check. **Rule of thumb: đã gõ cùng một multi-step instruction 2 lần → đó là một skill.**

#### A skill folder can hold more than instructions

Skill không chỉ là một file SKILL.md — **cả folder** mang được nhiều thứ:

- Đặt **`reference.md`** cạnh SKILL.md cho tài liệu chi tiết, link từ SKILL.md — Claude chỉ đọc khi cần độ sâu đó. File chính giữ ngắn.
- Đặt **scripts** vào folder: Claude **thực thi** chúng thay vì load nội dung vào context → skill mang theo tooling riêng, như một `check.sh` chạy mọi gates.
- **Takeaway:** giữ SKILL.md lean; đẩy vật liệu nặng (giải thích dài + scripts chạy được) sang side files. File lean mô tả *làm gì*; side files giữ *độ sâu và công cụ*.

#### Which instruction surface owns which rule

Ba chỗ để đặt instructions, dễ trộn lẫn — cách phân biệt nhanh:

- **Conventions áp dụng mọi lúc** (naming rules, file nằm ở đâu) → **CLAUDE.md**.
- **Procedures + reference material** gắn với một loại task cụ thể → **skill**.
- **Rule Claude không được phép bỏ qua** → **hook**, không phải hai cái trên.
  Vì CLAUDE.md và skills đều là *instructions Claude tuân theo*, còn hook là **code thực sự chạy**.
  Nếu việc bỏ qua rule là không chấp nhận được, đừng phó mặc cho instruction-following.

#### The recap

- Skill = folder chứa SKILL.md: **name**, **description** (thứ trigger nó), và **procedure**.
  Chỉ descriptions được load vào context cho đến khi skill cần đến → chi phí packaged mọi procedure lặp lại gần như bằng 0.
- Bắt đầu với verification: build skill, commit vào **`.claude/skills`** của project → cả team thừa hưởng cùng một nước đi.
  Work của mọi người được kiểm tra cùng một cách, tự động, không ai phải nhớ để hỏi.

### Bài 4: Permission modes

*(Lesson 4 of 9 · 5 min · slug: `permission-modes`)*

**Ý tưởng:** quyết định **một lần** những gì Claude được chạy mà không phải dừng hỏi — thay vì duyệt từng action theo từng prompt, chọn mode đúng mức tin cậy cho công việc.

#### The six permission modes

| Mode | Hành vi |
|---|---|
| **Manual** | Chỉ đọc (reads) không cần hỏi. Mọi thứ khác phải hỏi trước. |
| **Accept edits** | Chạy reads, file edits, và các bash command phổ biến trên file system không cần hỏi. Dành cho iterate code mà bạn review sau. |
| **Plan** | Research và đề xuất thay đổi, **không edit gì**. Reads chạy tự do; khi auto mode khả dụng, classifier của auto rà soát các command Claude chạy để khám phá và cho chạy không prompt những cái được duyệt. |
| **Auto** | Chấp nhận mọi thứ, với một **classifier model riêng** rà soát đa số action trước khi chạy. |
| **Don't ask** | Cho reads trong working directories + tools đã pre-approve. Mọi thứ đáng lẽ prompt → **auto-denied**. |
| **Bypass permissions** | Bỏ qua mọi check. Tương đương flag `dangerously-skip-permissions`. **Chỉ chạy trong container/VM cách ly.** |

#### Cycling with shift-tab

Không cần nhớ lệnh từng mode — nhấn **shift-tab** để cycle qua các mode hằng ngày: **manual → accept edits → plan → auto**. Status bar dưới màn hình luôn hiển thị mode hiện tại.

#### How auto mode works

- Auto là mode hands-off: Claude tự chạy, nhưng trước khi đa số action thực thi, một **classifier model riêng** rà soát.
  Classifier canh **intent** — phát hiện các nước đi leo thang vượt quá điều bạn thực sự yêu cầu.
- **Chặn:** production deploys và migrations; force pushing; pipe code tải về thẳng vào shell; gửi sensitive data ra external endpoint; hủy không thể hoàn tác các file tồn tại trước session.
- **Cho qua:** edits cục bộ trong project; cài dependencies từ lock file; read-only requests; push lên branch của chính bạn.
- **Guardrails của auto vẫn đang hoàn thiện** — xem docs cho block/allow lists hiện tại.

#### What the classifier can't do

- Classifier check **intent, không check correctness** — nó không bắt được code có chạy được hay không.
  Nhờ Claude refactor authentication mà nó viết ra authentication hỏng → classifier vẫn cho qua, vì **hỏng không nguy hiểm**.
- Vì vậy ghép auto mode với **stop hook chạy tests** — hai thứ cộng tác:
  - **Auto mode** canh intent *trong lúc* Claude chạy.
  - **Stop hook** xác nhận code thực sự chạy được *sau khi* Claude xong.
  - Một canh intent trước, một canh correctness sau.

#### Don't ask — cho unattended runs

- Đúng đắn khi **không có người** duyệt prompt: CI pipelines, scheduled jobs, overnight batches.
- Claude vẫn chạy những gì không cần approval ở Manual mode (reads trong working directories) + tools đã pre-approve;
  những gì đáng lẽ prompt bị **auto-denied** — chính là mục đích: pipeline tiếp tục chạy thay vì treo chờ một approval không ai ở đó để duyệt.

#### Match the mode to the job (tóm tắt)

1. **Auto** = hands-off; classifier check intent trước, stop hook check correctness sau.
2. **Don't ask** = unattended pipelines không người duyệt.
3. **Bypass permissions** = chỉ trong container/VM cách ly.

### Bài 5: Hooks

*(Lesson 5 of 9 · 7 min · slug: `hooks`)*

**Vấn đề với CLAUDE.md:** đó là *request*, không phải *guarantee*. Viết "always format after editing" thì Claude *thường* nghe. Nhưng trên long run không ai trông, "thường" là chưa đủ.

**Hook giải quyết:** hook là **deterministic code chạy tại điểm cố định trong loop** — nó **đảm bảo** behavior thay vì hy vọng. Biến rule từ "Claude thường nghe" thành **"Claude không thể bỏ qua."**

#### The hook events

Claude Code kích hoạt **~30 hook events** trong một session — chỉ cần nhớ một nhóm nhỏ, xếp dọc theo agentic loop (session bắt đầu → prompts vào → tools gọi → turn kết thúc):

| Event | Khi nào fire | Dùng cho |
|---|---|---|
| **PreToolUse** | Trước tool call | **Enforcement primitive** — chặn trước khi xảy ra. |
| **PostToolUse** | Sau tool call thành công | Auto-formatting / auto-lint. |
| **Stop** | Claude muốn kết thúc turn | Từ chối: "chưa xong" nếu điều kiện chưa đạt. Có **SubagentStop** tương ứng cho sub-agent. |
| **PreCompact / PostCompact** | Trước/sau compaction | Can thiệp quanh quá trình compact. |
| **InstructionsLoaded** | Khi CLAUDE.md/rule file load | Audit cái gì thực sự vào được context. |
| **SessionStart** | Đầu session, prime môi trường | Dùng startup source nếu chỉ muốn chạy trên fresh start. |

- **Gotcha hay gặp:** muốn re-inject context sau compaction → **đừng dùng PostCompact**. Dùng **SessionStart với compact matcher** — chỉ nó mới đưa output trở lại conversation.

#### PreToolUse: returning a decision as JSON

PreToolUse là nơi mạnh nhất vì **chặn được tool call trước khi chạy**. Cách "nói chuyện" với Claude: **in JSON ra stdout và exit 0**. Field chủ chốt là `permissionDecision` với 3 giá trị:

- `allow` — cho qua.
- `deny` — chặn.
- `ask` — đẩy về người dùng quyết định.
- (Có giá trị thứ 4 `defer`, chỉ áp dụng cho run `-p` non-interactive where calling process pause/resume tool — hiếm khi cần.)

Hình dạng JSON:

```json
{
  "hookSpecificOutput": {
    "hookEventName": "PreToolUse",
    "permissionDecision": "deny",
    "permissionDecisionReason": "...",
    "updatedInput": {
      "command": "..."
    }
  }
}
```

- Chú ý **`updatedInput`**: thay vì block, bạn có thể **viết lại** tool call — đó là cách redact một secret khỏi bash command mà vẫn cho nó chạy.
  **Catch:** `updatedInput` thay thế **toàn bộ** input object → phải echo lại các field không đổi, không thì mất.

#### Exit codes — cho hooks không trả JSON

Ba con số quan trọng:

- **0** = success. Nếu stdout là JSON, Claude parse; plain text bị ignore trên đa số event,
  **trừ SessionStart, UserPromptSubmit, UserPromptExpansion**
  — ở đó plain text được **thêm vào context** (chính điều này làm state-preserver hook hoạt động).
- **2** = **blocking error**. Stderr được đưa ngược lại cho Claude làm context. Đây là exit code chặn gần như ở mọi event.
- **Bất kỳ giá trị khác** = non-blocking; stderr được log, Claude cứ chạy tiếp.

- **Bẫy lớn nhất: exit 1.** Nghe như error nhưng **không chặn** — Claude vẫn chạy command. Muốn chặn thì **exit 2, không phải 1**.
- Vài wrinkle nữa: exit 2 chặn được cả **Stop** (cách bảo Claude "chưa xong").
  Nhưng **PostToolUse** fire *sau khi* tool đã chạy — block ở đó là quá muộn để chặn call (vẫn feed text lại cho Claude được).
  Một vài event **ignore blocking hoàn toàn**: Notification và SessionStart — SessionStart chỉ hiện stderr cho *bạn* xem, Notification ignore, cả hai cứ tiếp tục.

#### A real guardrail: redact instead of block

Ví dụ thực tế: PreToolUse guardrail trên tool **Bash** — matcher chọn tool để theo dõi, `if` clause (tùy chọn) thu hẹp về command cụ thể.

- Nước đi hiển nhiên: return `deny`, chặn call nguy hiểm — tốt.
- Nước đi ít biết và **thú vị hơn**: return `updatedInput` để **viết lại** call — strip một secret khỏi command mà vẫn cho chạy, thay vì chỉ từ chối.
- Demo trong bài: Claude được yêu cầu chạy command chứa secret "live-looking" → hook chặn lại, nhận diện pattern `sk_live_`, **hoán đổi bằng placeholder trước khi command kịp thực thi**.
  Command vẫn chạy, công việc vẫn xong, nhưng secret không bao giờ lọt qua.
  Đó là khác biệt giữa **blocking và redacting** — kiểu enforcement hook làm được **mọi lần, đúng mọi lần**.

#### Preserving state across a compact

Khi Claude compact conversation dài, nó drop nhiều chi tiết. **SessionStart hook với compact matcher** chạy ngay sau compaction — cho nó in ra summary ngắn về các file đang làm việc.

Summary quay lại context → Claude tiếp tục đúng chỗ thay vì khởi động nguội.

#### Wrapping up

Hooks biến rule Claude *thường* theo thành rule *luôn luôn* theo.

Vượt qua auto-formatting: canh tools bằng **PreToolUse**, chặn turn bằng **Stop**, giữ state qua compact.

Setup tốn công một chút nhưng hoàn vốn ngay lần đầu nó bắt được thứ gì trên run bạn không hề trông.

---

## Phần 3 — Automate repeat work

### Bài 6: Scheduled tasks and headless

*(Lesson 6 of 9 · 7 min · slug: `routines-and-headless` — hiển thị "Scheduled tasks and headless")*

Một khi đã tin Claude làm tốt một task, bước tiếp theo là **ngừng làm thủ công**.

Bài này covers 2 cách bàn giao:

- **Cloud scheduled tasks** (trước đây gọi là *routines*) — không phải build gì.
- **Headless mode** — kiểm soát hoàn toàn từ script của bạn.

Tưởng tượng như một **spectrum**: một đầu là cloud scheduled tasks chạy trên hạ tầng managed của Anthropic; đầu kia là headless mode / Agent SDK — chạy Claude Code từ code của chính bạn.

#### Scheduled tasks — a saved prompt that runs in the cloud

- Cloud scheduled task = cách trực tiếp nhất tự động hóa repeat work: **không script, không server**.
  Nó bundle 3 thứ — **prompt + repository nó làm việc + connectors cần thiết** — rồi chạy bundle đó trên cloud mỗi khi trigger.
- Điểm mấu chốt: hạ tầng là **của Anthropic** — không máy của bạn phải thức qua đêm, không workflow file phải maintain. Mô tả job một lần, nó chạy.
- **Scheduled task không nhất thiết cần "schedule"** — 3 loại trigger:
  - **Cron schedule** (vd mỗi sáng 9am).
  - **HTTP POST** vào API endpoint của nó — code của bạn tự kick off.
  - **GitHub event** (vd pull request mới landing).
- Fit tốt: prompt lặp lại theo trigger định kỳ — morning dependency audit, PR triager chạy khi PR mới vào, daily scan Sentry tickets xếp mức độ khẩn.
- **Mental model:** scheduled task = prompt + repo + connectors + trigger.

#### Two ways to create one

1. **Từ web:** `claude.ai/code/routines` — đặt tên, viết instructions mô tả Claude làm gì mỗi session, chọn repository, chọn trigger.
2. **Từ terminal trong Claude Code:** lệnh `/schedule`, mô tả bằng ngôn ngữ tự nhiên:

```
/schedule daily dependency audit at 9am
```

#### Ba điều cần biết trước khi dựa vào cloud scheduled tasks

1. **Research preview** — behavior và limits sẽ thay đổi, đừng ngạc nhiên.
2. **Recurring schedule chạy tối đa mỗi giờ một lần** — cần dày hơn thì không phải công cụ này.
3. **Mỗi run start từ fresh clone của default branch và push lên branch `claude/`**, trừ khi prompt của bạn nêu branch khác.
   Khi GitHub pull request event trigger run: repo của PR start từ **head commit của PR** (miễn nó là repository đầu tiên trong task).
   Kiểm soát branch nào run được push bằng **branch protection rules / rulesets trên GitHub** — lưu ý: rule mà GitHub access của bạn có thể bypass thì **sẽ không chặn** được push.

#### Headless mode — khi cần môi trường của bạn

Khi job cần môi trường của bạn hoặc logic bao quanh run → **headless mode** (docs giờ gọi là *non-interactive mode*).

- Lõi là flag **`-p`** (viết tắt `--print`): chạy Claude Code như **one-shot command**, không UI tương tác. Đọc stdin, ghi stdout — **pipe như mọi shell tool**:

```bash
claude -p "summarize the changes in this diff"
```

- Đáng biết: chạy `-p` đơn thuần, Claude load **cùng context** như session tương tác — hooks, skills, plugins, MCP servers, CLAUDE.md. Muốn bỏ hết → thêm `--bare` (xem dưới).

#### Getting structured output back

Vì headless pipe như shell tool, bạn thường cần **structured data** thay vì văn xuôi: ghép **JSON schema** với **JSON output format** — Claude ràng buộc output khớp schema.

Object khớp schema nằm trong field **`structured_output`** của JSON response → lôi ra bằng `jq`, pipe vào database hay script khác:

```bash
claude -p "Extract the exported function names from src/core/style.js" \
  --output-format json \
  --json-schema '{"type":"object","properties":{"functions":{"type":"array","items":{"type":"string"}}},"required":["functions"]}' \
  | jq '.structured_output.functions'
```

#### Multi-step automation with sessions

Việc trải nhiều bước không cần nhét vào một command — capture **session ID** từ JSON output rồi resume sau:

```bash
claude --resume "$(jq -r .session_id /tmp/plan.json)"
```

Script này khởi động việc, script kia resume với **đầy đủ context** — tiện khi lượt đầu tạo plan, lượt hai thi hành.

#### Consistent runs for CI — `--bare`

- **`--bare`** bỏ qua auto-discovery của hooks, skills, plugins, MCP servers, CLAUDE.md. Bạn có Claude với tools **Bash + file read + file edit**, cộng gì bạn truyền vào qua `--settings` / `--mcp-config`.
- Kết quả: mọi máy старт từ cùng setup, **startup nhanh hơn**.
- Lưu ý: bare mode **không dùng subscription login** → phải set **`ANTHROPIC_API_KEY`** trước.

#### The Agent SDK — Claude Code trong app của bạn

Bước cuối spectrum: **Agent SDK** — library nhúng Claude Code vào ứng dụng **TypeScript hoặc Python**. Cả hai ngôn ngữ expose hàm **`query`** và cùng primitives như CLI. Bạn truyền prompt + options:

- **`allowedTools`** — kiểm soát Claude được làm gì;
- **system prompt**;
- **permission mode**.

Rồi iterate qua messages Claude stream về, xử lý theo cách app cần. Cùng engine với CLI, chỉ khác là gọi được từ trong sản phẩm.

#### Which one should you reach for?

| Nhu cầu | Công cụ |
|---|---|
| Repeat work mặc định, không host gì | **Cloud scheduled tasks** |
| Job cần pipeline của bạn, pipe data qua script | **Headless `-p`** |
| CI cần cùng setup trên mọi máy | **`--bare`** |
| Công việc nằm trong sản phẩm của bạn | **Agent SDK** |

**Bắt đầu với cloud scheduled tasks; chỉ tụt xuống spectrum khi job cần thêm control.**

### Bài 7: GitHub Actions and Code Review

*(Lesson 7 of 9 · 6 min · slug: `github-actions-and-code-review`)*

**Nơi tốt nhất bàn giao repetitive work là pull request** — nơi review diễn ra, thay đổi đáp đất, và nhiều busywork sống.

Hai cách đặt Claude vào đây, giải hai vấn đề khác nhau:

- Một **managed service** bật lên là xong.
- Một **GitHub Action** tự tay wire.

#### The managed path: Code Review

- **Code Review** là service Anthropic-hosted, review PR qua **Claude GitHub app**. Không gì phải build hay host. Bật lên, nó bắt đầu post findings dạng **inline comment ngay trên dòng liên quan**.
- Setup: một **Owner** của Claude organization bật từ **Claude Code admin settings** → mục **Code review** → switch **Allow code review**.
  Sau đó Owner cài Claude GitHub app, chọn repos nó theo dõi, quyết định thời điểm chạy
  — nếu Owner không đồng thời là owner của GitHub organization thì một trong hai phải install + link app trước.

  Các lựa chọn timing:
  - Once khi PR mở;
  - Trên mọi push vào PR;
  - Chỉ khi ai đó comment **`@claude review`**.
- Khi bật: mọi thứ chạy trên hạ tầng Anthropic.
  **Bộ review agents phân tích diff đối chiếu với full codebase** — không chỉ các dòng đổi trong cô lập.
  Findings post dạng inline comment trên đúng dòng, **tag theo severity**, kèm summary table trong check run.
  Tính năng hay: **deduplicate và rank findings** — thay vì bức tường nitpicks, bạn đọc một handful vấn đề thật đáng chú ý.

#### What Code Review will and won't do

- **Không bao giờ approve hay block PR** — judgment call ở lại với con người. Claude flag; bạn quyết.
- **Không push fixes** — service chỉ post findings.
- Khả dụng trên plan **Team và Enterprise**.
- Vì service chỉ post findings, hành động là của bạn: fix code rồi push.
  Muốn kiểm tra fix trước khi push, chạy **`/code-review`** từ terminal — nó tự review diff của bạn, và flag **`--fix`** áp dụng findings của review đó vào working tree.

#### The do-it-yourself path: the GitHub Action

Code Review lo phần review. Khi job vượt ra ngoài review → **GitHub Action**: custom CI — implement thay đổi từ comment, chạy scheduled reports, bất cứ gì bạn thường viết workflow cho.

Nó chạy agent trên **PR comments, scheduled jobs, và mọi GitHub event**.

- Setup từ trong Claude Code: lệnh **`/install-github-app`** (cần **repo admin**). Slash command dẫn bạn qua cài GitHub app + set secret **`ANTHROPIC_API_KEY`** trên repo.
- Action: **`anthics/claude-code-action@v1`**. Các inputs thực dùng:

| Input | Ý nghĩa |
|---|---|
| `anthropic_api_key` | Bắt buộc khi run gọi Claude API — **trừ khi** auth bằng `claude_code_oauth_token` (từ Claude subscription) hoặc **workload identity federation** (set qua Claude Console service account, không cần stored secret). Không dùng với các cloud providers bên dưới. |
| `github_token` | Tùy chọn. Bỏ qua → action authenticate **như Claude GitHub app** đã cài lúc setup. Chỉ truyền token để override. |
| `trigger_phrase` | Cụm action lắng nghe trong comments. Mặc định `@claude`. |
| `use_bedrock` / `use_vertex` / `use_foundry` | Route run qua **Amazon Bedrock / Google Cloud's Agent Platform / Microsoft Foundry** thay vì Claude API — đăng nhập bằng cloud account thay vì API key. |
| `prompt` | Instruction cho automated run. Set nó → Claude chạy ngay trên event, không chờ mention. Bỏ qua → action chờ trigger phrase. |
| `claude_args` | Chuỗi CLI arguments truyền thẳng vào Claude Code. |

#### A workflow that responds to @claude

Đặt workflow vào `.github/workflows/claude.yaml` — lắng nghe `@claude` trên PR comments và issue comments.

Trong `permissions` của job, cấp **`id-token: write`** để action đăng nhập như Claude GitHub app. Step cốt lõi:

```yaml
- uses: anthropics/claude-code-action@v1
  with:
    anthropic_api_key: ${{ secrets.ANTHROPIC_API_KEY }}
    trigger_phrase: "@claude"
    claude_args: "--max-turns 5 --model claude-sonnet-5"
```

Giờ ai viết `@claude implement the spec in the linked Linear issue` trên PR → action nhặt lên. Claude push commits và post comments mô tả nó đã làm gì.

#### A workflow that runs on a schedule

Cùng action chạy daily rollup: **cron** trigger (vd 9:00 UTC) → action chạy `prompt` của bạn → đọc rollup trong log của run đó.

**Scheduled run không tự post comment.** Có thể thêm trigger **`workflow_dispatch`** để kick off thủ công từ Actions tab.

Khi chạy, theo dõi các bước trong **Actions tab** như mọi GitHub workflow.

#### Tuning the run with claude_args

`claude_args` là nơi fine-tune — vài núm đáng biết:

- **`--max-turns 5`** — hard cap cho agent loop, không chạy mãi được.
- **Permission mode** — job unattended thì chọn chế độ không dừng hỏi (không ai ở đó để trả lời).
- **Allowed tools** — đưa đúng những gì job cần, không hơn. Report → read-only.

#### Which one should you use?

- **PR review** → managed path: bật Code Review, GitHub app post inline findings, bạn fix + push.
- **Hơn review** → action: `/install-github-app` để setup, một workflow cho `@claude` mentions, một cho cron, mọi tuning nằm trong `claude_args`.
- **Bắt đầu bằng managed service. Chuyển sang action ngay khi cần Claude thực sự LÀ gì đó trong CI, chứ không chỉ comment về nó.**

---

## Phần 4 — Verify and share

### Bài 8: Trust it — Verifying unsupervised runs

*(Lesson 8 of 9 · 5 min · slug: `trust-it-verifying-unsupervised-runs`)*

**Tình huống:** bạn giao Claude một task, để nó chạy không theo dõi từng bước, giờ nó nói xong.

Trước khi ship, bạn cần cách kiểm tra thứ mình **không hề giám sát** — chính bước kiểm tra đó làm hands-off Claude Code đáng tin.

**Ý tưởng:** **verify tương xứng với độ "dây thừng" bạn trao.** Session ngắn bạn nhìn message trôi qua — liếc nhanh là đủ.

Run unattended hay job trong CI không người trong vòng — cần check thật: không ai thấy chuyện gì xảy ra, phải **tái thiết lại sau sự kiện**.

Công thức: **càng ít theo dõi, càng phải verify nhiều.**

#### Keep unattended runs in auto mode

- Run unattended ở nơi làm việc → giữ ở **auto mode** thay vì bypass permissions: classifier vẫn rà đa số action cho nguy hiểm — lưới an toàn đáng giữ.
- Nhưng hiểu rõ lưới đó làm gì/không làm gì: **classifier không bao giờ phán code đúng hay sai** — nó chỉ flag action nguy hiểm.
  Thanh verify của bạn giữ nguyên, đặt theo mức độ unsupervised của run.

#### Start with the diff, not the summary

- **Đừng bắt đầu bằng summary** của Claude về việc nó đã làm — bắt đầu bằng **chính diff**:
  1. Chạy **`/code-review`** để đi qua changes và flag issues.
  2. Rồi **tự mắt nhìn `git diff`**.
- Bẫy: summary gọn gàng đọc rất ổn, trong khi diff thật chạm vào file bạn **không hề ngờ** nó chạm. Summary không nói cho bạn điều đó — **diff sẽ nói**.
- Đọc thứ đã đổi: files thuộc plan đọc trước, rồi tìm mọi thứ ngoài plan. **Write-up sạch không phải bằng chứng code sạch.**

#### Turn tests into a gate, not a promise

- Gate thật cho unsupervised run: **tests có pass không** và **Claude có thực sự chạy chúng hay chỉ claiming là có**. Đừng để niềm tin lo — wire thành **hook** để Claude không bỏ qua được:
  - **Stop hook** chạy tests và **từ chối kết thúc turn khi fail**.
  - **Post-tool-use hook** lint + type check sau **mọi** edit.
- Chi tiết then chốt: **exit code**. Hook exit **mã 2** đưa failure thẳng lại cho Claude → Claude đọc failure và **tự sửa không cần bạn hỏi**.
  Và check fire trên **mọi run**, kể cả khi bạn quên yêu cầu.

#### Get a cold second opinion

- Sub-agent code review chạy trước PR dùng được ở đây: mở **session/sub-agent hoàn toàn mới** review code đã đổi với **không ký ức** về code được build thế nào.
- Vì nó không có cổ phần trong approach, nó bắt được những thứ run gốc **tự thuyết phục mình bỏ qua**. Reviewer thứ hai mắt lạnh tìm ra cái tác giả rationalized away.

#### Putting it together

Mức check nghiêm túng ngang mức run được unsupervised:

1. Tự đọc diff.
2. Biến tests thành hook gate turn.
3. Verify headless runs qua **JSON result và exit code**.
4. Xin cold second opinion cho mọi thứ quan trọng.

Làm vậy thì "Claude làm lúc tôi không nhìn" **không còn cần niềm tin**.

### Bài 9: Plugins

*(Lesson 9 of 9 · 7 min · slug: `plugins`)*

**Vấn đề:** setup đáng tin giá trị gấp bội khi cả team cùng chạy — nhưng di chuyển nó mới khó.

Bạn build một `.claude` tuyệt vời với skills, subagents, hooks... rồi sao? Mọi người copy-paste files giữa các máy và cầu nguyện chúng đồng bộ.

**Plugins sửa điều đó: cách Claude Code đóng gói một setup và chuyển từ người này sang người kia.**

Hai mặt: (1) dùng plugins người khác publish; (2) đóng gói plugin riêng khi đã có gì đáng chia sẻ.

#### What a plugin is

- Plugin = **một đơn vị cài đặt duy nhất**.
  Bundle mọi thứ bạn từng chia tay: **skills, subagents, hooks, MCP server configs**, cộng đuôi dài hơn — **LSP servers, background monitors, themes, và một lát của `settings.json`**.
  Một version, một install.
- Cài trực tiếp bằng tên trong session:

```
/plugin install github@claude-plugins-official
```

- Lệnh mở **details của plugin trước** để bạn review và chọn scope.
  Sau đó Claude Code cài và in summary ngắn: hoặc nói plugin **đã active trong session**, hoặc nhắc **`/reload-plugins`** và Claude Code tự chạy reload đó cho bạn.
  Bạn chỉ can thiệp khi reload **cảnh báo** message kế tiếp sẽ re-read toàn bộ conversation — khi đó chạy `/reload-plugins --force` để kích hoạt plugin dù sao.

#### Adding a marketplace for your team

- Với team, nước đi tốt hơn: thêm **private marketplace một lần** — nguồn dùng chung để plugins resolve qua:

```
/plugin marketplace add your-org/claude-plugins
```

- Đặt tên tùy ý; một khi đã add, **mọi install sau resolve qua nó**: centralized discovery, version tracking, updates tại một chỗ thay vì rải rác trên laptop mọi người.
  Duyệt qua **Discover tab** — liệt kê plugins trên các marketplace của bạn để tìm và chọn.

#### Read before you install — phần quan trọng nhất

- **Plugin chạy code trên máy bạn, với quyền của bạn.** Hooks của nó fire trên **mọi tool call khớp**.
  Cài plugin vì skills → bạn cũng nhận cả PreToolUse và Stop hooks của nó, **dù bạn có đọc chúng hay không**.
- Suy ngẫm: một community plugin có thể ship Stop hook **call ra network endpoint mỗi lần**, và không gì trong cấu hình bạn cảnh báo. Không phải lý do tránh plugins — mà là lý do **nhìn trước**.
- Trước khi cài, xem **details**: Claude Code cho biết nó sẽ cài gì, **ước lượng context cost**, kèm cảnh báo thẳng thắn rằng **Anthropic không kiểm soát nội dung third-party plugins**.
- Hai điều về nguồn gốc plugin:
  - Plugin lên được **community marketplace** vì *tác giả* gửi nó cho Anthropic.
  - **Official marketplace** được curated trên track riêng biệt.
- Nhưng **listed ≠ trusted**. Nguyên tắc giữ nguyên: chỉ install plugins / add marketplaces từ nguồn bạn thực sự tin, và check plugin thực sự làm gì trước khi bật.

#### Components run alongside yours

- Plugin **không overwrite** cấu hình của bạn — components của nó chạy **song song** với của bạn. Chủ yếu là tốt, nhưng có hệ quả cần hiểu:
  - **Hooks stack:** PreToolUse hook của plugin và của bạn **đều fire** trên mọi tool call, không cái nào thay cái nào. Chính vì vậy phải đọc details trước.
  - **Skills, agents, commands được namespaced** dưới tên plugin → không bao giờ đụng yours.
  - Plugin có thể ship `settings.json` nhưng chỉ **rất hẹp**: Claude Code chỉ honor **2 keys** — `agent` và `subagent` status line keys.
  - Key **`agent`** đáng dừng lại: set nó **thăng cấp một subagent của plugin lên main thread**, kèm system prompt, tool restrictions, và model của subagent đó.
  Nói cách khác, bật plugin có thể **thay đổi hành vi mặc định của Claude Code** — một lý do chính để nhìn kỹ trước cả khi bật.
- Sau khi cài: xem mọi thứ nó thêm, manage, và uninstall từ **plugin panel**.

#### Packaging your own plugin

Khi đã có `.claude` directory chạy tốt — đừng bắt team copy-paste giữa các máy. **Package nó.** Tin tốt: không cần restructure gì — plugin dùng **chính shape `.claude`** bạn đang dùng:

- Một folder cho mỗi skill.
- Một markdown file cho mỗi subagent dưới `agents`.
- `hooks/hooks.json` và `.mcp.json` tại plugin root.

**Directory structure làm phần lớn công việc** — Claude Code khám phá components theo convention.

#### The manifest

Bên trên là manifest **tùy chọn**, tại `.claude-plugin/plugin.json`, giữ name, version, description, author:

```json
{
  "name": "svg-splitter-review",
  "version": "0.1.0",
  "description": "Reviews the SVG Splitter repo",
  "author": {
    "name": "Lewis Menelaws"
  }
}
```

- Manifest optional — bỏ cũng vẫn discover components theo directory convention. Nhưng đáng biết:
  - **Name là field bắt buộc duy nhất.** Nó namespaced skills của bạn thành `/plugin-name:skill-name` — skill trong plugin này chạy như **`/svg-splitter-review:<skill-name>`** → không đụng skill của ai khác.
  - **Version nó như dependency bình thường** — đó là điều làm updates và version tracking chạy được trong team.

#### The takeaway

Hai rule đơn giản phủ gần hết:

1. **Khi dùng:** đọc trước khi cài — plugin chạy code với quyền của bạn; xem hooks, agents, MCP servers của nó trước.
2. **Khi build:** package `.claude` ngay khi nó chạy tốt. Một manifest, một install.

**Đó là toàn bộ ý nghĩa: một đơn vị cài đặt, và setup bạn tin tưởng đến được cả team.**

---

## Tổng kết toàn khóa

| # | Bài | Ý chính một dòng |
|---|---|---|
| 1 | Steering long sessions | Scope bằng plan mode trước; lái bằng `/compact` có instruction, Rewind, `/goal`, `/loop`; song song bằng worktrees + `.worktreeinclude`. |
| 2 | A CLAUDE.md that follows | CLAUDE.md là guidance không phải enforcement — giữ lean, hard rules đẩy sang hooks, rules specific + checkable, emphasis là ngân sách, sửa file liên tục. |
| 3 | Verification skills | Skill đầu tiên nên xây là verification skill (chạy tests, đọc diff, chặn test bị nới lỏng); SKILL.md lean + reference.md + scripts; CLAUDE.md = conventions, skill = procedures, hook = không được phép bỏ qua. |
| 4 | Permission modes | 6 mode (manual, accept edits, plan, auto, don't ask, bypass); auto = classifier canh intent + stop hook canh correctness; don't ask cho unattended; bypass chỉ trong container/VM. |
| 5 | Hooks | ~30 events; PreToolUse chặn/viết lại tool call qua JSON (`permissionDecision`, `updatedInput` redact secret); exit 0/2, exit 1 KHÔNG chặn; SessionStart + compact matcher giữ state sau compact. |
| 6 | Scheduled tasks & headless | Spectrum: cloud scheduled tasks (prompt + repo + connectors + trigger) → `-p` headless với `--json-schema`/`--resume` → `--bare` cho CI → Agent SDK cho product. |
| 7 | GitHub Actions & Code Review | Managed Code Review chỉ post findings, không approve/push; cần Claude LÀ trong CI → `claude-code-action@v1` với `claude_args`, `--max-turns`, permission mode, allowed tools. |
| 8 | Verifying unsupervised runs | Càng ít theo dõi càng verify nhiều: đọc diff (không đọc summary), tests wire thành hook exit 2, headless check JSON + exit code, xin cold second opinion. |
| 9 | Plugins | Plugin = bundle skills/subagents/hooks/MCP/settings; đọc trước khi cài (hooks chạy với quyền bạn); marketplace riêng cho team; package `.claude` có sẵn + manifest `.claude-plugin/plugin.json`. |

**Chuỗi tư duy xuyên suốt khóa:** *steer* (bài 1) → *configure* để Claude tự đúng (bài 2–5) → *automate* việc lặp (bài 6–7)
→ *verify* thứ không giám sát (bài 8) → *share* qua plugins (bài 9).

Mỗi bài nâng một bậc độ tự tin: từ điều khiển tay đến tự động hoàn toàn có kiểm chứng.
