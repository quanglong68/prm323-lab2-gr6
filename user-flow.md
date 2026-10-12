\# UX ANALYSIS: INFORMATION ARCHITECTURE \& USER FLOWS



\## 1. Kiến trúc Thông tin (Information Architecture - IA)



\### 1.1. Danh sách 8 Màn hình Độc lập (Core Screens)

Hệ thống bao gồm 8 màn hình riêng biệt (không tính các Dialog overlay và Bottom Sheet trạng thái) đáp ứng mục tiêu học tập và quản lý của sinh viên:



1\. \*\*SCR-01: Dashboard Screen (Trang chủ \& Tổng quan):\*\* Hiển thị lời chào, ngành học hiện tại, thanh tiến độ tích lũy tri thức toàn khóa, carousel trượt cảnh báo deadline khẩn cấp (≤ 3 ngày) và phím tắt thao tác nhanh.

2\. \*\*SCR-02: Syllabus Timeline Screen (Lộ trình Môn học):\*\* Cây tiến trình học tập theo trục thời gian (Timeline) chia theo 9 học kỳ; mỗi môn thể hiện rõ trạng thái dữ liệu (Chưa có tài liệu / Đã tải về / AI đã phân tích).

3\. \*\*SCR-03: Course Details Screen (Chi tiết Môn học \& Đề cương):\*\* Hiển thị thông tin sâu của môn học bóc tách từ FLM gồm: Mục tiêu đầu ra (LOs), Giáo trình chính, Danh mục đầu điểm đánh giá (Assignment, Progress Test, PE, FE) và Lịch trình từng Slot học.

4\. \*\*SCR-04: Tasks \& Deadline Screen (Quản lý Nhiệm vụ \& Deadline):\*\* Danh sách toàn bộ deadline trích xuất từ các ghi chú Markdown; hỗ trợ bộ lọc trạng thái (Hôm nay, Sắp tới, Đã hoàn thành) và cơ chế đánh dấu hoàn tất.

5\. \*\*SCR-05: Note Editor Screen (Soạn thảo Ghi chú \& Tạo Task):\*\* Trình soạn thảo văn bản hỗ trợ cú pháp Markdown, phím tắt chèn nhanh Task (`- \[ ] @due`), tự động gợi ý tên file an toàn tránh ghi đè dữ liệu gốc.

6\. \*\*SCR-06: Course Notes \& Files Screen (Kho Ghi chú Môn học):\*\* Danh mục toàn bộ các file ghi chú gắn với mã môn học cụ thể; phân loại rõ ràng giữa file đề cương gốc của trường (`FLM SYNC`) và ghi chú do người dùng viết (`USER NOTE`).

7\. \*\*SCR-07: AI Tutor Chat Screen (Trợ lý Hỏi đáp Tri thức):\*\* Giao diện hội thoại thông minh hỗ trợ sinh viên đặt câu hỏi, AI sử dụng công nghệ tìm kiếm ngữ cảnh (RAG) để trích xuất câu trả lời chính xác từ các file ghi chú cá nhân.

8\. \*\*SCR-08: FLM Sync \& Settings Screen (Đồng bộ FLM \& Cấu hình):\*\* Màn hình quản lý kết nối cổng trường FLM (trạng thái session, nút đồng bộ lại), thiết lập đường dẫn thư mục Vault ngoại tuyến và cấu hình API Key.



\---



\### 1.2. Sơ đồ Cấu trúc Điều hướng (Navigation Hierarchy)

Hệ thống sử dụng thanh điều hướng đáy (Bottom Navigation Bar) cố định cho 4 màn hình cấp cao nhất (Top-level), kết hợp nút Ghi chú nhanh (Quick Action FAB) ở trung tâm.



