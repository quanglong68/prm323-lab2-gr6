# AI DESIGN LOG: QUÁ TRÌNH TẠO VÀ TINH CHỈNH UI VỚI AI

Tài liệu này ghi lại toàn bộ quá trình làm việc với công cụ tạo giao diện bằng AI (Google Stitch) và trợ lý AI phản biện theo đúng quy trình bắt buộc tại Mục 4 và Mục 5 của đề bài Lab 2.

- **Dự án:** FPTU Second Brain Mobile (Ứng dụng đồng hành cho sinh viên SE Đại học FPT)
- **Persona:** Nguyễn Minh Đức (20 tuổi, SV SE, thao tác một tay trên xe bus, mạng chập chờn)
- **Công cụ AI sử dụng:**
  - **Google Stitch:** Tạo UI ban đầu và thực hiện các vòng lặp tinh chỉnh giao diện.
  - **Trợ lý AI phản biện độc lập:** Đánh giá UX theo 10 Usability Heuristics (Nielsen), tiêu chuẩn Accessibility (WCAG 2.1 AA) và Persona.

---

## 1. Thiết lập Ngữ cảnh & Khởi tạo Design System trong Google Stitch

Dự án sử dụng tính năng nạp trực tiếp tài liệu quy chuẩn **`design/DESIGN.md`** vào Stitch để trích xuất và cố định hệ thống Design System ngay từ đầu.

### 1.1. Phương thức Thiết lập
1. **Nạp Design Spec:** Chọn `Start with your design` trong Stitch và nạp toàn bộ nội dung từ file `design/DESIGN.md`.
2. **Trích xuất Design System:** Stitch tự động phân tích và tạo bộ quy chuẩn `FPTU Second Brain Mobile Design System` gồm:
   - **Bảng màu:** Cố định `Primary Blue` (`#1D4ED8`), `Secondary Teal` (`#0F766E`), nền sáng `Surface` (`#F8FAFC`).
   - **Typography:** Khóa font chữ `Inter` hỗ trợ đầy đủ tiếng Việt có dấu.
   - **Component Styles:** Nút bấm bo tròn `radius-full`, Card bo góc `radius-md`, thanh tìm kiếm và App Bar theo chuẩn Material Design 3.

### 1.2. Bằng chứng Trích xuất Design System từ Stitch
![FPTU Second Brain Mobile Design System](../assets/stitch/stitch-design-system.png)

*(Ảnh chụp màn hình bảng Design System do Google Stitch tự động trích xuất thành công từ file `design/DESIGN.md`)*

---

## 2. Tạo UI Ban Đầu (Initial UI Generation) - Toàn bộ 8 Màn hình

### 2.1. Prompt Nguyên văn gửi Google Stitch
Prompt tạo đồng thời 8 màn hình hệ thống bao phủ trọn vẹn Kiến trúc thông tin và 3 User Flows:

```text
Thiết kế toàn bộ hệ thống 8 màn hình cho ứng dụng di động Android mang tên "FPTU Second Brain Mobile" dành cho sinh viên ngành Kỹ thuật Phần mềm.

Quy tắc thiết kế cốt lõi (Material Design 3):
- Khung màn hình: 360 x 800 dp.
- Giao diện: Toàn bộ sử dụng Giao diện SÁNG (Light Theme), nền chính #F8FAFC, bề mặt Card #FFFFFF, xanh dương chủ đạo #1D4ED8, xanh Teal phụ #0F766E, nền cảnh báo #FEF3C7, nền lỗi #FEE2E2. Tuyệt đối không dùng Dark mode, không dùng phong cách Cyberpunk neon.
- Typography: Phông chữ Inter, toàn bộ chữ nội dung bắt buộc >= 14 sp. Chiều cao dòng thoáng để hiển thị rõ dấu tiếng Việt.
- Công thái học cảm ứng: Các vùng tương tác (nút bấm, checkbox, chip lọc, icon tab) phải đạt diện tích chạm tối thiểu 48 x 48 dp.
- Thanh điều hướng đáy (Bottom Navigation Bar 80 dp) cố định trên 4 màn hình chính cấp cao nhất: Trang chủ, Lộ trình, Việc làm, Ghi chú.

DANH SÁCH 8 MÀN HÌNH CHI TIẾT:

1. SCR-01: Trang chủ (Dashboard)
- Top App Bar (56 dp): Tiêu đề "Kỹ thuật Phần mềm", icon Cài đặt ở góc phải (48x48 dp) dẫn đến SCR-08.
- Phần 1 (Carousel hạn chót khẩn cấp): Danh sách cuộn ngang tối đa 3 thẻ cho các việc có hạn <= 3 ngày. Mỗi thẻ hiển thị: mã môn "PRM323", tên việc "Figma Prototype Lab 2", huy hiệu gồm icon đồng hồ + chữ "Hôm nay" (nền vàng #FEF3C7, chữ #92400E). Nút chữ "Xem tất cả" căn phải.
- Phần 2 (Thẻ môn gần đây): Thẻ hiển thị "PRM323 - Lập trình Di động Đa nền tảng", tiến độ "Slot 12/30", nút "Xem đề cương".
- Phần 3 (Banner trợ lý AI): Nền xanh nhạt #DBEAFE, chữ "Hỏi trợ lý AI về môn học", icon auto_awesome, nút chính "Đặt câu hỏi".
- Phần 4: Thanh tiến độ đồng bộ Vault 65%.
- Bottom Navigation Bar (80 dp): Tab "Trang chủ" đang chọn. FAB tròn (56x56 dp) ở góc phải đáy với icon cây bút ghi chú.

2. SCR-02: Lộ trình môn học (Timeline / Semester Courses)
- Top App Bar: Tiêu đề "Lộ trình học tập", chip chọn kỳ "Học kỳ Fall 2024 (Kỳ 5)" [Đang chọn].
- Thống kê tóm tắt: Thẻ thông tin "4 môn học • 11 tín chỉ • 100% đã tải đề cương offline".
- Danh sách môn học dạng thẻ dọc:
  * Môn 1: "PRM323 - Lập trình Di động Đa nền tảng" (3 tín chỉ), tiến độ Slot 12/30, huy hiệu "Đã tải về" (xanh lá #DCFCE7).
  * Môn 2: "SWP391 - Dự án Phát triển Phần mềm" (5 tín chỉ), tiến độ Sprint 2/4.
  * Môn 3: "ITE302c - Đạo đức Nghề nghiệp CNTT" (3 tín chỉ), tiến độ Slot 6/20.
- Bottom Navigation Bar: Tab "Lộ trình" đang chọn.

3. SCR-03: Chi tiết môn học (Course Details / FLM Syllabus)
- Top App Bar: Nút Back mũi tên trái (48x48 dp), tiêu đề "PRM323", icon góc phải auto_awesome "Hỏi AI môn này".
- Thẻ đầu trang: Tên môn "Lập trình Di động Đa nền tảng", 3 tín chỉ, huy hiệu "Đã tải về".
- Banner ngoại tuyến: Nền vàng nhạt #FEF3C7: "Đang ngoại tuyến • Dữ liệu đề cương lưu cục bộ".
- Thanh 3 Tab: "Lịch slot" [Đang chọn], "Đánh giá", "Tổng quan".
- Danh sách Slot:
  * Slot 11: "Kiến trúc State Management" (Đã xong, icon check xanh).
  * Slot 12: "Thiết kế UI Material 3 & Figma" (Hôm nay, chữ đậm).
  * Slot 13: "Lab 2: Usability & Handoff" (Sắp tới).
- Thanh đáy cố định: Nút chính "Xem ghi chú môn PRM323" (dẫn đến SCR-06).

4. SCR-04: Việc cần làm (Tasks & Deadlines)
- Top App Bar: Tiêu đề "Việc cần làm", hàng chip lọc: "Hôm nay" [Đang chọn], "Sắp tới", "Đã hoàn thành".
- Danh sách việc:
  * Việc 1 (Quá hạn): Checkbox bên trái (48x48 dp, cách chữ 8 dp). Tên "Nộp báo cáo Lab 1", môn "SWP391", huy hiệu icon lỗi + chữ "Quá hạn" (nền đỏ #FEE2E2, chữ #991B1B).
  * Việc 2 (Hôm nay): Checkbox 48x48 dp. Tên "Hoàn thiện Figma Prototype Lab 2", môn "PRM323", huy hiệu "Hôm nay" (nền vàng #FEF3C7, chữ #92400E).
- Thanh thông báo nổi (Snackbar SN-01) neo phía trên Bottom Nav: Nền tối #1E293B, chữ "Đã hoàn thành task", nút chữ màu xanh "HOÀN TÁC" (48x48 dp).
- Bottom Navigation Bar: Tab "Việc làm" đang chọn.

5. SCR-05: Soạn thảo ghi chú nhanh (Quick Note / Markdown Editor)
- Top App Bar: Nút Đóng 'X' góc trái (48x48 dp), tiêu đề "Ghi chú mới", nút góc phải "Lưu" (Primary Blue).
- Trạng thái lưu: Dòng chữ nhỏ "Đã tự động lưu vào Vault cục bộ • 1 phút trước".
- Vùng soạn thảo: Ô nhập tiêu đề "Tiêu chuẩn chấm điểm Lab 2 PRM323", ô soạn thảo nội dung Markdown bên dưới.
- Thanh công cụ định dạng neo trên bàn phím: Các icon nút bấm (48x48 dp) gồm Đậm (B), Nghiêng (I), Tiêu đề (H), Checkbox [ ], Chèn liên kết, Chèn ảnh.

6. SCR-06: Danh sách ghi chú Vault (Vault Notes Explorer)
- Top App Bar: Tiêu đề "Ghi chú của tôi", ô tìm kiếm nhanh "Tìm trong Obsidian Vault...".
- Hàng thư mục môn học (Chips cuộn ngang): "Tất cả" [Đang chọn], "PRM323", "SWP391", "ITE302c".
- Danh sách ghi chú:
  * Note 1: "PRM323 - Tổng hợp Flutter & M3.md", sửa lúc "Hôm nay 09:30", đoạn trích 2 dòng.
  * Note 2: "SWP391 - Biên bản họp Sprint 2.md", sửa lúc "Hôm qua".
- Bottom Navigation Bar: Tab "Ghi chú" đang chọn. FAB góc phải với icon dấu cộng (+) để tạo ghi chú mới.

7. SCR-07: Trợ lý AI môn học (AI Tutor Chat)
- Top App Bar: Nút Back mũi tên trái (48x48 dp), tiêu đề "Trợ lý AI", chip phụ "Ngữ cảnh: PRM323".
- Khung hội thoại:
  * Tin nhắn sinh viên (bên phải, nền xanh #1D4ED8, chữ trắng): "Cho mình hỏi Lab 2 PRM323 cần nộp những gì?".
  * Tin nhắn AI (bên trái, nền trắng #FFFFFF, viền xám nhạt, chữ tối): Trả lời gạch đầu dòng Markdown.
  * Thẻ trích dẫn nguồn (Citation Chip) dưới tin nhắn AI: Nền Teal nhạt #CCFBF1, icon tài liệu + chữ "Nguồn: PRM323_Syllabus.md", chạm được (48x48 dp).
- Thanh nhập liệu đáy: Ô nhập "Hỏi về môn học hoặc ghi chú...", nút tròn gửi icon Send màu xanh #1D4ED8.

8. SCR-08: Cài đặt & Đồng bộ Vault (Settings & Sync)
- Top App Bar: Nút Back mũi tên trái (48x48 dp), tiêu đề "Cài đặt & Đồng bộ".
- Phần 1 (Đồng bộ Obsidian Vault): Đường dẫn thư mục "/storage/emulated/0/Documents/ObsidianVault", nút "Chọn thư mục khác", Switch bật tắt "Tự động đồng bộ một chiều khi có mạng".
- Phần 2 (Bộ nhớ): "Đã lưu trữ 42 ghi chú, 4 đề cương môn học (Tổng: 18.4 MB)", nút "Xóa cache tạm".
- Phần 3 (Thông tin): Phiên bản app "v1.0.0-offline", liên kết "Về tác giả & Báo lỗi".
```

### 2.2. Kết quả từ Google Stitch (Ảnh chụp bằng chứng)
- Ảnh tổng quan toàn bộ 8 màn hình ban đầu do Google Stitch tạo ra:
  ![Overview 8 Screens Initial UI](../assets/stitch/initial-all-screens.png)
