
# AI DESIGN LOG: QUÁ TRÌNH TẠO VÀ TINH CHỈNH UI VỚI AI

Tài liệu này ghi lại toàn bộ các phiên làm việc với Google Stitch và trợ lý AI phản biện theo đúng quy trình bắt buộc tại Mục 4 và Mục 5 của đề bài Lab 2.

- **Dự án:** FPTU Second Brain Mobile
- **Persona:** Nguyễn Minh Đức (20 tuổi, SV SE, thao tác một tay trên xe bus, mạng chập chờn)
- **Công cụ AI sử dụng:** Google Stitch (tạo UI), Gemini (trợ lý AI phản biện Heuristic & Accessibility)

---

## 1. System Prompt (Ngữ cảnh nền tảng nạp vào Stitch)

Prompt thiết lập hệ thống định hình phong cách trước khi tạo màn hình:

```text
You are a senior mobile UI designer specializing in Material Design 3 (M3).
Design an Android academic companion mobile app named "FPTU Second Brain Mobile" for software engineering university students.

Core Constraints:
1. Base Frame: Android 360 x 800 dp viewport.
2. Theme: Pure LIGHT THEME only (Background #F8FAFC, Card Surface #FFFFFF, Primary Blue #1D4ED8, Secondary Teal #0F766E). Absolutely NO dark mode, NO cyberpunk neon, NO glassmorphism.
3. Typography: Inter font, all content text must be >= 14 sp. High line-height to support Vietnamese stacked diacritics.
4. Touch Ergonomics: All interactive targets (buttons, checkboxes, chips, tab icons) must have minimum 48 x 48 dp clickable area, optimized for one-handed thumb navigation.
5. Information Hierarchy: Crucial state indicators (deadlines, sync status) MUST have explicit text labels and semantic icons (do not rely on color alone).
6. Navigation Structure: Fixed Bottom Navigation Bar with 4 tabs: Trang chủ (Home), Lộ trình (Timeline), Việc cần làm (Tasks), Ghi chú (Notes). A circular FAB for "Ghi chú nhanh" positioned at bottom right.
```

---

## 2. Tạo UI Ban Đầu (Initial UI Generation)

### 2.1. Prompt Nguyên văn gửi Google Stitch
Prompt tạo hai màn hình chính của Flow 1 và Flow 2 (SCR-01 Trang chủ và SCR-04 Việc cần làm):

```text
Design two core screens for Android app "FPTU Second Brain Mobile":
Viewport: 360 x 800 dp, Light Theme.

Screen 1: SCR-01 Trang chủ (Dashboard)
- Top App Bar (56 dp): Title "Kỹ thuật Phần mềm", right action icon Settings (48x48 dp) linking to SCR-08.
- Section 1 (Urgent Deadlines Carousel): Horizontal cards for tasks due <= 3 days. Card shows subject code "PRM323", task title "Figma Prototype Lab 2", badge with schedule icon + text "Hôm nay" (Amber #FEF3C7, text #92400E). Text button "Xem tất cả" aligned right.
- Section 2 (Recent Course Card): Card showing "PRM323 - Lập trình Di động Đa nền tảng", slot progress "Slot 12/30", button "Xem đề cương".
- Section 3 (AI Banner): Light Blue #DBEAFE background, text "Hỏi trợ lý AI về môn học", icon auto_awesome, primary button "Đặt câu hỏi".
- Section 4: Linear progress bar (65% kiến thức đã đồng bộ).
- Bottom Navigation Bar (80 dp): 4 items (Trang chủ [Selected], Lộ trình, Việc cần làm, Ghi chú).
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
- Ảnh chụp màn hình SCR-01: `![SCR-01 Initial UI](../assets/stitch/initial-scr01.png)`
- Ảnh chụp màn hình SCR-04: `![SCR-04 Initial UI](../assets/stitch/initial-scr04.png)`
