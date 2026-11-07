# Claude 101 — Executive Reference

> **Nguồn:** Claude Academy — khóa *Claude 101* (15 lessons + 2 videos + Use Case Gallery 156 use cases)
> academy.claude.com · quét 11/2026
>
> **Đối tượng:** người làm technical đã quen dùng AI assistant. Bỏ toàn bộ phần onboarding/dẫn dắt; chỉ giữ facts mang tính quyết định.
>
> **File liên quan:**
>
> - 156 use cases chi tiết → `Claude_Course_UseCases.md`
> - Dev workflow → `Claude_Code_In_Action_Course.md`, `Claude_Code_101_Course.md`
> - Desktop → `Claude_Cowork_Course.md`
> - Slack → `Claude_Tag_Course.md`
> - API/platform → `Claude_Platform_101_Course.md`

---

## Executive Summary

Luận điểm xuyên suốt: **Claude mang intelligence; bạn mang context và judgment — giá trị nằm ở phép ghép đó.**

Triển khai thành 5 nguyên tắc vận hành:

| # | Nguyên tắc | Hệ quả thực hành |
| :--- | :--- | :--- |
| 1 | Claude xử lý **situation**, không chỉ **question** | Delegate việc có context cá nhân (draft của bạn, data của bạn); việc tra fact thuần túy vẫn của search box |
| 2 | Output chất lượng = prompt đúng khung + **iterate** + **verify có hệ thống** | 3 yếu tố prompt → troubleshooting → evals → delegation diligence loop |
| 3 | Chọn bề mặt theo **shape of work**, không chọn tab trước | Turn-by-turn → Chat · Hand-off → Cowork · Building software → Code |
| 4 | Tách bạch **knowledge** / **process** / **deliverables** | Projects lưu knowledge · Skills định nghĩa process · Artifacts sinh deliverables |
| 5 | Reach mở rộng theo 3 tầng: cá nhân → tổ chức → web | Connectors (MCP) → Enterprise Search (org knowledge) → Research (multi-source investigation) |

---

## 1. Mô hình hợp tác: situation, không chỉ question

**Ranh giới delegate không nằm ở chủ đề** — reviews, invoices, tỷ giá đều tra cứu được.
Ranh giới nằm ở chỗ **câu trả lời có cần "bạn" trong đó không**: bản draft của bạn, deck cũ của bạn, cách bạn đánh giá khách hàng.
Search box nhận một question; Claude nhận một situation.

| Search box xử lý được | Cần Claude (có ngữ cảnh cá nhân) |
| :--- | :--- |
| "Tỷ giá USD→EUR hôm nay?" | "Viết lại update trễ deadline của tôi sao cho đọc như một quyết định, không phải lời xin lỗi" |
| "Khác nhau giữa PO và invoice?" | "Cấu trúc tốt nhất cho QBR của tôi" |
| "Có bao nhiêu ngày làm việc giữa 3/3 và 24/3?" | "Đọc thread khiếu nại này — khách thực sự muốn gì trước khi tôi trả lời?" |

### 1.1 Năng lực cốt lõi

| Năng lực | Điểm đáng nhớ |
| :--- | :--- |
| Writing & content creation | Nhận chỉ dẫn personality/tone; iterate tới khi giọng văn đúng |
| Research & analysis | **Context window 200K+ tokens** (~500+ trang); tối đa **1M tokens** (Pro/Max/Team/Enterprise, model hỗ trợ) |
| Coding assistance | Write/debug/explain code đa ngôn ngữ — một trong những điểm mạnh lớn nhất |
| Problem-solving & reasoning | **Thinking mode**: suy luận từng bước cho vấn đề cần phân tích kỹ |
| Learning | **Learning mode**: dẫn dắt suy luận thay vì đưa sẵn đáp án |

### 1.2 Chọn model

