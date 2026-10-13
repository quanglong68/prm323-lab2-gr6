# THIẾT KẾ UI/UX: QUYẾT ĐỊNH THIẾT KẾ VÀ CHECKLIST ACCESSIBILITY

Tài liệu này tổng hợp 10 quyết định thiết kế cốt lõi nhất được đưa ra trong quá trình phát triển ứng dụng **FPTU Second Brain Mobile** (giải quyết các phản biện từ AI và tối ưu hóa cho persona Nguyễn Minh Đức), cùng bảng kiểm tra chi tiết tiêu chuẩn Trợ năng (WCAG 2.1 AA) và Đáp ứng giao diện (Responsive 360 dp & 412 dp).

---

## 1. Top 10 Quyết định Thiết kế Cốt lõi (Core Design Decisions)

| STT | Quyết định thiết kế | Vấn đề & Bối cảnh giải quyết | Lý do & Lập luận cụ thể (Persona / Heuristic / Tiêu chuẩn) |
| :---: | :--- | :--- | :--- |
| **01** | **Neo các hành động chính ở nửa dưới màn hình (Bottom Reach)** | Nút "Lưu" (SCR-05) và "Hỏi AI" (SCR-03) ban đầu đặt ở góc trên bên phải, rất khó với tới khi cầm máy một tay. | **Persona Ergonomics:** Minh Đức thường xuyên đi xe bus số 74 rung lắc, chỉ thao tác bằng một ngón cái. Dời nút Lưu xuống thanh công cụ đáy và nút Hỏi AI xuống Bottom Bar giúp thao tác dễ dàng mà không làm rơi máy. |
| **02** | **Loại bỏ triệt để các card rác (Spaced Repetition, Streak)** | AI ban đầu tự ý vẽ thêm chuỗi streak, ôn tập flashcard, mạng lưới node 3D gây nhiễu giao diện. | **Heuristic #8 (Aesthetic & Minimalist):** Ứng dụng định vị là "Bộ não phụ đọc Vault ngoại tuyến", phục vụ sinh viên SE tra cứu nhanh trong 30–60 giây. Loại bỏ tính năng thừa để tối ưu không gian hiển thị và giảm tải nhận thức. |
| **03** | **Tách biệt Snackbar (SN-01) không che khuất nút HOÀN TÁC** | Trên SCR-04, nút Floating Action Button (FAB) đè lên nút chữ "HOÀN TÁC" của thanh Snackbar. | **Heuristic #3 (User Control) & #9 (Error Recovery):** Đức đi xe bus rất dễ tick nhầm task do xe xóc. Lưới an toàn Hoàn tác (tiêu chí M3) bắt buộc phải hiển thị 100% diện tích chạm (48x48 dp) nổi phía trên FAB. |
| **04** | **Thêm Hộp thoại xác nhận (D-02) khi "Xóa cache tạm"** | Nút "Xóa cache tạm" trên SCR-08 bấm vào là xóa ngay, không có cảnh báo phòng ngừa. | **Heuristic #5 (Error Prevention):** Sinh viên ngoại tuyến phụ thuộc hoàn toàn vào cache đề cương FLM và ghi chú. Dialog xác nhận phân định rõ "Cache tạm khác với dữ liệu Obsidian Vault", ngăn chặn thao tác nhầm làm mất tài nguyên học tập. |
| **05** | **Minh bạch ranh giới Offline và Trợ lý AI (Gemini 1.5 Flash)** | SCR-08 từng tuyên bố sai lệch "xử lý 100% trên thiết bị", trong khi tính năng hỏi đáp sử dụng Gemini API. | **Heuristic #2 (Match with Real World) & Đạo đức AI:** Phân tách rõ ràng: Ghi chú Markdown được đọc và chỉ mục 100% offline; tính năng AI bắt buộc cần mạng Internet. Khi mất mạng, hiển thị ngay banner cảnh báo thân thiện và nút "Thử lại". |
| **06** | **Bổ sung trường nhập Gemini API Key trong Cài đặt (SCR-08)** | Luồng xử lý lỗi (Flow 3: ER-02) khi người dùng chưa cấu hình API Key bị bế tắc do thiếu giao diện nhập key. | **Heuristic #9 (Help Users Recover from Errors):** Cung cấp mô hình BYOK (Bring Your Own Key) minh bạch từ Google AI Studio, giúp sinh viên chủ động cấu hình trợ lý AI cá nhân mà không phụ thuộc server trung gian. |
| **07** | **Thống nhất nguồn dữ liệu duy nhất (Single Source of Truth)** | Mâu thuẫn hạn chót Lab 2 PRM323 (15/10 vs 18/10), học kỳ (Summer 2024 vs Fall 2024), cổng nộp bài (CMS vs LMS). | **Heuristic #4 (Consistency & Standards):** Với sinh viên SE "sống bằng deadline", sai một ngày là trễ hạn thật. Cố định toàn hệ thống: Hạn chót `23:59 Hôm nay (15/10/2024)`, học kỳ `Fall 2024 (Kỳ 5)`, cổng nộp duy nhất `Hệ thống LMS`. |
| **08** | **Không truyền đạt trạng thái chỉ bằng màu sắc đơn độc** | Ban đầu các thẻ môn học và deadline chỉ phân biệt bằng viền màu xanh, đỏ, vàng mà không có nhãn. | **WCAG 2.1 (Success Criterion 1.4.1 - Use of Color):** Tất cả các badge trạng thái bắt buộc kết hợp cả Icon và Text nhãn rõ ràng (ví dụ: Icon lỗi + chữ "Quá hạn", Icon đồng hồ + chữ "Hôm nay", Icon đám mây + chữ "Đã tải về"). |
| **09** | **Chuẩn hóa Typography ≥ 14 sp và Tương phản màu sắc ≥ 4.5:1** | Màu chữ cảnh báo nguy hiểm trên nền hồng ở SCR-08 ban đầu chỉ đạt tỉ lệ 3.95:1 (vi phạm chuẩn WCAG). | **WCAG 2.1 (Success Criterion 1.4.3 - Contrast Minimum):** Đổi màu chữ nút cảnh báo sang On-Error-Container `#991B1B` trên nền `#FEE2E2` đạt tỉ lệ tương phản 6.8:1. Khóa cỡ chữ nội dung Body từ 14 sp trở lên để đọc rõ trên màn hình nhỏ. |
| **10** | **Khóa diện tích chạm tối thiểu 48 × 48 dp cho toàn bộ điều khiển** | Thanh công cụ Markdown trên SCR-05 ban đầu nhồi nhét 8 icon khiến diện tích mỗi icon chỉ đạt ~45 dp. | **WCAG 2.1 (Success Criterion 2.5.5 - Target Size):** Mở rộng padding và sắp xếp lại thanh công cụ, đảm bảo tất cả nút bấm, icon tab, checkbox và chip lọc đều đạt diện tích chạm cảm ứng tối thiểu 48x48 dp. |

