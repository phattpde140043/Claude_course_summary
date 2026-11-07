# Editorial Style Guide — Thư viện tóm tắt Claude Academy

Quy chuẩn biên tập áp dụng cho toàn bộ tài liệu trong `Claude_course_summary/`. Mọi vòng cập nhật tài liệu đều lấy file này làm chuẩn tham chiếu.

> Metadata: last_updated 2026-11-07 · scope: Editorial Standards · source: báo cáo đánh giá biên tập 2026-11

## 1. Nguyên tắc cốt lõi

1. **Tiếng Việt là ngôn ngữ diễn đạt chính.** Tiếng Anh chỉ xuất hiện với ba vai trò: thuật ngữ kỹ thuật, tên riêng (sản phẩm, tính năng, API), và nội dung nguyên bản (code, command, prompt mẫu).
2. **Không dùng tiếng Anh để thay thế từ tiếng Việt thông thường** (ví dụ: dùng "analyze" thay "phân tích", "refine" thay "điều chỉnh").
3. **Bảo toàn kiến thức khi biên tập.** Mọi vòng biên tập chỉ sửa ngôn ngữ, câu văn và tính nhất quán. Không tự ý viết lại nội dung kỹ thuật chưa được xác minh — ghi vào danh sách "Cần xác minh" của báo cáo biên tập thay vì sửa.
4. **Giải thích hành động kèm lợi ích**, thay vì chỉ mô tả hành động bằng một cụm từ ngắn.

## 2. Ba phong cách tài liệu

| Phong cách | Áp dụng cho | Đặc điểm |
| --- | --- | --- |
| **A — Executive Reference** | `Claude_Course.md` | Kết luận trước, giải thích sau; bảng quyết định và framework; súc tích; không diễn giải lại kiến thức phổ thông |
| **B — Technical Learning Reference** | `Claude_Code_101_Course.md`, `Claude_Code_In_Action_Course.md`, `Claude_Cowork_Course.md`, `Claude_Tag_Course.md`, `Claude_Platform_101_Course.md` | Giải thích khái niệm và cơ chế; ví dụ thực tế; quy trình từng bước; giữ nguyên code, command, thuật ngữ API; nêu lý do và hệ quả kỹ thuật |
| **C — Practical Use Case Library** | `Claude_Course_UseCases.md` | Mô tả tình huống ngắn gọn; prompt sao chép được; output và tips dễ tra cứu; giữ tên use case gốc |
| **Transcript** | `AI_Engineering_Leadership_Multiplier_Transcript.md` | Giữ nguyên văn; không áp quy tắc biên tập |

## 3. Quy tắc ngôn ngữ

### 3.1 Giữ nguyên tiếng Anh (không dịch)

- Tên sản phẩm và tính năng: Claude Code, Claude Cowork, Claude Tag, Skills, MCP, SubAgents, Hooks…
- Thuật ngữ API và kiến trúc: Messages API, Tool Use, Agent Loop, Managed Agents, Context Window, Streaming Events, server-side execution…
- Tên connector và công cụ: Google Drive, Slack, Jira, GitHub…
- Code, command, tên file, đường dẫn, cấu hình.
- Prompt mẫu trong `Claude_Course_UseCases.md` (giữ nguyên để người đọc sao chép sử dụng trực tiếp).

### 3.2 Ưu tiên tiếng Việt khi diễn giải

| Nên ưu tiên | Hạn chế sử dụng |
| --- | --- |
| Ngữ cảnh | Context (khi không phải thuật ngữ) |
| Quy trình | Process |
| Kết quả đầu ra | Output (khi diễn giải; giữ "Output" làm nhãn cấu trúc trong UseCases) |
| Thực hiện | Execute |
| Triển khai | Implement |
| Điều chỉnh | Refine |
| Phân tích | Analyze |
| Đánh giá | Evaluate |
| Khả năng | Capability |
| Phạm vi | Scope |
| Bàn giao | Hand-off |
| Tích hợp | Wire in |
| Tính chủ động | Proactivity (khi diễn giải) |
| Trách nhiệm đảm nhận | Ownership (khi diễn giải) |

Lưu ý: đây không phải quy tắc dịch toàn bộ. `Context Window`, `Output Token`, `Implementation`, `Evaluation` vẫn giữ nguyên khi đề cập khái niệm kỹ thuật cụ thể.

### 3.3 Lần đầu xuất hiện

Thuật ngữ quan trọng: viết tiếng Việt kèm thuật ngữ gốc trong ngoặc ở lần đầu xuất hiện — ví dụ `Quản lý ngữ cảnh (Context Management)` — sau đó dùng một cách gọi nhất quán xuyên suốt tài liệu.

## 4. Cấu trúc câu và văn phong

- Câu có chủ ngữ và vị ngữ rõ ràng; một câu tập trung vào một luận điểm.
- Không nhồi nhiều thuật ngữ vào một câu; tách câu khi cần.
- Cấu trúc song song khi liệt kê.
- Khách quan, chuyên nghiệp, trực tiếp; không khẩu ngữ, không viết như hội thoại.
- Không dùng mũi tên (`→`) thay liên kết câu trong văn diễn giải; chỉ dùng trong bảng, sơ đồ hoặc quy trình có thứ tự.
- Không kéo dài câu chỉ để giải thích điều hiển nhiên.

## 5. Tiêu đề

- Tên bài học chính thức từ nguồn gốc: giữ nguyên tiếng Anh.
- Tiêu đề do người biên soạn tự đặt: ưu tiên tiếng Việt, kèm thuật ngữ trong ngoặc nếu cần.
- Không đổi tiêu đề trong các vòng biên tập nếu chưa xác định được nguồn gốc tiêu đề.

## 6. Độ chính xác nội dung

- Tránh tuyên bố tuyệt đối: "luôn luôn", "hoàn toàn tự động", "đảm bảo chính xác", "không bao giờ xảy ra", "tất cả các trường hợp" — đặc biệt với chủ đề AI, bảo mật, agentic workflows.
- Phân biệt thông tin từ tài liệu nguồn và nhận định của người biên soạn; nếu là suy luận, diễn đạt thận trọng.
- Thông tin dễ thay đổi (model versions, context window, tính năng beta, quyền truy cập, giá) phải ghi rõ thời điểm cập nhật.

## 7. Metadata mỗi tài liệu

Mỗi tài liệu kết thúc bằng một dòng metadata:

```markdown
> Metadata: cập nhật YYYY-MM-DD · nguồn: Anthropic Claude Academy · phạm vi: <phạm vi tóm tắt>
```

## 8. Quy ước Markdown

- Heading phân cấp nhất quán.
- Không lạm dụng bold; bold dành cho thuật ngữ lần đầu xuất hiện hoặc điểm cần nhấn mạnh.
- Bảng dành cho nội dung có thể so sánh; bullet dành cho danh sách; numbered list dành cho quy trình có thứ tự.
- Code block dành cho code, command và cấu hình.
