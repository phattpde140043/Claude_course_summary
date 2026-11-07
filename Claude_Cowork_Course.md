# Introduction to Claude Cowork — Tóm tắt khóa học

> **Nguồn & phương pháp quét** (11/2026): tải **raw HTML** (prerendered) của cả 14 bài tại [academy.claude.com/courses/introduction-to-claude-cowork](https://academy.claude.com/courses/introduction-to-claude-cowork)
> → Trích text sạch → tóm tắt đối chiếu từng phần.
> **Refer links** trong nội dung (5 bài support/docs) đã quét đầy đủ — xem Phần B.
> ℹ️ Không có YouTube link hay media asset nào trong nội dung 14 bài (video là embed nội bộ Academy; ảnh chỉ là og:image của khóa).

## Mục lục

| Phần | Nội dung |
| :--- | :--- |
| **A** | 14 bài học của khóa |
| **B** | 5 refer links: Get started · Safely · Work across M365 · Outlook · Chrome |

---

# PHẦN A — 14 bài học

## Bài 1: What is Claude Cowork (15′)

### Key takeaways
- **Cowork là Claude dựng cho *công việc*, không chỉ cho *câu trả lời*** — gặp bạn nơi bạn làm việc: máy local, cloud apps, hay browser
- **Cowork là về delegating**: chat vẫn là nơi nghĩ thành tiếng, draft, hỏi đáp; Cowork thêm khả năng mô tả **outcome** rồi Claude plan → execute → deliver toàn bộ
- Dựng cho việc **đa bước, chạy dài**, trải nhiều tools, kết thúc bằng **artifact thật**
- **Bạn giữ quyền kiểm soát**: Claude hiện plan trước khi bắt đầu; mặc định hỏi trước các hành động quan trọng (gửi, xóa, share); cho steer bất kỳ lúc nào

### Cowork thực chất là gì
Claude làm việc **cùng** bạn:

1. Trỏ vào folder/project
2. Connect các apps (Gmail, Slack, Google Drive, calendar)
3. Mô tả việc cần → Claude lập plan, chạy từng bước, dùng tools/files cần thiết, trả về **deliverable thật**

Dùng được trong desktop app, web, mobile; **desktop app** là chỗ dùng khi việc liên quan files trên máy (Claude mở/lưu trực tiếp).

Cách vào Cowork tùy version: có bản có tab riêng, có bản mô tả task trong conversation thường → Claude chuyển thành Cowork task.

**Mental model quan trọng nhất:** dùng Cowork cho việc bạn thường **tự làm**, không phải việc bạn thường **hỏi về**.

Cơ học:

- **Chat**: turn-by-turn, bạn tự ghép các bước
- **Cowork**: duy trì trọn mảng việc — pull từ nhiều tools cùng lúc, chạy plan đa bước, trả output hoàn chỉnh

### Cowork làm việc trong môi trường của bạn
- **On your files** — đọc folder bạn trỏ vào, viết output hoàn chỉnh về cùng chỗ
- **In your apps** — pull context từ email/calendar/messaging/drive/CRM đã connect
- **In your browser** — tool không có connector → **Claude in Chrome** đọc và hành động trên chính trang đó (dashboards, portals, mọi thứ sau login)
- **With your tools** — Claude *hành động*, không chỉ mô tả

### Chat vs Cowork vs Claude Code
> - **Chat** = thinking *with* Claude
> - **Cowork** = delegating *to* Claude
> - **Code** = building software *with* Claude.

- **Chat**: dialogue turn-by-turn — trao đổi nhanh, brainstorming, exploratory thinking, **một tool mỗi lúc**; purpose-built cho bounded exchanges
- **Cowork**: working session — với tới nhiều tools, giữ nhiệm vụ theo thời gian, trả finished outputs *(khoảng cách mà upload files vào Chat không bao giờ bít nổi)*
- **Code**: môi trường dev đầy đủ chạy trong codebase, có terminal + git — cho developer viết và ship phần mềm

Knowledge worker dành phần lớn thời gian cho hai cái đầu — cho những việc rất khác nhau.

## Bài 2: Setting up Claude Cowork (20′)

### Trỏ Claude vào folder
- Click **"Work in a project or folder"** trong prompt bar → chọn folder — **quyết định setup quan trọng nhất cho mỗi task**
- Folder là nơi việc sống, Claude đọc mọi file bên trong (Word, Excel, PDF, PPT...) và **lưu output về đúng chỗ đó**
- Folder là nơi Cowork có quyền **read AND write** — khác hẳn attach file vào tin nhắn
- Chọn folder **scoped cho một project/stream of work** (không cần cả Documents folder); folder thật có context phù hợp (source materials, templates)
- **Cloud files khác local**: nhiều connector (Google Drive, M365 mặc định) chỉ **read-and-search**; số khác create/edit được — kiểm tra mô tả từng connector khi bật
- Task khởi động từ web/phone với tới connectors nhưng **không** với tới local folders

### Thêm connectors
- Setup một lần trong **Customize**, bật/tắt theo từng task. Nhóm nên cài trước:
  - **Email + calendar** (Outlook qua M365 / Gmail)
  - **Messaging** (Slack / Teams)
  - **Cloud storage** (SharePoint, OneDrive, Google Drive, Box)
  - **CRM/project** (Notion, HubSpot, Salesforce, Asana, Linear)
- Bật xong tham chiếu tự nhiên trong prompt: *"Check what the team said in Slack about the launch"*
- Tool không có connector → Claude in Chrome là cầu nối (có thể không khả dụng trên một số enterprise plans)

### Permissions model
- Chọn folder = tự động authorize read/write trong đó
- 2 mode:
  - **"Ask before acting"** (mặc định — pause trước mỗi hành động chạm thế giới ngoài: gửi email, post message, share file)
  - **"Act without asking"** (chỉ dùng cho tools/tasks bạn tin tưởng)
- **Không đổi được ở cả 2 mode**: Claude *luôn* hỏi trước khi **permanently deleting** một file — prompt đó không thể skip

### Try it now (4 bước)
1. Chọn folder chứa việc thật (chưa yên tâm thì copy sang folder mới — nhưng dùng **vật liệu thật**, không phải toy files)
2. Connect một app (email + cloud storage thường có giá trị nhất đầu tiên)
3. Prompt: *"Take a look at everything in this folder and write me a brief on what you've learned — what's in the folder, how the documents relate to one another, any surprising insights..."*
4. Đọc brief, đối chiếu với hiểu biết của bạn: Claude bắt được gì bạn might have missed? Miss gì?

## Bài 3: What Cowork can do for you (10′)

### 3 pattern của task hợp với Cowork
1. **Multi-step** — trong một prompt: gather context → compare → research → draft → format. VD:
   - *triage tuần email feedback khách hàng thành themes kèm quotes*
   - *pull số từ 3 báo cáo + spreadsheet → dashboard tương tác*
2. **File-based** — mục tiêu là **artifact thật** (Word, spreadsheet, deck, PDF) đúng format cần; inputs cũng thật: Claude đọc/sửa/lưu file sẵn có trong folder. VD:
   - *proposal theo template chuẩn + meeting notes*
   - *monthly metrics report có charts từ raw spreadsheets*
3. **Multi-tool** — việc chạm Gmail, Slack, M365, calendar, CRM qua connectors; điểm khác chat thường: Cowork **plans across them và chạy cả chuỗi như một lần delegate**. VD:
   - *draft follow-up emails sau meeting từ invite + attendees + notes*
   - *search Slack mọi điều team nói về launch → synthesize thành update*

### Scheduled tasks (`/schedule`)
- 2 cách:
  - Gõ **`/schedule`** từ đầu (Claude draft prompt cho bạn review)
  - Hoặc tự nhiên hơn: **làm việc đó một lần**, confirm output đúng, rồi `/schedule` biến chính process đó thành recurring
- Chọn cadence (hourly, daily, weekdays, manual) → review prompt → accept
- **Nơi chạy tùy nhu cầu**:
  - Chỉ dùng connectors → chạy **remote**, máy không cần bật
  - Cần files/apps trên máy → chạy trên máy, **desktop app phải mở** đúng giờ (máy đóng/ngủ/tắt → Claude nhặt việc lại khi bạn trở về và báo biết là bị delay)
- Ý tưởng:
  - Friday review (what shipped + decisions trong Slack/Teams + preview tuần sau)
  - Monthly roll-up ngày 1
  - Morning briefing cho meetings từ notes cũ + email threads

### Làm việc xa bàn làm việc
- Web + mobile app: start từ điện thoại, check từ browser nào, nhận deliverable ở bàn. Task chạy **remote** — không gì cần để bật
- 2 lưu ý: task từ web/phone **không với tới folder trên máy** (cần local files → start từ desktop app); **task ở lại nơi nó bắt đầu** — muốn đổi nơi chạy thì start task mới
- VD:
  - Trên đường đi nhớ client call cần one-pager về support tickets quý trước → nhờ Cowork từ app điện thoại pull tickets từ support tool + draft — review khi tới chỗ
  - Vendor gửi hợp đồng sửa lúc offsite → so với bản năm trước trong Drive từ điện thoại
- ⚠️ Nếu organization quản lý Claude giúp bạn thì **admin quyết định** việc bật các tính năng này

## Bài 4: Hand Claude Cowork your first task (25′)

> Nhịp làm việc: *"less like prompting a chatbot, more like briefing a smart colleague who's about to disappear into a task and come back with something done."*

### Prompt tốt làm 3 việc
1. **Names the deliverable** — "a one-page brief", "a slide for the QBR", "a ranked list with notes per candidate": cụ thể format + độ dài tránh regenerate
2. **Names the inputs** — folder nào, channel nào, date range nào, application nào: Cowork tốt đúng mức context bạn trỏ vào
3. **Names specifics/nuances** — *"I want base, best, worst scenarios that account for the 3 new locations we opened in Q3"*: loại output mong muốn + insight chuyên môn Claude không tự thấy

Nhiều công hơn upfront — đổi lại phần back-and-forth dồn về **trước khi** Claude bắt đầu, thay vì 5 vòng "actually, can you also..."

### Trả lời clarifying questions
Claude hỏi để đóng gaps **trước khi** lao vào việc (khi delegate, Claude đi mất và quay lại với artifact hoàn chỉnh — mọi context gap phải lộ qua câu hỏi).

Đa số là multiple-choice, click cái phù hợp; không cái nào fit thì trả lời bằng lời của bạn.

### Steer mid-task
Theo dõi plan + progress. Lệch hướng (wrong source, wrong format, wrong tone) → **interrupt ngay**, không đợi xong rồi regenerate; chạy lệch nặng thì **stop run → refine prompt → start lại**.

*"Cowork is built for course corrections, and the cost of a redirect is low."*

### Review deliverable
Xem trước trong app hoặc mở file trong folder. Review như đọc draft của người bạn tin nhưng chưa biết rõ — **discernment bật**. Kiểm tra (nhất là vài lần đầu):
- **Đạt mục tiêu thực sự?** Hay tạo ra thứ gì đó khác tinh tế với yêu cầu?
- **Facts chính xác?** — nhờ Claude chỉ ra docs nó pull từ đâu, rồi tự kiểm tra source
- **Có gì nghe bịa?** — date/name/quote không truy được về input là **cờ đỏ, không phải feature**

Draft gần đúng → bảo Claude sửa (nó nhớ conversation, **edit nhanh hơn regenerate**). Draft sai kiểu **load-bearing** → prompt thiếu context load-bearing — chỉ Claude tới context mới và nhờ điều chỉnh.

## Bài 5: Get better results faster (2′)

**4 building blocks** khiến Claude tốt hơn theo thời gian (context bạn cung cấp một lần cứ tiếp tục trả lãi):
1. **Global instructions** — áp dụng mọi Cowork session
2. **Projects** — Claude tự buildup memory từ conversations bên trong
3. **Skills** — encode workflows lặp lại
4. **Plugins** — chia sẻ expertise của team

Không bắt đầu với cả 4 ngay ngày 1:

- Corrections lặp lại → global instruction candidates
- Workstream lặp → project
- Giải thích cùng workflow nhiều lần → skill đầu tiên
- Process hoàn thiện → plugin đáng share

(Bài 6: instructions + projects — lớp mọi người setup trước; Bài 7-8: skills + plugins kèm hands-on.)

## Bài 6: Standing context — Global instructions và projects (15′)

### Global instructions — standing brief cho mọi session
- Viết một lần trong **Settings → Global instructions** (bản cũ gọi "Instructions for Claude") → Claude tham chiếu trong **mọi** session: chat lẫn scheduled task
- Nên có: bạn là ai/làm gì; shorthand/acronyms (để khỏi phải giải thích "the QBR deck"); cách bạn muốn output (format, length, tone)
- Không cần hoàn hảo ngày một: corrections hay lặp lại (*"share the bottom line up front"*, *"don't use Oxford commas"*) chính là global-instruction candidates

### Projects — workspace scoped cho một stream of work
Global instructions nói về **bạn**; projects nói về **việc bạn đang làm**. Bên trong có 3 thứ bạn setup + 1 thứ Claude tự build:
- **Instructions** — như global nhưng scoped cho project (*"project này cho weekly transformation team meetings — mục đích gather data và chưng cất thành slide deck mỗi tuần"*)
- **Scheduled tasks** — recurring runs thuộc project (Friday status pull, pre-meeting brief, end-of-month rollup) — chạy với project context mỗi lần
- **Context** — folders/links Claude làm việc từ; mọi conversation trong project đều với tới
- **Memory** — Claude tự học từ conversations trong project (bạn không viết) — **đây là khác biệt**:
  - Ngoài project mỗi session fresh
  - Trong project, task mới mở ra đã có tình hình client, quyết định tuần trước, chuyện gì còn open

Phù hợp làm project:

- **Một client/account**
- **Recurring deliverable** (monthly report, quarterly review, weekly leadership update)
- **Một launch/initiative** (redesign, migration, rollout)

### 3 cách tạo project
- **From scratch** (rỗng, thêm dần)
- **From existing folder** (folder thành working directory của project)
- **From existing project** (instructions + knowledge chuyển theo)

Tạo: sidebar **Projects → New project**; đổi working folder/instructions/connectors bất cứ lúc nào.

> Starter template global instructions: *"I'm a [role] at [company], working on [main 1–2 streams of work]. Here are some common [acronyms/shorthand] you need to know. Most of my deliverables are [docs, decks, briefs, models].
> I want updates and briefs concise — lead with the recommendation, keep background to one paragraph. I like to review the .md previews before creating the final document file."*

## Bài 7: Skills — Teach Claude Cowork your way (10′)

### Skill là gì
**Reusable playbook** — folder của files + resources dạy Claude làm một loại việc cụ thể **theo cách bạn muốn**. Task khớp skill → Claude load playbook và làm theo.

Tự động dùng đúng lúc cần (không phải invoke bằng tên); cũng có thể explicit (*"use the board memo drafting skill"*).

### 4 building blocks của skill
1. **Instructions** (`SKILL.md`) — brief nói cho Claude skill làm gì, khi nào dùng, làm thế nào; viết như **runbook cho đồng nghiệp mới**
2. **Assets** — logos, brand templates, slide masters, fonts: nguyên liệu cho output "thật"
3. **References** — ví dụ output tốt, style guides, clause libraries: dạy Claude **"good" trông thế nào**
4. **Scripts** — code nhỏ cho phần process phải y hệt mỗi lần (variance calculation, structured comparison, chart/doc formatter)

Kết hợp tùy việc — có skill chỉ cần SKILL.md là đủ; có skill đủ cả 4. *"The mix follows the work: include what needs to be included, nothing more."*

### Build skill với Claude (nhanh nhất)
Prompt: *"I want to build a skill for [recurring process you're tired of re-explaining]. Walk me through what you need to know."*

1. Claude hỏi: skill làm gì, khi nào trigger, output tốt ra sao, resources nào
2. Xuất **skill folder** (SKILL.md + assets/references/scripts) sẵn install

Quản lý trong **Customize**; muốn sửa cứ nói correction — *"Add a step that flags any deal over $100K that slipped two stages"* — Claude update **in place**.

Skill hoạt động trong mọi conversation, kể cả trong project.

## Bài 8: Plugins — Encode your team's expertise (15′)

### Plugin là gì
**Packaged set of skills built around a job** — skills + connectors + **subagents** chúng phụ thuộc.
Subagent = purpose-built helper skill spin up để xử lý một phần việc trong context riêng — VD research subagent cho bước research, drafting subagent cho bước draft.

Expertise **đi theo install, không theo người**: install finance plugin → Claude biết cách team bạn phân tích equities.

### 2 hình dạng plugin
1. **End-to-end process bundle** — việc nhiều bước tuần tự: monthly-close plugin = skills kéo actuals + build variance table + draft board memo — team install một cái, có trọn process
2. **Bộ skills dùng nhiều nhất** — các jobs độc lập: finance plugin = variance analysis + financial modeling + investment-memo drafting + quarterly reports

Hình dạng đúng: plugin là package quanh **workflow** — "Renewal prep cho CS team" là plugin; "Equity research cho quỹ" là plugin.

### Install / Customize / Build
- **Install**: **Customize → Plugins** → chọn plugin khớp việc → **Install** → duyệt connectors plugin dùng → skills sẵn dùng ngay
- Anthropic publish plugins cho các role phổ biến (finance, legal, sales, marketing, customer support, PM...)
- **Customize**: marketplace plugin là **điểm khởi đầu mạnh, không phải câu trả lời cuối**:
  - Customize → Plugins → [tên] → **Customize** mở Cowork task để bạn làm cùng Claude định hình plugin: chỉ vào assets, share context, upload examples
  - VD: *"Here are our last three red-lined NDAs. Update the /nda-triage skill in this plugin so the format and tone match these"*
- **Build your own**: bundle skills workflow cần + connectors + package. Bắt đầu nhỏ: 1 skill → 3-4 skills là plugin đáng share (Bài 13)
- ⚠️ Admin có thể đã publish plugins cho org — **check Directory trước khi tự build**
- Try: gõ **`/setup-claude`** → Claude phỏng vấn loại việc bạn làm → đề xuất plugin phù hợp → install ngay từ chat

## Bài 9: Claude in Chrome (10′)

### Key takeaways
- **Cầu nối cho tools không có connector** — mọi thứ sống trong browser, Claude đọc và hành động trên trang
- **Chrome + Cowork làm việc cùng nhau**: Claude gather info + hành động trong browser, lấy kết quả build deliverable trong Cowork — *one conversation, both surfaces*
- Mặc định hỏi trước hành động nhạy cảm; bạn approve/deny từng cái

### Mở khóa được gì
- **Internal dashboards**: Tableau của finance, Looker của sales ops — Claude pull số, download về máy, dùng làm context cho Cowork tasks
- **Vendor portals & customer systems**: procurement portal không API, CRM sau SSO, support tool — Claude navigate, pull, hành động như bạn
- **Web apps sau login**: mọi thứ có browser interface (kể cả tool team bạn tự build) đều scriptable —
  *"Open the procurement system, find every PO from our top ten suppliers in Q3, and pull the line items into a spreadsheet"*
- **Web research kết thúc bằng deliverable**: mở 10 tabs, pull từng trang, thành brief — không copy-paste

### Ví dụ phối hợp với Cowork
Dashboard customer health sau login, không connector, cần summary một trang các account yellow/red trước thứ Sáu:
> *"Open the customer health dashboard in Chrome, pull every account showing yellow or red, and for each one, pull the past 30 days of activity from the customer's folder in Drive and recent threads in #customer-success in Slack.
> Build a one-page summary I can review before my Friday call."*

Claude giao browser steps cho Chrome, lấy data, pull thêm context từ Drive + Slack, build summary vào folder — **một lần delegate, ba nguồn context**.

### Watch-outs
- **Bạn phải tự đăng nhập** — Claude không sign in hộ; nó làm việc trong session bạn đã authenticated
- **Cân nhắc quyền trên web**: Claude thấy những gì bạn thấy — kể cả mọi thứ bạn có quyền trên open web; site nhạy cảm → thu hẹp phạm vi + review từng action trước approve

## Bài 10: Claude for Microsoft 365 (5′)

### Key takeaways
- Claude là **add-in ngay trong Word, Excel, PowerPoint, Outlook** — làm việc trên file/space đang mở
- **Một conversation mang context xuyên các apps**: build analysis trong Excel → đẩy sang PowerPoint làm slide; Word memo làm nguồn cho draft reply Outlook
- **Cowork vs M365 = công cụ khác nhau cho thời điểm khác**:
  - Cowork build deliverable hoàn chỉnh từ nhiều nguồn
  - Claude trong M365 để **refine, debug, shaping file bạn đang làm** — và mang context từ file đó sang docs khác

### Claude làm gì trong từng app
- **Excel**: phân tích dữ liệu, viết formulas, debug `#REF!` + circular references, chạy scenario tests không phá model, build sheet từ template, **cite ngược về cell cụ thể**
  - Move mạnh nhất: *"Pull the actuals from the Q3 sheet, compare them to the Q3 plan in the same workbook, and write the variance commentary in column F next to each line item"*
- **PowerPoint**: đọc slide master, fonts, color scheme → build slides đúng brand; charts **native, editable** (không phải ảnh dán); thao tác trên slide đang chọn
  - Move: *"Take the analysis I just did in Excel and turn it into a three-slide deck for the QBR, using our deck template"*
- **Word**: draft/revise/reformat tại chỗ; làm việc với **comments + tracked changes**; pull context từ connected sources
  - Move: *"Draft the executive summary based on the body of this memo and the source data referenced in the appendix"*
- **Outlook**: triage mail với context từ phần còn lại của công việc; draft replies phản ánh threads cũ, calendar, quyết định gần đây

### Chuỗi cross-app trong một conversation
- **Outlook → Word**: client brief vào inbox → *"Open the brief in Word and start the memo from our firm template"* — Word mở với attachment + email thread đã load trong sidebar
- **Word → Excel**: *"Build the market-sizing model behind option 2"* — Excel mở, pull assumptions từ brief Claude vừa đọc, build model multi-tab với formulas inspect được
- **Excel → PowerPoint**: *"Turn this into the steering-committee deck in the client template"* — deck build theo slide master, native charts với số mới nhất
- **Back to Outlook**: *"Find 30 minutes with the team before Thursday"* — invite draft với attendees, chờ bạn bấm Send

### Khi nào M365, khi nào Cowork
- **Cowork**: việc pull từ nhiều nguồn, kết thúc bằng deliverable (brief từ 20 source files; report từ CRM + 3 Slack channels; workflow theo schedule)
- **M365**: đang làm trong chính Office files — edit tại chỗ + mang context app này sang app kia

Công việc thật dùng cả hai: Claude build draft đầu của deck → bạn mở PowerPoint refine với Claude; Claude pull data vào model → bạn mở Excel nhờ Claude điều tra outlier.

*"The two surfaces hand off cleanly — and the file is the file in both cases."*

## Bài 11: Best practices for working safely (9′)

> Bài 2 là **sàn** (luôn hỏi trước delete; mặc định hỏi trước send/share). Bài này là phần **bạn** tự mang thêm.

### Setup để lỗi không với tới thứ quan trọng
1. **Dedicated working folder, không catch-all** — trỏ Claude vào Documents/Downloads/Desktop = để đồng nghiệp mới lục mọi file bạn có. Tạo folder cho việc, move/copy vào những gì cần, trỏ Claude vào đó
2. **Backup thứ không thay thế được trước khi bắt đầu** — deliverable client cũ, hợp đồng không cấp lại được: giữ bản sao nơi Cowork **không với tới** (cloud, folder khác, ổ không cắm)
   Claude có hỏi trước khi xóa — nhưng giá của việc click nhầm confirmation là giá của file
3. **Test workflow mới trên bản copy trước** — scheduled task chạy mỗi Friday: lần đầu chạy trên **bản copy của data**; thấy ổn rồi mới trỏ vào live folder

### Viết prompt không còn chỗ cho hành động sai
- **Cụ thể hoá destructive verbs**: *"Cut the section"* có thể đọc là remove khỏi view **hoặc** delete khỏi file; *"Update the file"* = rewrite **hoặc** add. Nếu đọc sai là không thể hoàn tác → nói rõ:
  - *"Remove the section from the draft, but keep the file"*
  - *"Add a new appendix; don't rewrite the existing sections"*
- **Ghi rõ bounds trong prompt**:
  - *"Only the 3 most recently updated files"*
  - *"Only contracts that closed in Q3"*
  - *"Don't message anyone — draft only"*
  - → Thu hẹp việc Cowork làm + cho bạn đường ranh rõ để nhận drift
- **Scheduled tasks: draft ban đầu** — chúng chạy khi bạn không xem; tới khi tự tin thì prompt nó **draft cho review** thay vì gửi thay bạn

### 3 kiểm tra tại thời điểm thực
1. **Đọc plan khi nó được tạo** — Claude trình plan trong progress tab: có hợp lý? đúng thứ tự? đúng sources? Redirect nếu cần
2. **Canh pattern bất thường** — không cần validate từng command; nhưng Claude đụng files/sites bạn không nhắc, hay scope phình → **stop task**
   *"Something feels off" là tín hiệu thật — hãy coi trọng nó*
3. **Approve confirmation một cách có chủ đích** — giữ "Ask before acting" cho mọi thứ send/post/share; confirmation hiện ra thì **đọc nó**
   *"Hầu hết sai lầm không xảy ra vì safeguard hỏng — mà vì ai đó click qua một confirmation không hoàn toàn là action họ định làm"*

### Khi Cowork KHÔNG phải công cụ đúng
- **Workflow được regulate cần audit trail** — hoạt động Cowork không nằm trong audit logs/data exports (Compliance API trả transcripts nhưng **chỉ Claude Enterprise**)
- **Việc bạn không tin đồng nghiệp nhanh thông minh làm không giám sát** — gửi legal doc cho counterparty, post thông báo công khai, push customer-facing change: *Claude prepares; you ship*
- **Dữ liệu cá nhân cực nhạy** ngoài ranh giới IT của bạn phê duyệt rõ ràng

> 📖 **Go deeper**: bài [Use Claude Cowork safely](https://support.claude.com/en/articles/13364135) (Phần B.2) nói rõ các guardrail có sẵn và phần bạn còn chịu trách nhiệm khi Claude hành động thay bạn.

## Bài 12: Validating skills for plugins (8′)

### Vì sao cần eval
Skill/plugin là **sản phẩm nhỏ người khác sẽ dùng**.

- Bạn — người build — biết workaround, biết cần hỏi gì, cho file gì, output phải ra sao
- **Teammate không biết gì cả** — họ diễn đạt hơi khác, đưa inputs hơi khác, hoặc dính **edge case** (tình huống thật nhưng ngoài thiết kế của skill)
  - Chính là chỗ skills hay vấp, và người dùng không hiểu vì sao

**Eval = try-out**: request thực tế vào → nhìn output → nói Claude sửa gì. Không code, không test script — chỉ phán đoán của bạn về "đủ tốt để gắn tên mình chưa".

### Hệ thống eval (qua skill-creator)
`skill-creator` (helper built-in) đưa evals vào quá trình build: sinh **2+ prompts thực tế**; mỗi prompt cho **một cặp output**: với skill và **không có skill** — bản sau là comparison point:

Không chỉ hỏi "output có ổn không" mà "có **tốt hơn** cái Claude tự làm không". Review từng cặp, feedback bằng tiếng Anh thường ngay trên review page — thực chất trả lời 2 câu:
- **Bản có skill là bản bạn sẽ dùng?** Có → ghi chú điều làm nó tốt hơn để skill giữ nguyên
- **Không → thiếu/sai gì?** Cụ thể: *"tone is too formal"*, *"it skipped the executive summary"* — cho Claude thứ để hành động; *"this isn't quite right"* thì không

Submit → **Claude revise skill theo feedback**.

### Iterate
- **Đổi một thứ mỗi lần** — round đầu thấy wordy **và** thiếu section: chọn cái quan trọng hơn, fix, re-run, rồi quay lại; bạn sẽ biết cái nào thực sự move the needle
- **Là loop, không phải gate một lần** — chưa ưng thì chạy lại; đa số skill sẵn sàng sau 1-2 rounds
- **Bar để ship**: các case bạn quan tâm pass **meaningfully better than baseline** + bạn đã **nêu tên các case chưa handle**
- Output đẹp ngay round đầu? Xong — *"evals are there for when you need confidence, not ceremony"*

## Bài 13: Share what you build with your team (8′)

### Phân phối plugin trong organization
Cách khuyến nghị: **private marketplace của org** — catalog plugin được duyệt, admin quản lý.

Phân phối là một **hand-off**: bạn mang plugin tới người sở hữu marketplace (team lead, enablement/ops owner, IT) — họ publish, chọn cách landing:
- **Available** — hiện trong company Directory, ai muốn thì install
- **Installed by default** — đã cài sẵn cho mọi người; họ tắt được
- **Required** — cài và **bật mãi** — hợp cho compliance checks ai cũng phải chạy giống nhau

Đồng nghiệp thấy plugin trong Directory gắn nhãn công ty, cạnh các plugin Anthropic công khai; dùng/turn off được (trừ Required), **không edit được** — updates chảy từ người maintain.

Cách này landed thế nào tùy admin org của bạn:

- Có nơi marketplace đã chạy + có owner rõ để trao
- Có nơi chưa bật — đối chiếu tình huống của bạn để biết next step (chưa biết ai là người mang plugin tới marketplace? **Đó chính là next step thật sự của bạn**)

### 4 thói quen giữ plugin shared khỏe
1. **One owner** — mỗi shared plugin có một người có tên: review changes, chạy evals sau mỗi edit, quyết định update/retire
2. **Evals trước mọi publish** — eval loop là gate: case quan trọng không hold up sau change → đừng push cho cả team
3. **Đặt tên skills/plugins cụ thể** — "meeting-prep" sẽ đụng 3 skill meeting-prep khác trong directory; "sales-customer-renewal-prep" thì không
4. **Review rhythm** — hàng quý: cái gì installed, cái gì thực sự dùng, cái gì stale → retire cái không ai chạy, amend theo feedback

## Bài 14: Wrap up and next steps (2′)

**Throughline**: Cowork vượt ra ngoài chat để **delegate việc thật** — mọi thứ khác xây trên đó. Chọn **một** việc làm tuần này:
1. **Set up memory** — global instructions 5 câu, hoặc project cho một stream of work đang có
2. **Schedule/start một task từ điện thoại** — recurring deliverable lên cadence, hoặc việc nảy ra ngoài giờ thì giao cho Cowork từ app
3. **Install một plugin** — Customize → Plugins, plugin gần role nhất, chạy vào việc tuần này
4. **Thử Claude in Chrome hoặc M365** — chọn surface khớp nơi công việc thật của bạn xảy ra
5. **Chia sẻ thứ bạn build** — use case, workflow, hay skill cho team; có thể bạn là "unlock" họ cần

**Học sâu hơn**:

- AI Fluency: Framework & Foundations
- AI Capabilities and Limitations
- Claude 101 (khóa nền tảng)
- Claude use-case library (lọc theo Cowork)

---

# PHẦN B — Refer links đã quét

## B.1 — Get started with Claude Cowork (Help Center)

### Bản chất & availability
- Cowork đem **năng lực agentic của Claude Code ra knowledge work ngoài coding**, không cần terminal
- Task chạy **remote trên cloud Anthropic** trong môi trường isolated; session + files gắn với account, theo bạn across desktop/web/mobile
- Chat và Cowork chung một nhà; bản **unified** mới (hộp thư không còn 2 nút Chat/Cowork): mọi conversation đều có thể thành Cowork task
- **Desktop (macOS/Windows, Linux beta)**: mọi gói trả phí
- **Web/Mobile**: Pro, Max, Ultra, Team (beta), Enterprise (owner bật)
- **Chrome side panel**: mọi gói trả phí (Enterprise: owner phải bật Chrome + cloud Cowork)

### Yêu cầu & chạy task
- Cần: gói trả phí + **desktop app mở & connected** (cho local files, browser use, computer use — dù session chạy cloud) + internet
- Task chạy: analyze → tạo plan → bẻ subtasks → chạy code/shell trong **isolated cloud env** → coordinate parallel workstreams → deliver outputs (preview/download)
- Trong task: progress indicators, transparent reasoning, mid-task steering, cross-device check-ins, parallel sub-agents, **deletion protection** (phải gõ "Allow" rõ ràng mới xóa vĩnh viễn)

### Năng lực chính
- Cross-device continuity
- Unattended execution (đóng laptop vẫn chạy)
- **Shared memory với chat** (tắt "Memory" qua menu + trước tin nhắn đầu)
- Local file access trực tiếp (desktop)
- Sub-agent coordination
- Professional outputs (Excel formulas chạy được, decks, docs)
- **Edit draft in-place** (bôi đen text → "Edit with Claude")
- Long-running không timeout
- Scheduled tasks thuần cloud
- Projects
- Browser actions (built-in desktop browser / Chrome của bạn qua extension / side panel)

### Permission modes (tên mới)
| Connector tool | Manual (trước đây "Ask before acting") | Auto (trước đây "Auto approve") | Skip (trước đây "Act without asking") |
| :--- | :--- | :--- | :--- |
| Tools đã approved | Approved | Read-only approved; **write/delete Claude quyết** | Approved |
| Tools cần approval | Hỏi bạn | Claude quyết (đã safety-review) | Approved |
| Tools bị block | Denied | Denied | Denied |

- **Auto** mặc định trên Pro/Max/Ultra/Team; **Manual** mặc định trên Enterprise
- Auto screen từng action cho risk (data exfiltration, prompt injection) → block cái unsafe, tìm đường an toàn hơn, hỏi lại nếu bị block liên tục (đã red-team nội bộ + bên thứ ba)
- **Skip**: không check gì — "chỉ dùng khi hoàn toàn tin tưởng mọi action"

### Config khác & lưu ý
- **Global instructions**: Settings > Cowork (unified: nằm trong "Instructions for Claude")
- **Folder instructions**: context gắn với local folder, Claude tự update được
- **Plugins**: skills + connectors + sub-agents lưu theo account, dùng chung Cowork/chat/Code
- **Scheduling**: `/schedule` hoặc mục "Scheduled" ở sidebar — không thiết bị nào cần thức
- **Usage**: task đa bước (code execution, file creation, connectors/browser) tốn usage theo từng bước
- Kéo dài limit: gom việc liên quan vào một task, conversation mới cho việc không liên quan, nói rõ khi chỉ cần câu trả lời nhanh
- **Security**:
  - Session isolated bảo vệ **máy bạn** nhưng **không giới hạn** những gì Claude làm qua quyền bạn cấp
  - File read/write chỉ trong folders đã connect
  - Network theo egress settings (⚠️ web fetch/web search + MCPs — kể cả Chrome — **không** bị egress chặn)
  - Team/Enterprise admin tắt được web search
- **Limitations**: không share session (chỉ share artifact); một số feature desktop-only
- **FAQ**: "Setting up Claude's workspace" = bình thường (Cowork tự update); task dừng — session local (task trước 6/10/2026 trên Pro/Max/Ultra) cần desktop mở, cloud session cứ chạy tiếp

## B.2 — Use Claude Cowork safely (Help Center)

### Mô hình rủi ro
- Tools chia 2 nhóm: **Read tools** (đọc email, chụp màn hình) và **Write tools** (xóa file, gửi invite, chạy commands, click) — write rủi ro hơn vì tạo hành động ngoài ý muốn
- Rủi ro = **những gì Claude đọc/thấy** × **những gì Claude được phép làm**
- Session chạy trong **cloud env tạm, isolated** (mỗi session một môi trường, không với tới network nhà/công ty, xóa sau đó); Claude chỉ tới máy bạn qua desktop app đang mở + folders đã connect
- ⚠️ Isolation giới hạn **nơi code chạy**, không giới hạn Claude đọc/làm gì
- **Prompt injection**: chỉ thị độc hại giấu trong content ngoài (VD email bảo Claude chuyển tiền)
- Tấn công cần **cả hai** điều kiện: đọc content ngoài ranh giới tin cậy **và** có quyền hành động hại → chặn một trong hai là yếu đi tấn công

### 6 lớp safeguard của Anthropic
1. Model training (RL nhận diện + từ chối chỉ thị độc hại, kể cả giả vờ khẩn cấp/có thẩm quyền)
2. Isolated cloud execution
3. **Content classifiers** quét mọi untrusted content vào context, flag nghi ngờ injection
4. Action screening trong auto mode
5. **Deletion protection** mọi mode
6. Computer use yêu cầu quyền từng app
- ⚠️ Xác suất tấn công thành công **vẫn non-zero** — cảnh giác vẫn cần

### 10 best practices
1. **Chọn lọc file access** — tránh files nhạy cảm (tài chính, credentials, hồ sơ cá nhân); dedicated folder + backup
2. **Giám sát tasks, không phải từng command** — canh file/site bất thường, scope creep; thấy sai → stop task
3. **Cẩn trọng scheduled tasks** — chạy cloud khi máy tắt: start đơn giản, tránh data nhạy cảm + hành động khó hoàn tác, review output sau mỗi run, pause task không dùng
4. **Oversight theo stakes**:
   - Manual cho files/accounts nhạy cảm, tool mới, hành động không đảo ngược (messages, purchases)
   - Skip = không action check
5. **Cẩn trọng computer use** — **không sandbox**: Claude click/type/navigate trực tiếp + chụp màn hình; block apps nhạy cảm (banking, healthcare, dating)
   - Link click trong app được phép có thể mở app khác chưa được phép
6. **Giới hạn web vào site tin cậy** — web là vector injection chính; side panel thấy trang hiện tại (kể cả đã login), session lưu vào history; egress không áp dụng cho web fetch/search/MCP
7. **Kiểm định MCPs/plugins** — plugin mở rộng tầm với của Claude; local MCP chạy với quyền program bình thường; chỉ dùng extension đã verify
8. **Canh cross-app data sharing** — add-in Excel/PPT có thể chuyển data giữa apps không cần chỉ dẫn; tránh info nhạy cảm khi Cowork đang hoạt động
9. **Hiểu tầm với cloud-session**:
   - Cloud task chỉ tới máy khi desktop mở + folder connected + trong quyền sẵn có
   - Pro/Max/Ultra: desktop task mới chạy cloud (task trước 6/10/2026 vẫn local)
   - Máy công ty managed: connected folders thành reachable từ cloud
10. **Báo cáo hành vi khả nghi** — Claude nói chuyện ngoài đề, truy cập resource bất thường, đòi data nhạy cảm không được hỏi → stop + report

- **Enterprise**: Compliance API ghi Cowork sessions; owner stream events sang SIEM qua **OpenTelemetry**
- **Trách nhiệm của bạn**: chịu trách nhiệm mọi thứ Claude làm thay mặt (nội dung publish, messages, purchases, data changes, scheduled/computer-use actions, tuân thủ ToS site bên thứ ba) — xem AUP for Agents
- ⚠️ Built-in browser + Claude in Chrome dùng cùng safeguards — Anthropic **không khuyến khích** dùng cho hành động liên quan thông tin nhạy cảm
- Computer use **vượt qua** permission gates + sandboxing các tool khác có

## B.3 — Work across M365 apps (docs)

> Cho Claude **đọc từ app M365 này và sửa app khác trong cùng một conversation**. ⚠️ Chỉ dùng khi đăng nhập **trực tiếp bằng Claude account** — KHÔNG hỗ trợ qua Bedrock/Vertex/Azure Foundry/LLM gateway.

- **Yêu cầu**: gói trả phí (Pro/Max/Team/Enterprise) + 4 add-in (Excel, PowerPoint, Word, Outlook) từ Microsoft AppSource, mỗi app activate ít nhất một lần
- **Bật**: Settings từng add-in → **"Let Claude work across files"** — Pro/Max bật mặc định; **Team/Enterprise mặc định TẮT**; toggle **per-device** (bật ở mỗi host muốn phối hợp)
- Bật xong thấy connected-app indicators trong sidebar
- **Cách chạy**: mô tả task nhiều files/apps → Claude tự coordinate, đọc/ghi files đang mở + email threads, **context tự chuyển giữa apps**
- **Ví dụ**:
  - Pull số từ Excel model vào slide PPT / memo Word
  - Update chart PPT bằng số mới từ Excel
  - Tóm tắt Word thành slides
  - Mở LOI đính kèm trong Word với Outlook thread đã load
  - Kéo số từ email vào Excel model đang mở
- **Skills áp dụng đúng app** trong cross-app task (skill modeling conventions cho Excel, slide template cho PPT)
- **Admin**: Organization settings → Office agents → toggle "Let Claude work across apps"; quản lý add-in qua M365 Admin Center
- **Data**:
  - Inputs/outputs xóa khỏi backend Anthropic trong **30 ngày**
  - Add-in **không** kế thừa custom data retention của org
  - **Không** nằm trong Enterprise audit logs/data exports (Enterprise có Compliance API thì được cover, không cần setup thêm)
  - Chat history lưu local browser (IndexedDB), clear từ Settings — nhưng clear local **không xóa** bản Anthropic giữ
- **Giới hạn**: Claude chỉ đọc/ghi files **đang mở** — không tự create/open/close/switch files
- ⚠️ Known issue: sau update M365 9-10/2026 trên Windows, một số người dùng mất chat history + uploaded skills trong add-in (Anthropic đang làm việc với Microsoft)

## B.4 — Claude for Outlook (docs)

> Add-in Outlook cho người làm việc chạy qua email (PE/IB associates quản lý deal flow, legal chạy đàm phán, consultants theo nhiều client threads). **Beta**, Pro/Max/Team/Enterprise.

### Làm được gì (kèm prompt mẫu)
- **Triage unread inbox** thành 3 nhóm: cần bạn / Claude xử lý (đến đã pre-drafted: scheduling asks, acknowledgments, standard-form docs) / noise (archive một lần chọn); mỗi action item kèm lý do 1 dòng:
  - *"What needs me?"*
  - *"Draft replies for everything you can handle"*
  - *"Archive all the calendar responses and newsletters"*
- **Draft replies đúng giọng bạn**, **không gửi**:
  - Hạ trong compose pane gốc
  - Tone học từ **sent folder** của bạn (độ dài câu, mức trang trọng)
  - Bỏ phần kết để Outlook tự thêm signature
  - Chọn reply vs reply-all có chủ đích, **cảnh báo trước khi thêm người ngoài thread** — *"Reply to this and agree to the extension, push back on the fee"*
- **Tóm tắt thread dài**: đã quyết gì / còn open / ai nợ gì — **mọi claim cite email cụ thể**, click citation mở đúng message — *"What's been decided and what's still open?"*
- **Đọc attachment inline**: `.docx`/`.xlsx` ngay trên email (`.pptx` → mở trong PowerPoint với thread làm context; **PDF chưa hỗ trợ inline** — save rồi upload qua sidebar)
- **Search mailbox theo chủ đề** (không chỉ keyword), kết quả là citations mở được email gốc — *"When did we last discuss the cap with Fernwood?"*
- **Tìm slot + tạo event**: check free/busy mọi attendee, tôn trọng working hours; invite draft vào form gốc, bạn bấm Send — *"Find 30 minutes with Dana and the Fernwood team next week"*
- **Prep meeting**: brief 1 trang từ thread cuối với từng attendee + documents đính kèm — *"Prep me for my 2pm"*

### Cài đặt
- **Hỗ trợ**: Outlook web, Windows (new + classic, cần M365 sub), Mac (M365 sub). **Không**: Outlook 2016/2019 perpetual/volume, iOS, Android, **Exchange on-premises** (cần Exchange Online)
- **Cá nhân**: AppSource → "Get it now" → mở email → nút Claude trên ribbon → sign in (ẩn thì Customize actions → check Claude)
- **Org deploy**: M365 Admin Center — bật "Let users access the Office Store" → Integrated apps → search → deploy → **Graph consent**
- ⚠️ PIM: Integrated apps không nhận role PIM-activated (known Microsoft issue) — deploy từ admin có role permanently active
- Block Store → deploy bằng **manifest XML** (pivot.claude.ai/manifest-outlook.xml), rollout tới 24h
- **Microsoft Graph consent**: Global Admin duyệt một lần tenant-wide: `Mail.ReadWrite`, `Calendars.Read`, `User.Read`, `offline_access` — hiệu lực ngay; skip thì mỗi user gặp "Need admin approval"
- **Entra app riêng** (chính sách không cho consent third-party multi-tenant):
  1. Register single-tenant app
  2. Redirect `brk-multihub://pivot.claude.ai`
  3. 4 Graph permissions
  4. Thêm `&graph_client_id=YOUR_CLIENT_ID` vào mọi URL manifest bắt đầu `https://pivot.claude.ai/?m=` (gõ đúng `&amp;`)
- **National clouds**: GCC High → `graph_cloud=us-gov-high`; DoD → `us-gov-dod` (bắt buộc); 21Vianet → `china`
- **Third-party platform**: dùng được không cần Claude account qua Bedrock/Vertex/Azure Foundry/LLM gateway

### Kiến trúc & dữ liệu
- Item đang mở đọc qua **Office.js**; việc mailbox-wide (thread retrieval, search, free/busy, move/flag) qua **Microsoft Graph**
- Mọi Graph call chạy **trong browser**, token nằm trong MSAL cache **không bao giờ gửi cho Anthropic**
- **Claude không bao giờ tự gửi mail** — add-in không xin quyền `Mail.Send`; mọi draft hạ **unsent**, bạn bấm Send
- Model: Claude account → Opus 4.7 / 4.6 / Sonnet 4.6; qua third-party → chỉ Opus 4.7
- Chat history: IndexedDB local, không sync; riêng theo surface + userID + orgID (Excel và Outlook riêng); clear local không xóa bản Anthropic
- Data retention 30 ngày backend; Enterprise: OpenTelemetry → SIEM, Compliance API; Pro/Max/Team không có observability/audit export
- ⚠️ **Prompt injection**: body/signature/attachment email là **untrusted input** (text ẩn chỉ thị Claude forward thread, draft reply bạn không yêu cầu) — review mọi draft, nhất là sender ngoài
- **Khuyến nghị beta**:
  - Không unattended sending (Claude vốn không tự gửi)
  - Đọc draft trước khi gửi cho client/counterparty
  - Không thay phán đoán của bạn về quan hệ
  - Mailbox chứa data privileged/regulated cần org controls

## B.5 — Get started with Claude in Chrome (Help Center)

### Tổng quan
- Extension cho Claude **đọc, click, navigate website cùng bạn** — khởi chạy từ **Chrome side panel, Claude Cowork, hoặc Claude Code**
- **Chỉ gói trả phí**: Pro, Max, Ultra, Team, Enterprise
- Side panel giờ chạy như **Cowork session** (Max/Ultra/Team; Pro theo rollout; Enterprise admin bật) — Enterprise cần owner bật Chrome + cloud Cowork, không thì classic experience
- **Cài**: chỉ Chrome (không Chromium khác, không mobile) → Web Store → "Add to Chrome" → sign in → pin extension → cấp permissions

### Permissions của extension
| Permission | Mục đích |
| :--- | :--- |
| sidePanel | Panel chat cạnh trang |
| storage / unlimitedStorage | Lưu preferences + data lớn (workflow instructions) |
| scripting | Đọc text trang |
| debugger | Điều khiển browser (click, gõ, chụp màn hình) |
| tabs / tabGroups | Mở/đóng + nhóm tab của Claude riêng (màu riêng) |
| alarms / notifications / offscreen | Scheduled tasks, alerts, âm nền |
| system.display | Biết kích thước màn hình để click chính xác |
| webNavigation | Can thiệp trên site rủi ro cao |
| declarativeNetRequestWithHostAccess | Nhận diện với server Anthropic (analytics/troubleshooting) |
| nativeMessaging | Tích hợp tương lai với Desktop/Code |
| downloads | Lưu/mở file trong workflows |

### 3 chế độ sử dụng
1. **Claude Code integration** — vòng **build-test-verify**: build trong terminal → deploy URL → verify trong browser
   - Claude đọc console logs, errors, network requests, DOM state; so thiết kế Figma, live debugging, automated testing
2. **Claude Desktop control** (Chat/Cowork/Code) — Claude mở Chrome, hành động như người (click/gõ/điền form)
   - Setup: Settings → Customize → Connectors → Claude in Chrome → bật + cài extension; connector **mặc định tắt từng conversation**
   - Cowork cũng có **built-in browser** (không cần cài) đang rollout — chọn browser ưa thích ở Settings > Cowork
3. **Chrome side panel** — chat cạnh trang hiện tại; chạy như Cowork session → conversation lưu history, sync web/Desktop/mobile, **skills/plugins/connectors hoạt động như desktop Cowork**
   - Mặc định Auto mode + safety reviews
   - Revert: menu 3 chấm → "Switch back to classic"

### Tính năng chính
- **Workflow recording** (classic panel) — ghi các bước để Claude lặp lại, lưu thành shortcuts
- Đọc **console logs** (errors, network, DOM)
- **Scheduled tasks** (daily→annually, icon đồng hồ)
- **Multi-tab management** (kéo tab vào nhóm của Claude, tương tác đồng thời)
- Site-specific navigation built-in (Slack, Google Calendar, Gmail, Google Docs, GitHub)
- **1Password beta (macOS)** — Claude xin credentials, bạn duyệt sinh trắc, **Claude không bao giờ thấy password/mã**
- Background workflows (đổi tab vẫn chạy, Chrome giữ mở)
- Chia sẻ visual context + upload ảnh (screenshots, vùng chọn; nạp vào forms/expense reports)
- **Shortcuts** lưu prompts, gọi bằng `/`, lên schedule được
- Contextual suggestions theo trang

### Giới hạn & lưu ý
- Local files / máy bạn / cross-surface Chrome control → **cần Desktop mở & connected** (dù cloud session); side panel đọc tab hiện tại không cần setup nhưng local tasks không chạy theo cách này
- Recording workflows chỉ có ở classic panel
- Team/Enterprise: admin kiểm soát extension + **allowlist/blocklist sites**
- ⚠️ Claude tương tác trực tiếp website thay bạn — có classifiers nhưng rủi ro; đọc "Use Claude in Chrome safely" trước khi dùng

---

# Phụ lục: Nguồn đã quét

| Nhóm | Nguồn |
| :--- | :--- |
| **Khóa chính (raw HTML)** | `/courses/introduction-to-claude-cowork/` — what-is-cowork · getting-set-up · scheduled-tasks · the-task-loop · research-analysis-at-scale · giving-cowork-context · file-document-tasks · plugins-cowork-as-a-specialist · claude-in-chrome · claude-for-microsoft-365 · permissions-usage-choosing-your-model · validating-skills-for-plugins · share-what-you-build-with-your-team · troubleshooting-next-steps |
| **Refer links (5)** | [Get started with Claude Cowork](https://support.claude.com/en/articles/13345190) · [Use Claude Cowork safely](https://support.claude.com/en/articles/13364135) · [Work across M365 apps](https://claude.com/docs/office-agents/work-across-apps) (redirect từ support 13892150) · [Claude for Outlook](https://claude.com/docs/office-agents/outlook) (redirect từ support 14855664) · [Get started with Claude in Chrome](https://support.claude.com/en/articles/12012173) |
| **Không quét (ngoài phạm vi)** | claude.com/download (trang tải app) · các link khóa học nền tảng (AI Fluency, Claude 101 — đã có trong `Claude_Course.md`) |

> ✅ **Độ phủ**: 14/14 bài đọc từ **raw HTML gốc** và tóm tắt đầy đủ từng section — key takeaways, prompts mẫu, watch-outs, lesson reflection.
> 5/5 refer links quét trọn nội dung (2 link support đã redirect sang docs mới — theo tới đích).
> ℹ️ **YouTube/media**: không có link YouTube hay asset media công khai nào trong nội dung (video = embed Academy, ảnh = og:image của khóa).
