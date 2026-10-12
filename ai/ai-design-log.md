# AI DESIGN LOG: QUÁ TRÌNH TẠO VÀ TINH CHỈNH UI VỚI AI

Tài liệu này ghi lại toàn bộ quá trình làm việc với công cụ tạo giao diện bằng AI (Google Stitch) và trợ lý AI phản biện theo đúng quy trình bắt buộc tại Mục 4 và Mục 5 của đề bài Lab 2.

- **Dự án:** FPTU Second Brain Mobile (Companion App cho sinh viên SE Đại học FPT)
- **Persona:** Nguyễn Minh Đức (20 tuổi, SV SE, thao tác một tay trên xe bus, mạng chập chờn)
- **Công cụ AI sử dụng:**
  - **Google Stitch:** Tạo UI ban đầu và thực hiện các vòng lặp tinh chỉnh giao diện.
  - **Gemini:** Trợ lý AI phản biện UX độc lập theo 10 Usability Heuristics (Nielsen), tiêu chuẩn Accessibility (WCAG 2.1 AA) và Persona.

---

## 1. Thiết lập Ngữ cảnh & Khởi tạo Design System trong Google Stitch

Thay vì để Stitch tự do chọn phong cách ngẫu nhiên (dễ bị lệch sang nền tối Cyberpunk của bản desktop), dự án sử dụng tính năng nạp trực tiếp tài liệu quy chuẩn **`design/DESIGN.md`** vào Stitch để trích xuất và cố định hệ thống Design System ngay từ đầu.

### 1.1. Phương thức Thiết lập
1. **Nạp Design Spec:** Chọn `Start with your design` trong Stitch và nhập toàn bộ nội dung từ file `design/DESIGN.md`.
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
Prompt tạo 2 màn hình bao phủ flow chính (SCR-01 Trang chủ thuộc Flow 1 và SCR-04 Việc cần làm & Snackbar Hoàn tác thuộc Flow 2):