| Model | Khi nào | Lưu ý |
| :--- | :--- | :--- |
| **Claude Opus** | Tác vụ phức tạp nhất (multi-step financial analysis) | Hybrid reasoning; đổi model = mở chat mới |
| **Claude Sonnet** | Everyday use — **recommended default** | Cân bằng năng lực/chi phí |
| **Extended thinking** | Phân tích sâu | Tăng **latency** — câu hỏi đơn giản thì Sonnet + tắt thinking trước |

### 1.3 Nền tảng

- **Constitutional AI:** align human values, minh bạch.
- **Steerable:** tùy chỉnh theo personality/tone/hành vi.
- **Đồng bộ mọi thiết bị** (web, desktop, mobile): conversations, projects, memory, preferences.

---

## 2. Prompting & verification: khung 3 yếu tố → iterate → verify

### 2.1 Khung prompt 3 yếu tố

| Yếu tố | Câu hỏi tự vấn |
| :--- | :--- |
| **Setting the stage** | Vai trò, mục tiêu, context Claude nên biết |
| **Defining the task** | Hành động cụ thể: write / analyze / build… |
| **Specifying rules** | Format, style/tone, examples đính kèm |

Ví dụ đầy đủ:

> *"Tôi là marketing lead tại streaming startup, chuẩn bị Series A pitch deck
> → research thị trường streaming phim độc lập: trends, đối thủ, cơ hội tăng trưởng
> → web research kèm citations, report ≤ 5 trang, có executive summary + market analysis + competitive landscape + growth opportunities."*

Context bổ sung qua 3 kênh:

- **Uploads:** PDF, DOCX, CSV, TXT, PNG, JPEG — parse cả text lẫn images/charts.
- **Connectors:** xem §5.1.
- **Settings > Account > "Instructions for Claude":** preferences toàn cục.

### 2.2 Iterate — output đầu tiên chỉ là điểm khởi đầu

1. **Follow-up questions:** "Mở rộng điểm 2?", "Ngắn gọn hơn?"
2. **Feedback:** "Tốt, nhưng tone casual hơn"
3. **Redirect/restart:** "Ý tôi là X không phải Y"; tệ nhất thì chat mới

Tip: icon **bút chì** trên message → edit & resubmit prompt thay vì thêm message.

### 2.3 Troubleshooting nhanh

| Triệu chứng | Nguyên nhân | Sửa |
| :--- | :--- | :--- |
| Response chung chung | Thiếu context | Thêm audience, role, constraints |
| Quá dài/quá ngắn | Claude phải đoán | Nêu rõ số từ / mức chi tiết |
| Sai format | Biết *cái gì* không biết *như thế nào* | Show, don't tell — đưa ví dụ format |
| Tự tin nhưng sai fact | Nghe hợp lý, dễ tin | Verify fact quan trọng, hỏi mức tự tin, bật web search |
| Sai tone | Default không hợp | Mô tả tone trực tiếp hoặc đính kèm mẫu style |

### 2.4 Verify: evals + delegation diligence loop

**4D Framework for AI Fluency** (Dakan & Feller):

- **Delegation** — việc gì nên cho AI.
- **Description** — giao tiếp rõ ràng.
- **Discernment** — đánh giá phản biện.
- **Diligence** — trách nhiệm + đạo đức.

Fluency là *judgment*, không phải biết bấm nút.

**Eval 4 bước:**

1. Thu 5–10 ví dụ của task thật.
2. Viết test prompts với context tự nhiên.
3. So sánh output (accuracy, tone, gaps).
4. Refine prompt và lặp.

**Delegation diligence loop** — xây niềm tin trên dữ liệu đã biết kết quả đúng:

1. **Identify** task phân tích muốn delegate.
2. **Find** dữ liệu quá khứ có kết quả đã biết.
3. **Reproduce & evaluate:** AI làm lại phân tích, đối chiếu kết quả đã biết, ghi chú gaps.
4. **Refine** mô tả → test lại.
5. **Quyết định:** match → tự tin dùng cho dữ liệu mới; không match sau vài lần → **task này không delegate**.