```text

App Root

├── \[Bottom Navigation Bar] (Cấp cao nhất - Level 1)

│   ├── Tab 1: SCR-01 Dashboard Screen (Màn hình mặc định)

│   ├── Tab 2: SCR-02 Syllabus Timeline Screen

│   ├── Tab 3: SCR-04 Tasks \& Deadline Screen

│   ├── Tab 4: SCR-08 FLM Sync \& Settings Screen

│   └── \[Center FAB]: Mở nhanh SCR-05 Note Editor Screen (Modal Push)

│

├── \[Màn hình Điều hướng sâu - Level 2]

│   ├── Từ SCR-01 / SCR-02 ──> SCR-03 Course Details Screen

│   │                              └── Nhấn "Xem ghi chú môn" ──> SCR-06 Course Notes Screen

│   │                                                                 └── Nhấn "Sửa file" ──> SCR-05 Note Editor Screen

│   ├── Từ SCR-01 (Banner AI) ──> SCR-07 AI Tutor Chat Screen

│   └── Từ SCR-04 (Nhấn vào Task) ──> SCR-05 Note Editor Screen (Mở file chứa task)

```



\---



\## 2. Chi tiết 3 User Flow Hoàn chỉnh



\---



\### Flow 1: Tra cứu Nội dung Slot \& Đề cương Đánh giá Môn học (Syllabus Inspection Flow)

\- \*\*Điểm bắt đầu:\*\* Sinh viên mở app tại màn hình chính (SCR-01 Dashboard Screen).

\- \*\*Mục tiêu:\*\* Tra cứu xem môn học tiếp theo có bao nhiêu slot, hôm nay học chủ đề gì và cấu trúc bài thi gồm những cột điểm nào.

\- \*\*Điểm kết thúc:\*\* Người dùng nắm rõ thông tin buổi học và quay lại Dashboard hoặc mở ghi chú của môn.



```mermaid

flowchart TD

&#x20;   Start(\[Bắt đầu: Mở app tại SCR-01 Dashboard]) --> CheckContext{Đức muốn tra cứu môn nào?}

&#x20;   

&#x20;   CheckContext -->|Môn đang học hôm nay| TapQuickCard\[Nhấn thẻ môn học nhanh trên Dashboard]

&#x20;   CheckContext -->|Môn thuộc kỳ khác| NavTimeline\[Chuyển sang Tab 2: SCR-02 Syllabus Timeline]

&#x20;   

&#x20;   NavTimeline --> SelectSemester\[Cuộn chọn Học kỳ mong muốn]

&#x20;   SelectSemester --> TapSubjectNode\[Nhấn vào ô môn học cụ thể]

&#x20;   

&#x20;   TapQuickCard --> OpenDetails\[Điều hướng đến SCR-03 Course Details]

&#x20;   TapSubjectNode --> OpenDetails

&#x20;   

&#x20;   OpenDetails --> ViewTabs{Chọn thông tin cần xem}

&#x20;   ViewTabs -->|Xem lịch slot và chủ đề| ReadSchedule\[Cuộn xem danh sách Slot học và Nhiệm vụ]

&#x20;   ViewTabs -->|Xem cấu trúc điểm thi| ReadAssessment\[Xem bảng trọng số điểm: PT, Assignment, PE, FE]

&#x20;   

&#x20;   ReadSchedule --> NextAction{Hành động tiếp theo?}

&#x20;   ReadAssessment --> NextAction

&#x20;   

&#x20;   NextAction -->|Muốn ghi chú bài học| NavNotes\[Nhấn Kho tài liệu -> Chuyển sang SCR-06 Course Notes]

&#x20;   NextAction -->|Đã nắm xong thông tin| BackNav\[Nhấn nút Back trên AppBar]

&#x20;   

&#x20;   NavNotes --> EndFlow1(\[Kết thúc Flow 1])

&#x20;   BackNav --> EndFlow1

```



\- \*\*Nhánh thành công (Happy Path):\*\* Mở app -> Nhấn thẻ môn học đang học trên Dashboard -> Mở SCR-03 -> Xem ngay lịch slot và đầu điểm thi trong vòng 2 chạm.