```text
Design an Android mobile app named "FPTU Second Brain Mobile" for software engineering university students.

Core Design Rules (Material Design 3):
- Viewport: 360 x 800 dp frame.
- Theme: Clean LIGHT THEME only (Background #F8FAFC, Card Surface #FFFFFF, Primary Blue #1D4ED8, Secondary Teal #0F766E, Warning Container #FEF3C7, Error Container #FEE2E2). Absolutely NO dark mode, NO cyberpunk neon.
- Typography: Inter font, all content text must be strictly >= 14 sp. High line-height.
- Touch Ergonomics: Interactive targets (buttons, checkboxes, chips, tab icons) must be at least 48 x 48 dp.

Screen 1: SCR-01 Trang chủ (Dashboard)
- Top App Bar (56 dp): Title "Kỹ thuật Phần mềm", right icon Settings linking to SCR-08.
- Section 1 (Urgent Deadlines Carousel): Horizontal cards for tasks due <= 3 days. Each card shows subject code "PRM323", task name "Figma Prototype Lab 2", badge with schedule icon + text "Hôm nay" (Amber #FEF3C7, text #92400E). Text button "Xem tất cả" aligned right.
- Section 2 (Recent Course Card): Card showing "PRM323 - Lập trình Di động Đa nền tảng", slot progress "Slot 12/30", button "Xem đề cương".
- Section 3 (AI Banner): Light Blue #DBEAFE background, text "Hỏi trợ lý AI về môn học", icon auto_awesome, button "Đặt câu hỏi".
- Section 4: Linear progress bar (65% kiến thức đã đồng bộ).
- Bottom Navigation Bar (80 dp): 4 items (Trang chủ [Active], Lộ trình, Việc cần làm, Ghi chú).
- Floating Action Button (FAB): 56x56 dp at bottom right with edit icon.

Screen 2: SCR-04 Việc cần làm (Tasks & Deadline)
- Top App Bar: Title "Việc cần làm", filter chip row: "Hôm nay" [Selected], "Sắp tới", "Đã hoàn thành".
- Task List:
  * Item 1 (Overdue): Left checkbox (48x48 dp touch target). Center: "Nộp báo cáo Lab 1", course "SWP391", badge with error icon + text "Quá hạn" (Red #FEE2E2, text #991B1B).
  * Item 2 (Due Today): Checkbox 48x48 dp. Title "Hoàn thiện Figma Prototype Lab 2", course "PRM323", badge "Hôm nay" (Amber #FEF3C7, text #92400E).
- Floating Snackbar (SN-01) above bottom nav: Background #1E293B, text "Đã hoàn thành task", blue text button "HOÀN TÁC".
- Bottom Navigation Bar: Tab "Việc cần làm" [Selected].
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
| **1** | **SCR-04** (Việc cần làm) | **Heuristic #3:** User Control & Freedom<br>**Heuristic #5:** Error Prevention | **Mất hoàn toàn thanh Snackbar Hoàn tác (SN-01):** Stitch hoàn toàn không vẽ thanh Snackbar nổi có nút "HOÀN TÁC" 8 giây khi tick task như yêu cầu. Khi Đức di chuyển trên xe bus bị rung lắc, nếu lỡ tay chạm nhầm task, người dùng không thể phục hồi ngay lập tức (vi phạm tiêu chí đo lường M3). | **Nghiêm trọng (Critical)** |
| **2** | **SCR-01 & SCR-04** | **Heuristic #8:** Aesthetic & Minimalist Design<br>**Persona Goal:** G1 & G2 | **Nhiễu thị giác do tự ý thêm tính năng ngoài phạm vi:** Stitch tự ý chèn các card ngoài luồng: *"Chuỗi 14 ngày tập trung"*, *"GPA 3.65"*, *"Sprint Fall 2024"*, *"Flashcards"*, *"Lịch học"*, *"Mẹo nhỏ học tập"*. Chúng chiếm diện tích lớn, đẩy phần quan trọng nhất (Carousel deadline khẩn cấp và đề cương) xuống khuất màn hình. | **Cao (High)** |
| **3** | **SCR-01 & SCR-04** | **WCAG 2.1 AA:** Content Presentation<br>**Heuristic #7:** Flexibility & Efficiency | **Lỗi cắt cụt nhãn trên Navigation Bar:** Ở màn hình 360 dp, nhãn Tab 3 bị cắt cụt thành `"Việc cần l..."` kèm dấu ba chấm. Điều này gây khó nhận diện khi sinh viên nhìn lướt nhanh trên đường đi. | **Cao (High)** |
| **4** | **SCR-01** (Trang chủ) | **Heuristic #4:** Consistency & Standards<br>**IA & Scope** | **App Bar sai cấu trúc và xuất hiện nút ngoài phạm vi:** App Bar tự sinh cụm Tìm kiếm, Chuông thông báo và Avatar người dùng (trong khi app chỉ đọc Vault offline cục bộ); làm mất icon Cài đặt (SCR-08) ở góc phải. Trên thẻ deadline còn tự thêm nút "Nộp bài" (nộp LMS) không thuộc phạm vi app. | **Trung bình (Medium)** |
| **5** | **SCR-04** (Việc cần làm) | **WCAG Accessibility:** Touch Target Size (Min 48x48 dp)<br>**Heuristic #5:** Error Prevention | **Vùng chạm Checkbox quá nhỏ và dính liền thân Card:** Ô Checkbox để đánh dấu task có diện tích thực tế chỉ khoảng 20x20 dp và nằm sát chữ. Thao tác một tay bằng ngón cái rất dễ bấm trượt vào thân thẻ (mở trình soạn thảo) thay vì tick xong task. | **Nghiêm trọng (Critical)** |

---

## 4. Bảng Ghi nhận Quyết định của Sinh viên (Student Decision Matrix)

| Phát hiện AI | Quyết định của sinh viên | Lý do lập luận cụ thể (Gắn với Persona & Ràng buộc) |
| :--- | :---: | :--- |
| **1. Thiếu Snackbar Hoàn tác (SN-01)** | **CHẤP NHẬN (Accept)** | Đây là tính năng cốt lõi của Flow 2 và là tiêu chí đo lường bắt buộc **M3** trong `ux/persona.md`. Bắt buộc phải thêm Snackbar nổi với nút "HOÀN TÁC" hiển thị 8 giây vào SCR-04. |
| **2. Tự sinh các card rác (GPA, Streak, Flashcard)** | **CHẤP NHẬN (Accept)** | Persona Đức chỉ cần mở app nhanh 30–60 giây để tra cứu. Các tính năng này nằm ngoài phạm vi đã nêu trong `ux/user-flow.md`. Cần loại bỏ hoàn toàn để trả lại diện tích cho Carousel deadline và môn học. |
| **3. Cắt cụt chữ "Việc cần l..." trên Navigation Bar** | **CHỈNH SỬA (Modify)** | Do chiều ngang 360 dp bị giới hạn. Rút ngắn nhãn Tab 3 thành **"Việc làm"** để vừa vặn, đảm bảo hiển thị trọn vẹn chữ tiếng Việt không bị dấu ba chấm. |
| **4. App Bar sai icon & có nút "Nộp bài"** | **CHẤP NHẬN (Accept)** | App chạy ngoại tuyến không kết nối tài khoản. Thay cụm chuông/avatar bằng đúng **icon Cài đặt** (dẫn đến SCR-08) và xóa nút "Nộp bài". |
| **5. Checkbox bé dưới 48 dp, dễ bấm nhầm** | **CHẤP NHẬN (Accept)** | Persona Đức thao tác bằng ngón cái khi di chuyển. Cần mở rộng bounding box của Checkbox đạt chuẩn **48 × 48 dp**, tạo khoảng cách tối thiểu 8 dp với thân thẻ để tránh chạm nhầm. |
