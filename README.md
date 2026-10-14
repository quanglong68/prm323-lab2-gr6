# PRM323 Lab 2 — FPTU Second Brain Mobile

Bộ hồ sơ thiết kế UX/UI cho ứng dụng Android hỗ trợ sinh viên FPTU tra cứu đề cương offline, quản lý deadline, ghi chú Obsidian Vault và hỏi AI. Đây là bài thiết kế, không phải mã nguồn Flutter.

## Tài liệu bàn giao

| Hạng mục | Nội dung |
| --- | --- |
| Figma | [PRM323 Lab 2 — FPTU Second Brain](https://www.figma.com/design/0gpT8zQmaDiCmcklbFuTSq/PRM323_Lab2_FPTU_Second_Brain) |
| Persona | [ux/persona.md](ux/persona.md) |
| User flow | [ux/user-flow.md](ux/user-flow.md) — 3 prototype flow chính và nhánh AI Flow 1A |
| Design brief/system | [design/DESIGN.md](design/DESIGN.md) |
| Screen specification | [design/screen-spec.md](design/screen-spec.md) |
| Design decisions & accessibility | [design/design-decisions.md](design/design-decisions.md) |
| AI design log | [ai/ai-design-log.md](ai/ai-design-log.md) — Google Stitch và UX critique bằng Claude |
| Flutter handoff | [handoff/flutter-handoff.md](handoff/flutter-handoff.md) |
| Stitch evidence | [assets/stitch](assets/stitch/) — ảnh ban đầu và ba vòng lặp |
| Final UI exports | [assets/figma](assets/figma/) — 8 màn hình cùng dialog và biến thể lỗi, 360 × 800 |

## Các trang Figma

1. 01 User Flow
2. 02 Wireframe
3. 03 Final UI
4. 04 Design System
5. 05 Components
6. 06 Prototype

Prototype có 3 điểm bắt đầu: Flow 1 (tra cứu môn), Flow 2 (deadline/undo), Flow 3 (ghi chú/đồng bộ). Hỏi AI là nhánh Flow 1A từ SCR-03, không phải prototype độc lập thứ tư.

## Phạm vi

Android mobile-first, Material Design 3, light theme, Inter, khung Figma chính 360 × 800 dp; responsive tại 412 dp được mô tả trong `design/design-decisions.md`. Vault hỗ trợ đọc/ghi cục bộ offline; hỏi Gemini API cần mạng.
