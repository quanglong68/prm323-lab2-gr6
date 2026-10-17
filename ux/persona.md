# UX RESEARCH: USER PERSONA & PROBLEM STATEMENT



---

## 1. Thông tin Chủ đề & Lý do Xác định Số lượng Persona

- **Tên dự án:** FPTU Second Brain Mobile
- **Chủ đề đăng ký:** Study Planner (Ứng dụng đồng hành quản lý lộ trình học tập theo đề cương FLM, hạn nộp bài và kho ghi chú Markdown ngoại tuyến cho sinh viên ngành Kỹ thuật Phần mềm — ĐH FPT).
- **Giả định kỹ thuật nền tảng:** Thư mục ghi chú Markdown (`Obsidian Vault`) và các file đề cương môn học (`FLM SYNC`) đã được đồng bộ sẵn giữa laptop và bộ nhớ trong của điện thoại (`/storage/emulated/0/Documents/Obsidian/FPTU`). Ứng dụng di động đóng vai trò đọc/ghi cục bộ trực tiếp trên thư mục này và gọi Gemini API khi có mạng.
- **Lý do xây dựng 01 Primary Persona (`P02`):**
  - Theo quy chuẩn Lab 2 (bài làm cá nhân), một Primary Persona cần xác định rõ nhóm người dùng và phạm vi tác vụ mà thiết kế cốt lõi phục vụ. P02 là nhóm **sinh viên SE tại FPTU đã có thói quen lưu trữ bài học bằng Markdown trên máy tính và cần công cụ đồng hành khi di chuyển bằng điện thoại**.
  - P01 và P03 được bổ sung theo yêu cầu giảng viên làm Secondary Personas để ghi nhận nhu cầu ở đầu/cuối hành trình học; các nhu cầu của họ chưa làm thay đổi phạm vi 8 màn hình và 3 prototype flow hiện tại, vốn tập trung vào P02.

---

## 2. Hồ sơ Primary Persona Chuẩn hóa (12 Trường Lõi & Chi tiết Bắt buộc Lab 2)

### Tóm tắt Định danh
- **Mã & Mức ưu tiên:** `P02 · Primary Persona` (Ưu tiên cao nhất — quyết định 100% kiến trúc thông tin và luồng tương tác cốt lõi).
- **Họ và tên giả định:** Nguyễn Minh Đức
- **Nhãn nhóm hành vi (Archetype):** *“Sinh viên SE tra cứu ngoại tuyến và ghi nhanh một tay khi di chuyển”*
- **Câu nói đại diện (Quote):**
  > *“Giữa hai ca học hoặc lúc đang đứng trên xe bus, mình chỉ có chưa tới một phút để xem hôm nay học slot mấy và tối nay có bài Lab nào đến hạn nộp trên LMS.”*


---

### Bảng 12 Trường Lõi (Core Fields theo PRM393 Persona Guideline)

