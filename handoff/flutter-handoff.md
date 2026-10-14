# Flutter Handoff — FPTU Second Brain Mobile

## Quy tắc toàn cục

- Android portrait; thiết kế chuẩn 360 × 800 dp, kiểm tra 412 dp. PNG tham chiếu cuối nằm trong `assets/figma/`.
- Material Design 3, light theme, Inter (fallback Roboto), tiếng Việt. Dùng SafeArea/MediaQuery cho system insets.
- Nội dung tối thiểu 14 sp; Navigation label 12 sp là ngoại lệ được ghi trong design brief. Touch target tối thiểu 48 × 48 dp; khoảng cách tối thiểu 8 dp.
- Contrast chữ thường ≥ 4.5:1, chữ lớn/UI control ≥ 3:1; không dùng màu làm tín hiệu duy nhất.
- Lưới 4 dp; lề 16 dp tại 360, 20 dp tại 412. Xem `design/DESIGN.md` để biết giá trị đầy đủ.
- Flow prototype có 3 điểm bắt đầu. Hỏi AI là Flow 1A, nhánh từ SCR-03.

## Responsive từ 600 dp

Các bố cục rộng là yêu cầu handoff để triển khai/kiểm tra; Figma hiện ưu tiên mobile, không khẳng định đã có frame tablet.

- Từ 600 dp: BottomNavigationBar chuyển thành NavigationRail; nội dung một cột, căn giữa, giới hạn khoảng 840 dp; lề 24–32 dp.
- Từ 840 dp: Roadmap có thể dùng danh sách môn + chi tiết hai pane; Notes dùng danh sách + nội dung ghi chú hai pane. Ở 600–839 dp dùng một pane.
- SCR-05 giới hạn vùng soạn khoảng 720 dp; dialog căn giữa tối đa khoảng 560 dp.
- Giữ target 48 dp và cho phép cuộn khi text scale tăng. Rà soát tràn chữ tiếng Việt tại 360, 412, 600 và 840 dp.

## Token → Flutter

| Token | Flutter mapping | Giá trị/ghi chú |
| --- | --- | --- |
| color-primary / on-primary / primary-pressed | ColorScheme.primary / onPrimary; custom pressed | #1D4ED8 / #FFFFFF / #1E40AF |
| primary-container / on-primary-container | primaryContainer / onPrimaryContainer | #DBEAFE / #1E3A8A |
| secondary / secondary-container / on-secondary-container | secondary / secondaryContainer / onSecondaryContainer | #0F766E / #CCFBF1 / #115E59 |
| surface / surface-container / surface-container-high | surface / surfaceContainerLowest / surfaceContainerHigh | #F8FAFC / #FFFFFF / #F1F5F9 |
| on-surface / on-surface-variant / outline / outline-variant | onSurface / onSurfaceVariant / outline / outlineVariant | #0F172A / #475569 / #64748B / #CBD5E1 (outline-variant chỉ trang trí) |
| error / error-container / on-error-container | error + semantic colors | #DC2626 / #FEE2E2 / #991B1B |
| warning / warning-container / on-warning-container | custom semantic colors | #B45309 / #FEF3C7 / #92400E |
| success / success-container / on-success-container | custom semantic colors | #15803D / #DCFCE7 / #166534 |
| disabled-container / on-disabled / skeleton | custom states | #E2E8F0 / #94A3B8 / #E2E8F0 |
| scrim / inverse-surface / inverse-on-surface / inverse-primary | scrim + inverse ColorScheme | #0F172A at 40%; #1E293B / #F8FAFC / #93C5FD |
| headline-large / headline-medium | TextTheme.headlineLarge / headlineMedium | Inter 28/22 sp; line height 34/28 |
| title-large / title-medium | titleLarge / titleMedium | 18/16 sp; line height 24/22 |
| body-large / body-medium / body-semibold | bodyLarge / bodyMedium + weight | 16/14 sp; line height 24/20 |
| label-large / label-small | labelLarge / labelSmall | 14/12 sp; small chỉ dùng navigation |
| spacing-2xs / xs / sm / md | constants | 4 / 8 / 12 / 16 dp |
| spacing-lg / xl / 2xl | constants | 20 / 24 / 32 dp |
| radius-xs / sm / md / lg / xl / full | constants | 4 / 8 / 12 / 16 / 24 / 999 dp |
| elevation tokens | CardTheme / state elevation | theo bảng elevation trong DESIGN.md |

