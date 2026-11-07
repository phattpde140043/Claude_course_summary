# Claude 101 — Executive Reference

> **Nguồn:** Claude Academy — khóa *Claude 101* (15 lessons + 2 videos + Use Case Gallery 156 use cases)
> academy.claude.com · quét 11/2026
>
> **Đối tượng:** người làm technical đã quen dùng AI assistant. Bỏ toàn bộ phần onboarding/dẫn dắt; chỉ giữ các thông tin mang tính quyết định.
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

Claude cung cấp năng lực xử lý và suy luận; con người cung cấp ngữ cảnh và khả năng phán đoán. Giá trị thực sự nằm ở sự kết hợp giữa hai yếu tố này.

Toàn bộ khóa học triển khai luận điểm trên thành 5 nguyên tắc vận hành:

| # | Nguyên tắc | Hệ quả thực hành |
| :--- | :--- | :--- |
| 1 | Làm việc với tình huống, không chỉ câu hỏi | Giao cho Claude việc có ngữ cảnh cá nhân (bản draft của bạn, dữ liệu của bạn); việc tra cứu thông tin thuần túy vẫn thuộc về công cụ tìm kiếm |
| 2 | Chất lượng đầu ra cần được cải thiện và kiểm chứng | Khung prompt 3 yếu tố → iterate → troubleshooting → evals → delegation diligence loop |
| 3 | Chọn công cụ theo đặc điểm công việc | Chat: tương tác liên tục · Cowork: task nhiều bước · Code: phát triển phần mềm |
| 4 | Phân biệt tri thức, quy trình và sản phẩm đầu ra | Projects quản lý tri thức · Skills chuẩn hóa quy trình · Artifacts tạo sản phẩm dùng/chia sẻ được |
| 5 | Mở rộng khả năng truy cập thông tin | Theo 3 tầng: cá nhân (Connectors/MCP) → tổ chức (Enterprise Search) → bên ngoài (Research) |

---

## 1. Mô hình hợp tác: situation, không chỉ question

Ranh giới giữa những công việc nên giao cho Claude và những công việc có thể tự tra cứu không nằm ở chủ đề. Ngay cả reviews, invoices hay tỷ giá cũng có thể được xử lý bằng công cụ tìm kiếm thông thường.
Ranh giới nằm ở chỗ **câu trả lời có cần "bạn" trong đó không**: bản draft của bạn, deck cũ của bạn, cách bạn đánh giá khách hàng.
Công cụ tìm kiếm nhận một câu hỏi (question); Claude nhận một tình huống (situation).

| Search box xử lý được | Cần Claude (có ngữ cảnh cá nhân) |
| :--- | :--- |
| "Tỷ giá USD→EUR hôm nay?" | "Viết lại update trễ deadline của tôi sao cho đọc như một quyết định, không phải lời xin lỗi" |
| "Khác nhau giữa PO và invoice?" | "Cấu trúc tốt nhất cho QBR của tôi" |
| "Có bao nhiêu ngày làm việc giữa 3/3 và 24/3?" | "Đọc thread khiếu nại này — khách thực sự muốn gì trước khi tôi trả lời?" |

### 1.1 Năng lực cốt lõi

| Năng lực | Điểm đáng nhớ |
| :--- | :--- |
| Writing & content creation | Nhận chỉ dẫn về giọng văn và phong cách; iterate tới khi đúng yêu cầu |
| Research & analysis | **Context window 200K+ tokens** (~500+ trang tài liệu); tối đa **1M tokens** (Pro/Max/Team/Enterprise, model hỗ trợ) |
| Coding assistance | Write/debug/explain code đa ngôn ngữ — một trong những điểm mạnh lớn nhất |
| Problem-solving & reasoning | **Thinking mode**: suy luận từng bước cho vấn đề cần phân tích kỹ |
| Learning | **Learning mode**: dẫn dắt suy luận thay vì đưa sẵn đáp án |

### 1.2 Chọn model

