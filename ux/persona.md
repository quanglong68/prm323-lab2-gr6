# User Personas · FPTU Second Brain Mobile

> Các hồ sơ được tách riêng theo PRM393 Persona Guideline. Tất cả hiện là **Proto-Persona**, không phải nghiên cứu đã xác thực. Dữ liệu chưa có nguồn được ghi rõ là giả định/chưa biết.

## Phạm vi sản phẩm

FPTU Second Brain Mobile giúp sinh viên tra cứu đề cương đã sync, quản lý deadline, ghi chú Markdown trong Obsidian Vault và hỏi AI khi có Internet. Figma hiện tập trung P02 với 8 màn hình Final UI và 3 prototype flow. P01/P03 được bổ sung theo yêu cầu giảng viên; đề xuất riêng chưa được xem là tính năng đã triển khai.

## Ba hồ sơ riêng

| Mã | Persona | Ưu tiên | Hồ sơ |
|---|---|---|---|
| P01 | Lê Hoàng Nam · năm nhất BBA, Kỳ 1 | Secondary · tìm hiểu học vụ, hình thành kế hoạch | [P01-le-hoang-nam.md](personas/P01-le-hoang-nam.md) |
| P02 | Nguyễn Minh Đức · năm ba SE, Kỳ 5 | Primary · tra cứu offline, deadline, note, AI | [P02-nguyen-minh-duc.md](personas/P02-nguyen-minh-duc.md) |
| P03 | Trần Thảo Vy · năm cuối Ngôn ngữ Anh, Kỳ 8–9 | Secondary · prerequisite, Capstone, phương án GPA | [P03-tran-thao-vy.md](personas/P03-tran-thao-vy.md) |

Mỗi file có 12 trường lõi, tuổi/vai trò, thói quen thiết bị, accessibility, scenario, success criteria và liên kết need → UI → test. Mục chưa có dữ liệu được ghi rõ. Xem [PRM393 Persona Guideline](https://prm393-material.web.app/persona-guideline).

## Coverage & khác biệt thiết kế

| Persona | Nhu cầu khác biệt | Định hướng UI/test | Phạm vi hiện tại |
|---|---|---|---|
| P01 | Hiểu đề cương/điều kiện môn và chia thời gian tự học khi mới vào FPTU | Onboarding có nguồn; lịch tuần có slot bận/khoảng trống; test tìm quy chế/lập lịch | Đề xuất, chưa nằm trong prototype |
| P02 | Tra cứu slot/deadline, ghi note và phục hồi khi offline/sync/AI lỗi | 8 màn hình và 3 flow; target M1–M4; usability test | Persona chính được Figma hiện tại phục vụ |
| P03 | Đối chiếu môn nợ/prerequisite và quyết định học cải thiện | Bảng tiến độ có nguồn; mô phỏng GPA với giả định rõ; test bằng dữ liệu đã xác minh | Đề xuất, chưa nằm trong prototype |

## Vấn đề sản phẩm

Sinh viên FPTU cần tìm đề cương, deadline và ghi chú học tập nhanh từ nhiều nguồn, thường trên điện thoại và có thể trong điều kiện mạng không ổn định. Phạm vi hiện tại giải quyết sâu workflow của sinh viên SE năm ba (P02); nhu cầu đầu/cuối hành trình được ghi nhận để định hướng nghiên cứu tiếp.

## P02 · mục tiêu usability (targets, chưa phải kết quả)

- **M1:** từ SCR-01 mở SCR-03 trong ≤8 giây và ≤3 chạm.
- **M2:** lưu note ở SCR-05 trong ≤15 giây.
- **M3:** 5/5 người thử hoàn tác hoặc xử lý lỗi sync đúng, không mất dữ liệu.
- **M4:** 5/5 hiểu lỗi kết nối AI và thử lại mà không mất câu hỏi.

## Evidence & assumption backlog

| Mã | Nội dung | Trạng thái / xác minh |
|---|---|---|
| SRC-01 | Mô tả P01/P03 do giảng viên cung cấp | Reported brief; chưa có interview/observation |
| SRC-02 | Scope, màn hình, luồng và giới hạn kỹ thuật trong project/Figma | Bằng chứng về thiết kế, không chứng minh hành vi người dùng |
| A-01 | Thiết bị, tần suất, workflow hiện tại P01/P03 | Chưa biết; phỏng vấn từng nhóm |
| A-02 | Tần suất 5–8 lần/ngày, 42 note, session timeout, xe bus/workaround của P02 | Chỉ coi là finding khi có nguồn research log xác nhận |
| A-03 | Accessibility cá nhân | Chưa biết; hỏi tự nguyện, không suy đoán từ baseline UI |
| A-04 | Quy chế điểm danh/PE/FE, prerequisite/GPA | Đối chiếu nguồn FPTU chính thức đúng ngành/khóa và ngày hiệu lực |

## Research backlog

1. Phỏng vấn/quan sát P01 về lần gần nhất tìm đề cương, hiểu quy chế và tự xếp lịch; hỏi thiết bị, công cụ, workaround.
2. Xác minh workflow FLM/LMS/Obsidian, mạng, tần suất và phục hồi lỗi của P02; ghi mã nghiên cứu ẩn danh, ngày, nguồn.
3. Phỏng vấn P03 về nguồn bảng điểm, prerequisite, GPA và ưu tiên tốt nghiệp/GPA; dùng dữ liệu mẫu nếu chưa được phép dùng dữ liệu cá nhân.
4. Chạy usability test; cập nhật success criteria từ số liệu thực, không báo target thành kết quả.

## Tài liệu liên quan

- [User flow](user-flow.md)
- [Screen specification](../design/screen-spec.md)
- [Design decisions & accessibility](../design/design-decisions.md)