## Component → Flutter widget

| Figma component | Flutter suggestion | Trạng thái |
| --- | --- | --- |
| Button | FilledButton, OutlinedButton, TextButton, FloatingActionButton | Default, pressed, disabled, loading |
| TextField/SearchField | TextField hoặc TextFormField | Default, focused, filled, error, disabled |
| CourseCard/NoteCard | Card + InkWell | Default/pressed; semantics chứa tên và status |
| TaskItem | custom row + Checkbox | checkbox và mở chi tiết là hai hit target; Undo 8 giây |
| BottomNavigation | NavigationBar; NavigationRail khi ≥600 dp | selected: Home/Roadmap/Tasks/Notes |
| AppBar | AppBar | default/action |
| D-01 dialog | AlertDialog | confirm/cancel; back/outside theo prototype |
| LoadingState | skeleton hoặc CircularProgressIndicator | chỉ hiển thị trong lúc tải |
| EmptyState | custom icon + message + CTA | một hành động chính |
| ErrorState | banner/page error + retry | giữ dữ liệu/input hiện có |
| Chip/filter | FilterChip/ActionChip | selected có label/icon |
| Progress | LinearProgressIndicator | kèm số liệu chữ |
| Snackbar | ScaffoldMessenger | Undo không bị FAB/navigation che |

## Screen-by-screen handoff

Mỗi mục nêu đủ Layout, Components, States, Interactions, Navigation và Constraints. PNG là tham chiếu Figma final.

### SCR-01 — Home
- **Layout:** trang cuộn gồm lời chào, trạng thái Vault, deadline khẩn cấp, thẻ Vault; navigation cố định.
- **Components:** AppBar action đồng bộ/cài đặt, deadline cards, Vault card, NavigationBar.
- **States:** populated, skeleton loading, Vault chưa kết nối/empty, offline banner.
- **Interactions:** tất cả deadline → SCR-04; course → SCR-03; sync/settings → SCR-08.
- **Navigation:** start mặc định; tabs đến SCR-02/SCR-04/SCR-06.
- **Constraints:** ngày và trạng thái không bị cắt; icon + label. Ref: `assets/figma/SCR-01_Home.png`.

### SCR-02 — Roadmap
- **Layout:** chọn kỳ/tìm kiếm, tiến độ tuần, danh sách CourseCard cuộn.
- **Components:** term chips, SearchField, chart, CourseCard.
- **States:** populated, loading, empty, pressed.
- **Interactions:** chọn kỳ/tìm; mở PRM323 → SCR-03.
- **Navigation:** tab 2, back theo quy tắc chung.
- **Constraints:** biểu đồ có số liệu text; trạng thái không chỉ dựa vào màu. Ref: `assets/figma/SCR-02_Roadmap.png`.

### SCR-03 — Course Detail
- **Layout:** thông tin môn/tiến độ, cảnh báo offline, tabs nội bộ và actions.
- **Components:** AppBar, course/progress cards, tabs, Ask AI, Documents.
- **States:** populated, thiếu syllabus/empty, offline.
- **Interactions:** Ask AI → SCR-07 (Flow 1A); Documents → SCR-06 lọc PRM323.
- **Navigation:** push từ SCR-01/02; back về origin.
- **Constraints:** giữ course context; không yêu cầu đăng nhập FLM trên mobile. Ref: `assets/figma/SCR-03_CourseDetail.png`.

### SCR-04 — Tasks
- **Layout:** filters, semester progress, urgent tasks đầu danh sách, nhóm upcoming/completed.
- **Components:** chips, TaskItem có checkbox/detail hit target riêng, Snackbar, FAB nếu hiện diện.
- **States:** populated, loading, empty theo filter, completed + Undo.
- **Interactions:** chạm nội dung task → SCR-05; checkbox đổi trạng thái và mở Undo 8 giây.
- **Navigation:** tab 3; editor quay về context trước hoặc Notes.
- **Constraints:** checkbox 48 × 48 dp; Snackbar không bị FAB che; Undo khôi phục đúng trạng thái. Ref: `assets/figma/SCR-04_Tasks.png`.