| Model | Khi nào | Lưu ý |
| :--- | :--- | :--- |
| **Claude Opus** | Tác vụ phức tạp nhất (phân tích tài chính nhiều bước) | Hybrid reasoning; đổi model phải mở chat mới |
| **Claude Sonnet** | Sử dụng hằng ngày — **lựa chọn mặc định được khuyến nghị** | Cân bằng năng lực/chi phí |
| **Extended thinking** | Phân tích sâu | Tăng **latency** — câu hỏi đơn giản nên dùng Sonnet và tắt thinking |

### 1.3 Nền tảng

- **Constitutional AI:** nhất quán với giá trị con người, minh bạch.
- **Steerable:** tùy chỉnh theo phong cách, giọng văn và hành vi.
- **Đồng bộ trên mọi thiết bị** (web, desktop, mobile): conversations, projects, memory, preferences.

---

## 2. Prompting & verification: khung 3 yếu tố → iterate → verify

### 2.1 Khung prompt 3 yếu tố

| Yếu tố | Câu hỏi tự vấn |
| :--- | :--- |
| **Setting the stage** | Vai trò, mục tiêu, ngữ cảnh Claude nên biết |
| **Defining the task** | Hành động cụ thể: write / analyze / build… |
| **Specifying rules** | Format, giọng văn/phong cách, ví dụ đính kèm |

Ví dụ đầy đủ:

> *"Tôi là marketing lead tại streaming startup, chuẩn bị Series A pitch deck
> → research thị trường streaming phim độc lập: trends, đối thủ, cơ hội tăng trưởng
> → web research kèm citations, report ≤ 5 trang, có executive summary + market analysis + competitive landscape + growth opportunities."*

Bổ sung ngữ cảnh qua 3 kênh:

- **Uploads:** PDF, DOCX, CSV, TXT, PNG, JPEG — xử lý được cả text lẫn hình ảnh/biểu đồ.
- **Connectors:** xem §5.1.
- **Settings > Account > "Instructions for Claude":** tùy chọn ưu tiên toàn cục.

### 2.2 Iterate — output đầu tiên chỉ là điểm khởi đầu

1. **Follow-up questions:** "Mở rộng điểm 2?", "Ngắn gọn hơn?"
2. **Feedback:** "Tốt, nhưng tone casual hơn"
3. **Redirect/restart:** "Ý tôi là X không phải Y"; nếu kết quả vẫn không đạt yêu cầu, hãy bắt đầu một cuộc hội thoại mới

Mẹo: biểu tượng **bút chì** trên message cho phép chỉnh sửa và gửi lại prompt, thay vì thêm một message mới.

### 2.3 Troubleshooting nhanh

| Triệu chứng | Nguyên nhân | Sửa |
| :--- | :--- | :--- |
| Response chung chung | Thiếu ngữ cảnh | Thêm audience, vai trò, ràng buộc |
| Quá dài/quá ngắn | Claude phải đoán | Nêu rõ số từ / mức chi tiết |
| Sai format | Biết *cái gì* không biết *như thế nào* | Show, don't tell — đưa ví dụ format |
| Tự tin nhưng thông tin không chính xác | Nghe hợp lý, dễ tin | Kiểm chứng thông tin quan trọng, hỏi mức độ tự tin, kích hoạt chức năng tìm kiếm trên web |
| Sai tone | Mặc định không phù hợp | Mô tả tone trực tiếp hoặc đính kèm mẫu style |

### 2.4 Verify: evals + delegation diligence loop

**4D Framework for AI Fluency** (Dakan & Feller):

- **Delegation** — việc gì nên cho AI.
- **Description** — giao tiếp rõ ràng.
- **Discernment** — đánh giá phản biện.
- **Diligence** — trách nhiệm + đạo đức.

Fluency về bản chất là *năng lực phán đoán* (judgment), không phải chỉ là biết thao tác.

**Eval 4 bước:**

1. Thu 5–10 ví dụ của task thật.
2. Viết test prompts với context tự nhiên.
3. So sánh output (accuracy, tone, gaps).
4. Refine prompt và lặp.

**Delegation diligence loop** — xây niềm tin trên dữ liệu đã biết kết quả đúng:

1. **Identify** — chọn task phân tích muốn giao.
2. **Find** — tìm dữ liệu quá khứ đã có kết quả đúng.
3. **Reproduce & evaluate** — AI làm lại phân tích, đối chiếu kết quả đã biết, ghi chú gaps.
4. **Refine** — hoàn thiện yêu cầu, test lại.
5. **Quyết định** — kết quả khớp → tự tin dùng cho dữ liệu mới; không khớp sau vài lần thử → **task này không nên giao**.

Case minh họa (Rio, Valley Veterans Services):

- Lần 1: AI xác định đúng correlation giữa attendance và placement, nhưng bỏ sót insight về chương trình kết hợp housing + job.
- Hoàn thiện yêu cầu nêu rõ *program type* → AI bắt được insight này.
- Thiếu *enrollment dates* thì AI tự suy đoán (infer) sai — cần cung cấp đủ dữ liệu cho cohort analysis.

> **"Validation builds confidence, but it doesn't eliminate responsibility"** — bạn vẫn phải chịu trách nhiệm (accountable) và minh bạch (transparent) về vai trò của AI.

### 2.5 Cá nhân hóa

| Tính năng | Cơ chế | Default |
| :--- | :--- | :--- |
| **Memory** | Tự lưu vai trò, tùy chọn, quyết định cũ và phong cách làm việc; xem lại/chỉnh sửa tại Settings > Memory; đồng bộ trên mọi thiết bị | **Bật** Free/Pro/Max · **Tắt** Team/Enterprise (cần org Owner cho phép) |
| **Skills** | Instructions tái sử dụng, Claude tự áp dụng khi liên quan | Xem §4.2 |

---

## 3. Bề mặt làm việc: chọn theo đặc điểm công việc (shape of work)

**Nguyên tắc: nhận diện đặc điểm công việc trước — lựa chọn bề mặt theo sau.**

| Đặc điểm công việc | Bề mặt | Dấu hiệu | Tính năng riêng |
| :--- | :--- | :--- | :--- |
| **Turn-by-turn** (tương tác từng lượt) | **Chat** | Câu trả lời định hình câu hỏi tiếp theo (brainstorm, drafting, thinking aloud); cần phán đoán ở mỗi bước | Quick entry (double-tap `Option` trên Mac), screenshots/window sharing, dictation, desktop connectors |
| **Hand-off** (bàn giao cả quy trình) | **Cowork** (Pro/Max/Team/Enterprise) | Task đa bước tuần tự; output là file hoàn chỉnh đặt đúng vị trí; công việc trải qua nhiều công cụ; cần chạy theo lịch trình | Local folder access · Scheduled tasks (chạy remote kể cả khi máy sleep) · Subagents song song · Projects · Browser use · Computer use (research preview, Pro/Max) · Plugins (bundles theo role: sales/finance/legal) |
| **Building software** (xây dựng phần mềm) | **Code tab** (Pro/Max/Team/Enterprise) | Viết/test/chạy/ship code trong codebase thật | Visual diffs, built-in terminal, git-backed versioning · Local: folder tự chọn + dev server · Cloud: GitHub repo, session tồn tại sau khi đóng app (Cowork cũng chạy cloud trên Pro/Max) |

**Kiểm soát trong Cowork:**

- Claude hỏi clarifying questions và hiện plan để bạn theo dõi.
- Bật chế độ **ask-first** → Claude tạm dừng, xin phê duyệt trước các hành động nhạy cảm (VD: gửi email).

**Autonomy settings (Code):** Manually Approve / Accept edits / Plan (soạn plan trước khi thay đổi bất kỳ nội dung nào).

### 3.1 Bản đồ 8 bề mặt

