# Claude Course Summary

Thư viện tóm tắt các khóa học **Claude Academy** (academy.claude.com) — biên soạn bằng tiếng Việt, giữ nguyên thuật ngữ chuyên ngành tiếng Anh. Đối tượng: người làm việc trong lĩnh vực technical đã quen sử dụng AI assistant.

> Toàn bộ nội dung được quét từ **raw text** của các bài học (kể cả sub-links, media links) cập nhật 11/2026, đảm bảo không bỏ sót thông tin chuyên môn.

---

## Mục lục

### 1. Nền tảng — Claude 101

| Tài liệu | Nội dung |
| :--- | :--- |
| [**Claude_Course.md**](Claude_Course.md) | Tài liệu tham chiếu điều hành của khóa Claude 101, viết theo phong cách McKinsey (kết luận trước, bảng quyết định). Gồm: Executive Summary · mô hình hợp tác (situation vs question, chọn model) · prompting & verification (khung 3 yếu tố, evals, delegation diligence loop) · 8 bề mặt làm việc (Chat/Cowork/Code…) · kiến trúc tri thức (Projects/Skills/Artifacts) · mở rộng reach (Connectors/MCP, Enterprise Search, Research) · bảng yêu cầu theo plan |
| [**Claude_Course_UseCases.md**](Claude_Course_UseCases.md) | Tra cứu **156 use cases** theo 14 nhóm role (Chung, Finance, Sales, Marketing, Operations, Education, Legal, Engineering, Product, Design, Research, HR, Data, Cá nhân) — mỗi use case có prompt mẫu theo bước |

### 2. Developer — Claude Code

| Tài liệu | Nội dung |
| :--- | :--- |
| [**Claude_Code_101_Course.md**](Claude_Code_101_Course.md) | Khóa Claude Code 101 (16 bài): cài đặt, Explore→Plan→Code→Commit, context management, `/review`, CLAUDE.md, subagents, skills, MCP, hooks, automation |
| [**Claude_Code_In_Action_Course.md**](Claude_Code_In_Action_Course.md) | Khóa Claude Code in Action (4 phần): Steer the work · Configure Claude · Automate repeat work · Verify and share — kèm tổng kết thực hành |

### 3. Bề mặt làm việc chuyên biệt

| Tài liệu | Nội dung |
| :--- | :--- |
| [**Claude_Cowork_Course.md**](Claude_Cowork_Course.md) | Khóa Introduction to Claude Cowork (11 bài): setup, hand-off task, global instructions, projects, skills, plugins, Claude in Chrome, Claude for Microsoft 365, best practices an toàn |
| [**Claude_Tag_Course.md**](Claude_Tag_Course.md) | Khóa Claude Tag — hợp tác với Claude trong Slack (11 bài): DM/public channel/private channel, memory & instructions, proactivity, schedule công việc định kỳ, viết request hiệu quả |

### 4. Platform & API

| Tài liệu | Nội dung |
| :--- | :--- |
| [**Claude_Platform_101_Course.md**](Claude_Platform_101_Course.md) | Khóa Claude Platform 101: API call đầu tiên, chọn model, agent loop, tool use, thinking, built-in tools, skills, MCP, context management, managed agents, prompt engineering |

### 5. Tham khảo thêm

| Tài liệu | Nội dung |
| :--- | :--- |
| [**AI_Engineering_Leadership_Multiplier_Transcript.md**](AI_Engineering_Leadership_Multiplier_Transcript.md) | Full transcript (raw, verbatim) bài nói "AI: The Engineering Leadership Multiplier" — kèm metadata và chapters theo timestamp |

---

## Lộ trình đọc gợi ý

| Bạn là ai | Đọc theo thứ tự |
| :--- | :--- |
| Người mới với hệ sinh thái Claude | `Claude_Course.md` → `Claude_Course_UseCases.md` (chọn role của mình) |
| Developer / DevOps | `Claude_Course.md` → `Claude_Code_101_Course.md` → `Claude_Code_In_Action_Course.md` |
| Team lead / Quản trị | `Claude_Course.md` → `Claude_Tag_Course.md` → `Claude_Cowork_Course.md` |
| Builder / Tích hợp API | `Claude_Platform_101_Course.md` → `Claude_Code_In_Action_Course.md` |

## Quy ước biên soạn

- **Ngôn ngữ:** tiếng Việt; thuật ngữ chuyên ngành giữ nguyên tiếng Anh (không dịch).
- **Phong cách:** tài liệu tổng (`Claude_Course.md`) viết theo phong cách McKinsey — kết luận trước, bảng quyết định, không phần dẫn dắt. Các tài liệu chi tiết giữ cấu trúc theo bài học của khóa gốc.
- **Độ phủ:** quét raw text toàn bộ lesson + sub-links + media links; bảng quyết định, con số cụ thể (context window, plan-gates, security model) được giữ nguyên 100%.
- **Ngày cập nhật:** 11/2026.
