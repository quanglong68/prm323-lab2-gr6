# P02 · Nguyễn Minh Đức — Sinh viên năm ba ngành SE

**Trạng thái:** Proto-Persona · **Vai trò:** Primary Persona · **Phạm vi sản phẩm cốt lõi.** Hồ sơ dựa trên mô tả trong project và giả định thiết kế; cần đối chiếu research log trước khi gọi là finding.

**Tóm tắt:** Nguyễn Minh Đức, 20 tuổi, sinh viên năm 3 Kỹ thuật Phần mềm (SE), Kỳ 5. Archetype: *Sinh viên SE tra cứu offline, theo dõi deadline và ghi nhanh khi lịch học dày.* Quote tổng hợp để minh họa, không phải trích dẫn phỏng vấn: “Giữa hai ca học, mình muốn xem nhanh slot hôm nay và việc đến hạn mà không phải tìm qua nhiều nơi.”

| Trường cốt lõi | Hồ sơ |
|---|---|
| **01. Identity & Archetype** | Nguyễn Minh Đức, 20 tuổi; sinh viên năm 3 SE, Kỳ 5; cần kết nối lịch môn, deadline và ghi chú trên điện thoại. |
| **02. Persona Priority** | **Primary.** 8 màn hình Final UI và 3 prototype flow phục vụ tra cứu môn, task/note, đồng bộ Vault và hỏi AI. |
| **03. Usage Context** | Project mô tả tra cứu giữa ca học/di chuyển trên Android 360–412 dp; thời gian chú ý ngắn, mạng có thể chập chờn. Đây là bối cảnh thiết kế cần xác thực, không coi thời lượng/tần suất là nghiên cứu đã chứng minh. |
| **04. Goals** | 1) Tra cứu nhanh slot/đề cương đã lưu. 2) Nhìn thấy deadline tập trung và sửa được thao tác nhầm. 3) Ghi/tìm note Markdown, hỏi AI có nguồn khi cần. |
| **05. Job to Be Done** | Khi đang đổi phòng hoặc di chuyển, tôi muốn tìm bài học và việc đến hạn từ một nơi trên điện thoại, kể cả khi mạng yếu, để chuẩn bị đúng việc và không mất ghi chú. |
| **06. Current Behaviors** | Workflow được mô hình hóa trong project: đọc đề cương FLM đã sync, quản lý note Markdown trong Obsidian Vault và theo dõi deadline LMS. Tần suất, thao tác thật và workaround cá nhân chưa có nguồn nghiên cứu gắn mã; cần kiểm chứng. |
| **07. Pain Points** | 1) Tìm slot/đề cương qua nhiều nơi trên màn hình nhỏ gây mất thời gian. 2) Deadline trong nhiều ghi chú có thể bị bỏ sót. 3) Mất mạng làm gián đoạn AI/đồng bộ và gây lo mất nội dung. Đây là giả thuyết sản phẩm cần nghiên cứu/usability test. |
| **08. Motivations** | Tra cứu nhanh; kiểm soát ghi chú cá nhân; nhận biết rõ trạng thái offline/đồng bộ; phục hồi được khi chạm nhầm. |
| **09. Constraints** | App mobile đọc/ghi Vault cục bộ; đề cương được sync sẵn, không tự cào FLM. AI cần Internet/API. Thiết kế hướng thao tác một tay, tiếng Việt rõ trên Android. Baseline accessibility: tương phản AA, chữ ≥14 sp, target ≥48 dp. Quyền truy cập dữ liệu phải minh bạch. |
| **10. Key Scenarios** | **Tra cứu:** giữa buổi học, mở Home xem task đến hạn rồi mở roadmap/course detail đã tải. **Ghi và phục hồi:** tạo checklist, lưu Vault; nếu sync lỗi thì xem nguyên nhân, thử lại và giữ nội dung. Scenarios dựa trên các flow hiện tại, cần test với người dùng. |
| **11. Success Criteria** | Mục tiêu test (chưa phải kết quả): **M1** mở SCR-03 trong ≤8 giây/≤3 chạm; **M2** lưu note ở SCR-05 trong ≤15 giây; **M3** 5/5 người thử hoàn tác/xử lý lỗi sync đúng; **M4** 5/5 hiểu lỗi AI và thử lại không mất câu hỏi. Báo kết quả sau khi thực sự test. |
| **12. Evidence & Status** | Proto-Persona tổng hợp từ scope/Figma/tài liệu project, chưa validated. Chỉ gắn mã OBS/peer khi có ghi chú ẩn danh, ngày và nguồn. Tần suất 5–8 lần/ngày, 42 note, session timeout, bus và workaround cần xác minh trước khi coi là finding. |

## Lab 2 · Tuổi, vai trò, thiết bị và accessibility

- **Tuổi/vai trò:** 20 tuổi, sinh viên năm 3 SE, Kỳ 5 (hồ sơ project).
- **Thói quen thiết bị:** Sản phẩm nhắm Android mobile-first; laptop được dự kiến cho soạn thảo sâu/sync file. Tần suất 5–8 lần/ngày không phải finding nếu thiếu nhật ký/quan sát.
- **Accessibility:** Chưa ghi nhận nhu cầu cá nhân. Baseline: Light theme; Inter/tiếng Việt rõ, body ≥14 sp; tương phản ≥4.5:1 văn bản thường/≥3:1 chữ lớn và điều khiển; target ≥48×48 dp; trạng thái có icon + nhãn + màu; Auto Layout tại 360/412 dp. Xác minh bằng audit và usability test.

## Need → UI → kiểm chứng

| Need | UI/giả thuyết hiện có | Kiểm chứng |
|---|---|---|
| Tra cứu slot offline | SCR-01 → SCR-02 → SCR-03, nhãn tải về/offline | M1: thời gian và số chạm |
| Không bỏ sót việc, cứu thao tác nhầm | SCR-04, nhóm deadline, SN-01 Undo | Nhận diện task và hoàn tác |
| Ghi note, phục hồi sync | SCR-05 → SCR-06; SCR-08 → D-01 → error/retry | M2/M3: lưu, xử lý lỗi, giữ nội dung |
| Hỏi AI có căn cứ | SCR-07, giữ câu hỏi khi mất mạng, nguồn trích dẫn | M4: hiểu trạng thái và phục hồi |

**Liên quan:** [Mục lục/coverage/research backlog](../persona.md).