| Bề mặt | Điểm mạnh | Nơi chạy |
| :--- | :--- | :--- |
| **Claude.ai** | Task chung: research, viết, phân tích, tạo file | Web, desktop, mobile |
| **Claude Code** | Codebase navigation, git workflows, tự động hóa công việc lặp lại ít giá trị gia tăng (lint fixes, merge conflicts, release notes) | Terminal, IDE, browser, Slack |
| **Claude Cowork** | Task đa bước, briefs, tổ chức file, phân tích | Desktop (+ web/mobile Pro/Max) |
| **Claude Tag** | Hợp tác nhóm trong Slack: soạn replies, tóm tắt threads, chuẩn bị meeting, onboard qua channel history; bàn giao bug report sang Claude Code session kèm ngữ cảnh | Slack workspace |
| **Claude Design** | Brief/sketch/screenshot → interactive prototype dạng artifact; sinh và so sánh nhiều phương án; khớp design system để bàn giao | Mọi conversation + claude.ai/design |
| **Claude for Excel** | Hiểu formulas/calculation flow multi-tab; update assumptions giữ dependencies; debug #REF!/#VALUE!/circular refs; build pivot tables | M365 sidebar |
| **Claude for PowerPoint / Word / Outlook** (beta) | PPT: outline→deck, chỉnh gọn nội dung, tái cấu trúc · Word: draft theo template, xử lý tracked changes, grounding vào connected sources · Outlook: phân loại inbox, soạn replies có ngữ cảnh threads + calendar | M365 sidebar |
| **Claude in Chrome** | Web research khi đang browse, quản lý email, điền form lặp lại, test flows nhiều bước, giữ ngữ cảnh xuyên suốt các tab (CRMs, dashboards) | Chrome sidebar (Pro/Max/Team/Enterprise) |

An toàn trong Claude in Chrome: xin permission trước hành động rủi ro (mua sắm, chia sẻ dữ liệu cá nhân); chặn mặc định các trang tài chính/nội dung người lớn; admin kiểm soát toàn tổ chức và danh sách trang bị hạn chế.

---

## 4. Kiến trúc tri thức: Projects (tri thức) · Skills (quy trình) · Artifacts (sản phẩm đầu ra)

### 4.1 Projects — workspace có memory riêng

**Dùng khi có ≥1 dấu hiệu:**

- Reference materials dùng lặp lại (meeting notes, reports, historical data).
- Requirements nhất quán (tone, template, trích nguồn).
- Cộng tác nhóm trên một ngữ cảnh chung.

**Setup 3 bước:**

1. **Create:** Sidebar → Projects → + New Project.
   ⚠️ *Claude không thấy project description* — chỉ dành cho con người. Visibility: private hoặc share org (gói Work).
2. **Project instructions:** ngữ cảnh → quy trình → tone/style → yêu cầu cụ thể; áp dụng cho **mọi chat** trong project.
3. **Knowledge base:** upload PDF/DOCX/CSV/TXT/HTML + Google Drive.
   **Đặt tên file mô tả nội dung** — Claude truy xuất (retrieve) theo tên: `Q4-2024-Brand-Guidelines.pdf` ≫ `document1.pdf`.

**RAG:** khi gần chạm context window limit, Claude tự chuyển sang **Retrieval Augmented Generation** — tìm kiếm trong files, chỉ nạp phần liên quan → tăng capacity lên **~10 lần**, có indicator hiển thị.

**Collaboration:** permission `Can view` / `Can edit` / `Owner`; chia sẻ theo name/email, danh sách, hoặc "Everyone at [org]".

**Best practices:**

- Bắt đầu với 1 use case rồi mở rộng.
- **Doc lỗi thời → câu trả lời lỗi thời** — cập nhật knowledge base.
- Instructions mơ hồ → kết quả thiếu nhất quán.
- Tham chiếu tài liệu theo tên ("Dựa trên Q3 report, top concerns là gì?").

### 4.2 Skills — gói process tái sử dụng

**Định nghĩa:** các folder gồm instructions, scripts và resources mà Claude tự động nạp khi cần. Nếu từng nhờ Claude tạo file Excel/PPT/Word/PDF, bạn đã dùng Anthropic Skills chạy ngầm.

| Loại | Nguồn | Ví dụ |
| :--- | :--- | :--- |
| **Anthropic Skills** | Built-in, Anthropic duy trì | Document creation: Excel, Word, PowerPoint, PDF |
| **Custom Skills** | Tự tạo / org tạo | Quarterly variance analysis, brand voice review, compliance checklist |

**Kích hoạt:** Settings > Capabilities → bật **Code execution and file creation** (Team/Enterprise: Owner quản org-wide) → Customize > Skills → bật/tắt từng skill.
Chạy trong **sandboxed environment**; có thể bật **Allow limited network access** khi cần dữ liệu bên ngoài.