| Trường (Field) | Nội dung chi tiết |
| :--- | :--- |
| **01. Identity & Archetype** | **Nguyễn Minh Đức** — Sinh viên năm 3 ngành Kỹ thuật Phần mềm (Học kỳ Fall 2024 - Kỳ 5), nhóm hành vi *“Học tập đa thiết bị, tra cứu ngoại tuyến và thao tác nhanh một tay khi di chuyển”*. |
| **02. Persona Priority** | **Primary Persona.** Mọi quyết định về cấu trúc điều hướng 4 tab, chế độ đọc Offline-first, vị trí nút ở vùng ngón cái và cơ chế hoàn tác (Undo) đều phục vụ trực tiếp cho P02. |
| **03. Usage Context** | - **Không gian & Thời gian:** Khi đang đứng/ngồi trên xe bus công cộng, đi bộ chuyển phòng giữa các ca học tại campus FPTU, hoặc 5 phút đầu giờ trong phòng lab.<br>- **Thiết bị:** Điện thoại Android màn hình phổ thông (~360–412 dp).<br>- **Sự chú ý:** Bị phân tán cao, môi trường rung lắc, thường chỉ cầm điện thoại bằng một tay, mỗi phiên mở app chỉ kéo dài **30–60 giây**. |
| **04. Goals** | - **G1 — Nắm cấu trúc và nội dung slot môn học:** Xem nhanh tiến độ slot (VD: `Slot 12/30`), nội dung từng buổi và các đầu điểm đánh giá (`Assignment`, `PT`, `PE`, `FE`) từ đề cương FLM đã lưu ngoại tuyến.<br>- **G2 — Tổng hợp công việc cần làm:** Gom toàn bộ deadline rải rác trong các file Markdown về một danh sách tập trung có phân loại *Quá hạn / Hôm nay / Sắp tới*.<br>- **G3 — Tra cứu ghi chú bài học:** Tìm lại nhanh kiến thức và tóm tắt môn học (như `PRM323`, `SWP391`) bằng bộ lọc môn hoặc hỏi Trợ lý AI có trích dẫn nguồn.<br>- **G4 — Ghi chép nhanh (Quick Capture):** Tạo nhanh ghi chú Markdown hoặc thêm đầu việc mới kèm hạn nộp ngay trên lớp chỉ với vài chạm. |
| **05. Job to Be Done (JTBD)** | - **JTBD 1 (Tra cứu & Deadline):** *“Khi đang di chuyển trên xe bus hoặc đổi phòng học với mạng 4G chập chờn, tôi muốn xem ngay nội dung slot học hôm nay và các bài Lab sắp hết hạn nộp mà không cần đăng nhập lại cổng trường, để chủ động chuẩn bị bài và không bị trễ deadline trên LMS.”*<br>- **JTBD 2 (Ghi nhanh & Hỏi AI):** *“Khi giảng viên vừa nhắc một lưu ý chấm điểm hoặc khi cần ôn nhanh kiến thức đã chép, tôi muốn ghi lại ngay bằng một tay hoặc đặt câu hỏi cho AI dựa trên chính kho Vault của mình, để tiết kiệm thời gian lục tìm từng file lẻ.”* |
| **06. Current Behaviors** | - Trên laptop: Ghi chép bài giảng và việc cần làm bằng cú pháp Markdown (`- [ ] Tên việc`) trong Obsidian Vault.<br>- Trên điện thoại (5–8 lần/ngày): Mở trình duyệt vào web FLM/LMS để xem lịch học và mở ứng dụng đọc file để dò tìm deadline.<br>- **Workaround hiện tại:** Chụp ảnh màn hình lịch học/deadline lưu vào thư viện ảnh hoặc tự nhắn tin cho chính mình trên Zalo/Telegram, dẫn đến thông tin bị trôi và phân mảnh. |
| **07. Pain Points** | 1. **Tra cứu đề cương FLM bất tiện trên mobile:** Web FLM nhiều bảng biểu nhỏ, không tối ưu màn hình dọc và liên tục hết phiên đăng nhập (session timeout) → *Hậu quả:* Tốn 2–3 phút chỉ để xem 1 slot học.<br>2. **Dễ bỏ sót hạn nộp bài (Deadline):** Các task nằm rải rác trong 42 file ghi chú của nhiều môn (`PRM323`, `SWP391`...) → *Hậu quả:* Quên nộp báo cáo Lab đúng hạn (23:59 trên LMS).<br>3. **Gián đoạn khi mất mạng:** Mạng 4G trên xe bus hoặc Wi-Fi phòng học chập chờn làm tê liệt các công cụ thuần đám mây → *Hậu quả:* Không xem được tài liệu và mất câu hỏi đang gõ cho AI.<br>4. **Chạm nhầm khi thao tác một tay:** Xe rung lắc dễ làm ngón cái bấm nhầm vào ô checkbox hoàn thành việc → *Hậu quả:* Mất dấu công việc quan trọng chưa làm. |
| **08. Motivations** | - **Tốc độ & Tức thời:** Mở app là thấy ngay hạn chót khẩn cấp và slot học hiện tại.<br>- **Kiểm soát & An tâm (Offline-first):** Dữ liệu nằm trong máy, đọc/ghi không phụ thuộc Internet.<br>- **An toàn thao tác:** Có lưới an toàn (Undo / Dialog xác nhận) khi bấm nhầm. |
| **09. Constraints** | - **Kỹ thuật & Quyền hạn:** App mobile chỉ đọc/ghi thư mục Vault cục bộ; không cào dữ liệu FLM trực tiếp (việc đồng bộ FLM thực hiện từ desktop).<br>- **Kết nối mạng:** Thường xuyên ngoại tuyến; tính năng Trợ lý AI (`Gemini 1.5 Flash`) bắt buộc cần mạng và API Key hợp lệ.<br>- **Công thái học:** Thao tác một tay bằng ngón cái trên màn hình 360–412 dp dưới ánh sáng ban ngày. |
| **10. Key Scenarios** | - **Tình huống 1 (Trên xe bus - Flow 1 & Flow 2):** 07:15 sáng trên xe bus đến trường, mạng 4G yếu (*Tác nhân*), Đức mở app bằng một tay để kiểm tra hạn nộp bài tập trong ngày và xem trước nội dung Slot 12 môn PRM323 (*Mục đích*). Đức thấy ngay cảnh báo `"Hoàn thiện Figma Prototype Lab 2 · Hôm nay 23:59"` trên `SCR-01`, lỡ tay chạm nhầm checkbox trên `SCR-04` nhưng bấm kịp `"HOÀN TÁC"` trên thanh Snackbar trong 8 giây, sau đó mở `SCR-03` xem đề cương ngoại tuyến (*Kết quả*).<br>- **Tình huống 2 (Tại lớp học - Flow 3 & Flow 1A):** Giảng viên vừa phổ biến tiêu chuẩn chấm điểm Lab 2 (*Tác nhân*), Đức mở `SCR-05` soạn nhanh checklist Markdown và bấm nút `"Lưu vào Vault"` ngay sát cạnh dưới màn hình (*Mục đích*). Khi cần ôn lại, Đức vào `SCR-07` hỏi AI và nhận câu trả lời trích dẫn trực tiếp từ đề cương `PRM323` (*Kết quả*). |
| **11. Success Criteria** | Hoàn thành các tác vụ cốt lõi được chứng minh qua 4 chỉ số đo lường định lượng **M1, M2, M3, M4** quy định chi tiết tại **Mục 5** bên dưới. |
| **12. Evidence & Status** | - **Phân loại:** `Proto-Persona` kết hợp quan sát định tính sơ bộ (chưa phải Statistical Persona diện rộng).<br>- **Cơ sở dữ liệu:** Tự quan sát quy trình học tập thực tế của tác giả tại kỳ 5 ngành SE ĐH FPT TP.HCM (`OBS-SELF-01`, 10/2026) và trao đổi nhanh với 3 sinh viên cùng lớp học môn PRM323 & SWP391 (`OBS-PEER-01..03`).<br>- **Giả định cần kiểm chứng thêm:** Tỷ lệ sinh viên duy trì cấu trúc thư mục Obsidian đồng nhất giữa laptop và điện thoại; ngưỡng thời gian 8 giây của thanh Snackbar Hoàn tác khi di chuyển thực tế. |

