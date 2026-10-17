# P01 · Lê Hoàng Nam — Sinh viên năm nhất

**Trạng thái:** Proto-Persona · **Vai trò:** Secondary Persona · **Nguồn:** mô tả do giảng viên cung cấp; chưa có phỏng vấn/quan sát.

**Tóm tắt:** Nam, 18 tuổi, sinh viên năm nhất ngành Quản trị Kinh doanh (BBA), Kỳ 1; vừa qua định hướng/tiếng Anh dự bị và đang làm quen cách học tại FPTU. Archetype: *Sinh viên mới cần hiểu yêu cầu môn và biến lịch học thành kế hoạch tự học.* Quote minh họa, không phải trích dẫn nghiên cứu: “Em có nhiều môn mới nhưng chưa rõ xem đề cương ở đâu và nên chia thời gian tự học thế nào.”

| Trường cốt lõi | Hồ sơ |
|---|---|
| **01. Identity & Archetype** | Lê Hoàng Nam, 18 tuổi; sinh viên năm nhất BBA, Kỳ 1; người mới làm quen cách học tại FPTU. |
| **02. Persona Priority** | **Secondary.** Đại diện nhóm sinh viên mới cần định hướng học vụ. P01 giúp xác định hướng onboarding/lập kế hoạch; 8 màn hình và 3 prototype flow hiện tại vẫn ưu tiên P02, chưa triển khai các tính năng riêng của Nam. |
| **03. Usage Context** | Đầu Kỳ 1, sau định hướng/tiếng Anh dự bị; cần tìm đề cương FLM, hiểu lịch theo slot, điểm danh và PE/FE. Thiết bị, địa điểm, tần suất và mức độ gián đoạn chưa được cung cấp, cần nghiên cứu. |
| **04. Goals** | 1) Tìm đúng đề cương và hiểu trọng số/điều kiện qua môn. 2) Biết việc cần chuẩn bị theo từng môn. 3) Lập lịch tự học khả thi cho khoảng 5–6 môn đại cương. |
| **05. Job to Be Done** | Khi bắt đầu kỳ học và chưa quen quy trình FPTU, tôi muốn hiểu yêu cầu của từng môn và nhìn thấy thời gian có thể tự học, để biết cần làm gì và sắp xếp việc học. |
| **06. Current Behaviors** | Đã biết từ brief: vừa trải qua định hướng/tiếng Anh dự bị và chưa hình thành thói quen tự xếp lịch. Công cụ đang dùng, cách tra FLM và workaround chưa có dữ liệu; không suy đoán thành hành vi quan sát. |
| **07. Pain Points** | 1) Không biết bắt đầu tìm đề cương FLM ở đâu. 2) Khó hiểu trọng số và điều kiện đạt môn. 3) Chưa biết phân bổ thời gian cho nhiều môn. Tần suất và hậu quả cụ thể cần phỏng vấn xác nhận. |
| **08. Motivations** | Mong muốn bắt nhịp kỳ học, tránh bỏ sót yêu cầu môn và dần tự chủ việc học. Đây là suy luận từ mô tả giảng viên, cần xác thực. |
| **09. Constraints** | Kiến thức về quy trình học vụ còn mới. Tư vấn điểm danh/điều kiện qua môn cần nguồn chính thức và ngày hiệu lực. Dữ liệu FAP/FLM chỉ dùng khi được cung cấp hoặc cấp quyền. Thiết bị, năng lực số và accessibility cá nhân chưa biết. |
| **10. Key Scenarios** | **Đầu kỳ:** chọn môn, tìm đề cương và phần đánh giá để xác định trọng số/điều kiện qua môn. **Đầu tuần:** xem thời khóa biểu đã xác nhận, tìm khoảng trống và lập lịch ôn. Scenario đề xuất từ brief, chưa được quan sát. |
| **11. Success Criteria** | Mục tiêu test đề xuất: Nam tìm đúng đề cương và chỉ ra điều kiện qua môn từ nguồn dẫn chứng; tạo lịch tự học dựa trên thời khóa biểu thật. Ghi nhận hoàn thành/sai, thời gian và mức tự tin; đặt ngưỡng sau usability test. |
| **12. Evidence & Status** | Proto-Persona từ mô tả giảng viên; chưa có interview/observation ID. Giả định về công cụ, thiết bị, lịch thật và hiểu biết quy chế cần kiểm chứng; xem [research backlog](../persona.md#research-backlog). |

## Lab 2 · Tuổi, vai trò, thiết bị và accessibility

- **Tuổi/vai trò:** 18 tuổi, năm nhất BBA, Kỳ 1 (brief giảng viên).
- **Thói quen thiết bị:** Chưa có dữ liệu thiết bị, OS, tần suất hay cách thao tác; hỏi trong phỏng vấn. Android 360–412 dp là phạm vi sản phẩm, không phải thói quen đã xác nhận của Nam.
- **Accessibility:** Chưa có nhu cầu cá nhân được báo cáo. Baseline mobile của dự án: chữ tiếng Việt dễ đọc, tương phản WCAG 2.1 AA, vùng chạm ≥48 dp, trạng thái có nhãn/icon thay vì chỉ màu, co giãn 360–412 dp. Xác minh bằng audit UI và hỏi người tham gia.

## Need → giả thuyết UI → kiểm chứng

- **Hiểu đề cương/quy chế:** lối vào môn học có nhãn rõ; phần đánh giá giải thích thuật ngữ và dẫn nguồn chính thức. Task test tìm điều kiện qua môn; ghi độ chính xác, thời gian, khả năng giải thích lại.
- **Lên lịch tự học:** tổng quan tuần làm rõ slot bận và thời gian trống; người dùng sửa/xác nhận lịch gợi ý. Test với thời khóa biểu mẫu đã xác nhận; ghi xung đột và số lần cần trợ giúp.

**Phạm vi:** onboarding, lịch FAP và tư vấn điểm là đề xuất nghiên cứu, chưa phải chức năng có trong Figma/prototype hiện tại.