**Hành vi:**

- Claude **tự chọn** skill khi liên quan (không cần kích hoạt thủ công).
- Việc dùng skill hiển thị trong chain of thought.
- File execution tạo **phiên bản mới** (không edit bản gốc).
- Formats: .xlsx/.pptx/.docx/.pdf.
- Lưu ý: nếu Claude Slides/Docs đang bật, yêu cầu có thể trả về **artifact** thay vì file.

**Tạo custom skill (không cần code):**

1. Mô tả skill trong chat.
2. Trả lời interview questions (mục đích, output tốt, use cases).
3. Upload reference materials (templates, style guides, exemplars).
4. Save skill → quản lý/sửa qua Customize.

Fallback: download file → Customize > Skills > Add → Upload skill.

**Security:** chỉ cài custom skills từ nguồn đáng tin cậy (trusted sources); kiểm tra nội dung trước khi dùng; custom skill ở trạng thái private cho tới khi bạn chủ động chia sẻ.

### 4.3 Phân công Projects vs Skills

> **"Projects store knowledge, skills perform tasks."** — Projects trả lời *cái gì* (what), Skills trả lời *thế nào* (how); hai bên bổ trợ nhau (skill có thể truy xuất knowledge từ project).

| | Projects | Skills |
| :--- | :--- | :--- |
| **Mục đích** | Lưu tri thức để Claude tham chiếu | Định nghĩa quy trình để Claude thực thi |
| **Điểm mạnh** | Ngữ cảnh dài hạn, tài liệu tham chiếu, cộng tác nhóm | Workflow lặp lại, task đa bước, phương pháp nhất quán |
| **Hiện diện** | Tri thức có mặt trong mọi chat của project | Instructions áp dụng khi skill được gọi (invoke) |

### 4.4 Artifacts — deliverables chỉnh sửa & chia sẻ được

Các output độc lập (documents, decks, designs, dashboards, prototypes) mở trong **cửa sổ riêng cạnh chat**; **được lưu trong tab Artifacts**, độc lập với conversation. Chủ động yêu cầu tạo: *"Create this as an artifact"*.

| Tool | Dùng cho | Năng lực |
| :--- | :--- | :--- |
| **Claude Design** | Landing pages, mockups, prototypes | Import design system để draft đúng brand; chỉnh sửa trên canvas (kéo, resize, align) |
| **Claude Slides** | Presentations | Notes/reports → outline + dàn slide; sửa, thêm ảnh, present trong Claude, export |
| **Claude Docs** | Living documents | Draft + clarifying questions + giải thích lựa chọn trong comments; collaborative real-time; nhúng charts từ connected tools |

Có trên mọi plan kể cả Free (admin có thể tắt). Charts nhúng là **snapshots** — cần nhờ Claude refresh. Liên thông: *"turn this doc into a deck"*, *"make a one-pager from this deck"*.

**Artifact vs file creation:**

- **Artifact** — mở và cập nhật ngay trong Claude, chia sẻ bằng link.
- **File** — .docx/.xlsx/.pptx/PDF tải về dùng app khác.

**3 cách chỉnh sửa (có thể kết hợp):**

1. **Chỉnh sửa trực tiếp** — gõ, kéo; nội dung bạn sửa và nội dung Claude tạo cùng tồn tại.
2. **Comment** — @-mention Claude trên phần tử cụ thể.
3. **Just ask** — yêu cầu trong conversation.

**Chia sẻ theo plan:**

| Plan | Hành vi |
| :--- | :--- |
| Mặc định mọi plan | Private; người nhận cần tài khoản Claude; mời theo name/email với quyền view/comment/edit từng người |
| Pro/Max | Thêm lựa chọn chia sẻ link cho bất kỳ ai — chỉ artifact được chia sẻ, conversation vẫn private |
| Team/Enterprise | Link mặc định trong org; chia sẻ ra ngoài cần Owner bật (Organization settings > Artifacts) |

**Export:**