---

### Chi tiết Bắt buộc cho Lab 2 (Optional Details theo Guideline & Rubric)

1. **Độ tuổi & Vai trò:** 20 tuổi — Sinh viên năm 3 chuyên ngành Kỹ thuật Phần mềm (SE), Đại học FPT TP.HCM (đang học song song các môn đồ án và lập trình di động như `SWP391`, `PRM323`).
2. **Thói quen dùng thiết bị:** Dùng kết hợp Laptop (soạn thảo sâu, đồng bộ FLM) và Điện thoại Android (kiểm tra nhanh 5–8 lần/ngày, cầm một tay theo chiều dọc).
3. **Nhu cầu & Ràng buộc Trợ năng (Accessibility & Responsive Constraints):**
   - **Giao diện sáng (Light Theme chuẩn):** Nền sáng (`#F8FAFC` / `#FFFFFF`) chống lóa khi nhìn ngoài trời hoặc trên xe bus; độ tương phản màu đạt chuẩn **WCAG 2.1 AA** (tối thiểu **4.5:1** với văn bản thường và **3:1** với chữ lớn/điều khiển UI).
   - **Cỡ chữ & Hiển thị tiếng Việt:** Chữ nội dung tối thiểu **14 sp** (font `Inter`), chiều cao dòng thoáng để không cắt dấu tiếng Việt.
   - **Vùng chạm cảm ứng (Touch Target):** Mọi phần tử tương tác (nút bấm, checkbox hoàn thành việc, icon điều hướng, chip lọc) đạt tối thiểu **48 × 48 dp**; checkbox trên `SCR-04` tách rời khỏi vùng chạm mở file của dòng tối thiểu 8 dp để chống bấm nhầm.
   - **Ưu tiên vùng ngón cái (Thumb Zone):** Các hành động chính (Bottom Navigation 4 tab, nút `"Lưu vào Vault"` ở `SCR-05`, nút `"Hỏi trợ lý AI"` ở `SCR-03`, thanh Snackbar `"HOÀN TÁC"`) đều đặt ở nửa dưới màn hình.
   - **Không truyền đạt thông tin chỉ bằng màu sắc:** Mọi trạng thái hạn nộp và đồng bộ đều kết hợp **Icon + Nhãn chữ + Màu nền** (VD: `"Quá hạn · Hôm qua 23:59"`, `"Hôm nay · 23:59"`, `"Đã tải về"`, `"Đang ngoại tuyến"`).
   - **Co giãn đa kích thước (Responsive):** Bố cục dùng Auto Layout (`Fill container`), đảm bảo hiển thị không tràn chữ trên cả chiều rộng **360 dp** và **412 dp**.