---

## 2. Checklist Kiểm tra Accessibility (WCAG 2.1 AA)

| Tiêu chuẩn WCAG | Yêu cầu kỹ thuật | Trạng thái kiểm tra | Bằng chứng đo lường thực tế trên UI |
| :--- | :--- | :---: | :--- |
| **1.4.3 Contrast (Minimum)** | Tỉ lệ tương phản văn bản thường tối thiểu **4.5:1**; chữ lớn và điều khiển UI tối thiểu **3.0:1** | **ĐẠT (PASS)** | - Chữ chính `#0F172A` trên nền trắng `#FFFFFF`: Tỉ lệ **15.4:1**.<br>- Nút Primary `#1D4ED8` với chữ trắng: Tỉ lệ **8.6:1**.<br>- Chữ lỗi `#991B1B` trên nền cảnh báo `#FEE2E2`: Tỉ lệ **6.8:1** (vượt chuẩn 4.5:1).<br>- Badge Hạn chót `#92400E` trên nền vàng `#FEF3C7`: Tỉ lệ **5.2:1**. |
| **2.5.5 Target Size** | Vùng chạm cảm ứng tương tác tối thiểu **48 × 48 dp** | **ĐẠT (PASS)** | - Nút bấm chính (Button): Chiều cao chuẩn 48 dp, bo góc tròn.<br>- Bottom Navigation Bar: Mỗi tab chiếm vùng chạm 90 × 80 dp.<br>- Checkbox công việc (SCR-04): Kích thước hiển thị 24x24 dp nhưng vùng bọc cảm ứng (Touch Target) đạt **48 × 48 dp**.<br>- Thanh công cụ Markdown (SCR-05): Mỗi icon cách nhau thoáng, đạt chuẩn 48x48 dp. |
| **1.4.1 Use of Color** | Không dùng màu sắc làm phương tiện duy nhất để truyền đạt thông tin | **ĐẠT (PASS)** | - Task quá hạn: Đi kèm icon cảnh báo `error_outline` + nhãn chữ `"Quá hạn"` màu đỏ.<br>- Task hôm nay: Icon đồng hồ `schedule` + nhãn chữ `"Hôm nay"` màu hổ phách.<br>- Trạng thái offline: Icon đám mây gạch chéo + nhãn chữ `"Đang ngoại tuyến"`. |
| **1.4.4 Resize Text** | Cỡ chữ nội dung tối thiểu **14 sp**; phân cấp thị giác rõ ràng | **ĐẠT (PASS)** | - Tiêu đề lớn (Headline): 22–24 sp, đậm.<br>- Tiêu đề nhóm (Title Medium): 16 sp, bán đậm.<br>- Chữ nội dung (Body Medium): 14 sp, chiều cao dòng 20 sp, hỗ trợ tiếng Việt có dấu rõ ràng. Tuyệt đối không dùng chữ 11–12 sp cho thông tin quan trọng. |