- Deck → .pptx / Google Slides / .pdf.
- Design → .pptx / .pdf / .html.
- Doc → Google Docs / .docx.

**5 mẹo thực hành:**

1. **Yêu cầu đúng sản phẩm đầu ra** — "summarize Q3" chỉ ra chat text; "turn Q3 into a one-page doc for leadership" ra artifact chia sẻ được.
2. **Nêu cụ thể** — budget tracker có chart + cảnh báo overspend.
3. **Mô tả người dùng cuối** — flowchart "cho nhân viên mới" khác với framing cho engineering team.
4. **Xây trên kết quả có sẵn** — *"best artifacts come at the end of a conversation"*, lúc ngữ cảnh giàu nhất.
5. **Refresh dữ liệu cũ.**

---

## 5. Mở rộng khả năng truy cập thông tin: Connectors → Enterprise Search → Research

### 5.1 Connectors — Claude truy cập và tương tác với các công cụ thực tế của bạn

Thay vì dán bản sao nội dung, bạn **tham chiếu trực tiếp file/thread gốc**; sau khi kết nối, Claude có thể tìm kiếm, đọc và — ở nơi được cấp quyền — **thực hiện hành động thay bạn**.
Nền tảng là **MCP (Model Context Protocol)** — "USB-C for AI": chuẩn mở (open standard), một interface chung cho mọi connector.

**2 loại:**

- **Web connectors** — dịch vụ cloud: Google Drive, Notion, Slack, Asana.
- **Desktop extensions** — chạy local qua Desktop app: local files, browser control, native apps.

Nguyên tắc nhanh: dữ liệu local → desktop extension; dịch vụ internet → web connector.

**Kết nối:** directory tại **claude.ai/directory** hoặc Customize > Connectors. Web connector 5 bước:

1. **Find** connector trong directory.
2. **Connect** (Team/Enterprise: Owner thêm org-wide trước).
3. **Authenticate** tài khoản.
4. **Grant permissions** — xem xét kỹ.
5. **Test** kết nối.

Desktop extensions: Settings > Extensions > Install. Nếu chưa có tool cần dùng → thêm custom connector.

**Ứng dụng theo nhóm:**

- **Project management** (Asana, Linear, Jira): task ưu tiên, tạo task, launch status.
- **Communication** (Slack, Gmail): tìm thread hợp đồng, draft reply, nhắc quyết định.
- **Documentation** (Notion, Drive, Confluence): tìm guidelines, tóm tắt notes.
- **Business** (Stripe, PayPal, HubSpot): xu hướng doanh thu, giao dịch >$1,000.

**Security:**

- **Scoped access** đúng mức cần.
- **"Claude sees what you see"** — Claude chỉ thấy data bạn có quyền, không thấy inbox người khác.
- Có thể thu hồi quyền (**revocable**) bất cứ lúc nào.
- Chỉ cài đặt từ **nguồn đáng tin cậy**.

### 5.2 Enterprise Search — tri thức của cả tổ chức (Team/Enterprise, admin kích hoạt)

Entry **"Ask {Org}"** trong sidebar — một "project dựng sẵn cho cả tổ chức": knowledge base công ty được nạp sẵn, tối ưu riêng cho **việc thu thập thông tin** (khác với chat thường + connectors).
Trả lời **luôn kèm citations**.

**Phù hợp** — câu hỏi trải nhiều nguồn hoặc cần tổng hợp:

- Cập nhật diễn biến trong thời gian vắng mặt (blockers của project X).
- Tra cứu policy và quy trình.
- Research nội bộ (lý do khách chọn đối thủ).
- Onboarding (ai phụ trách billing).
- Theo dõi các quyết định đã đưa ra.

**Setup 2 bước:**

1. **Admin:** "Ask Your Org" → Set up → connect tools.
   Bắt buộc ≥1 **Documents connector** (Google Drive/SharePoint) + ≥1 **Chat connector** (Slack/Teams); email là tùy chọn nhưng nên bật; đặt tên project.
2. **Users:** mở project → authenticate từng service → hỏi.

Nguồn dữ liệu kết nối càng đầy đủ, kết quả tìm kiếm càng toàn diện.

**Security:**