---

## 2A. Persona Bổ sung theo yêu cầu giảng viên

> **Phạm vi:** P02 · Nguyễn Minh Đức vẫn là Primary Persona mà 8 màn hình và 3 prototype flow hiện tại phục vụ. P01 và P03 là Secondary Personas để mở rộng nghiên cứu và định hướng sản phẩm; các tính năng đặc thù bên dưới là đề xuất, chưa được xem là chức năng đã triển khai trong Figma/prototype.
>
> **Chất lượng bằng chứng:** Thông tin P01/P03 dưới đây được tổng hợp từ yêu cầu persona do giảng viên cung cấp, chưa có phỏng vấn hoặc kiểm chứng người dùng. Các hành vi/động lực chưa được cung cấp được ghi rõ là giả định cần xác thực.

### P01 · Sinh viên năm nhất — Lê Hoàng Nam

**Tóm tắt định danh**

- **Mã & mức ưu tiên:** `P01 · Secondary Persona`.
- **Họ tên giả định:** Lê Hoàng Nam, 18 tuổi.
- **Archetype:** *“Sinh viên mới cần biến quy chế và đề cương thành kế hoạch học tập dễ hiểu”*.
- **Quote giả lập:** *“Em biết mình có nhiều môn phải học, nhưng chưa rõ xem đề cương ở đâu và nên chia thời gian tự học thế nào.”* (Câu minh họa, không phải trích dẫn phỏng vấn.)