### SCR-05 — Note Editor
- **Layout:** editor toàn màn hình; metadata/title, Markdown edit/preview, toolbar đáy có Save.
- **Components:** AppBar/back, course/tag chips, editor, preview, checklist action, format toolbar, Save.
- **States:** create, edit, autosaved, invalid filename, save failure.
- **Interactions:** soạn Markdown/checklist; lưu → SCR-06; back về origin.
- **Navigation:** mở từ task/note; hỗ trợ nhiều nguồn vào.
- **Constraints:** keyboard không che Save; làm rõ autosave và explicit save; hỗ trợ text scale. Ref: `assets/figma/SCR-05_NoteEditor.png`.

### SCR-06 — Notes
- **Layout:** Vault status, search, subject filters, list và helper callout.
- **Components:** SearchField, filter chips, NoteCards gắn USER NOTE/FLM SYNC, FAB nếu có.
- **States:** populated, filtered, no results, no notes.
- **Interactions:** note → SCR-05; tìm/lọc; tạo note.
- **Navigation:** tab 4; đích xem Vault offline trong Flow 1A.
- **Constraints:** phân biệt loại note bằng chữ/icon; title dài được wrap. Ref: `assets/figma/SCR-06_Notes.png`.

### SCR-07 — Ask AI
- **Layout:** context/model AppBar, connection banner, chat/citations, prompts, composer đáy.
- **Components:** chat bubbles, citation card, retry banner, prompt chips, composer/send.
- **States:** suggestions, loading, answer, no sources, network/config error.
- **Interactions:** gửi câu hỏi; citation mở nguồn; retry gửi lại câu hỏi đã giữ.
- **Navigation:** Flow 1A từ SCR-03; back giữ question và course context.
- **Constraints:** AI cần mạng; Vault vẫn tra cứu offline; không báo AI chạy offline. Ref: `assets/figma/SCR-07_AskAI.png`.

### SCR-08 — Sync Vault
- **Layout:** Vault path/status, rescan controls, AI config, capacity.
- **Components:** AppBar, path selector, switch, sync button, API key field, status card.
- **States:** connected, confirmation overlay, loading, success, inaccessible Vault.
- **Interactions:** sync now → D-01; confirm chạy sync; cancel đóng; failure → error state.
- **Navigation:** từ action trên SCR-01; retry từ error trở lại đây.
- **Constraints:** bảo vệ API key; thông báo chính xác nơi lưu và yêu cầu mạng. Ref: `assets/figma/SCR-08_SyncVault.png`.

### D-01 — Sync confirmation
- **Layout:** modal căn giữa trên SCR-08, mô tả + 2 actions.
- **Components:** AlertDialog, cancel/confirm, scrim.
- **States:** mở, dismissed, confirming.
- **Interactions:** cancel/back/outside dismiss; confirm bắt đầu đồng bộ.
- **Navigation:** dismiss trả về SCR-08 nền.
- **Constraints:** focus semantics, label rõ, contrast đạt chuẩn. Ref: `assets/figma/D-01_SyncConfirmation.png`.

### SCR-08_SyncError — Sync failure
- **Layout:** nguyên nhân lỗi, cam kết dữ liệu cục bộ còn nguyên, retry.
- **Components:** error icon/text, retry, optional choose-folder action.
- **States:** permission/path error, retrying, recovered.
- **Interactions:** Retry → SCR-08; choose folder mở picker khi implement.
- **Navigation:** đến sau sync thất bại; Back theo flow app.
- **Constraints:** nêu nguyên nhân và hành động; không dùng riêng màu đỏ. Ref: `assets/figma/SCR-08_SyncError.png`.

## Kiểm tra khi triển khai

Đối chiếu Figma page 06 và `design/screen-spec.md`; kiểm tra back navigation, giữ input khi lỗi, retry, trạng thái loading, semantics, contrast và overflow tại các độ rộng đã nêu. 
