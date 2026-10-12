# AI DESIGN LOG: QUÁ TRÌNH TẠO VÀ TINH CHỈNH UI VỚI AI

Tài liệu này ghi lại toàn bộ quá trình làm việc với công cụ tạo giao diện bằng AI (Google Stitch) và trợ lý AI phản biện theo đúng quy trình bắt buộc tại Mục 4 và Mục 5 của đề bài Lab 2.

- **Dự án:** FPTU Second Brain Mobile (Ứng dụng đồng hành cho sinh viên SE Đại học FPT)
- **Persona:** Nguyễn Minh Đức (20 tuổi, SV SE, thao tác một tay trên xe bus, mạng chập chờn)
- **Công cụ AI sử dụng:**
  - **Google Stitch:** Tạo UI ban đầu và thực hiện các vòng lặp tinh chỉnh giao diện[cite: 11, 14].
  - **Gemini:** Trợ lý AI phản biện UX độc lập theo 10 Usability Heuristics (Nielsen), tiêu chuẩn Accessibility (WCAG 2.1 AA) và Persona[cite: 11, 14].

---

## 1. Thiết lập Ngữ cảnh & Khởi tạo Design System trong Google Stitch

Thay vì để Stitch tự do chọn phong cách ngẫu nhiên (dễ bị lệch sang nền tối Cyberpunk của bản desktop), dự án sử dụng tính năng nạp trực tiếp tài liệu quy chuẩn **`design/DESIGN.md`** vào Stitch để trích xuất và cố định hệ thống Design System ngay từ đầu[cite: 16].

### 1.1. Phương thức Thiết lập
1. **Nạp Design Spec:** Chọn `Start with your design` trong Stitch và nhập toàn bộ nội dung từ file `design/DESIGN.md`[cite: 16].
2. **Trích xuất Design System:** Stitch tự động phân tích và tạo bộ quy chuẩn `FPTU Second Brain Mobile Design System` gồm:
   - **Bảng màu:** Cố định `Primary Blue` (`#1D4ED8`), `Secondary Teal` (`#0F766E`), nền sáng `Surface` (`#F8FAFC`).
   - **Typography:** Khóa font chữ `Inter` hỗ trợ đầy đủ tiếng Việt có dấu.
   - **Component Styles:** Nút bấm bo tròn `radius-full`, Card bo góc `radius-md`, thanh tìm kiếm và App Bar theo chuẩn Material Design 3.

### 1.2. Bằng chứng Trích xuất Design System từ Stitch
![FPTU Second Brain Mobile Design System](../assets/stitch/stitch-design-system.png)

*(Ảnh chụp màn hình bảng Design System do Google Stitch tự động trích xuất thành công từ file `design/DESIGN.md`)*

---

## 2. Tạo UI Ban Đầu (Initial UI Generation)

### 2.1. Prompt Nguyên văn gửi Google Stitch
Prompt tạo 2 màn hình bao phủ flow chính (SCR-01 Trang chủ thuộc Flow 1 và SCR-04 Việc cần làm & Snackbar Hoàn tác thuộc Flow 2)[cite: 14, 19]:

```text
Thiết kế giao diện ứng dụng di động Android mang tên "FPTU Second Brain Mobile" dành cho sinh viên ngành Kỹ thuật Phần mềm.

Quy tắc thiết kế cốt lõi (Material Design 3):
- Khung màn hình: 360 x 800 dp.
- Giao diện: Chỉ dùng giao diện SÁNG (Light Theme), nền chính #F8FAFC, bề mặt Card #FFFFFF, xanh dương chủ đạo #1D4ED8, xanh Teal phụ #0F766E, nền cảnh báo #FEF3C7, nền lỗi #FEE2E2. Tuyệt đối không dùng Dark mode, không phong cách Cyberpunk neon.
- Typography: Phông chữ Inter, toàn bộ chữ nội dung bắt buộc >= 14 sp. Chiều cao dòng thoáng để hiển thị rõ dấu tiếng Việt.
- Công thái học cảm ứng: Các vùng tương tác (nút bấm, checkbox, chip, icon tab) phải đạt tối thiểu 48 x 48 dp.

Màn hình 1: SCR-01 Trang chủ
- Top App Bar (56 dp): Tiêu đề "Kỹ thuật Phần mềm", icon Cài đặt ở góc phải (48x48 dp) dẫn đến SCR-08.
- Phần 1 (Carousel hạn chót khẩn cấp): Danh sách cuộn ngang tối đa 3 thẻ cho các việc có hạn <= 3 ngày. Mỗi thẻ hiển thị: mã môn "PRM323", tên việc "Figma Prototype Lab 2", huy hiệu gồm icon đồng hồ + chữ "Hôm nay" (nền vàng #FEF3C7, chữ #92400E). Nút chữ "Xem tất cả" căn phải.
- Phần 2 (Thẻ môn gần đây): Thẻ hiển thị "PRM323 - Lập trình Di động Đa nền tảng", tiến độ "Slot 12/30", nút "Xem đề cương".
- Phần 3 (Banner trợ lý AI): Nền xanh nhạt #DBEAFE, chữ "Hỏi trợ lý AI về môn học", icon auto_awesome, nút chính "Đặt câu hỏi".
- Phần 4: Thanh tiến độ (65% kiến thức đã đồng bộ).
- Thanh điều hướng đáy (80 dp): 4 tab (Trang chủ [Đang chọn], Lộ trình, Việc cần làm, Ghi chú).
- Nút hành động nổi (FAB): 56x56 dp ở góc dưới bên phải với icon cây bút chỉnh sửa.

Màn hình 2: SCR-04 Việc cần làm
- Top App Bar: Tiêu đề "Việc cần làm", hàng chip lọc: "Hôm nay" [Đang chọn], "Sắp tới", "Đã hoàn thành".
- Danh sách việc:
  * Việc 1 (Quá hạn): Checkbox bên trái (vùng chạm 48x48 dp). Ở giữa: tên việc "Nộp báo cáo Lab 1", môn "SWP391", huy hiệu gồm icon lỗi + chữ "Quá hạn" (nền đỏ #FEE2E2, chữ #991B1B).
  * Việc 2 (Hôm nay): Checkbox 48x48 dp. Tên việc "Hoàn thiện Figma Prototype Lab 2", môn "PRM323", huy hiệu "Hôm nay" (nền vàng #FEF3C7, chữ #92400E).
- Thanh thông báo nổi (Snackbar SN-01) neo phía trên thanh điều hướng đáy: Nền tối #1E293B, chữ "Đã hoàn thành task", nút chữ màu xanh "HOÀN TÁC".
- Thanh điều hướng đáy: Tab "Việc cần làm" [Đang chọn].
```

### 2.2. Kết quả từ Google Stitch (Ảnh chụp bằng chứng)
- Giao diện ban đầu SCR-01 Trang chủ:
  ![SCR-01 Initial UI](../assets/stitch/initial-scr01.png)

- Giao diện ban đầu SCR-04 Việc cần làm:
  ![SCR-04 Initial UI](../assets/stitch/initial-scr04.png)

---

## 3. Phản biện UX & Accessibility bằng AI (AI Critique)

### 3.1. Prompt Yêu cầu AI Phản biện
```text
Bạn là chuyên gia thẩm định UX/UI di động. Hãy đánh giá 2 màn hình ban đầu (SCR-01 Trang chủ và SCR-04 Việc cần làm) do Google Stitch vừa tạo ra cho ứng dụng "FPTU Second Brain Mobile".
Tiêu chuẩn đánh giá bắt buộc:
1. 10 Heuristics Usability của Jakob Nielsen.
2. Quy chuẩn Trợ năng (WCAG 2.1 AA): Contrast, Touch target >= 48x48 dp, Chữ nội dung >= 14 sp, Không dùng màu đơn độc.
3. Hồ sơ Persona: Nguyễn Minh Đức (20 tuổi, SV SE FPTU, thao tác một tay trên xe bus, mạng chập chờn, app đọc Obsidian Vault ngoại tuyến).

Yêu cầu: Chỉ ra ít nhất 5 phát hiện lỗi cụ thể gắn trực tiếp với các thành phần trên 2 màn hình này.
```

### 3.2. Bản Phản biện Chi tiết từ AI (5 Phát hiện Cụ thể)