- **Permission mirroring** — chỉ hiển thị content bạn vốn có quyền trong tool gốc.
- Conversations giữ **private**.
- **No separate indexing** — data không bị index/lưu riêng.

### 5.3 Research — quy trình điều tra có hệ thống (Pro/Max/Team/Enterprise)

Research hoạt động như một quy trình nghiên cứu có tính chủ động, thay vì chỉ thực hiện một lần tìm kiếm đơn lẻ. Claude có thể tiếp tục tìm kiếm, mở rộng các hướng điều tra và bổ sung những thông tin còn thiếu trước khi tổng hợp kết quả.

- Dùng **Thinking** để lập kế hoạch trước khi tìm kiếm.
- Một lần chạy kéo dài vài phút, tổng hợp hàng trăm nguồn.
- Mọi claim đều có **citations kiểm chứng được**.

**4 bước:**

1. **Plan approach** — phân tách yêu cầu, xác định các góc điều tra.
2. **Multiple searches** — xây trên kết quả của nhau.
3. **Synthesize** — tổng hợp web + integrations (Gmail, Calendar, Drive).
4. **Citations** — kiểm chứng được.

**Bật:** nút **+** → Research → submit (⚠️ cần bật **web search** — nằm cùng menu). Vì mỗi lần chạy mất vài phút, hãy đầu tư vào prompt:

- **Nêu cụ thể mục tiêu** — không "EV market" mà "thị trường pin: key players, tech trends, supply chain risks phục vụ quyết định đầu tư".
- **Chỉ định cấu trúc** — nêu tên từng section.
- **Kèm ràng buộc** — budget, timeline, geography.
- **Hoàn thiện prompt cùng Claude** trước khi chạy.

**Với integrations:**

- "Tóm tắt discussion Project X qua email/Slack, rồi research industry best practices."
- "Review calendar tuần tới và research từng công ty gặp."
- "Tìm docs pricing nội bộ và so với đối thủ."

### 5.4 Bảng quyết định 4 chiều

| Dùng **Research** khi… | Dùng **web search** khi… | Dùng **Thinking** khi… | Dùng **Enterprise Search** khi… |
| :--- | :--- | :--- | :--- |
| Báo cáo đa nguồn toàn diện | Cần một thông tin nhanh, cụ thể | Deep reasoning, không cần info ngoài | Đáp án từ docs/Slack/email nội bộ |
| Phân tích web + integrations | Chỉ 1–2 nguồn | Toán, debug code, logic | Onboarding: policy, process, quyết định cũ |
| Điều tra nếu làm thủ công sẽ mất hàng giờ | Tốc độ ưu tiên | Đáp án đến từ suy luận, không thu thập | Câu hỏi đặc thù công ty, không có trên web |
| So sánh cạnh tranh/nhà cung cấp | | | |

---

## 6. Use cases theo role — khởi đầu từ pattern có sẵn

| Role | Pattern tiêu biểu |
| :--- | :--- |
| **Chung** | Tạo project status reports · phân tích patterns trong user feedback · đóng gói brand guidelines thành **skill** |
| **Sales** | Xây **battle card library** (competitive intel) · chuẩn bị cho deal (research prospects + talking points) · sales reports từ pipeline data |
| **Marketing** | Phân tích campaign performance (insight → budget reallocation) · điều chỉnh content cho từng nền tảng |
| **Finance** | Xây financial models · soạn investment memos · giải mã + mở rộng spreadsheet thừa kế |
| **HR** | Soạn hướng dẫn onboarding cho nhân viên mới theo role |
| **Legal** | Theo dõi discovery timelines · phân tích patterns trong legal documents |
| **Research** | Lập plan literature review · kiểm chứng statistics từ raw data |

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

Team/Enterprise: admin quyết định bật/tắt designs, decks, documents; Owner quản lý skills, connectors và chia sẻ artifact ra ngoài ở phạm vi org.

### B. Settings — tham chiếu nhanh

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

> **Nguyên tắc chốt:** "Claude is designed to be a collaborator, not a replacement" — bắt đầu từ **một recurring task** trong tuần rồi iterate. Kỹ năng sẽ sắc qua thực hành.