Case minh họa (Rio, Valley Veterans Services):

- Lần 1: AI đúng correlation attendance↔placement nhưng miss insight chương trình housing+job.
- Refine yêu cầu rõ *program type* → bắt được insight.
- Thiếu *enrollment dates* thì AI tự infer sai — phải cung cấp đủ dữ liệu cho cohort analysis.

> **"Validation builds confidence, but it doesn't eliminate responsibility"** — bạn vẫn accountable và transparent về vai trò AI.

### 2.5 Cá nhân hóa

| Tính năng | Cơ chế | Default |
| :--- | :--- | :--- |
| **Memory** | Tự lưu role, preferences, quyết định cũ, working style; review/edit tại Settings > Memory; đồng bộ mọi thiết bị | **Bật** Free/Pro/Max · **Tắt** Team/Enterprise (cần org Owner cho phép) |
| **Skills** | Instructions tái sử dụng, Claude tự áp dụng khi liên quan | Xem §4.2 |

---

## 3. Bề mặt làm việc: chọn theo shape of work

**Nguyên tắc: nhận diện công việc trước — tab theo sau.**

| Shape of work | Bề mặt | Dấu hiệu | Tính năng riêng |
| :--- | :--- | :--- | :--- |
| **Turn-by-turn** | **Chat** | Câu trả lời định hình câu hỏi tiếp theo (brainstorm, drafting, thinking aloud); cần judgment ở mỗi bước | Quick entry (double-tap `Option` trên Mac), screenshots/window sharing, dictation, desktop connectors |
| **Hand-off** | **Cowork** (Pro/Max/Team/Enterprise) | Task đa bước tuần tự; output là files hoàn chỉnh đúng chỗ; việc trải nhiều tools; chạy theo schedule | Local folder access · Scheduled tasks (chạy remote kể cả khi máy sleep) · Subagents song song · Projects · Browser use · Computer use (research preview, Pro/Max) · Plugins (bundles theo role: sales/finance/legal) |
| **Building software** | **Code tab** (Pro/Max/Team/Enterprise) | Viết/test/chạy/ship code trong codebase thật | Visual diffs, built-in terminal, git-backed versioning · Local: folder tự chọn + dev server · Cloud: GitHub repo, session tồn tại sau khi đóng app (Cowork cũng chạy cloud trên Pro/Max) |

**Kiểm soát trong Cowork:**

- Claude hỏi clarifying questions và hiện plan để theo dõi.
- Đặt **ask-first** → Claude pause xin approve hành động nhạy cảm (VD gửi email).

**Autonomy settings (Code):** Manually approve / Accept edits / Plan (draft plan trước khi đổi bất cứ thứ gì).

### 3.1 Bản đồ 8 bề mặt

| Bề mặt | Best for | Nơi chạy |
| :--- | :--- | :--- |
| **Claude.ai** | Task chung: research, viết, phân tích, tạo file | Web, desktop, mobile |
| **Claude Code** | Codebase navigation, git workflows, automate việc tẻ nhạt (lint fixes, merge conflicts, release notes) | Terminal, IDE, browser, Slack |
| **Claude Cowork** | Task đa bước, briefs, tổ chức file, phân tích | Desktop (+ web/mobile Pro/Max) |
| **Claude Tag** | Hợp tác team trong Slack: draft replies, summarize threads, meeting prep, onboard qua channel history; handoff bug report → Claude Code session kèm context | Slack workspace |
| **Claude Design** | Brief/sketch/screenshot → interactive prototype dạng artifact; sinh + so sánh nhiều directions; khớp design system để handoff | Mọi conversation + claude.ai/design |
| **Claude for Excel** | Hiểu formulas/calculation flow multi-tab; update assumptions giữ dependencies; debug #REF!/#VALUE!/circular refs; build pivot tables | M365 sidebar |
| **Claude for PowerPoint / Word / Outlook** (beta) | PPT: outline→deck, tighten copy, restructure · Word: draft theo template, xử lý tracked changes, ground vào connected sources · Outlook: triage inbox, draft replies có context threads + calendar | M365 sidebar |
| **Claude in Chrome** | Web research khi đang browse, quản lý email, điền form lặp lại, test flows nhiều bước, giữ context xuyên tabs (CRMs, dashboards) | Chrome sidebar (Pro/Max/Team/Enterprise) |

