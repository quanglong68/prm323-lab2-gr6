\# UX RESEARCH: PERSONA \& PROBLEM STATEMENT



\## 1. Thông tin Chủ đề Ứng dụng

\- \*\*Tên dự án:\*\* FPTU Second Brain Mobile (Study \& Deadline Planner)

\- \*\*Lĩnh vực:\*\* Giáo dục \& Quản lý học tập cá nhân (Study Planner)

\- \*\*Mô tả cụ thể:\*\* Ứng dụng di động hỗ trợ lập kế hoạch học tập, tự động đồng bộ đề cương FLM, theo dõi lịch slot và cảnh báo deadline khẩn cấp cho sinh viên ngành Kỹ thuật Phần mềm (Software Engineering) tại Đại học FPT.



\---



\## 2. Chân dung Người dùng Mục tiêu (Primary Persona)



\### Thông tin cơ bản

\- \*\*Họ và tên:\*\* Nguyễn Minh Đức

\- \*\*Độ tuổi:\*\* 20 tuổi (Sinh viên năm 2 - Học kỳ 4)

\- \*\*Chuyên ngành:\*\* Kỹ thuật Phần mềm (Software Engineering), Đại học FPT TP.HCM

\- \*\*Vai trò:\*\* Sinh viên chính quy đang theo học 5 môn chuyên ngành nặng (Java Backend, Mobile Cross-platform, Database...) cùng đồ án môn học.



\### Bối cảnh hằng ngày

\- Mỗi tuần học từ 15 đến 20 slot trên trường, lịch học thay đổi theo từng ngày.

\- Thường xuyên phải di chuyển giữa các phòng lab và giảng đường; chỉ mở laptop khi ngồi vào bàn code, còn trên đường đi hoặc nghỉ giữa giờ chủ yếu thao tác trên điện thoại thông minh.

\- Phải theo dõi bài tập và thông báo trên nhiều nền tảng cùng lúc: Cổng FLM (thông tin về ngành học, tài liệu các môn học), Coursera (bài tập tuần, quiz), Google Classroom và các nhóm chat dự án.



\### Mục tiêu (Goals)

\- Không bao giờ bị trễ các bài nộp đồ án hoặc bài tập slot (tránh bị cấm thi PE/FE).

\- Nắm rõ tiến độ từng môn học: Biết môn hiện tại có tổng bao nhiêu slot, cấu trúc điểm thi gồm những bài nào (Progress Test, Practical Exam, Final Exam) mà không cần đăng nhập lại cổng FLM phức tạp.

\- Ghi chú nhanh các yêu cầu bài tập của giảng viên ngay trên lớp bằng điện thoại và đồng bộ về kho ghi chú cá nhân.



\### Nỗi đau \& Rào cản (Pain Points)

\- \*\*Quá tải thông tin:\*\* Đề cương môn học trên FLM hiển thị bảng biểu phức tạp, không tối ưu cho màn hình điện thoại di động, mỗi lần tra cứu phải đăng nhập lại từ đầu.

\- \*\*Bỏ quên deadline:\*\* Thường xuyên quên các deadline nhỏ lẻ (quiz, lab) do không có màn hình cảnh báo tập trung, chỉ nhớ ra khi hạn chót còn dưới 24 giờ.

\- \*\*Phân mảnh ghi chú:\*\* Ghi chú bài học rải rác trên nhiều app khác nhau (ghi chú điện thoại, giấy nháp), khi cần ôn thi thì không tìm lại được tài liệu liên quan đến từng slot học.



\### Thói quen sử dụng thiết bị

\- \*\*Thiết bị chính:\*\* Smartphone Android tầm trung (màn hình 6.5 inch, tần số quét 90Hz, độ phân giải Full HD+).

\- \*\*Thời gian sử dụng:\*\* Sử dụng điện thoại liên tục trong ngày; phần lớn thao tác app bằng 1 tay khi đang đi bộ hoặc ngồi xe bus.

\- \*\*Môi trường sử dụng:\*\* Thường dùng trong điều kiện ánh sáng yếu (phòng trọ ban đêm, phòng lab tối).



\### Nhu cầu Trợ năng (Accessibility Needs)

\- \*\*Giao diện nền tối (Dark Mode):\*\* Ưu tiên độ tương phản cao để giảm mỏi mắt khi học tập và tra cứu ban đêm.

\- \*\*Vùng chạm lớn (Touch Targets):\*\* Các nút bấm hành động nhanh (thêm task, tick hoàn thành) phải đủ lớn ($\\ge 48\\times48$ dp) để bấm chính xác bằng ngón tay cái khi đang di chuyển.

\- \*\*Cảnh báo thị giác rõ ràng:\*\* Không chỉ dùng màu sắc đơn thuần để báo deadline gấp, mà cần có văn bản trạng thái rõ ràng (nhãn "Quá hạn", "Còn 1 ngày") để tránh nhầm lẫn.



\---



\## 3. Phát biểu Vấn đề (Problem Statement)

Sinh viên ngành Kỹ thuật Phần mềm FPTU thường xuyên bị trễ hạn nộp bài và mất phương hướng ôn thi do thông tin cấu trúc điểm, số slot môn học và danh sách deadline bị phân mảnh trên nhiều hệ thống phức tạp, thiếu một công cụ di động trực quan giúp tra cứu tức thì và cảnh báo nhiệm vụ khẩn cấp.



\---



\## 4. Tiêu chí Thành công Đo được (Measurable Success Metrics)

1\. \*\*Thời gian tra cứu thông tin môn:\*\* Sinh viên có thể mở app và xem được chi tiết đầu điểm (PE, FE) cùng tổng số slot của một môn học bất kỳ trong \*\*dưới 10 giây\*\*.

2\. \*\*Thời gian tạo task mới:\*\* Sinh viên có thể tạo thành công một ghi chú deadline mới trực tiếp từ màn hình chính trong \*\*dưới 15 giây\*\* (thỏa mãn tiêu chí đề bài yêu cầu $< 20$ giây).

3\. \*\*Tỷ lệ phục hồi thao tác:\*\* 100% các thao tác lỡ tay đánh dấu hoàn thành nhiệm vụ có thể được hoàn tác (Undo) ngay lập tức bằng một chạm.

