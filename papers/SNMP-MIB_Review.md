\# Bài báo này có trọng tâm nghiên cứu là phát hiện các DoS flooding attacks cùng với Brute Force attacks.

Và phương pháp được đưa ra là tạo tập dữ liệu thu được trên môi trường thử nghiệm thật.



\## Các khái niệm cần tìm hiểu:

tập dữ liệu SNMP-MIB/ SNMP-MIB Dataset

các cuộc tấn công làm ngập lụt Từ chối dịch vụ (DoS)/ DoS flooding attacks

Giao thức Quản lý Mạng Đơn giản (SNMP)/ Simple Network Management 

Protocol (SNMP)

&#x20;Cơ sở Thông tin Quản lý (MIB)/  Management 

Information Base (MIB)

Brute Force attack

Interface, IP, TCP and ICMP

&#x20;Intrusion Detection System (IDS); IDS evaluation dataset

Network Anomaly

common Types of DoS Flooding Attack:

1\) TCP-SYN Attack

2\) UDP Flood Attack

3\) ICMP-ECHO Attack

4\) HTTP Flood Attack

5\) Slowloris Attack

6\) Slowpost Attack

User Datagram Protocol (UDP)



Trước hết, ta có thể hiểu DoS flooding attacks là các cuộc tấn công nhằm bơm một lượng thông tin rác khổng lồ làm tắc nghẽn hệ thống mạng, và để ngăn chặn các cuộc tấn công này thì ta có IDS để phát hiện các cuộc tấn công. Vấn đề được đặt ra ở đây là các dataset hiện có không đủ khả năng để mô tả lại các cuộc tấn công ngoài đời thực.

Và vì thế, mục tiêu của tác giả là tạo ra một tập dữ liệu toàn diện nhất, đó là SNMP-MIB dataset. Qua đó thì các nhà nghiên cứu khác có thể dùng chính dataset đó để phát triển các công cụ phát hiện xâm nhập một cách tốt nhất.



\# Nhap qua

Định nghĩ về SNMP-MIB dataset

SNMP: Là một giao thức lớp ứng dụng phổ biến dùng để cấu hình, quản lý và thu thập thông tin từ các thiết bị mạng (như máy tính, bộ chuyển mạch, máy chủ, bộ định tuyến)

MIB: Là một cơ sở dữ liệu đi kèm với SNMP, làm nhiệm vụ lưu trữ các thông số, trạng thái (hay còn gọi là các "biến đối tượng") của mạng. Khi mạng có hoạt động bất thường (như bị tấn công), các biến MIB cụ thể sẽ bị thay đổi.

=> Dataset SNMP-MIB: Đây là kết quả cuối cùng—một bộ dữ liệu gồm 4.998 bản ghi. Mỗi bản ghi ghi lại giá trị của 34 biến MIB quan trọng nhất tại một thời điểm nhất định để xem chúng biến động thế nào khi bị tấn công.



Các bước để tạp dataset:

Bước 1: Thiết lập môi trường mạng thực: Tác giả xây dựng một mạng cục bộ biệt lập với Internet để đảm bảo tính chân thực, bao gồm 1 bộ định tuyến (router), 2 bộ chuyển mạch (switches) và 2 mạng con. Mạng con thứ nhất có 1 máy tính đóng vai trò Attacker; mạng con thứ hai có 1 máy tính làm Victim.

Bước 2: Tạo lưu lượng mạng bình thường (Normal Traffic Generation): Sử dụng phần mềm LanTrafficV2 cài đặt trên các máy tính để tự động tạo ra các luồng dữ liệu (TCP, UDP, ICMP) qua lại giữa 2 mạng con. Lưu lượng bình thường được duy trì ở tốc độ lên tới 50 Mbps để giả lập một mạng đang hoạt động thực tế.

Bước 3: Phát động các cuộc tấn công: Máy Attacker sử dụng hàng loạt công cụ mã nguồn mở để tấn công máy Victim bằng các kịch bản khác nhau

Bước 4: Trong khi các cuộc tấn công đang diễn ra, một chương trình bằng ngôn ngữ Java sẽ "hỏi" bộ định tuyến cứ mỗi 15 giây một lần để chép lại 34 chỉ số MIB. Con số 15 giây được chọn vì nó đủ nhanh để bắt được dấu vết tấn công nhưng không làm máy móc bị quá tải.