\- \*\*Nhánh thay thế (Alternate Path):\*\* Mở app -> Chuyển tab SCR-02 Timeline -> Chọn kỳ học trước đó để tra cứu lại chuẩn đầu ra môn điều kiện -> Mở SCR-03.



\---



\### Flow 2: Quản lý Deadline \& Phục hồi Thao tác Nhầm lẫn (Task Management \& Undo Recovery Flow)

\*(Flow bắt buộc có nhánh lỗi và phục hồi theo quy định đề bài)\*

\- \*\*Điểm bắt đầu:\*\* Sinh viên nhận thấy cảnh báo deadline khẩn cấp trên SCR-01 hoặc mở tab SCR-04 Tasks \& Deadline.

\- \*\*Mục tiêu:\*\* Kiểm tra bài tập cần hoàn thành trong ngày và tick chọn hoàn thành task.

\- \*\*Điểm kết thúc:\*\* Danh sách nhiệm vụ được cập nhật chính xác, khôi phục thành công nếu lỡ tay bấm nhầm.



```mermaid

flowchart TD

&#x20;   Start(\[Bắt đầu: Mở SCR-01 Dashboard]) --> NoticeUrgent{Cách truy cập danh sách task?}

&#x20;   

&#x20;   NoticeUrgent -->|Nhấn Banner khẩn cấp| DirectTask\[Nhấn thẻ deadline trên Carousel cảnh báo]

&#x20;   NoticeUrgent -->|Nhấn Tab chuyên biệt| NavTasks\[Chuyển sang Tab 3: SCR-04 Tasks and Deadline]

&#x20;   

&#x20;   DirectTask --> ViewTaskList\[Hiển thị danh sách nhiệm vụ trên SCR-04]

&#x20;   NavTasks --> ViewTaskList

&#x20;   

&#x20;   ViewTaskList --> FilterTask\[Lọc theo: Hôm nay hoặc Còn hạn gấp]

&#x20;   FilterTask --> ActionCheck\[Đức nhấn Checkbox đánh dấu Hoàn thành task]

&#x20;   

&#x20;   ActionCheck --> StateChange\[Task bị gạch ngang và chuyển sang trạng thái Đã xong]

&#x20;   StateChange --> TriggerSnackbar\[Hệ thống hiển thị Snackbar: Đã hoàn thành task kèm nút HOÀN TÁC trong 8s]

&#x20;   

&#x20;   TriggerSnackbar --> DecisionNode{Đức có bấm nhầm khi đi xe bus không?}

&#x20;   

&#x20;   DecisionNode -->|Bấm đúng: Thao tác chủ đích| KeepDone\[Không làm gì thêm, Snackbar tự biến mất sau 8s]

&#x20;   KeepDone --> UpdateVault\[File Markdown gốc được cập nhật: dấu x được ghi vào task]

&#x20;   UpdateVault --> EndHappy(\[Kết thúc Flow 2 - Thành công])

&#x20;   

&#x20;   DecisionNode -->|Lỗi: Lỡ tay chạm nhầm| TapUndo\[Đức nhấn nút HOÀN TÁC trên Snackbar trong vòng 8s]

&#x20;   TapUndo --> RecoveryAction\[Hệ thống hủy bỏ thao tác: Khôi phục task về trạng thái Chưa xong]

&#x20;   RecoveryAction --> ShowToast\[Hiển thị thông báo nhẹ: Đã khôi phục nhiệm vụ]

&#x20;   ShowToast --> EndRecovery(\[Kết thúc Flow 2 - Phục hồi lỗi hoàn tất])

```



\- \*\*Nhánh thành công (Happy Path):\*\* Người dùng tick vào ô Checkbox của task -> Task chuyển thành đã làm -> Snackbar thông báo xuất hiện và tự ẩn sau 8 giây -> Task lưu vĩnh viễn.