| Trường (Field) | Nội dung chi tiết |
| :--- | :--- |
| **01. Identity & Archetype** | Lê Hoàng Nam, 18 tuổi, sinh viên năm nhất ngành Quản trị Kinh doanh (BBA), Kỳ 1. Vừa qua định hướng/tiếng Anh dự bị; còn bỡ ngỡ với cách tổ chức học tập tại FPTU. |
| **02. Persona Priority** | **Secondary Persona.** Đại diện nhóm sinh viên mới; giúp đánh giá khả năng giải thích thông tin học vụ và lập kế hoạch. Không thay đổi trọng tâm của prototype hiện tại vốn được thiết kế cho P02. |
| **03. Usage Context** | Bắt đầu kỳ đầu tiên, cần làm quen với FLM, thời khóa biểu theo slot, yêu cầu điểm danh và quy chế PE/FE. Thiết bị, thời điểm, tần suất và điều kiện mạng chưa được cung cấp; cần xác thực trước khi dùng làm tiêu chí thiết kế chi tiết. |
| **04. Goals** | Hiểu nơi tìm đề cương FLM và cách đọc trọng số/điều kiện qua môn; lập lịch tự học thực tế cho khoảng 5–6 môn đại cương. |
| **05. Job to Be Done (JTBD)** | *“Khi bắt đầu kỳ học và chưa quen quy trình FPTU, tôi muốn hiểu yêu cầu của từng môn và nhìn thấy thời gian rảnh trong tuần, để biết cần học gì và sắp xếp việc tự học.”* |
| **06. Current Behaviors** | Đề bài cho biết Nam vừa trải qua định hướng/tiếng Anh dự bị và chưa có thói quen xếp lịch tự học. Công cụ đang dùng, cách tra cứu FLM và cách quản lý thời gian cụ thể chưa có dữ liệu; không suy diễn thành hành vi đã quan sát. |
| **07. Pain Points** | Không biết tìm đề cương FLM ở đâu; chưa hiểu cách tính trọng số và điều kiện qua môn; khó tự chia lịch cho 5–6 môn đại cương cùng lúc. |
| **08. Motivations** | Mong muốn hiểu kỳ học mới, tránh bỏ sót yêu cầu quan trọng và hình thành thói quen tự học. Đây là suy luận từ pain point, cần phỏng vấn để xác thực. |
| **09. Constraints** | Kiến thức về quy trình và quy chế FPTU còn mới. Tư vấn điểm/điều kiện qua môn phải dựa trên nguồn chính thức, có thời điểm hiệu lực; tích hợp FAP/FLM cần quyền truy cập và dữ liệu được xác nhận. |
| **10. Key Scenarios** | Đầu kỳ: chọn một môn, mở đề cương và tìm phần đánh giá/điều kiện qua môn. Đầu tuần: xem thời khóa biểu đã xác nhận, tìm khung giờ trống và tạo lịch tự học. |
| **11. Success Criteria** | Bản nháp mục tiêu kiểm thử: người dùng tìm được đề cương và xác định đúng điều kiện qua môn từ nguồn trích dẫn; lập được lịch tự học tuần dựa trên thời khóa biểu thật. Ngưỡng thời gian/tỷ lệ hoàn thành cần được xác lập sau usability test. |
| **12. Evidence & Status** | **Proto-Persona**, dựa trên mô tả giảng viên cung cấp trong yêu cầu bổ sung; chưa có transcript phỏng vấn, dữ liệu FAP/FLM hoặc kiểm chứng quy chế. Các giả định cần kiểm chứng: công cụ hiện dùng, mức độ hiểu FLM, lịch học thực tế và nhu cầu nhận tư vấn điểm. |

**Nhu cầu tính năng chuyên biệt (đề xuất, chưa triển khai):**

- **Tư vấn môn học/kỳ học:** giải thích cách đọc trọng số và quy tắc qua môn bằng ngôn ngữ dễ hiểu. Ví dụ ngưỡng điểm trong đề bài chỉ được hiển thị như nội dung có nguồn chính thức và ngày hiệu lực, không hard-code thành lời khuyên AI không kiểm chứng.
- **Gợi ý lịch tự học:** đề xuất khoảng trống từ thời khóa biểu FAP do người dùng cung cấp hoặc kết nối được cấp quyền; cho phép sửa/xác nhận trước khi tạo lịch.