Chrome safety: hỏi permission trước hành động rủi ro (mua sắm, share data cá nhân); chặn mặc định financial/adult sites; admin kiểm soát org-wide + restrict sites.

---

## 4. Kiến trúc tri thức: Projects (knowledge) · Skills (process) · Artifacts (deliverables)

### 4.1 Projects — workspace có memory riêng

**Dùng khi có ≥1 dấu hiệu:**

- Reference materials dùng lặp lại (meeting notes, reports, historical data).
- Requirements nhất quán (tone, template, trích nguồn).
- Team collaboration trên context chung.

**Setup 3 bước:**

1. **Create:** Sidebar → Projects → + New Project.
   ⚠️ *Claude không thấy project description* — chỉ dành cho con người. Visibility: private hoặc share org (gói Work).
2. **Project instructions:** context → process → tone/style → specific requirements; áp dụng cho **mọi chat** trong project.
3. **Knowledge base:** upload PDF/DOCX/CSV/TXT/HTML + Google Drive.
   **Đặt tên file mô tả** — Claude retrieve theo tên: `Q4-2024-Brand-Guidelines.pdf` ≫ `document1.pdf`.

**RAG:** khi gần chạm context window limit, Claude tự chuyển sang **Retrieval Augmented Generation** — search files, chỉ nạp phần liên quan → capacity **~10x**, có indicator hiển thị.

**Collaboration:** permission `Can view` / `Can edit` / `Owner`; share theo name/email, danh sách, hoặc "Everyone at [org]".

**Best practices:**

- Start với 1 use case rồi mở rộng.
- **Doc lỗi thời → câu trả lời lỗi thời** — cập nhật knowledge base.
- Instructions mơ hồ → kết quả thiếu nhất quán.
- Tham chiếu tài liệu theo tên ("Dựa trên Q3 report, top concerns là gì?").

### 4.2 Skills — gói process tái sử dụng

**Định nghĩa:** folders of instructions, scripts, resources mà Claude loads dynamically. Nếu từng nhờ Claude tạo file Excel/PPT/Word/PDF — bạn đã dùng Anthropic Skills chạy ngầm.

| Loại | Nguồn | Ví dụ |
| :--- | :--- | :--- |
| **Anthropic Skills** | Built-in, Anthropic duy trì | Document creation: Excel, Word, PowerPoint, PDF |
| **Custom Skills** | Tự tạo / org tạo | Quarterly variance analysis, brand voice review, compliance checklist |

**Kích hoạt:** Settings > Capabilities → bật **Code execution and file creation** (Team/Enterprise: Owner quản org-wide) → Customize > Skills → switch từng skill.
Chạy trong **sandboxed environment**; có thể bật **Allow limited network access** khi cần external data.

**Hành vi:**

- Claude **tự chọn** skill khi liên quan (không trigger tay).
- Usage hiện trong chain of thought.
- File execution tạo **phiên bản mới** (không edit bản gốc).
- Formats: .xlsx/.pptx/.docx/.pdf.
- Lưu ý: nếu Claude Slides/Docs đang bật, yêu cầu có thể trả về **artifact** thay vì file.

**Tạo custom skill (không cần code):**

1. Mô tả skill trong chat.
2. Trả lời interview questions (mục đích, output tốt, use cases).
3. Upload reference materials (templates, style guides, exemplars).
4. Save skill → quản lý/sửa qua Customize.

Fallback: download file → Customize > Skills > Add → Upload skill.

