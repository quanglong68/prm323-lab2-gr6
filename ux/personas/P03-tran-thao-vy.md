# P03 · Trần Thảo Vy — Sinh viên năm cuối

**Trạng thái:** Proto-Persona · **Vai trò:** Secondary Persona · **Nguồn:** mô tả do giảng viên cung cấp; chưa có phỏng vấn/quan sát.

**Tóm tắt:** Trần Thảo Vy, 22 tuổi, sinh viên năm cuối ngành Ngôn ngữ Anh, Kỳ 8–9; chuẩn bị Capstone và xét điều kiện tốt nghiệp. Archetype: *Sinh viên cuối khóa cần rà soát prerequisite và chọn phương án học tập có căn cứ.* Quote minh họa, không phải trích dẫn nghiên cứu: “Trước khi làm Capstone, mình muốn biết còn thiếu điều kiện nào và lựa chọn học cải thiện ảnh hưởng ra sao.”

| Trường cốt lõi | Hồ sơ |
|---|---|
| **01. Identity & Archetype** | Trần Thảo Vy, 22 tuổi; sinh viên năm cuối Ngôn ngữ Anh, Kỳ 8–9; chuẩn bị Capstone và rà điều kiện tốt nghiệp. |
| **02. Persona Priority** | **Secondary.** Đại diện tác vụ cuối hành trình học, khác P02 (tra cứu slot, deadline, Vault) ở việc đối chiếu chương trình/điểm. Tính năng riêng chưa có trong Figma/prototype hiện tại. |
| **03. Usage Context** | Trước đăng ký Capstone/kỳ tiếp theo hoặc xét tốt nghiệp; cần đối chiếu bảng điểm với chương trình đúng ngành/khóa. Thiết bị, địa điểm, tần suất và quy trình hiện tại chưa được cung cấp. |
| **04. Goals** | 1) Biết môn nợ/rớt cần xử lý. 2) Xác nhận prerequisite trước Capstone. 3) So sánh lựa chọn học lại/cải thiện và tác động GPA dự kiến. |
| **05. Job to Be Done** | Khi chuẩn bị Capstone và xét tốt nghiệp, tôi muốn đối chiếu tiến độ học với yêu cầu chương trình và cân nhắc các phương án còn thiếu, để chọn bước tiếp theo mà không bỏ sót điều kiện. |
| **06. Current Behaviors** | Brief cho biết Vy cần nhận diện môn nợ/prerequisite và lựa chọn cải thiện GPA. Nguồn tra cứu, công cụ, workaround và tần suất chưa có dữ liệu; cần phỏng vấn, không suy diễn. |
| **07. Pain Points** | 1) Khó nhớ môn còn nợ/rớt. 2) Không chắc môn tiên quyết phải đạt trước Capstone. 3) Khó ước lượng học cải thiện ảnh hưởng GPA ra sao. Tần suất/hậu quả cần xác nhận. |
| **08. Motivations** | Hoàn tất điều kiện Capstone/tốt nghiệp và đưa quyết định học lại dựa trên thông tin rõ ràng. Ưu tiên giữa tốt nghiệp đúng hạn và GPA cần xác thực. |
| **09. Constraints** | Cần bảng điểm chính xác, chương trình đúng ngành/khóa và quy tắc hiện hành. Điểm là dữ liệu nhạy cảm; cần cấp quyền rõ ràng và chỉ dùng nguồn được xác nhận. Thiết bị, kỹ năng số và accessibility cá nhân chưa biết; không giả định app đã truy cập FAP. |
| **10. Key Scenarios** | **Trước Capstone:** đối chiếu bảng điểm đã xác nhận với khung chương trình để tìm prerequisite còn thiếu. **Trước kỳ mới:** thử các kịch bản học cải thiện với quy tắc GPA công bố. Đây là scenario từ brief, chưa được kiểm chứng. |
| **11. Success Criteria** | Mục tiêu test đề xuất: từ dữ liệu mẫu đã xác minh, Vy tìm đúng prerequisite còn thiếu, mở được nguồn/quy tắc và giải thích giả định của một kịch bản GPA. Đo độ chính xác, thời gian, lỗi và mức hiểu; đặt ngưỡng sau test. |
| **12. Evidence & Status** | Proto-Persona từ mô tả giảng viên; chưa có interview/observation ID, bảng điểm mẫu hay xác minh chương trình. Cần kiểm chứng khóa, công cụ hiện tại, quy tắc GPA/prerequisite và ưu tiên mục tiêu. |

## Lab 2 · Tuổi, vai trò, thiết bị và accessibility

- **Tuổi/vai trò:** 22 tuổi, sinh viên năm cuối Ngôn ngữ Anh, Kỳ 8–9 (ngành đã được xác nhận).
- **Thói quen thiết bị:** Chưa có dữ liệu; hỏi về thiết bị dùng tra điểm/đăng ký môn, tần suất và mạng. Không gán mặc định thói quen Android của sản phẩm cho Vy.
- **Accessibility:** Nhu cầu cá nhân chưa biết. Nếu mở rộng lên mobile, áp dụng baseline dự án: chữ Việt rõ, tương phản AA, target ≥48 dp, nhãn/icon kèm màu, layout 360–412 dp. Hiển thị nguồn/giả định; bảo vệ dữ liệu điểm. Xác minh bằng audit và test có đồng thuận.

## Need → giả thuyết UI → kiểm chứng

- **Tìm điều kiện còn thiếu:** giả thuyết bảng tiến độ đánh dấu prerequisite, nêu mã môn/nguồn/phiên bản và không chỉ dựa vào màu. Test nhiệm vụ tìm môn thiếu bằng dữ liệu đã xác nhận.
- **Đánh giá lựa chọn cải thiện:** giả thuyết mô phỏng cho phép so sánh kịch bản, thấy đầu vào/quy tắc và chỉnh giả định. Test người dùng diễn giải kết quả, đối chiếu với phép tính chuẩn đã xác minh.

**Phạm vi:** prerequisite checker và GPA simulator là đề xuất tương lai; Figma hiện tại chưa tích hợp bảng điểm hay các chức năng đó.