### P03 · Sinh viên năm cuối — Trần Thảo Vy

**Tóm tắt định danh**

- **Mã & mức ưu tiên:** `P03 · Secondary Persona`.
- **Họ tên giả định:** Trần Thảo Vy, 22 tuổi.
- **Ngành theo mô tả giảng viên:** Thiết kế Mỹ thuật số (GD) / Ngôn ngữ Anh, Kỳ 8–9. Cần xác nhận một ngành cụ thể nếu đây là hồ sơ người dùng thật; giữ nguyên mô tả gộp từ yêu cầu hiện tại.
- **Archetype:** *“Sinh viên cuối khóa cần rà điều kiện tốt nghiệp và chọn phương án cải thiện GPA”*.
- **Quote giả lập:** *“Trước khi làm Capstone, mình muốn biết còn thiếu môn tiên quyết nào và học cải thiện môn nào sẽ có ích nhất.”* (Câu minh họa, không phải trích dẫn phỏng vấn.)

| Trường (Field) | Nội dung chi tiết |
| :--- | :--- |
| **01. Identity & Archetype** | Trần Thảo Vy, 22 tuổi, sinh viên năm cuối Kỳ 8–9; ngành được cung cấp là GD / Ngôn ngữ Anh (cần làm rõ một ngành). Đang chuẩn bị Capstone và xét điều kiện tốt nghiệp. |
| **02. Persona Priority** | **Secondary Persona.** Đại diện nhu cầu rà soát chương trình học cuối khóa. Các nhu cầu này định hướng nghiên cứu tương lai, không hàm ý prototype hiện có đã kết nối bảng điểm hoặc khung chương trình. |
| **03. Usage Context** | Trước Capstone hoặc khi chuẩn bị xét tốt nghiệp, cần đối chiếu tiến độ đã học với khung chương trình và điều kiện môn tiên quyết. Thiết bị, cách theo dõi hiện tại và thời điểm cụ thể chưa được cung cấp. |
| **04. Goals** | Xác định môn còn nợ/rớt; biết môn tiên quyết nào phải hoàn tất trước Capstone; cân nhắc môn nên học cải thiện để nâng GPA. |
| **05. Job to Be Done (JTBD)** | *“Khi chuẩn bị Capstone và xét tốt nghiệp, tôi muốn đối chiếu kết quả học tập với khung chương trình và thử các phương án học lại/cải thiện, để biết bước tiếp theo mà không bỏ sót điều kiện.”* |
| **06. Current Behaviors** | Đề bài cho biết Vy đang cần nhớ/nhận diện môn nợ, môn tiên quyết và phương án cải thiện GPA. Nguồn tra cứu hiện tại, quy trình kiểm tra và cách tính GPA chưa được mô tả; cần phỏng vấn để xác thực. |
| **07. Pain Points** | Khó nhớ môn nào bị nợ/rớt; không chắc môn tiên quyết nào bắt buộc phải qua trước khóa luận; không biết học cải thiện môn nào có lợi nhất cho GPA. |
| **08. Motivations** | Hoàn tất Capstone, đáp ứng điều kiện ra trường và đưa ra lựa chọn học tập có căn cứ. Sự ưu tiên tương đối giữa tốt nghiệp đúng hạn và GPA cần xác thực. |
| **09. Constraints** | Cần bảng điểm chính xác, khung chương trình đúng ngành/khóa và quy tắc tiên quyết/GPA hiện hành. Dữ liệu học tập nhạy cảm; cần người dùng cấp quyền, xem nguồn tính toán và tự xác nhận trước khi dựa vào kết quả. |
| **10. Key Scenarios** | Trước đăng ký Capstone: so sánh bảng điểm với khung chương trình để phát hiện môn tiên quyết còn thiếu. Trước đăng ký kỳ tiếp theo: mô phỏng một số lựa chọn học lại/cải thiện và xem tác động dự kiến đến GPA. |
| **11. Success Criteria** | Bản nháp mục tiêu kiểm thử: người dùng nhận diện đúng môn còn thiếu từ dữ liệu và khung chương trình đã xác minh; hiểu giả định và kết quả của từng kịch bản GPA. Các ngưỡng chính xác cần thống nhất với quy chế chính thức và usability test. |
| **12. Evidence & Status** | **Proto-Persona**, dựa trên mô tả giảng viên cung cấp; chưa có transcript, bảng điểm mẫu hoặc xác minh khung chương trình. Giả định cần kiểm chứng: ngành/khóa cụ thể, cách tính GPA, dữ liệu hệ thống có thể truy cập và mức độ ưu tiên của từng mục tiêu. |

