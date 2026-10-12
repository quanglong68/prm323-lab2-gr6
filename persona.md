# UX RESEARCH: PERSONA & PROBLEM STATEMENT

## 1. Cơ sở Xây dựng Persona (Background & Observations)
- **Phương pháp tiếp cận:** Dựa trên quá trình tự quan sát thói quen học tập của bản thân tác giả khi theo học các môn chuyên ngành Kỹ thuật Phần mềm (SE) tại Đại học FPT, kết hợp trao đổi nhanh với các bạn cùng lớp về những rào cản khi theo dõi tiến độ môn học trên điện thoại.
- **Giả định kỹ thuật nền tảng (Technical Assumption):** Thư mục ghi chú Markdown (Obsidian Vault) được giả định đã được đồng bộ sẵn giữa máy tính và bộ nhớ điện thoại thông qua dịch vụ đám mây (Google Drive / Git / Obsidian Sync). Ứng dụng di động này đảm nhiệm việc đọc, phân loại, tìm kiếm và tạo nhanh ghi chú trực tiếp từ thư mục đó.

---

## 2. Thông tin Chủ đề Dự án
- **Tên dự án:** FPTU Second Brain Mobile
- **Chủ đề đăng ký:** Study Planner (quản lý bài học theo đề cương, hạn nộp bài và kho tri thức môn học)
- **Mô tả cụ thể:** Ứng dụng di động hỗ trợ sinh viên Kỹ thuật Phần mềm FPTU tra cứu nội dung slot học theo đề cương FLM đã lưu ngoại tuyến, tổng hợp các đầu việc cần làm (được ghi chú theo cú pháp Markdown) và hỗ trợ tra cứu nhanh kiến thức môn học trên thiết bị di động.

---

## 3. Chân dung Người dùng Mục tiêu (Primary Persona)

### Thông tin cơ bản
- **Họ và tên:** Nguyễn Minh Đức (Nhân vật đại diện)
- **Độ tuổi:** 20 tuổi
- **Vai trò:** Sinh viên ngành Kỹ thuật Phần mềm (Software Engineering), Đại học FPT TP.HCM, đang trong giai đoạn theo học các môn chuyên ngành (Java Web, Cross-Platform Mobile, Database...).

### Bối cảnh hằng ngày
- Sử dụng máy tính xách tay để lập trình và ghi chép tài liệu học tập bằng các file Markdown trong thư mục cá nhân.
- Thường xuyên di chuyển giữa các phòng học, phòng lab và đi lại bằng xe bus công cộng.
- Trong lúc di chuyển hoặc nghỉ giữa các tiết học, Đức chủ yếu sử dụng điện thoại thông minh để kiểm tra công việc và thông tin bài học.
- Mạng di động hoặc Wi-Fi trường đôi khi chập chờn hoặc mất kết nối khi di chuyển, gây khó khăn nếu phải truy cập các trang web yêu cầu mạng liên tục.

### Thói quen sử dụng thiết bị (Giả định thiết kế)
- **Thiết bị chính:** Điện thoại Android kích thước màn hình phổ biến (~412 dp chiều rộng viewport).
- **Thao tác:** Phần lớn các thao tác tra cứu nhanh diễn ra khi đang đứng hoặc đi lại, chủ yếu thao tác bằng ngón tay cái của một tay.
- **Tần suất:** Mở app nhanh nhiều lần trong ngày, mỗi lần chỉ kéo dài từ vài chục giây đến một phút để kiểm tra việc cần làm hoặc xem nội dung slot học tiếp theo.

### Mục tiêu của người dùng (Goals)
1. **Nắm cấu trúc và nội dung slot môn học:** Xem nhanh tổng số slot học, nội dung bài học từng slot và danh mục các đầu điểm đánh giá (Assignment, Progress Test, Practical Exam, Final Exam) từ dữ liệu đề cương đã tải về, xem được ngay cả khi không có mạng.
2. **Tổng hợp công việc cần làm:** Có một nơi tập trung hiển thị các hạn nộp bài tập mà bản thân đã chủ động ghi chú (theo quy ước cá nhân `- [ ] Tên việc @due dd/mm/yyyy`) để không bị bỏ quên các bài tập thành phần.
3. **Tra cứu ghi chú bài học:** Dễ dàng tìm lại các đoạn code mẫu, ghi chú bài giảng liên quan đến môn học mà không phải mở từng file Markdown riêng lẻ.
4. **Ghi chép nhanh (Quick Capture):** Tạo nhanh một ghi chú bài học hoặc một đầu việc mới kèm hạn chót ngay trong lớp học chỉ với vài thao tác.

