# Introduction to Claude Tag — Tóm tắt khóa học

> **Nguồn & phương pháp** (11/2026): tải **raw HTML** 11 bài tại [academy.claude.com/courses/introduction-to-claude-tag](https://academy.claude.com/courses/introduction-to-claude-tag) → đọc trọn → tóm tắt.
> **Refer links** (10 trang docs `claude.com/docs/claude-tag/` + 1 blog) quét đầy đủ ở Phần B.
> ⚠️ Claude Tag đang **public beta** — behavior có thể thay đổi. Không có YouTube/media link nào trong nội dung.

## Mục lục

| Phần | Nội dung |
| :--- | :--- |
| **A** | 11 bài học (DM · public channel · private channel · memory/instructions · proactivity · routines · viết request · mở rộng ownership) |
| **B** | Docs tham chiếu: how-it-works · agent-identity · security · commands · memory · routines · when-claude-responds · good-habits · use-cases · troubleshooting + blog human-agent teams |

---

# PHẦN A — 11 bài học

## Bài 1: Tag Claude to see what you can do (10′)

### Claude Tag là gì
**Claude trong Slack workspace của team.** Trong channel, gõ `@Claude` + nói nhu cầu → Claude trả lời trong **thread dưới message**.

Claude **đọc sẵn nội dung channel** trước khi trả lời, nên bạn không phải giải thích lại background. Nếu channel có connected tools (Google Drive, calendar, ticketing...) → Claude look up thông tin và **make changes** luôn tại chỗ.

Cả channel thấy thread, ai cũng reply để thêm chi tiết hoặc đổi hướng Claude đang làm.

Điểm khác biệt so với chatbot — vì hoạt động ngay trong channel, Claude làm việc được cả **khi không ai tag**:
- **Untagged replies**: channel nhận requests/problems (IT help, bug-report) — hướng dẫn Claude **một lần** về những message nào cần xử lý; từ đó Claude tự xử lý message mới: giải đáp câu hỏi, hỏi thêm thông tin còn thiếu, tag đúng owner
- **Standing responsibility**: Claude trông giữ một việc qua nhiều ngày/tuần (giữ launch checklist cập nhật, báo khi một mục trễ tiến độ)
- **Routines**: mô tả task một lần (*"post a summary of this channel every Monday at 9am"*) → Claude lặp theo schedule

### Khác chat với Claude ở đâu
- **Reply trong thread** để thêm context/đổi hướng — Claude đọc mọi reply ở đó, **không cần tag lại**
- Link **Configure** dưới mỗi reply mở channel settings

### Làm được gì khi không có tools
Ngay cả khi chưa có connection nào: đọc thread + history channel (kể cả pinned), **search nội dung workspace**, viết + chạy code trong sandbox (biến CSV thành chart, thread dài thành doc).

### 3 nơi làm việc
- **DM** (bài 2)
- **Public channel** (bài 3)
- **Private channel** (bài 4)

Claude như nhau ở cả ba nơi — ba yếu tố thay đổi: **ai tham gia được, Claude truy cập được tới đâu, và nơi lưu giữ những gì nó học**.

> **Try:** `/invite @Claude` trong channel bạn hay làm → tag một câu hỏi ngắn về recent work của channel → done khi Claude trả lời và câu trả lời tận dụng nội dung đã được post ở đó. (Không reply → nhờ người quản lý Claude Tag bật cho channel.)

## Bài 2: Claude in a DM (15′)

### Khi nào dùng DM
Muốn Claude **hành động dưới tài khoản bạn, trong tools của bạn, trên việc chỉ mình bạn thấy** → DM. Ở đây Claude là **extension của bạn**; trong channel nó làm việc dưới tên riêng của nó.

DM cũng là nơi **thử nghiệm trước khi người khác nhìn thấy**.

Làm được:

- **Claude làm việc như bạn**: chạy trên Claude account của bạn với connectors của bạn — đọc calendar, email, files
- **Thử nghiệm riêng tư**: soạn thảo draft, hỏi điều chưa muốn post lên channel
- **Catch up public channel**: nói tên channel → Claude tìm kiếm giúp bạn, không phải tự post
- **Routines cá nhân**: morning brief chỉ post cho riêng bạn

*Nếu tổ chức tắt DMs → dùng channel chỉ gồm mình bạn và Claude.*

### Claude dùng được gì trong DM
- **Daily tools của bạn**: calendar, email, files (qua personal connectors)
- **Thông tin workspace**: mọi public channel qua search, khi bạn nêu tên
- **Gì bạn mang vào**: attachments, images, text paste vào thread

Câu hỏi khám phá: *"What do you know about me, and what sorts of things can you do for my work?"* / *"What can you access from here?"*

### Privacy & giới hạn
- Những gì Claude học trong DM **giữ riêng DM** — không vào workspace notes
- connectors ngắt được bất cứ lúc nào
- việc làm trong tools của bạn diễn ra **dưới tên bạn** → review trước khi cho phép gửi/thay đổi
- DM không visible cho channel nào (và ngược lại, connections của channel không vào DM)
- **Giới hạn (chính là điểm mạnh)**:
  - không ai khác thấy/tiếp tục được (đồng nghiệp không thể thêm hiểu biết, sửa, hoặc pick up khi bạn vắng)
  - làm từ tools của bạn — CRM/tracker của team channel **không có** ở đây
  - điều Claude học chỉ có **một mình bạn** tận dụng được (nói trong public channel thì cả channel cùng được hưởng)

> **Try — morning brief:** mở DM, chỉ các channels quan trọng (hoặc: *"search the workspace and tell me what you find about me, my work and my priorities, then propose the channels you should watch for me"*)
> → yêu cầu brief (khi nào, xem gì, mang về gì) → lần đầu tới thì **sharpen trong thread**:
> - format "more scannable, always include links"
> - track theo thời gian "count how many questions in #sales-requests went unanswered for a day"
> - prioritize "messages from [names] first; skip routine posts"

## Bài 3: Claude in a public channel (15′)

### Khi nào dùng public channel
Muốn Claude **dùng tools của team**, trên việc **người khác thấy — sửa — tiếp tục được**. Điều Claude học ở đây giúp **mọi người trong channel** → *"khi hơn một nơi đều làm được, chọn public channel"*.

Claude thấy **toàn bộ history channel kể cả trước khi được thêm** + mọi tools connected. Ai setup Claude Tag quyết định tools từng channel; **mặc định không cần Claude account** để tag (org trả tiền).

### Connections thêm gì
Channel kết nối GitHub, Google Drive, CRM, team calendar → Claude đi thẳng từ discussion sang work:
- **Sales**: pull account từ CRM trước call
- **Data**: chạy warehouse query trả lời câu hỏi trong thread
- **Support**: draft reply trên support ticket
- **Engineering**: mở PR cho fix team vừa agree

Trong tools team, Claude hành động **như chính nó** — account riêng, access channel được cấp. Result vào thread theo form bạn yêu cầu, hoặc **page** Claude tiếp tục edit (link team mở lại được).

### Personal connectors — cho request của bạn
Claude cũng dùng **personal connectors** của bạn (calendar, inbox, issue tracker) khi *request của bạn trong channel* cần — VD `@Claude add Thursday's launch review to my calendar`. Khi đó Claude làm **dưới tên bạn** (như DM).

Trước khi dùng, Claude hiện prompt **chỉ bạn thấy**:
- **Allow**: post trực tiếp — Claude check từng response, giữ cái sensitive cho bạn review (check có thể miss)
- **Allow with review**: duyệt từng response trước khi post
- **Don't allow**: không dùng connectors cho request này
- (Enterprise: Owner có thể bỏ 1 trong 2 lựa chọn Allow)

### Privacy
- **Team connection**: ai trong channel cũng dùng được với đúng access của account Claude — account edit được tracker thì **ai cũng nhờ Claude sửa ticket**; chỉ read được thì chỉ look up
- **Your connectors**: chỉ phục vụ request của bạn, dưới tên bạn; người khác trong thread **không direct được** công việc đó; nút **Stop** dưới message để dừng task đang dùng connectors của bạn
- Không đọc được private channels / DMs của người khác từ đây
- Info restricted → private channel (bài 4); việc chỉ mình thấy → DM (bài 2)

> **Try:** hỏi `@Claude what can you access from this channel?` → chọn 1 tool → nhờ fetch **1 record thật** → mở record ở nguồn đối chiếu (đủ mới? thiếu gì? có nói nguồn mỗi con số?) → lệch thì nói trong thread xem nó tự sửa.
> Có colleague thì nhờ họ reply 1 correction — *đó là phần DM không làm được*. Link Configure cũng list connections của channel.

## Bài 4: Claude in a private channel (10′)

### Khi nào dùng
Việc chứa info chỉ nhóm cụ thể được thấy — people matters, finance, legal, customer escalation confidential. Bạn đã giữ những việc đó trong private channel; **Claude giữ đúng boundary đó**.

Mọi thứ của bài 3 hoạt động cho members: threads ai trong nhóm cũng correct/continue được, history + connected tools của channel, untagged replies, routines.

Tool connect **riêng cho channel này** (billing system trong private finance channel) — chỉ members mới nhờ Claude dùng được; Claude chỉ làm được những gì account được phép, giữ ở **mức access tối thiểu việc cần**.

Channel hưởng **workspace notes** Claude đã học từ public channels, nhưng **không thêm gì vào đó**.

### Boundary = ranh giới của Claude
- **Chỉ members** cho Claude đọc/act ở đây — từ channel/DM khác, Claude xử sự **như thể channel này + tools + memory của nó không tồn tại**; replies chỉ members thấy
- Học được lưu **chỉ vào channel notes** — *không bao giờ* vào workspace notes → confidential context không thể nổi lên channel người khác
- **Member list = access list**: account đọc được gì thì mọi member cũng truy cập được qua Claude → *keep it tight*
- Mọi action attributable: Claude dùng account riêng trong tools — log của tool ghi rõ Claude làm gì, khi nào
- **Guests & shared channels**: do admin quyết định (guest channels); nơi Claude trả lời thì không search phần còn lại của workspace từ đó

> **Try:** `/invite @Claude` trong private channel → hỏi access → chạy 1 task nhạy cảm. Done khi reply chỉ hiện trong channel đó và chỉ dùng những gì channel đó giữ.

## Bài 5: Pick the right place for the work (10′)

### Quyết định như chọn chỗ hỏi đồng nghiệp
- DM được đồng nghiệp thì DM Claude
- việc của nhóm cụ thể → private channel của nhóm
- cả team dùng được → public channel nơi việc đó diễn ra

**Nơi hỏi quyết định ai được hưởng lợi**: public — colleagues đọc được câu trả lời, correction của bạn cải thiện replies sau của **cả channel**; DM — chỉ mình bạn.

### Nhiều nơi fit → public channel
3 thứ DM không có:
1. **Người khác build on work**: colleague thấy thread → thêm context bạn không có, sửa chi tiết, nhận việc tiếp khi bạn vắng — Claude đọc mọi reply đó
2. **Claude học giúp cả channel**: correction lưu vào channel notes, Claude dùng cho mọi người ở đó
3. **Setup một lần phục vụ mọi người**: tools + instructions + routines của channel work cho tất cả — mỗi bổ sung làm request sau **ngắn hơn** và result **tốt hơn**

DM/private phù hợp cho việc của riêng mình/nhóm — dùng cho việc khác đồng nghĩa với đưa nội dung không cần riêng tư vào nơi riêng tư.

> Check nhanh nơi bạn đứng: hỏi Claude *"what can you access from here?"*

## Bài 6: Refine Claude's work through memory and instructions (10′)

### Hai nơi cho thứ nên tồn tại

| | **Memory** | **Channel instructions** |
| :--- | :--- | :--- |
| Là gì | Notes Claude tự viết về channel (+ bạn thêm bằng message) | Rules người quản lý nhập vào settings của channel |
| Cách đổi | Nói với Claude trong message | Sửa trang Configure (dưới mọi reply của Claude) |
| Dùng cho | Corrections, preferences, ai chịu trách nhiệm phần gì — những gì Claude tự ghi nhận khi làm việc | Purpose của channel, tone, khi nào reply, điều **không bao giờ** làm — cho **mọi thread** |

> ⚠️ **Note mâu thuẫn instruction → instruction thắng.**
> Nguyên tắc chọn: **mức độ rule phải giữ vững** (*how firmly a rule should hold*) — rule đang thử nghiệm hoặc còn lỏng lẻo → memory; rule đã được chứng minh và **phải đúng trong mọi thread** → instructions.

### Memory
- Thêm: `@Claude remember for this channel: …` — Claude cũng tự save khi làm việc; đọc notes **trước khi trả lời**; ai trong channel cũng thêm/sửa/xóa được
- Scope:
  - **Channel notes** (riêng từng channel; notes DM scoped bạn, chỉ bạn)
  - **Workspace notes** (đọc ở mọi channel; **chỉ save từ public channel**, chỉ dành cho những gì ai cũng cần biết — VD naming rule toàn công ty)
- Duy trì:
  - `@Claude what do you remember about this channel?` (xem)
  - `remember for this channel: [bản sửa]` (sửa)
  - `that's outdated, forget the entry about [topic]` (xóa stale)

  Owner của Claude org xem/sửa/xóa notes trong admin settings claude.ai

### Channel instructions
- VD: *"This channel handles billing questions. Keep replies short. Never contact customers directly."* — đọc ở **đầu mỗi thread**
- ⚠️ Là **guidance theo sát, không phải hard lock** — việc tuyệt đối không được xảy ra → dùng **setting hoặc access control**, đừng dựa vào câu chữ
- Good uses:
  - purpose của channel
  - loại message nào cần reply mà không cần tag
  - tone/length của replies
  - sources trả lời dựa từ đâu
  - file lưu vào đâu
- Sửa tại **Configure** (ai có Claude account ở org cũng sửa được, trừ khi admin **lock**)
- cùng trang: setting **Respond automatically** + danh sách connected tools (chỉ admin/channel managers đổi)
- **Changes áp dụng cho thread mới** → test trong fresh thread

**Ví dụ instructions cho bug-triage channel:** *"triages customer bug reports for the billing service. Khi message có error ID → thread: look up monitoring tool, link dashboard, propose owner. Không tag thì giữ im lặng.
Replies < 6 dòng; link logs thay vì paste. File confirmed bugs vào tracker với label from-chat. Investigation read-only; never touch production."*

### Luồng thực dụng
Feedback về format/voice lưu được ở **cả hai nơi**. Thử nhanh: nói *"keep replies under six lines"* trong channel → Claude save vào memory và làm theo.

Rule **đã ổn định** → **promote vào channel instructions** (không có quyền sửa thì nhờ người quản lý).

### Bảng chẩn đoán khi kết quả không đạt
| Hiện tượng | Nguyên nhân | Fix |
| :--- | :--- | :--- |
| Replies mỏng/generic | Thiếu tools chứa việc | Nhờ manager connect tools vào channel |
| Claude trả lời việc nên để yên | Thiếu clarity về role | Định nghĩa job trong channel instructions |
| Cùng correction lặp lại | Chỉ nói 1 lần trong thread | Nói *"remember for this channel"* |
| Claude không respond | Chưa bật cho channel | Nhờ manager bật |

> **Try:** xem memory → làm 1 task quen, thấy Claude miss nguyên tắc nào của team (*"we always check what we shipped before recommending something new"*, *"we prioritize by impact to retention, not just effort"*)
> → save vào memory → giao việc tương tự trong thread mới, xem câu trả lời shift thế nào.

## Bài 7: Proactivity — để Claude trả lời không cần tag (15′)

### Một channel, một loại việc
Claude biết đến từ chính channel đó (history + instructions + memory + tools).

**Giữ một loại việc mỗi channel** cùng tools phù hợp → Claude học kỹ job đó và trở thành **specialist của channel**. Đây chính là điều khiến proactivity hữu ích: channel chỉ có một job thì Claude phân biệt được message nào là việc của mình.

### Cơ chế
Bật automatic replies → Claude **đọc liên tục**, đánh giá từng message và tự quyết định có tham gia hay không. Dạy qua instruction:
> `@Claude remember for this channel: when someone posts an account name or asks about an open item, reply even if nobody tagged you. Stay out of scheduling and social chatter.`

→ Save vào notes, Claude dùng khi cân nhắc quyết định reply.

### Untagged replies tạo giá trị ở đâu
- **Support/feedback channel**: câu hỏi vào → Claude trả lời ngay từ knowledge base, không chờ ai tag
- **Reference/policy channel**: *"what's the onboarding process?"* → trả lời từ policy doc
- **Project channel**: *"what did we decide about the API?"* → tìm decision; *"how does that affect the mobile work?"* → **connect the dots**, tăng tốc conversation
- **Incident channel**: đọc reports, **spot pattern**, flag — không ai cần tag

### Standing responsibility (bước xa hơn reply từng message)
Giao Claude một **job** — tự quyết việc cần làm và hành động qua nhiều ngày/tuần:
- **Coordination**: launch/event nhiều threads — đọc nơi decisions land, update trackers, remind owners khi đến hạn, flag slipped
- **Owning an outcome**: mục tiêu cụ thể (queue < 1 ngày old; migration xong cuối quý) — theo dõi ảnh hưởng, tự làm được thì làm, **mang đến cho bạn phần cần quyết định kèm recommendation**
- **Continuity through change**: việc chạy nhiều tháng người xoay vòng — nhớ decided & why, trả lời *"where did we land on this"*, chỉ ra proposal mới mâu thuẫn quyết định cũ

Khởi động: document standard process + bật automatic replies → Claude sharpen theo thời gian. Khi đã ổn định → thêm vào **channel instructions** (instructions outrank memory).

Khóa *Building Effective Human-Agent Teams* đề cập sâu roles + hand-off.

### Tắt / tinh chỉnh
Channel ồn → **cải thiện instructions cho cụ thể hơn trước**, rồi:
- Tắt hẳn: `@Claude only respond when someone @-mentions you` (đổi **Respond automatically** của cả channel)
- Tinh chỉnh: `@Claude answer questions about our decisions and the work we're doing. Skip scheduling.` (qua notes)
- Im một thread: `@Claude only respond when I @-mention you` (gửi trong thread đó)
- `!mute` trong thread im đúng thread đó (`!unmute` đảo ngược)

## Bài 8: Put recurring work on a schedule (10′)

### Loại routine
- **Weekly/daily reports**: status digest, tóm tắt decisions, danh sách blocked/waiting
- **Continuous monitoring**: watch một channel/repository cho changes cụ thể — khi phát hiện thay đổi thì post alert/summary
- **Regular checks**: review pending, flag overdue/at-risk, surface patterns

### Setup = 1 message: đọc gì, tìm gì, post gì, khi nào
> `@Claude every weekday at 9am, compare the onboarding tracker with what was said in this channel yesterday, and post only what needs attention:
> anything overdue, and anything the thread says has slipped that the tracker still shows on time.
> Name the owner, link the message, and suggest a next step. If nothing needs attention, post nothing.`

Vào ngày yên tĩnh, routine không post gì — nhờ vậy **mọi post của routine đều đáng đọc**. Routine chạy với tools của channel nên so sánh được nhiều nguồn.

**First post = draft**: reply trong thread để điều chỉnh — Claude đọc feedback, học và áp dụng cho **mọi run sau**.

### Quản lý (thuộc channel, ai cũng làm được)
- **List**: `@Claude what routines do you have set up in this channel?` hoặc `@Claude !scheduled`
- **Change/pause**: mô tả thay đổi — *"pause the Monday digest until I say I'm back"*
- **Stop**: nêu tên — *"stop the Friday status"*
- Routine **tiếp tục chạy kể cả khi người setup rời** channel/org; người còn lại pause/stop được

## Bài 9: Write a request Claude can work with (15′)

Giao Claude **task/trách nhiệm** (không phải câu hỏi) → cần instruction khác: Claude phải hiểu việc đủ để biết **khi nào bước vào, khi nào xong, quyết định ra sao khi bạn không có mặt**.

### Step 1 — Chọn việc
- **Outcome thinking**: hình dung giao cho người hiểu workspace hoàn toàn — bạn nhờ họ gộp/tìm hiểu gì?
- **Inputs**: Claude truy cập được các tools/files/threads mà việc cần? Hỏi `@Claude what can you access from this channel?` — thiếu → chuyển task sang channel có tools đó, hoặc nhờ admin connect
- **Ai thấy work**: sensitive → private channel

### Step 2 — Viết request
1. **Goal trước, process sau**: muốn đạt gì, vì sao, good result trông ra sao và gửi về đâu; steps/constraints bạn quan tâm — phần còn lại để Claude tự quyết, biết **intent** giúp Claude quyết tốt các chi tiết bạn không nói
2. **Trỏ inputs**: channel, workspace search, connections của channel, files; có ví dụ good result → link/paste/chỉ chỗ tìm
3. **Gắn cơ chế kiểm tra**: rubric cho good result · yêu cầu **link sources** · tách *verified* khỏi *inferred*
4. **Nêu priorities**: audience, mức polish, điều tránh, **decisions nào mang về cho bạn** — khi Claude gặp lựa chọn ngoài dự kiến mà bạn chưa nói, các lựa chọn đó là phán đoán của nó
5. **Form của kết quả**: ngắn → thread; kết quả người khác sẽ mở/xem lại/chuyển tiếp → **page** (Claude publish dashboard/report/prototype trên claude.ai + post link; cả channel mở được; request sau trong thread **update cùng link đó**)

Biến thể:
- việc lớn phức tạp → nhờ Claude **propose outline trước** để align
- exploratory/ambiguous → nói rõ, cho câu hỏi + lý do, để Claude đề xuất vài hướng rồi mới chọn
- proactive/scheduled → nói rõ own gì, đâu bạn quyết

**north star**: một mục tiêu measurable mà team pin trong channel Claude đọc → Claude tự đề xuất work hướng tới mục tiêu đó.

### Step 3 — Để Claude làm
Claude post note ngắn xác nhận đã bắt đầu → làm việc **không cần bạn**; bất kỳ ai trong channel cũng có thể tham gia. Bạn sẽ thấy:
- **Progress checklist edit tại chỗ** — 1 message Claude cập nhật khi làm (edit **không gửi notification** — hãy nhìn items được tick; hoặc yêu cầu "message tôi ở các decision point lớn")
- **Reply mới** khi cần bạn (câu hỏi, vấn đề không tự giải quyết được) hoặc có kết quả — có câu hỏi thì Claude **chờ** bạn
- **Im = đang làm**; bị chặn thì Claude thường nói ra thay vì im lặng
- ⚠️ **Edit message đã gửi không tác dụng — gửi reply mới**; mỗi top-level message = task mới; task riêng → thread riêng (channel notes vẫn áp mọi thread)

### Step 4 — Review kết quả
Đọc trước khi dùng; stakes cao thì đọc kỹ hơn — kết quả trong thread **không có** dashboards/documents bạn vẫn kiểm đối. Vì đã build cơ chế kiểm tra trước đó, hãy theo dõi links/files/queries nó cite. Sửa theo nguyên nhân:
- Nhìn **nhầm chỗ**/không truy cập được đúng chỗ → chuyển channel có tool / nhờ admin connect
- **Thiếu** → hỏi nó đã search sources nào (có thể bị chặn hoặc dừng sớm)
- **Request không rõ** → reply viết lại (muốn gì, form, priorities, nhìn đâu)
- **Miss pattern của team** (kể cả cách check work) → save vào memory cho cả channel
- Lỗi khác → troubleshooting docs; `@Claude !help` liệt kê commands

## Bài 10: Expand what Claude owns (15′)

### Bốn lớp cộng dồn thành ownership
- **Connections** (bài 3): Claude biết tools team dùng + thông tin sẵn có
- **Corrections** qua memory + instructions (bài 6): Claude biết cách team nghĩ
- **Untagged replies** (bài 7): Claude biết **khi nào** tự hành động
- **Routines** (bài 8): Claude biết **khi nào bắt đầu** không cần ai hỏi

→ Context của team, colleagues shape được, làm việc hướng mục tiêu **hàng tuần** chứ không chỉ 1 request. Tất cả quản lý tại **Configure page** của channel (mỗi channel một page; full member đăng nhập org mở được).

### Từ task → ongoing job
Claude chạy độc lập trên nhiều channels, nhiều tasks song song → bạn delegate/steer ở **cấp team**.

Bạn verify càng nhiều thì scope giao cho Claude càng lớn: vai trò của bạn dịch chuyển từ chỉ đạo từng task sang **đặt goals + review những decisions quan trọng**.

Bạn set standard một lần, Claude xử routine cases, bạn chỉ review decisions. **Attention của bạn giờ là giới hạn** → nhờ Claude **gom các câu hỏi lại** và **đính kèm recommendation cho mỗi decision**.

Đây là cách các team ở Anthropic làm: delegate có ranh giới, giữ human judgment cho các quyết định cần nó.

> **Try — giao 1 ongoing job:** chọn việc bạn giữ khỏe theo thời gian (launch, stream of decisions, resource mọi người phụ thuộc)
> → tạo channel riêng cho work đó → connect tracker + channels + docs Claude cần đọc → post ownership message, VD:
> *"The goal: we launch on October 14 with no open blockers. You own keeping us unblocked until then. Read the tracker and these channels.
> When something is stuck, find out whether we need information or a decision. Get the information yourself. Bring me anything about scope, timeline, or a real trade-off, grouped twice a week."*
> → Đưa feedback khi Claude làm đúng hoặc bỏ sót. Done khi: ownership message đã post + Claude từng tự act 1 lần mà không được nhờ + nó mang cho bạn **1 decision thay vì tự quyết**.

## Bài 11: Review your team's habits (10′)

Checklist rà từng channel (tốt nhất: channel team giao Claude nhiều việc nhất) — theo habit từng bài.

Mỗi "**no**" = một điểm cần cải thiện để thử + bài học cover nó; trả lời hết các dòng → checklist **tự tạo message** bạn post cho Claude trong channel đó để khởi động các gap còn thiếu.

**Next resources:**

- tasks to try (việc nên thử)
- best practices (kinh nghiệm thực hành tốt)
- use cases theo loại channel (cho mọi người)
- *Building Effective Human-Agent Teams* (team lead)
- customize Claude Tag + connect team tools (người setup).

> Key takeaway: habits là **của team**, không của một người — check cùng nhau và **viết kết quả ra nơi Claude đọc được**.

---

# PHẦN B — Docs tham chiếu

## B.1 — How Claude Tag works (concepts)

### Session model
- Mỗi **thread** Claude tham gia chạy một **session riêng** với **sandbox riêng** (mỗi thread một sandbox, không share state).
  Channel có top-level session riêng (ngoài các thread) xử lý @-mention top-level — `!restart` ở top level thay session channel
- **5-step loop**:
  1. tag/routine khởi động
  2. sandbox build
  3. working loop với access của channel, checklist edit tại chỗ
  4. result vào thread
  5. quiet period — **sandbox release, thread giữ nguyên**; reply mới rebuild sandbox và chạy tiếp
- Sandbox chạy **cùng engine với Claude Code on the web** — clone GitHub repos, edit, push branch/PR. Ngay cả khi không connect gì, Claude vẫn đọc thread + channel history + workspace search + chạy code

### Checklist & steering
- Task dài: reply đầu là **checklist sống** edit tại chỗ — Slack **không notify khi edit** → thread im = đang làm (không phải stuck); mở thread xem items tick. Stuck thật → Claude nói ra
- **Ai trong channel cũng steer được** bằng reply trong thread (không cần tag lại); nút **Stop** trên working indicator (DM không có) dừng nhưng giữ session
- ⚠️ **Edit message**: Claude nhận note (cả 2 versions vào transcript) nhưng **không phải instruction mới**; **delete reply**: Claude không biết; **delete message đầu thread**: session đóng (transcript vẫn lưu phía Anthropic)

### Kết quả post về đâu
- Reply (câu hỏi ngắn)
- file/chart đính kèm
- **page edit liên tục** (digests, indexes)
- **hosted page trên claude.ai** (dashboards, prototypes) — sau session vẫn mở được, ai vào được source channel thì xem được, update qua thread

Code work → **draft PR dưới Claude GitHub App**.

### Channel access & cross-channel
- Access set **per channel** (admin áp cho channel/workspace/toàn Slack/bundle) — cùng capability cho **mọi người** hỏi ở đó (predictable, clean audit)
- Thread **lock** skills/plugins/instructions lúc start; **connectors + domain rules enforce từng request** — thêm mới chạy được ngay trong thread đang chạy (Claude không báo — hãy gọi tên service); thread mới pick mọi thay đổi
- **Hỏi ở đâu quyết định làm được gì ở channel khác**:
  - public channel → đọc + post/reply/react được ở public channel khác Claude là member
  - private channel/group DM → chỉ đọc (không post)
  - DM → chỉ top-level posts sau khi bạn **Approve and post**
  - Post bên ngoài luôn kèm **attribution line** (*"Sent by Claude in #team-eng on behalf of @jordan"*); reply ở thread đích quay về conversation bạn hỏi
  - `follow #incidents and tell me here if...` — theo dõi channel khác, act về nơi bạn hỏi (follow đặt từ thread hết hạn sau 7 ngày không hoạt động)

### Session context & memory
- Mention Claude giữa thread có sẵn → chỉ nhận **window** messages (bots filtered) — thread dài cần **restate các thông tin critical**
- **Sống qua idle**:
  - conversation + context ✓
  - channel memory ✓
  - work pushed/posted/PR ✓ (ngoài hệ thống)
  - **files chỉ trong sandbox ✗** (recreate nếu hỏi) → việc dài: nhờ push branch/post draft sớm
- Session thay mới khi:
  - `!restart`
  - stuck & fail (message kế tiếp)
  - channel session: ~1 giờ không hoạt động / config changed / ~1 ngày tuổi

  Claude **ngừng đọc top-level** sau ~100 messages kể từ lần cuối nó post (mention đánh thức)

### Claude Tag vs Cowork vs Claude Code
| | Claude Tag | Cowork | Claude Code |
| :--- | :--- | :--- | :--- |
| Ở đâu | Slack channels | claude.ai chat | Terminal/IDE |
| Access ai | Của team (service accounts admin set theo channel) | Của bạn (personal OAuth connectors) | Của bạn (local credentials + filesystem) |
| Ai thấy work | Cả channel | Chỉ bạn | Chỉ bạn |

### Admin thấy gì
Không có page/export nào hiện từng message người dùng gửi Claude:
- analytics (spend theo channel)
- **Activity page** (scheduled work, memory files, network events — Owners)
- Slack threads (như mọi member)
- session transcripts (Anthropic giữ).

## B.2 — How agent identity works

### Danh tính theo nơi message
- **Channel + group DM**: Claude dùng **service accounts riêng** (Owner provisions) — Claude app trên Slack, **Claude GitHub App** trên GitHub (PR author + link ngược về Slack thread), service account trong mọi tool khác.
  Hành động attribute về các account đó — team thấy ai làm gì
- **DM 1-1** (user đã connect Claude account): session chạy trên **claude.ai account của người dùng** với personal connectors — work attribute **về bạn** (trừ PR vẫn do Claude GitHub App author, nhưng chỉ repos connect trên account bạn)
  **billing về seat của bạn** thay vì org
- Claude Tag DM 1-1 vs **Claude Code in Slack**: hai thứ trông giống nhau — PR mở **dưới tên bạn** = Claude Code in Slack, không phải Claude Tag

### Personal connectors trong channel
Task của bạn cần những gì chỉ connectors của bạn mới truy cập được → Claude hỏi trước. 3 lựa chọn:
- **Allow**
- **Allow with review** (Enterprise admin có thể bắt buộc)
- **Don't allow**

Work chạy với quyền của bạn, ghi tên bạn; request người khác trong thread chạy với access của channel.

Claude thiết kế nhận direction từ **chủ connector** — post của người khác trong thread chỉ là information, không phải instructions; chủ connector có thể yêu cầu dừng.

### Agent Proxy (biên mạng)
Request ra ngoài sandbox (trừ GitHub API/git) qua Agent Proxy, check **3 allow layers** — qua nếu **một** cho phép:
1. Host khớp **allowed websites** của credential → proxy gắn credential, forward (credential **không** vào model/sandbox; đã save không hiện lại — write-only)
2. **Allowed domain** áp cho channel (không credential) → forward
3. **Network access setting của environment** (mặc định **Limited access** — package registries + dev hosts chuẩn) → forward
4. Không khớp → **block** (Claude nêu tên host bị chặn trong thread để admin add)

Chỉ **HTTP/HTTPS** qua được — SSH/native database protocol không qua được dù host có allow. `curl`/`fetch` trong sandbox cũng theo rules này.

**Web search ≠ fetch**: search chạy trên server Anthropic (không cần domain entry, không qua Agent Proxy) — Claude **quote được** trang search thấy mà **không mở được link đó** (mở URL = request từ sandbox, cần allow).

## B.3 — Security and data handling

- **Sandbox không giữ credentials**: credential store riêng; Agent Proxy inject tại biên khi request khớp rule. Session chạy ephemeral sandbox (như Claude Code on the web); thread im → sandbox release
- **Không available** cho org:
  - **Zero Data Retention (ZDR)**
  - **CMEK**
  - HIPAA config — vì Claude Tag giữ channel memory + session transcripts
- **Default-deny egress** + GitHub proxy riêng: GitHub API/git không qua 3 layers mà qua GitHub proxy — **chỉ repos admin granted** (public repos clone được không cần credential)
- **Service accounts**: dùng **dedicated account mỗi service** (VD `claude@yourcompany.example`) — audit tách bạch, revoke không ảnh hưởng đến tài khoản người thật
- **Isolate credentials giữa channels**: access áp tại channel / workspace / toàn Slack / **channel rule** (pattern tên channel). Bundle finance chỉ áp 1 private channel → sessions channel khác chạy **như thể credential đó không tồn tại**.
  ⚠️ Credential đầu tiên add ở tab Connectors áp **toàn Slack** ngay — muốn giới hạn: add qua bundle/channel page/Add credential (off everywhere → chọn chỗ áp dụng)
- **Slack Connect channel**: Claude chỉ dùng bundles **attach trực tiếp channel đó** (+ bundles cho Slack Connect); workspace/Slack-page credentials **không** tới; personal connectors không tới
- **Artifact visibility**: ai vào được source channel → mở được page; **không có share setting**; updates qua thread/comment trên page. Guest + Channel only → không publish artifacts
- **Member access**: mặc định ai trong workspace cũng invoke được (không cần Claude account) — Team: *Restrict to your organization*; Enterprise: *restrict theo role có capability Claude Tag in Slack*

## B.4 — Commands (`@Claude !…`)

| Command | Tác dụng |
| :--- | :--- |
| `!help` | Liệt kê commands (theo workspace; Slack Connect: chỉ !help/!mute/!unmute/!restart/!fast — công ty kia chỉ !help) |
| `!configure` | Link Configure page của channel (trong DM → link admin settings) |
| `!restart` | Thay session kẹt/sai context — trong thread: thay session thread (rereads thread); top-level: thay session channel. Cần quyền message session |
| `!status` | Note **chỉ mình thấy** — Claude còn đang làm không, bao lâu; không interrupt |
| `!mute` / `!unmute` | Im/bật **riêng thread** (không có channel-level mute; top-level → hint). **Thumbs-down button** trên reply = mute thread (👎 reaction không); mention kèm request tự unmute |
| `!fast` / `!fast off` | Fast mode (nhanh hơn, đắt hơn/token; chạy trên **Opus** — có thể đổi model session; reply footer nêu model). Kèm bảng lỗi + cách xử |
| `!feedback [text]` | Mở form gửi feedback; text kèm thành draft |
| `!scheduled [#channel]` | List routines channel (hoặc channel khác qua mention — trả lời riêng bạn) |
| `!fork <prompt>` / `!fork #channel <prompt>` | Tiếp tục conversation trong **thread mới** (link 2 chiều, prompt required) — chỉ thread trong **public channel**; channel đích phải public + bạn & Claude là member |

## B.5 — What Claude Tag remembers (memory docs)

- Memory **thuộc channel, không thuộc người**; tích lũy 3 cách:
  - bạn nói ("remember...")
  - Claude tự save khi làm
  - **đọc past sessions** (không full-text search — nêu timeframe/topic)
- Bảng read/save:
  - **Public channel** — đọc channel notes + workspace notes, save cả hai
  - **Private channel** — đọc workspace notes (read-only), save **chỉ** channel notes
  - **Group DM** — chỉ notes của group DM đó
- DM notes lưu **cùng workspace** (không theo Claude account của bạn) — bị xóa khi Owner disconnect workspace
- Channel đổi public↔private → notes theo channel; workspace notes đã save từ lúc public **ở lại** workspace (không nên shared → nhờ Owner xóa)
- **Make it stick**: nói tường minh `remember for this channel: ...`; **giữ ngắn** (budget/channel hạn — entry dài crowd out); playbooks dài → **repo Claude đọc được** (link runbook/style guide thay vì đưa hết vào memory)
- Check/correct: `what do you remember about this channel?` → sửa/xóa stale; sau khi sửa nhờ Claude **ghi bản sửa** vào memory; **prune định kỳ** (routine weekly review memory hoạt động tốt)
- Owner xem/sửa/xóa **memory files** trong Claude Tag admin settings

## B.6 — Set up routines (docs)

### 3 loại + recipes
- **Scheduled jobs**: `@Claude every weekday at 9am, read the open threads... post a one-line status per item. Skip anything with a ✅ reaction.` — **nêu output format** để scannable
- **Watch channels**: `watch #product-announce, #eng-announce... Once a day, post here if anything is relevant to user education. Skip days with nothing.` — **nêu cả channels + topic**
- **Follow a PR** (subscribe): `subscribe to PR #482 in acme/data-pipeline. When CI finishes or a review lands, post here, and tag me if anything failed.` — cách **duy nhất** Claude react GitHub events; không routine cho repo events khác
- Recipes:
  - daily standup ("waiting on someone" để surface actions)
  - weekly digest
  - watch PR until merge
  - **alert investigation** (mỗi 2h check dashboard, post first-pass diagnosis cho alert mới — cần connection Datadog/PagerDuty)
  - **auto triage** (standing role qua `remember for this channel` — dedupe/answer/route)

### Nơi post & quản lý
- Routine setup **từ thread** → report trong thread đó (chừng nào session sống); session stuck → chạy về top-level → muốn về thread: disable + setup lại từ thread. Setup **top-level** → announce ngắn + work trong thread dưới
- List (`!scheduled`; hỏi trong thread chỉ ra routines của thread đầu — hỏi *"every routine in this channel"* để đủ)
- reschedule/pause/stop (nêu tên)
- đổi nội dung = stop + setup lại
- Routines channel **sống qua người setup rời đi**; DM routines theo account người — tắt khi bị xóa khỏi org

### Boundaries
- Chạy với channel connections như interactive
- public → public khác (label nguồn)
- group DM chỉ post trong đó
- **không DM người** (chỉ completion/failure notice cho người setup khi Slack account connected)
- ⚠️ **Schedules chạy theo UTC** — nêu timezone ("9am Pacific"; không nêu → theo Slack profile; `!scheduled` list UTC)
- DST lệch 1h → nhờ reschedule
- PR jobs dùng GitHub connection admin set.

## B.7 — Control when Claude Tag responds

### Trigger theo nơi
| Nơi viết | Trả lời không tag? |
| :--- | :--- |
| DM 1-1 | Luôn (message nào cũng gửi Claude) |
| Thread Claude đang trong | Có (mọi reply tới nó, khỏi mention) |
| Channel top-level | **Đôi khi** — Claude quyết; @-mention để đảm bảo |
| Group DM top-level | Đôi khi |
| Message app/bot khác | **Không** (đọc làm context; reply chỉ khi bot @Claude) |

@-mention → Claude **react emoji** trong vài giây (đã nhận) → trả lời thread hoặc mở working session (working indicator + Stop). Reaction mà không có indicator = đang cân nhắc/trả lời trực tiếp.

### 5 hành động với message không tag
1. **Không làm gì** (bình thường nhất — channel chưa dạy loại message nào cần trả lời)
2. **Offer to help** — 1 dòng, hoặc **private suggestion** (card *"From Claude, only you can see this"* + Yes/No; hết hạn sau 1 ngày)
3. **Short reply** — khi câu trả lời đã có sẵn (history/memory), gọn trong 1 message; display name plain **Claude**
4. **Working session** trong thread — chỉ khi ai đó trong channel đã dạy loại work đó
5. **Hand-off sang session đang chạy** — message thêm chi tiết cho việc đang làm ở thread khác (không post gì ở đây)

Claude còn **ghi nhận channel có act theo unprompted replies hay bỏ qua** — bị ignore thì reply ít đi. (Working sessions hiển thị **Claude [reviewing the launch checklist]**.)

### Respond automatically (setting từng channel, mặc định ON)
Đổi tại 3 nơi (cùng 1 setting):
- nói với Claude trong channel
- **Configure page**
- admin settings claude.ai

Admin set **Channel member edits = Block** → member không đổi được (Claude từ chối yêu cầu qua Slack; channel manager vẫn đổi Configure page). Không có bản workspace-wide — tắt từng channel.

### Im lặng / giảm noise
- 1 thread: *"only respond when I @-mention you"* hoặc `!mute` (thumbs-down cũng mute thread)
- Cả channel: Respond automatically **off** — post top-level (không phải trong thread): `@Claude only respond in this channel when someone @-mentions you directly.`; Claude decline → admin đã lock → nhờ admin
- Private suggestions: ⋯ menu → **Mute for a week** (chỉ áp cho mình bạn, mọi channel trong org); channel mention-only = không suggestions
- Trường hợp cuối cùng: `/remove @Claude`

### Khi Claude ngừng đọc channel
**Message volume** (đếm từ lần cuối Claude post) hoặc **>10 ngày không mention + không post** → ngừng đọc (không báo). @-mention từ người đánh thức cả hai trường hợp.

Mention trả lời mà unprompted không quay lại → setting Respond automatically đang off.

### Messages không bao giờ được trả lời
- Edit message thêm mention (không trigger — xóa gửi mới)
- channel có **guests** (mặc định off — admin bật được, và khi bật vẫn **không workspace search** từ channel có guest)
- channel shared workspaces thuộc **Claude org khác nhau** (refusal message)
- **Slack Connect** với công ty khác (mặc định off, không báo)

Shared cùng 1 Claude org → trả lời nhưng chỉ default access/settings của org (channel-specific repos/instructions không áp dụng).

## B.8 — Good habits (docs)

### Work in the open
- **Public**: mọi thread + checklist + results channel đọc được; những gì team viết ra (decisions, conventions, postmortems) là context Claude dùng — *"knowledge sống trong DM hoặc nói miệng là vô hình với nó"*
- **Share control** — reply vào thread người khác khởi động là cách work được chuyển giao
- **Grant broad access** — nguồn dữ liệu kết nối càng đầy đủ, kết quả càng hữu ích; connections scoped vào agent identity nên **không lộ data cá nhân** của ai
- **Destination not route** — nói outcome; definition-of-done làm cụ thể
- **Tolerate the mess** — draft thô ban đầu trong thread hữu ích hơn draft hoàn thiện trong DM: *thread là workspace, không phải deliverable*

### Mention
Claude không add ai vào channel; không quyết định mention có notify.
- **Public channel**: người được mention thấy ở Activity dù chưa join
- **private**: không notify, phải mời
- **User group**: nhờ "notify group" (plain text handle không notify; app cũ cần Slack admin re-approve)

Claude **không bao giờ ping @channel/@here/@everyone**.

### Viết task tự đóng
- **Name the outcome, not the activity** — "post the project status and tag me when it's up" ✓; "look at this" ✗ (open-ended report)
- **Detail**: background có sẵn (thread/channel/tool) → **link + 1 câu outcome**, không cần nhắc lại.
  Sai tốn kém → viết thành **constraints**: rules phải theo, checks là verification, những gì không được chạm vào
  — VD: *"migrate the export config. Hard rules: no behavior change, don't touch the billing module, every old key keeps working as an alias. Done means the full test suite passes."*
- ⚠️ **Constraints steer nhưng không restrict** — gì phải không-bao-giờ thì enforce **ngoài conversation**: repository permissions, branch protection, required checks
- **Definition of done** (bảng ai đóng thread):

| End condition | Ai đóng | VD |
| :--- | :--- | :--- |
| Objective check pass | **Claude tự** | "Done when CI is green" |
| Bạn approve result chuẩn bị sẵn | Bạn, 1 click | "Draft the memo and post for approval" |
| Bạn chọn giữa options | Bạn, 1 chữ | "Research A and B and recommend one" |
| Không có điều kiện verify được | Không ai | Reframe thành **câu hỏi** thay vì task |

  - Điều kiện phải **observable bởi Claude** ("CI green" cần access CI — không có thì đổi điều kiện bạn tự đóng); **spell out hết** ("babysit this PR until it merges" = approvals + comments resolved + go-ahead của bạn)
  - Task Claude tự đóng → nhờ **attach proof** (source link, chart, test output, diff) — bạn đọc proof, không đọc transcript.
    Long-running: **durable là một phần của done** (post file / push branch / mở draft PR sớm). Calibrate: channel mới check tất cả; nới dần khi output đứng vững

- **Decisions nào quay về bạn**: nói rõ tự quyết gì / mang về gì — không nói thì Claude tự phán đoán từng case (hoặc tự quyết định chừng nào nên hỏi). ⚠️ Cần enforce → branch protection, không chỉ prompt
- **Format cho recurring** (🔴 person/🟡 watch/🟢 fine, skip 🟢) — hoặc "use the format from your 9am post going forward"
- **Steer explicitly**: `@Claude remember for this channel: always format reports as a table, and ask before posting anything longer than a screen` (cả 2 chiều: thêm structure hoặc bớt noise)

### Đúng chỗ
- **Thread mới cho task mới** (session mang cả conversation; multi-task thread → quá dài); fan-out nhờ Claude mở thread mỗi việc; `!fork` tiếp tục discussion
- **3 surfaces**:

| | Team channel | Channel riêng của bạn | DM 1-1 |
| :--- | :--- | :--- | :--- |
| Access | Connections channel (admin) | Connections channel (admin) | Personal connectors của bạn |
| Memory | Team builds | Bạn build | Ngoài channel/workspace memory |
| Ai thấy | Cả channel | Bạn + người mời | Bạn |
| Billing | Organization | Organization | Seat của bạn |

  - DM trả lời private về public channel được (nêu tên channel) — nhưng chỉ bảo đảm privacy của câu trả lời, không mở rộng thêm reach
  - đọc **full history** public channel cần member (search thì không)
  - private channel chỉ hỏi từ bên trong
  - Slack Connect / cross-workspace limits; **nhiều nơi work được → chọn channel** (work ở đó được cộng dồn)

### Dạy điều gì đó stick (bảng 6 nơi)
| Muốn Claude biết | Đặt ở | Ai viết | Với tới |
| :--- | :--- | :--- | :--- |
| Channel này nên behave thế nào | **Channel memory** (nói + remember) | Ai trong channel | Channel đó (workspace note nếu từ public) |
| Conventions + setup cho 1 repo | **`CLAUDE.md`** ở repo root | Ai có repo write | Session nào làm việc repo đó |
| Rules của channel, outrank memory | **Channel instructions** (Configure) | Members (trừ khi lock) | Channel đó |
| Correction riêng tư cho channel | **Managed instructions** (private managing channel) | Full members đã setup | Channel đó |
| Dùng tool đúng cách, org-wide | **Skill** trong org marketplace | Owner (ai cũng đề xuất PR) | Mọi nơi nó được add |
| Rules nhiều channels | **Workspace/Slack instructions** (admin) | Owner/Tag admin | Mọi channel workspace/Slack |

`CLAUDE.md` mang cả **install commands** (session sandbox có tool chuẩn — repo cần runtime/db client thì ghi commands, Claude chạy khi cần). *CLAUDE.md là guidance; required status check là gate.* Có thể nhờ Claude mở PR đề xuất sửa skill.

### Configure page & vận hành
Configure link (footer) hoặc `!configure`:
- **Respond automatically** toggle
- **Channel instructions** (outrank memory; save → áp session mới)
- tab **Tools and access**: Connections (xem), Plugins (add được trừ khi admin lock), channel manager có thêm Access bundles + GitHub repos

Giữ số thread khớp năng lực review:
- **1 channel/project**
- **batch reviews** (một lúc rẻ hơn rải rác — mỗi lần quay lại là context reload)
- **✅ thread đóng** + dạy digest routine skip chúng.

## B.9 — Use case library (13 use cases)

| Use case | Cho ai | Claude làm | Connections |
| :--- | :--- | :--- | :--- |
| Catch up | Mọi người | Tóm tắt thread/channel/điều chờ bạn | Không |
| Your own channel | Mọi người | Scratch questions, digests, theo dõi việc bạn đã hứa | Không (tracker/GitHub tùy chọn) |
| Triage requests | Support/ops/IT | Trả lời được, flag trùng, route phần còn lại, rollup themes | Không |
| Threads → docs & tickets | Mọi người | Decision doc, memo, ticket, reply send-ready, hosted page | Không (Drive/tracker tùy chọn) |
| Track projects + chase approvals | PM/leads | Status digests, follow-up sign-off đỗ | Không |
| Find answers in docs | Mọi người | Tra policy/runbook/decision + source | Drive/Notion/Confluence |
| Review documents vs checklist | Ops/compliance | Check docs theo checklist, findings từng mục | Drive/Notion/Confluence |
| Answer data questions | Analysts | Query warehouse, trả chart (hoặc chart từ Slack) | BigQuery/Snowflake/Redshift (chart từ Slack: không cần) |
| Fix bugs | Engineering | Reproduce, draft PR, theo CI tới green | GitHub (Datadog/Sentry tùy chọn) |
| Work with GitHub | Eng | Trả lời câu hỏi repo, watch PR, chores → draft PR | GitHub |
| Watch monitors & alerts | On-call/SRE | Check dashboard theo lịch, điều tra trước khi ai hỏi | Datadog/Sentry/PagerDuty |
| Pull deal & account state | Sales/CS | Trả lời account, pre-call brief, weekly pipeline digest | Salesforce/HubSpot/Gong |
| Marketing team | Marketing | Policy Q&A, drafts từ campaign threads, weekly metrics digest | HubSpot/Salesforce + Drive/Notion + BQ/Snowflake |

Connections theo nhóm:
- Knowledge/docs → find answers
- Issue tracking → tickets/projects
- Data warehouse → data questions
- GTM → deal state
- Monitoring → alerts
- Code (GitHub) → bugs/PR/CI.

## B.10 — Troubleshooting (bản rút gọn theo nhóm)

**Im lặng:** @Claude không react không reply → check:
1. app cài chưa (autocomplete có APP badge?)
2. Claude trong channel chưa (`/invite` — **không chạy trong thread**)
3. Tag bật cho channel chưa (3 loại notice: *isn't on yet* / *disabled* / *legacy retired*)

- Trả lời cho bạn không cho teammate → member access restriction
- **Reacted/indicator mà không reply** → `!status` (chỉ mình thấy, không interrupt); im quá lâu → `!restart` (⚠️ last resort — bỏ dở midway, không resume được)
- Queued/failed to start → chờ vài phút / mention retry
- **Edit thêm mention không trigger** → xóa gửi mới
- Slack Connect im → mặc định off
- Guest channels → remove guests / admin bật (bật rồi vẫn không workspace search)
- "Couldn't check this channel" → guest-check fail tạm — mention lại

**Trả lời sai/ồn:** Confident-but-wrong → check source links, "which channels did you search?", "show me the query" (sai phổ biến nhất là **incomplete** — 1 nguồn/1 date range); definition-of-done yêu cầu source mọi figure.
- Reply mọi message trong thread → "only respond when I @-mention you"
- Reply không tag → Respond automatically off (post **top-level**)
- Muốn rút lại → edit chỉ thành note, delete không tới được Claude — **nói bằng reply mới**
- Xóa message Claude post → chỉ áp dụng message session hiện tại, khi người trong conversation yêu cầu, permanent (transcript vẫn còn)
- "Conversation too long" → thread mới (paste summary)

**Dừng giữa chừng:** API errors/rate limits → auto-retry ~2 phút (tối đa 3; mention để retry sớm; rate limit là momentary, **không phải** spend limit).
- Usage credits hết → admin mua, mention retry
- Couldn't clone repo → transient hoặc repo không granted
- **Disconnected** (sandbox dừng) → conversation + work đã push/post sống; **files chỉ trong sandbox mất** — fresh machine thì Claude tự re-check; mention để chạy lại bước bị cắt
- "Something went wrong" → mention retry

**Work mất/stale:** Files mất → workspace recycled — nhờ recreate + push/post sớm.
- Thread cũ fail, thread mới OK → thread giữ config lúc start → `!restart`
- Sai repository → **nêu repo trong message đầu** ("in acme/data-pipeline, fix...")
- Quên instructions → memory là curated note không transcript — `remember for this channel`, giữ ngắn
- Session link not-found → session thuộc agent identity: sign-in account org paired + khớp Slack identity (email khác → connect Slack account qua DM); private channel chỉ members

**Access:** Connection mới không hiện trong session đang chạy → **gọi tên service** / thread mới.
- "Can't access channel từng đọc" — public: search được nhưng đọc trực tiếp cần invite; private: chỉ đọc từ bên trong
- Connector chạy claude.ai không Slack → DM dùng account connectors của bạn; setup tại claude.ai **Customize > Connectors**; chỉ DM mới pick up
- Personal connectors cần **Opus 5 bật org-wide** (Claude dùng cho checks) — tắt thì decline
- Không mở link được nhưng search thấy → fetch cần admin allow host
- **SSH/native DB không qua proxy** (chỉ HTTP/HTTPS) → dùng HTTP API
- Spend limits (3 loại messages: Claude Tag spend limit / individual extra / org extra) → admin nâng hoặc chờ reset; "Rate-limited delivering" ≠ spend limit — chờ vài giây gửi lại
- "Can't access this organization" → sai account browser

**DMs:** Environment error → mention lại (thường clear).
- Seat không đủ → DM cần seat có **Claude Code** (Enterprise: Standard/Usage-Based Chat + Cowork); channel vẫn tag được
- DM bị org tắt → dùng channel
- Group DM không support (Slack Connect/Grid) → channel/DM 1-1
- "Agents can only be added at the start of DMs" → Slack rule: chuyển sang private channel (Slack gợi ý) hoặc DM Claude trực tiếp

## B.11 — Blog: Building Effective Human-Agent Teams

AI work chuyển từ **single-player** (1 người + 1 chat window) sang **multiplayer** — human-agent teams trong workspace chung (Slack). Nền tảng kỹ thuật agents cần:
- persistent memory
- credentials không gắn con người
- broad ongoing access.

**4 bài học:**
1. **Work in public; broad context** — agent chỉ hiểu từ **text tìm được** (Slack, docs, code): *"if it's not written down and accessible, it doesn't exist."*
   Vài workspace-level boundaries thay vì chia sẻ từng item; docs viết với agent là một audience chính; việc nhạy cảm → DM/apps cá nhân
2. **Role rõ + tools đúng** cho mỗi người & agent — một roster, một bộ artifacts, một workspace; không có role rõ → "fleets of personal AIs", trùng lặp, context vụn; người giữ các việc judgment-heavy
3. **North star cho proactive** — người định nghĩa + ghi lại mục tiêu gắn mission; chỉ agents được chọn (skills + trust) mới đề xuất workstreams mới; human meetings dịch về decisions giá trị nhất
4. **Trust theo thời gian** — autonomy theo reliability đã chứng minh (một team đạt 500 bug fixes độc lập)
   - verification trước human review (tests, rubrics, **Doer-Verifier** — một agent làm, một agent check)
   - reflection cycles (weekly "lessons & missteps")
   khi agent đã độc lập, dạy agent xem **human attention là tài nguyên khan hiếm**: gom câu hỏi, cap review items, cap workload ngày

**5 câu tự vấn:** info public + searchable chưa? roster + ownership viết ra được chưa? ai cũng có tools đúng chưa? có rubrics/tests verify việc chính chưa? có north star rõ để tham chiếu chưa?

> Takeaway: các pattern này không mới (goals rõ, role rõ, documentation, quality bars) — agents khiến chi phí của việc **bỏ qua chúng trở nên đắt hơn**.

---

# Phụ lục: Nguồn đã quét

| Nhóm | Nguồn |
| :--- | :--- |
| **Khóa chính (raw HTML, 11 bài)** | `/courses/introduction-to-claude-tag/` — tag-claude-and-see-what-happens · claude-in-a-dm · claude-in-a-public-channel · claude-in-a-private-channel · pick-the-right-place-for-the-work · refine-claudes-learning-through-feedback · proactivity-let-claude-reply-without-being-tagged · put-recurring-work-on-a-schedule · write-a-request-claude-can-work-with · expand-what-claude-owns · review-your-teams-habits |
| **Docs concepts** | [how-it-works](https://claude.com/docs/claude-tag/concepts/how-it-works) · [agent-identity](https://claude.com/docs/claude-tag/concepts/agent-identity) · [security-and-data](https://claude.com/docs/claude-tag/concepts/security-and-data) |
| **Docs users** | [commands](https://claude.com/docs/claude-tag/users/commands) · [memory](https://claude.com/docs/claude-tag/users/memory) · [proactivity (routines)](https://claude.com/docs/claude-tag/users/proactivity) · [when-claude-responds](https://claude.com/docs/claude-tag/users/when-claude-responds) · [good-habits](https://claude.com/docs/claude-tag/users/good-habits) · [use-cases](https://claude.com/docs/claude-tag/users/use-cases) · [troubleshooting](https://claude.com/docs/claude-tag/users/troubleshooting) |
| **Khác** | [Blog: Building Effective Human-Agent Teams](https://claude.com/blog/building-effective-human-agent-teams) · `claude.ai/customize/connectors` (trang setup connectors) |
| **Được nhắc, ngoài phạm vi** | `claude.com/docs/claude-tag/users/prompt-library` (thư viện prompt) · `claude.com/docs/claude-tag/admins/*` (setup-overview, add-connections, restrict-access, configure-github, attach-to-scope, skills-repo, audit, data-lifecycle...) — tài liệu admin vận hành · khóa *Building Effective Human-Agent Teams* (beta, Academy) |

> ✅ **Độ phủ:** 11/11 bài đọc từ **raw HTML gốc**; 10/10 docs pages + blog quét trọn nội dung chính. ℹ️ Không có YouTube/media links trong nội dung (video = embed Academy).