**Nhu cầu tính năng chuyên biệt (đề xuất, chưa triển khai):**

- **Prerequisite Check:** đối chiếu bảng điểm do người dùng cung cấp/ủy quyền với khung chương trình đúng ngành và khóa; nêu rõ môn thiếu, nguồn dữ liệu và quy tắc đối chiếu.
- **Mô phỏng học lại/cải thiện GPA:** cho phép thử các kịch bản với quy tắc tính GPA đã xác minh, trình bày giả định và kết quả dự kiến; không khẳng định thay cho cố vấn học tập hoặc hệ thống chính thức.

---

## 3. Phát biểu Vấn đề (Problem Statement)

> Sinh viên ngành Kỹ thuật Phần mềm FPTU khi học nhiều môn chuyên ngành thường tốn nhiều thời gian tìm kiếm lại đề cương, hạn nộp bài và nội dung ghi chép do thông tin phân tán trên cổng FLM/LMS và nhiều file Markdown cá nhân, trong khi thời gian tra cứu giữa các tiết học rất ngắn (30–60 giây), thao tác chủ yếu bằng một tay trên điện thoại và trong điều kiện kết nối mạng không ổn định.

---

## 4. Từ Persona đến Quyết định Thiết kế & Giả thuyết Thử nghiệm

Bảng dưới đây chuyển hóa trực tiếp các nhu cầu và rào cản của `P02 · Nguyễn Minh Đức` thành các quyết định thiết kế cụ thể trên 8 màn hình Figma:

