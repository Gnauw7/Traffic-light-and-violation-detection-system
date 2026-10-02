# Hệ Thống Đèn Giao Thông và Phát Hiện Vi Phạm Vượt Đèn Đỏ Sử Dụng IC Số

<br>
<div align="center">
  <img width="100%" alt="real-circuit" src="https://github.com/user-attachments/assets/34bc7113-d394-4c1c-a609-1f43ba9830c4" />
</div>
<br> 

Đây là một dự án thiết kế phần cứng số, bao gồm việc mô phỏng và chế tạo một hệ thống đèn giao thông cơ bản được tích hợp bộ đếm ngược và cơ chế cảnh báo vi phạm. Điểm nổi bật của dự án là toàn bộ mạch được thiết kế hoàn toàn bằng các IC số cơ bản, **không sử dụng bất kỳ vi điều khiển hoặc bo mạch Arduino nào**.

Clip demo
https://youtube.com/shorts/TPbXV9Gl-JE

## 🎯 Các Tính Năng Chính

* **Điều khiển tự động** chu kỳ hoạt động của đèn giao thông (Xanh - Vàng - Đỏ).
* **Hiển thị thời gian đếm ngược** cho từng pha bằng LED 7 đoạn.
* **Cảnh báo vi phạm vượt đèn đỏ:** Tích hợp cảm biến hồng ngoại (IR) để phát hiện chuyển động. Cảm biến này được thiết kế về mặt logic để *chỉ kích hoạt hệ thống cảnh báo trong giai đoạn đèn đỏ*.

## ⚙️ Nguyên Lý Hoạt Động

<br>
<div align="center">
  <img width="853" height="653" alt="Block Diagram" src="https://github.com/user-attachments/assets/2dc94270-c066-41cf-9f5b-e3899bd4839e" />
</div>
<br>

* **Khối Tạo Xung & Đếm:** Xung vuông được tạo ra từ bộ định thời NE555 được đưa vào chân clock của IC 74192. IC 74192 thực hiện việc đếm và xuất ra mã BCD (Binary-Coded Decimal – mã thập phân mã hóa nhị phân).
* **Khối Hiển Thị:** Mã BCD được đưa qua IC 74247 để giải mã, kéo các chân tương ứng xuống mức LOW nhằm điều khiển LED 7 đoạn, từ đó hiển thị giá trị đếm ngược.
* **Khối Cảm Biến Phát Hiện Vi Phạm:** Để đảm bảo cảm biến chỉ kích hoạt cảnh báo khi phương tiện vượt đèn đỏ, tín hiệu đầu ra của cảm biến IR và tín hiệu pha đèn đỏ (từ chân Q0 của IC 4017) được đưa qua cổng logic AND (IC 7408). Vì vậy, cổng AND đảm bảo điều kiện logic chính xác: chỉ khi Đèn Đỏ đang BẬT (Logic 1) **VÀ** cảm biến phát hiện chuyển động (Logic 1), còi/đèn cảnh báo mới được kích hoạt.

## 🛠️ Các Linh Kiện Phần Cứng

Hệ thống sử dụng các IC cơ bản thuộc dòng 74LS/HC và CMOS:

* **Module NE555:** Đóng vai trò là bộ tạo xung clock cho hệ thống.
* **IC CD4017:** Bộ đếm Johnson 10 trạng thái, được sử dụng để đếm và điều khiển quá trình chuyển đổi giữa các pha đèn.
* **IC 74147:** Bộ mã hóa ưu tiên 10 ngõ vào sang 4 ngõ ra.
* **IC 74192:** Bộ đếm BCD tăng/giảm (được sử dụng cho bộ đếm ngược).
* **IC 74247:** Bộ giải mã/điều khiển từ BCD sang LED 7 đoạn (loại Anode chung).
* **IC 7404:** IC gồm 6 cổng đảo (NOT), được sử dụng để đảo mức logic.
* **IC 7408:** IC gồm 4 cổng AND 2 đầu vào, được sử dụng để khóa/mở điều kiện kích hoạt cảm biến.
* **Cảm Biến Hồng Ngoại (IR):** Phát hiện các vật thể đang di chuyển.
* **LED:** Bao gồm LED 7 đoạn và các LED đơn màu (Đỏ, Vàng, Xanh).

## 💻 Công Cụ & Kết Quả Thực Tế

<br>
<div align="center">
  <img width="100%" alt="Proteus Simulation" src="https://github.com/user-attachments/assets/516f00b7-d4f4-4c95-aafa-cbeab9d27daf" />
</div>
<br>

* **Phần Mềm Thiết Kế & Mô Phỏng:** Sơ đồ nguyên lý của hệ thống đã được thiết kế và mô phỏng thành công bằng **Proteus**.
* **Phần Cứng Thực Tế:** Đã hoàn thành thiết kế layout PCB, in mạch, bố trí linh kiện và hàn mạch.
* **Kết Quả:** Mạch phần cứng hoạt động đúng theo chu kỳ đã thiết kế, chuyển đổi giữa các pha chính xác, LED 7 đoạn hiển thị rõ ràng và cảm biến phát hiện hành vi vượt đèn đỏ hoạt động ổn định.

<br>
<div align="center">
  <img width="100%" alt="Final Hardware" src="https://github.com/user-attachments/assets/16da6a4c-0b7b-4b51-b2aa-f0a46b32004d" />
</div>
<br>

## 👥 Thành Viên Thực Hiện

*Dự án này được thực hiện bởi các sinh viên thuộc Trường Đại học Khoa học Tự nhiên, ĐHQG-HCM (Nhóm L):*

* Võ Thái Minh Triều (23130249)
* Nguyễn Thị Kiều Trang (23130248)
* Lê Quốc Thịnh (23130236)
* Đinh Việt Quang (23130212)