| STT | Màn hình vi phạm | Tiêu chuẩn vi phạm | Phát hiện thực tế trên giao diện Stitch | Mức độ nghiêm trọng |
| :---: | :--- | :--- | :--- | :---: |
| **1** | **SCR-04** (Việc cần làm) | **Heuristic #3:** User Control & Freedom<br>**Heuristic #5:** Error Prevention | **Mất hoàn toàn thanh Snackbar Hoàn tác (SN-01):** Stitch hoàn toàn không vẽ thanh Snackbar nổi có nút "HOÀN TÁC" 8 giây khi tick task như yêu cầu[cite: 16]. Khi Đức di chuyển trên xe bus bị rung lắc, nếu lỡ tay chạm nhầm task, người dùng không thể phục hồi ngay lập tức (vi phạm tiêu chí đo lường M3). | **Nghiêm trọng (Critical)** |
| **2** | **SCR-01 & SCR-04** | **Heuristic #8:** Aesthetic & Minimalist Design<br>**Persona Goal:** G1 & G2 | **Nhiễu thị giác do tự ý thêm tính năng ngoài phạm vi:** Stitch tự ý chèn các card ngoài luồng: *"Chuỗi 14 ngày tập trung"*, *"GPA 3.65"*, *"Sprint Fall 2024"*, *"Flashcards"*, *"Lịch học"*, *"Mẹo nhỏ học tập"*. Chúng chiếm diện tích lớn, đẩy phần quan trọng nhất (Carousel deadline khẩn cấp và đề cương) xuống khuất màn hình. | **Cao (High)** |
| **3** | **SCR-01 & SCR-04** | **WCAG 2.1 AA:** Content Presentation<br>**Heuristic #7:** Flexibility & Efficiency | **Lỗi cắt cụt nhãn trên Navigation Bar:** Ở màn hình 360 dp, nhãn Tab 3 bị cắt cụt thành `"Việc cần l..."` kèm dấu ba chấm. Điều này gây khó nhận diện khi sinh viên nhìn lướt nhanh trên đường đi[cite: 16]. | **Cao (High)** |
| **4** | **SCR-01** (Trang chủ) | **Heuristic #4:** Consistency & Standards<br>**IA & Scope** | **App Bar sai cấu trúc và xuất hiện nút ngoài phạm vi:** App Bar tự sinh cụm Tìm kiếm, Chuông thông báo và Avatar người dùng (trong khi app chỉ đọc Vault offline cục bộ); làm mất icon Cài đặt (SCR-08) ở góc phải. Trên thẻ deadline còn tự thêm nút "Nộp bài" (nộp LMS) không thuộc phạm vi app. | **Trung bình (Medium)** |
| **5** | **SCR-04** (Việc cần làm) | **WCAG Accessibility:** Touch Target Size (Min 48x48 dp)<br>**Heuristic #5:** Error Prevention | **Vùng chạm Checkbox quá nhỏ và dính liền thân Card:** Ô Checkbox để đánh dấu task có diện tích thực tế chỉ khoảng 20x20 dp và nằm sát chữ[cite: 16]. Thao tác một tay bằng ngón cái rất dễ bấm trượt vào thân thẻ (mở trình soạn thảo) thay vì tick xong task. | **Nghiêm trọng (Critical)** |

---

## 4. Bảng Ghi nhận Quyết định của Sinh viên (Student Decision Matrix)

| Phát hiện AI | Quyết định của sinh viên | Lý do lập luận cụ thể (Gắn với Persona & Ràng buộc)[cite: 14, 20] |
| :--- | :---: | :--- |
| **1. Thiếu Snackbar Hoàn tác (SN-01)** | **CHẤP NHẬN (Accept)** | Đây là tính năng cốt lõi của Flow 2 và là tiêu chí đo lường bắt buộc **M3** trong `ux/persona.md`. Bắt buộc phải thêm Snackbar nổi với nút "HOÀN TÁC" hiển thị 8 giây vào SCR-04[cite: 16]. |
| **2. Tự sinh các card rác (GPA, Streak, Flashcard)** | **CHẤP NHẬN (Accept)** | Persona Đức chỉ cần mở app nhanh 30–60 giây để tra cứu. Các tính năng này nằm ngoài phạm vi đã nêu trong `ux/user-flow.md`. Cần loại bỏ hoàn toàn để trả lại diện tích cho Carousel deadline và môn học. |
| **3. Cắt cụt chữ "Việc cần l..." trên Navigation Bar** | **CHỈNH SỬA (Modify)** | Do chiều ngang 360 dp bị giới hạn. Rút ngắn nhãn Tab 3 thành **"Việc làm"** để vừa vặn, đảm bảo hiển thị trọn vẹn chữ tiếng Việt không bị dấu ba chấm[cite: 16]. |
| **4. App Bar sai icon & có nút "Nộp bài"** | **CHẤP NHẬN (Accept)** | App chạy ngoại tuyến không kết nối tài khoản. Thay cụm chuông/avatar bằng đúng **icon Cài đặt** (dẫn đến SCR-08) và xóa nút "Nộp bài". |
| **5. Checkbox bé dưới 48 dp, dễ bấm nhầm** | **CHẤP NHẬN (Accept)** | Persona Đức thao tác bằng ngón cái khi di chuyển. Cần mở rộng bounding box của Checkbox đạt chuẩn **48 × 48 dp**, tạo khoảng cách tối thiểu 8 dp với thân thẻ để tránh chạm nhầm[cite: 16]. |