**Security:** chỉ install custom skills từ trusted sources; review nội dung trước khi dùng; custom skills upload private tới khi share.

### 4.3 Phân công Projects vs Skills

> **"Projects store knowledge, skills perform tasks."** — Projects là *what*, Skills là *how*; bổ trợ nhau (skill có thể pull knowledge từ project).

| | Projects | Skills |
| :--- | :--- | :--- |
| **Purpose** | Lưu knowledge Claude tham chiếu | Định nghĩa process Claude thực thi |
| **Best for** | Long-term context, tài liệu tham chiếu, team collaboration | Workflow lặp lại, task đa bước, methodology nhất quán |
| **Persistence** | Knowledge có mặt trong mọi chat của project | Instructions áp dụng khi skill được invoke |

### 4.4 Artifacts — deliverables chỉnh sửa & chia sẻ được

Outputs standalone (documents, decks, designs, dashboards, prototypes) mở trong **cửa sổ riêng cạnh chat**; **persist trong Artifacts tab** độc lập với conversation. Ép tạo: *"Create this as an artifact"*.

| Tool | Dùng cho | Năng lực |
| :--- | :--- | :--- |
| **Claude Design** | Landing pages, mockups, prototypes | Import design system cho draft đúng brand; edit canvas (kéo, resize, align) |
| **Claude Slides** | Presentations | Notes/reports → outline + dàn slide; sửa, thêm ảnh, present trong Claude, export |
| **Claude Docs** | Living documents | Draft + clarifying questions + giải thích lựa chọn trong comments; collaborative real-time; nhúng charts từ connected tools |

Có trên mọi plan kể cả Free (admin có thể tắt). Charts nhúng là **snapshots** — nhờ refresh. Liên thông: *"turn this doc into a deck"*, *"make a one-pager from this deck"*.

**Artifact vs file creation:**

- **Artifact** — mở/cập nhật trong Claude, share bằng link.
- **File** — .docx/.xlsx/.pptx/PDF tải về dùng app khác.

**3 cách edit (kết hợp được):**

1. **Edit trực tiếp** — gõ, kéo; edit của bạn và Claude cùng tồn tại.
2. **Comment** — @-mention Claude trên phần tử cụ thể.
3. **Just ask** — yêu cầu trong conversation.

**Sharing theo plan:**

| Plan | Hành vi |
| :--- | :--- |
| Mặc định mọi plan | Private; người nhận cần tài khoản Claude; mời theo name/email với quyền view/comment/edit từng người |
| Pro/Max | Thêm lựa chọn share link cho bất kỳ ai — chỉ artifact được share, conversation vẫn private |
| Team/Enterprise | Link mặc định trong org; external sharing cần Owner bật (Organization settings > Artifacts) |

**Export:**

- Deck → .pptx / Google Slides / .pdf.
- Design → .pptx / .pdf / .html.
- Doc → Google Docs / .docx.

**5 pro tips:**

1. **Request the deliverable** — "summarize Q3" ra chat text, "turn Q3 into a one-page doc for leadership" ra artifact chia sẻ được.
2. **Be specific** — budget tracker có chart + cảnh báo overspend.
3. **Describe the end user** — flowchart "cho nhân viên mới" ≠ framing cho engineering team.
4. **Build on prior work** — *"best artifacts come at the end of a conversation"*, lúc context giàu nhất.
5. **Refresh stale data.**

---

## 5. Mở rộng reach: Connectors → Enterprise Search → Research

### 5.1 Connectors — Claude với tới tools thật của bạn

Thay vì dán bản copy, **tham chiếu file/thread thật**; sau khi kết nối: search, read, và (nơi được phép) **act thay bạn**.
Nền tảng là **MCP (Model Context Protocol)** — "USB-C for AI", open standard, một interface cho mọi connector.

**2 loại:**

- **Web connectors** — dịch vụ cloud: Google Drive, Notion, Slack, Asana.
- **Desktop extensions** — chạy local qua Desktop app: local files, browser control, native apps.