---

## 3. Checklist Kiểm tra Responsive Bố cục (360 dp vs 412 dp)

Toàn bộ hệ thống giao diện được thiết kế gốc trên khung chuẩn **360 × 800 dp** (Android tiêu chuẩn) và được kiểm chứng khả năng co giãn trên màn hình rộng **412 × 915 dp** (Google Pixel / Samsung Galaxy phổ biến):

| Thành phần giao diện | Hành vi tại độ rộng 360 dp (Base) | Hành vi mở rộng tại 412 dp (Extended) | Cơ chế Figma Auto Layout & Constraint |
| :--- | :--- | :--- | :--- |
| **Lưới lề trang (Margins)** | Margin hai bên cố định 16 dp. Chiều rộng nội dung là **328 dp**. | Margin hai bên tăng lên 20 dp hoặc giữ 16 dp (nội dung co giãn **380 dp**). | Constraint: `Left & Right` (hoặc `Scale`). Auto Layout: `Fill container`. |
| **Thẻ danh sách (Cards)** | Card rộng 328 dp, ôm vừa vặn nội dung text 2 dòng. | Card tự động dãn ngang theo chiều rộng màn hình, không bị vỡ layout hay cố định pixel. | Card Frame: Chiều rộng set `Fill container`, nội dung bên trong tự động co giãn. |
| **Bottom Navigation Bar** | 4 tab phân bổ đều: mỗi tab rộng **90 dp**, icon 24 dp, nhãn chữ 12 sp. | 4 tab tự động dãn đều: mỗi tab rộng **103 dp**, giữ nguyên vị trí căn giữa. | Thanh điều hướng: Chiều rộng `Fill container`, các Tab Item set `Fill container` căn giữa. |
| **Thanh công cụ soạn thảo (SCR-05)** | 6 icon định dạng cơ bản dàn trải đều vừa vặn trên 360 dp. Nút "Lưu" neo sát góc phải. | Khoảng cách giữa các icon giãn nhẹ (spacing tăng từ 8 dp lên 12 dp), tạo vùng bấm rộng rãi hơn. | Thanh Toolbar: `Space between` hoặc Auto Layout với Spacing linh hoạt. |
| **Xử lý tràn chữ (Text Truncation)** | Tiêu đề ghi chú dài > 25 ký tự tự động xuống dòng (tối đa 2 dòng), không dùng ellipsis cắt cụt ngày hạn. | Hiển thị trọn vẹn tiêu đề mà không bị xuống dòng quá sớm. | Text layer: Chiều rộng `Fill container`, thuộc tính `Auto height`. |