\- \*\*Nhánh lỗi \& Phục hồi (Error \& Recovery Path):\*\* Do rung lắc khi đi xe bus, Đức chạm nhầm vào nút Checkbox của một bài tập chưa làm xong -> Task biến mất khỏi danh sách chờ -> Nhờ thanh thông báo Snackbar neo ở đáy màn hình hiển thị trong 8 giây, Đức kịp thời nhấn \*\*"HOÀN TÁC" (Undo)\*\* trong 1 chạm -> Trạng thái task ngay lập tức được khôi phục nguyên vẹn, ngăn chặn nguy cơ quên nộp bài.



\---



\### Flow 3: Ghi chú Nhanh \& Hỏi đáp Tri thức qua AI Tutor (Quick Capture \& AI Knowledge Retrieval Flow)

\- \*\*Điểm bắt đầu:\*\* Sinh viên muốn ghi chú nhanh bài tập trên lớp hoặc đặt câu hỏi tra cứu kiến thức cũ.

\- \*\*Mục tiêu:\*\* Lưu nhanh một ghi chú kèm deadline mới, hoặc nhờ AI tìm kiếm nội dung ghi chú trong Vault.

\- \*\*Điểm kết thúc:\*\* Ghi chú mới được lưu an toàn không ghi đè file gốc, hoặc nhận được câu trả lời từ AI kèm trích dẫn.



```mermaid

flowchart TD

&#x20;   Start(\[Bắt đầu: Sinh viên đang ở bất kỳ màn hình nào]) --> ChooseGoal{Nhu cầu của Đức?}

&#x20;   

&#x20;   ChooseGoal -->|Ghi chép bài tập trên lớp| TapFAB\[Nhấn nút trung tâm Quick Note FAB]

&#x20;   TapFAB --> OpenEditor\[Mở màn hình SCR-05 Note Editor]

&#x20;   OpenEditor --> AutoGen\[Hệ thống tự điền mã môn gợi ý và tên file an toàn]

&#x20;   AutoGen --> InputContent\[Nhập nội dung ghi chú bài học]

&#x20;   InputContent --> InsertShortcut\[Nhấn nút tắt Tạo Task -> Chèn cú pháp @due vào con trỏ]

&#x20;   InsertShortcut --> TapSave\[Nhấn nút Lưu vào Vault]

&#x20;   TapSave --> ValidateName{Kiểm tra tên file?}

&#x20;   

&#x20;   ValidateName -->|Trùng tên file đề cương gốc| ShowError\[Báo lỗi đỏ: Không được ghi đè đề cương FLM, hãy đổi tên]

&#x20;   ShowError --> InputContent

&#x20;   

&#x20;   ValidateName -->|Tên hợp lệ| SaveSuccess\[Tự gắn tag #USER\_NOTE và lưu vào máy]

&#x20;   SaveSuccess --> ViewInList\[Điều hướng đến SCR-06 xem danh sách ghi chú môn]

&#x20;   ViewInList --> EndFlow3A(\[Kết thúc Flow 3A])

&#x20;   

&#x20;   ChooseGoal -->|Tra cứu kiến thức cũ| OpenChat\[Mở SCR-07 AI Tutor Chat từ Dashboard]

&#x20;   OpenChat --> EnterPrompt\[Nhập câu hỏi tra cứu kiến thức môn học]

&#x20;   EnterPrompt --> SendQuery\[Nhấn gửi câu hỏi]

&#x20;   SendQuery --> CheckNetwork{Kiểm tra kết nối mạng?}

&#x20;   

&#x20;   CheckNetwork -->|Có mạng| AISearching\[Hiển thị chỉ báo: AI đang tìm kiếm trong Vault...]

&#x20;   AISearching --> DisplayAnswer\[Hiển thị câu trả lời Markdown và Thẻ trích dẫn file nguồn]

&#x20;   DisplayAnswer --> EndFlow3B(\[Kết thúc Flow 3B])

&#x20;   

&#x20;   CheckNetwork -->|Mất mạng hoặc Sóng yếu| ShowNetError\[Hiển thị Error State: Không thể kết nối AI, hãy kiểm tra mạng]

&#x20;   ShowNetError --> RetryAction{Hành động phục hồi}

&#x20;   RetryAction -->|Thử lại| SendQuery

&#x20;   RetryAction -->|Rời đi| BackHome\[Quay về Dashboard xem ghi chú offline]

&#x20;   BackHome --> EndFlow3B

```