Rule of thumb: local → desktop extension; internet → web connector.

**Kết nối:** directory tại **claude.ai/directory** hoặc Customize > Connectors. Web connector 5 bước:

1. **Find** connector trong directory.
2. **Connect** (Team/Enterprise: Owner thêm org-wide trước).
3. **Authenticate** tài khoản.
4. **Grant permissions** — review kỹ.
5. **Test** kết nối.

Desktop extensions: Settings > Extensions > Install. Không có tool → thêm custom connector.

**Ứng dụng theo nhóm:**

- **Project management** (Asana, Linear, Jira): task ưu tiên, tạo task, launch status.
- **Communication** (Slack, Gmail): tìm thread hợp đồng, draft reply, nhắc quyết định.
- **Documentation** (Notion, Drive, Confluence): tìm guidelines, tóm tắt notes.
- **Business** (Stripe, PayPal, HubSpot): xu hướng doanh thu, giao dịch >$1,000.

**Security:**

- **Scoped access** đúng mức cần.
- **"Claude sees what you see"** — chỉ data bạn có quyền, không inbox người khác.
- **Revocable** bất cứ lúc nào.
- Chỉ install từ **trusted sources**.

### 5.2 Enterprise Search — tri thức cả organization (Team/Enterprise, admin kích hoạt)

Entry **"Ask {Org}"** trong sidebar — "pre-built project cho cả organization": knowledge base công ty nạp sẵn, tối ưu riêng cho **information gathering** (khác chat thường + connectors).
Trả lời **luôn kèm citations**.

**Phù hợp** — câu hỏi trải nhiều nguồn/cần synthesis:

- Bắt kịp khi vắng mặt (blockers của project X).
- Policy & process.
- Research nội bộ (lý do khách chọn đối thủ).
- Onboarding (ai phụ trách billing).
- Tracking quyết định.

**Setup 2 bước:**

1. **Admin:** "Ask Your Org" → Set up → connect tools.
   Bắt buộc ≥1 **Documents connector** (Google Drive/SharePoint) + ≥1 **Chat connector** (Slack/Teams); email optional nhưng nên; đặt tên project.
2. **Users:** mở project → authenticate từng service → hỏi.

Càng nhiều connectors → kết quả càng toàn diện.

**Security:**

- **Permission mirroring** — chỉ hiển thị content bạn vốn có quyền trong tool gốc.
- Conversations **private**.
- **No separate indexing** — data không bị index/lưu riêng.

### 5.3 Research — systematic investigator (Pro/Max/Team/Enterprise)

Agentic, không phải single search:

- Nhiều searches xây trên nhau, Claude tự đuổi lead + lấp gaps.
- Dùng **Thinking** để plan trước.
- Chạy vài phút, hàng trăm nguồn.
- Mọi claim có **citations kiểm chứng được**.

**4 bước:**

1. **Plan approach** — bẻ yêu cầu, map góc điều tra.
2. **Multiple searches** — xây trên kết quả của nhau.
3. **Synthesize** — gộp web + integrations (Gmail, Calendar, Drive).
4. **Citations** — kiểm chứng được.

**Bật:** nút **+** → Research → submit (⚠️ cần **web search** bật — cùng menu). Vì run mất vài phút, đầu tư vào prompt:

- **Specific về mục tiêu** — không "EV market" mà "thị trường pin: key players, tech trends, supply chain risks phục vụ quyết định đầu tư".
- **Specify structure** — sections theo tên.
- **Include constraints** — budget, timeline, geography.
- **Refine prompt với Claude** trước khi bật.

**Với integrations:**

- "Tóm tắt discussion Project X qua email/Slack, rồi research industry best practices."
- "Review calendar tuần tới và research từng công ty gặp."
- "Tìm docs pricing nội bộ và so với đối thủ."

### 5.4 Bảng quyết định 4 chiều