| Nhu cầu / Vấn đề của P02 | Ý tưởng / Quyết định thiết kế để thử nghiệm | Màn hình & Component áp dụng | Cách kiểm chứng (Validation) |
| :--- | :--- | :--- | :--- |
| **G1 / Pain Point 1 & 3:** Xem lịch slot và đầu điểm khi mạng yếu, không muốn đăng nhập lại FLM. | Lưu đề cương dưới dạng file cục bộ trong Vault; hiển thị rõ huy hiệu `"Đã tải về"` và banner `"Đang ngoại tuyến"` nhưng vẫn cho đọc đủ 3 tab *Lịch slot · Đánh giá · Tổng quan*. | `SCR-02_Roadmap`, `SCR-03_CourseDetail` (`CourseCard`, `Badge`, Banner Offline) | Đo thời gian và số lần chạm để mở đề cương môn `PRM323` từ Trang chủ (**Tiêu chí M1**). |
| **G2 / Pain Point 2:** Dễ quên hạn nộp bài Lab nằm rải rác trong nhiều file. | Đưa khối `"Hạn chót khẩn cấp"` lên đầu `SCR-01` và gom nhóm `"Khẩn cấp & Quá hạn"` lên đầu `SCR-04` kèm nhãn chữ + thời gian cụ thể. | `SCR-01_Home`, `SCR-04_Tasks` (`TaskItem`, `Badge`) | Quan sát khả năng nhận diện ngay bài tập quá hạn/hôm nay trong 5 giây đầu mở app. |
| **Pain Point 4:** Rung lắc trên xe bus dễ chạm nhầm ô hoàn thành việc hoặc bấm nhầm nút đồng bộ. | Tách vùng chạm checkbox (48×48 dp); hiển thị Snackbar `"Đã hoàn thành"` kèm nút `"HOÀN TÁC"` trong 8 giây (không bị FAB che); thêm Dialog xác nhận `D-01` trước khi quét/đồng bộ lại Vault. | `SCR-04_Tasks` (`SN-01`), `SCR-08_SyncVault` (`D-01_SyncConfirmation`, `SCR-08_SyncError`) | Test kịch bản chạm nhầm và phục hồi lỗi trên Prototype (**Tiêu chí M3**). |
| **G4 / Constraint công thái học:** Soạn nhanh ghi chú bằng một tay, không với ngón cái lên góc trên màn hình. | Đặt thanh công cụ Markdown và nút chính `"Lưu vào Vault"` cố định ở cạnh đáy màn hình (`SCR-05`); tự động lưu nháp vào Vault cục bộ. | `SCR-05_NoteEditor` (`Button`, `SyncStatus`, Bottom Action Bar) | Đo thời gian tạo mới hoặc cập nhật ghi chú kèm checklist (**Tiêu chí M2**). |
| **G3 / Pain Point 3:** Cần hỏi AI về môn học nhưng hay mất mạng hoặc lỗi truy cập. | Hiển thị rõ model `Gemini 1.5 Flash`, thẻ trích dẫn nguồn đề cương `PRM323`, và banner cảnh báo `"Mất kết nối Internet"` kèm nút `"Thử lại"` giữ nguyên câu hỏi. | `SCR-06_Notes`, `SCR-07_AskAI`, `SCR-08_SyncVault` (`ErrorState`, Citation Card) | Kiểm tra khả năng người dùng hiểu nguyên nhân lỗi mạng/Vault và bấm phục hồi (**Tiêu chí M4**). |

---

## 5. Tiêu chí Thành công Đo được (Measurable Target Metrics)

Các tiêu chí dưới đây là thước đo định lượng khi kiểm thử khả năng sử dụng (Usability Testing) trên Figma Prototype với 5 sinh viên thuộc nhóm Persona P02:

1. **M1 — Tốc độ tra cứu thông tin môn học (Mô phỏng ngoại tuyến):** Từ màn hình chính (`SCR-01`), người thử nghiệm mở được chi tiết môn học (`SCR-03`) để xem tiến độ slot và đầu điểm đánh giá của một môn bất kỳ trong **≤ 8 giây** và qua **không quá 3 lần chạm**.
2. **M2 — Tốc độ tạo/lưu ghi chú và công việc mới:** Người thử nghiệm hoàn thành thao tác mở trình soạn thảo (`SCR-05`), kiểm tra/nhập nội dung checklist bài tập môn học và bấm `"Lưu vào Vault"` trong **≤ 15 giây**.
3. **M3 — Khả năng phục hồi thao tác nhầm lẫn (Undo & Recovery):** **5/5 người thử nghiệm** thực hiện hoàn tác thành công một tác vụ vừa lỡ tay đánh dấu hoàn thành thông qua thanh thông báo (`Snackbar` hiển thị **8 giây**), hoặc xử lý đúng hộp thoại xác nhận (`D-01`) và nút `"Thử lại"` khi gặp lỗi đồng bộ Vault (`SCR-08_SyncError`).
4. **M4 — Nhận diện và phục hồi sự cố kết nối AI:** **5/5 người thử nghiệm** hiểu rõ nguyên nhân khi mất kết nối mạng lúc hỏi trợ lý AI (`SCR-07`) — biết rằng vẫn tra cứu được 42 ghi chú ngoại tuyến — và biết cách chạm `"Thử lại"` để tiếp tục mà không làm mất câu hỏi đã gõ.