\- \*\*Nhánh thành công (Happy Path):\*\* 

&#x20; - \*Tạo ghi chú:\* Bấm FAB -> SCR-05 -> Soạn ghi chú -> Bấm nút "Tạo Task" chèn hạn nộp -> Lưu thành công vào SCR-06.

&#x20; - \*Hỏi đáp AI:\* Vào SCR-07 -> Gửi câu hỏi -> AI hiển thị câu trả lời trích xuất từ ghi chú kèm thẻ nguồn dẫn.

\- \*\*Nhánh lỗi \& Phục hồi:\*\*

&#x20; - \*Lỗi đặt tên file:\* Cố tình đặt tên file trùng với mã đề cương của trường (ví dụ `PRM392.md`) -> Hệ thống cảnh báo đỏ và chặn lưu, gợi ý tự đổi thành `PRM392\_Note\_1.md`.

&#x20; - \*Lỗi mất mạng khi hỏi AI:\* Đang gửi câu hỏi thì mất kết nối -> Màn hình hiển thị trạng thái Error rõ ràng với nút "Thử lại" mà không làm mất nội dung câu hỏi vừa gõ trong ô nhập liệu.



\---



\## 3. Bảng Ánh xạ User Flow sang Màn hình (Screen Mapping Table)



Bảng đối chiếu chứng minh toàn bộ 8 màn hình trong kiến trúc thông tin đều được sử dụng trong ít nhất một User Flow, thỏa mãn tiêu chí chấm điểm Information Architecture:



| Mã Màn hình | Tên Màn hình (Screen Name) | Cấp bậc (Level) | Flow 1 (Tra cứu) | Flow 2 (Deadline \& Undo) | Flow 3 (Ghi chú \& AI) | Vai trò trong hệ thống |

| :--- | :--- | :---: | :---: | :---: | :---: | :--- |

| \*\*SCR-01\*\* | Dashboard Screen | Level 1 | \*\*X\*\* (Start) | \*\*X\*\* (Start) | \*\*X\*\* | Màn hình trung tâm, khởi đầu điều hướng |

| \*\*SCR-02\*\* | Syllabus Timeline Screen | Level 1 | \*\*X\*\* | | | Trực quan hóa 9 kỳ học và trạng thái môn |

| \*\*SCR-03\*\* | Course Details Screen | Level 2 | \*\*X\*\* (Goal) | | | Đề cương chi tiết: Slot học \& Đầu điểm thi |

| \*\*SCR-04\*\* | Tasks \& Deadline Screen | Level 1 | | \*\*X\*\* (Goal) | | Quản lý nhiệm vụ, lọc task \& thực thi Undo |

| \*\*SCR-05\*\* | Note Editor Screen | Level 2 | | \*\*X\*\* | \*\*X\*\* (Goal) | Soạn thảo Markdown, tạo task, chặn ghi đè |

| \*\*SCR-06\*\* | Course Notes \& Files Screen | Level 2 | \*\*X\*\* | | \*\*X\*\* (End) | Phân loại file FLM gốc vs User Note cá nhân |

| \*\*SCR-07\*\* | AI Tutor Chat Screen | Level 2 | | | \*\*X\*\* (Goal) | Trợ lý RAG tra cứu tri thức ngữ cảnh |

| \*\*SCR-08\*\* | FLM Sync \& Settings Screen | Level 1 | | | \*\*X\*\* (Config) | Quản lý session FLM, đồng bộ Vault ngoại tuyến |