| Dùng **Research** khi… | Dùng **web search** khi… | Dùng **Thinking** khi… | Dùng **Enterprise Search** khi… |
| :--- | :--- | :--- | :--- |
| Báo cáo đa nguồn toàn diện | Cần 1 fact nhanh, cụ thể | Deep reasoning, không cần info ngoài | Đáp án từ docs/Slack/email nội bộ |
| Phân tích web + integrations | Chỉ 1–2 nguồn | Toán, debug code, logic | Onboarding: policy, process, quyết định cũ |
| Điều tra mất hàng giờ nếu làm tay | Tốc độ ưu tiên | Đáp án đến từ suy luận, không thu thập | Câu hỏi đặc thù công ty, không có trên web |
| So sánh cạnh tranh/nhà cung cấp | | | |

---

## 6. Use cases theo role — khởi đầu từ pattern có sẵn

| Role | Pattern tiêu biểu |
| :--- | :--- |
| **Chung** | Generate project status reports · phân tích patterns trong user feedback · đóng gói brand guidelines thành **skill** |
| **Sales** | Build **battle card library** (competitive intel) · prepare for deals (research prospects + talking points) · sales reports từ pipeline data |
| **Marketing** | Analyze campaign performance (insight → budget reallocation) · adapt content across platforms |
| **Finance** | Build financial models · draft investment memos · decode + mở rộng spreadsheet thừa kế |
| **HR** | New hire onboarding guides theo role |
| **Legal** | Track discovery timelines · phân tích patterns trong legal documents |
| **Research** | Plan literature review · verify statistics từ raw data |

**Use Case Gallery (156 use cases, 11/2026)** — phân bố theo nhóm:

- **Chung:** 28 · **Cá nhân:** 18 · **Finance:** 18 · **Sales:** 12 · **Marketing:** 12 · **Operations:** 11
- **Education:** 10 · **Legal:** 10 · **Engineering:** 9 · **Product:** 7 · **Design:** 7 · **Research:** 7
- **HR:** 6 · **Data:** 1

Mỗi trang có prompt mẫu theo bước (Describe the task → Give Claude context → …) + nút "Try in Claude". → Chi tiết đầy đủ trong `Claude_Course_UseCases.md`.

---

## Phụ lục: Key facts

### A. Yêu cầu theo plan

| Tính năng | Plan |
| :--- | :--- |
| Artifacts (Design/Slides/Docs), Claude Design | Mọi plan kể cả Free (admin có thể tắt) |
| Cowork, Research | Pro, Max, Team, Enterprise |
| Computer use (Cowork) | Pro, Max (research preview) |
| Claude in Chrome | Pro, Max, Team, Enterprise |
| Enterprise Search | Team, Enterprise (admin kích hoạt) |
| Memory default | Bật Free/Pro/Max · Tắt Team/Enterprise |

Team/Enterprise: admin quyết định bật/tắt designs, decks, documents; Owner quản org-wide skills, connectors, external artifact sharing.

### B. Settings quick reference

| Việc cần làm | Đường dẫn |
| :--- | :--- |
| Preferences toàn cục | Settings > Account > "Instructions for Claude" |
| Memory review/edit | Settings > Memory |
| Bật Skills (code execution + file creation) | Settings > Capabilities |
| Quản lý skills | Customize > Skills |
| Tìm/thêm connectors | claude.ai/directory · Customize > Connectors · nút + > Connectors |
| Desktop extensions | Settings > Extensions |
| Cowork plugins | Customize > Plugins |

### C. Tài nguyên tiếp theo

- Collaborating with AI.
- AI Capabilities and Limitations.
- Use Case Gallery.
- Anthropic Help Center + Prompting docs.
- Connector Directory.
- Loạt khóa chuyên sâu: Claude Code in Action, Introduction to Claude Cowork.

> **Nguyên tắc chốt:** "Claude is designed to be a collaborator, not a replacement" — bắt đầu từ **một recurring task** trong tuần, iterate. Kỹ năng sắc qua thực hành.