### Nỗi đau & Rào cản (Pain Points)
- **Tra cứu đề cương bất tiện:** Trang web FLM của trường hiển thị bảng biểu phức tạp, không tối ưu cho màn hình điện thoại và thường xuyên hết hạn phiên đăng nhập (session timeout), khiến việc tra cứu slot học rất mất thời gian.
- **Dễ sót hạn nộp bài:** Các bài tập và deadline được ghi rải rác trong nhiều file bài học khác nhau, nếu không mở từng file thì dễ quên mất việc cần nộp trong ngày.
- **Gián đoạn kết nối:** Khi mạng chập chờn hoặc mất mạng, việc tra cứu tài liệu học tập trên các cổng trực tuyến bị ngưng trệ hoàn toàn.
- **Thao tác nhầm lẫn khi di chuyển:** Khi thao tác một tay trên đường đi, người dùng rất dễ bấm nhầm nút đánh dấu hoàn thành nhiệm vụ và làm mất dấu công việc chưa làm.

### Ràng buộc Thiết kế & Trợ năng (Accessibility Constraints)
- **Giao diện sáng (Light Theme chuẩn):** Thiết kế nền sáng làm giao diện chính theo đúng yêu cầu đề bài. Đảm bảo độ tương phản màu (contrast) đạt chuẩn WCAG: tối thiểu 4.5:1 với văn bản thường và 3:1 với chữ lớn và thành phần điều khiển. Chữ nội dung tối thiểu 14 sp. (Dark theme được xếp vào phạm vi mở rộng trong tương lai).
- **Khu vực tương tác thuận tiện ngón cái:** Các hành động cốt lõi (chuyển tab, nút tạo ghi chú nhanh, thao tác hoàn thành task) được bố trí ưu tiên ở nửa dưới màn hình để dễ thao tác một tay.
- **Kích thước vùng chạm:** Tất cả các nút bấm hành động (nút hoàn thành, nút sửa, icon điều hướng) đạt kích thước tối thiểu 48 × 48 dp, bố trí khoảng cách hợp lý để tránh chạm nhầm.
- **Thông tin trực quan đa chiều:** Không biểu đạt trạng thái khẩn cấp chỉ bằng màu sắc đơn thuần; các hạn chót luôn có nhãn chữ đi kèm (ví dụ: "Quá hạn", "Hôm nay", "Còn 2 ngày").
- **Kiểm thử đa kích thước:** Bố cục được thiết kế co giãn linh hoạt và kiểm tra hiển thị trên cả hai độ rộng màn hình 360 dp và 412 dp.

---

## 4. Phát biểu Vấn đề (Problem Statement)
Sinh viên ngành Kỹ thuật Phần mềm FPTU khi học nhiều môn chuyên ngành thường tốn nhiều thời gian tìm kiếm lại đề cương, hạn nộp bài và nội dung ghi chép do thông tin phân tán trên nhiều hệ thống và file cá nhân, trong khi thời gian tra cứu giữa các tiết học rất ngắn, thao tác chủ yếu bằng một tay trên điện thoại và trong điều kiện kết nối mạng không ổn định.

---

## 5. Tiêu chí Thành công Đo được (Measurable Target Metrics)
Các tiêu chí dưới đây được xác định làm mục tiêu đo lường khi thực hiện bài kiểm tra khả năng sử dụng (Usability Testing) trên bản mẫu Figma Prototype với 5 sinh viên:

1. **Tốc độ tra cứu thông tin môn học (Mô phỏng ngoại tuyến):** Từ màn hình chính, người thử nghiệm mở được danh sách đầu điểm đánh giá và nội dung buổi học của một môn bất kỳ trong **≤ 8 giây** và qua **không quá 3 lần chạm**.
2. **Tốc độ tạo deadline mới:** Người thử nghiệm hoàn thành thao tác mở khung ghi chú nhanh, nhập tên bài tập, chọn môn học và hạn nộp trong **≤ 15 giây**.
3. **Khả năng phục hồi thao tác nhầm lẫn:** 5/5 người thử nghiệm thực hiện hoàn tác (Undo) thành công một tác vụ vừa lỡ tay đánh dấu hoàn thành thông qua thanh thông báo (Snackbar) có thời gian hiển thị **8 giây** (thời lượng đủ dài để người thao tác một tay kịp phản xạ).
