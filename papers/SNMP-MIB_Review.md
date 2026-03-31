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





Các nhà nghiên cứu đang gặp khó khăn do thiếu hụt các tập dữ liệu thực tế. Hầu hết các tập dữ liệu hiện có đều phụ thuộc vào các phương pháp tiếp cận dựa trên mô phỏng, vốn không thể thể hiện chính xác và đúng bản chất của các kịch bản xâm nhập và bất thường mạng. Ta có thể hiểu DoS flooding attacks là các cuộc tấn công nhằm bơm một lượng thông tin rác khổng lồ làm tắc nghẽn hệ thống mạng, và để ngăn chặn các cuộc tấn công này thì ta có IDS để phát hiện các cuộc tấn công. Vấn đề được đặt ra ở đây là các dataset hiện có không đủ khả năng để mô tả lại các cuộc tấn công ngoài đời thực.Vì vậy, việc tạo ra các tập dữ liệu thực tế là rất quan trọng vì nó cho phép đánh giá chính xác và thích hợp các kỹ thuật phát hiện



Thay vì soi xét từng gói tin (packet) siêu nhỏ, việc này cực kỳ tốn tài nguyên và làm chậm hệ thống. Nhóm tác giả chọn cách tiếp cận theo hướng thống kê thông qua SNMP và MIB.



SNMP Là giao thức tầng ứng dụng dùng để quản lý và giám sát các thiết bị mạng (Router, Switch, Server...).

\# Vai trò: Nó đóng vai trò thu thập thông tin từ các thiết bị, phát hiện các thông số bất thường



MIB Là một cơ sở dữ liệu nằm trong thiết bị mạng, lưu trữ các biến số phản ánh trạng thái của thiết bị đó.

\# Mỗi khi có một hoạt động bất kỳ, các biến số trong MIB sẽ thay đổi. Ví dụ: Nếu bị tấn công từ chối dịch vụ (DoS), số lượng gói tin ICMP hoặc lỗi IP sẽ tăng vọt.



\### Vậy thành quả của tác giả có thể hiểu là:


Thiết lập giải pháp khai thác dữ liệu thống kê từ SNMP-MIB để thay thế việc phân tích gói tin thô nặng nề. Họ đã tinh lọc và định danh bộ 34 biến MIB nhạy cảm nhất trong hàng ngàn biến số MIB có sẵn qua thuật toán đo độ lợi thông tin, giúp tối ưu hóa khả năng nhận diện tấn công đa tầng. Từ đó, nhóm xây dựng một mô hình thực nghiệm thực tế và bộ dữ liệu 4998 bản ghi chất lượng cao, chứng minh khả năng phát hiện xâm nhập một cách nhẹ nhàng và hiệu quả. Cuối cùng, nghiên cứu xác lập quy trình lấy mẫu 15 giây/lần là khoảng thời gian tối ưu để đảm bảo phát hiện nhanh các cuộc tấn công hiện đại mà không gây gánh nặng cho thiết bị mạng



Các bước để tạp dataset:

Bước 1: Thiết lập môi trường mạng thực: Tác giả xây dựng một mạng cục bộ biệt lập với Internet để đảm bảo tính chân thực, bao gồm 1 bộ định tuyến (router), 2 bộ chuyển mạch (switches) và 2 mạng con. Mạng con thứ nhất có 1 máy tính đóng vai trò Attacker; mạng con thứ hai có 1 máy tính làm Victim.

Bước 2: Tạo lưu lượng mạng bình thường (Normal Traffic Generation): Sử dụng phần mềm LanTrafficV2 cài đặt trên các máy tính để tự động tạo ra các luồng dữ liệu (TCP, UDP, ICMP) qua lại giữa 2 mạng con. Lưu lượng bình thường được duy trì ở tốc độ lên tới 50 Mbps để giả lập một mạng đang hoạt động thực tế.

Bước 3: Phát động các cuộc tấn công: Máy Attacker sử dụng hàng loạt công cụ mã nguồn mở để tấn công máy Victim bằng các kịch bản khác nhau

Bước 4: Trong khi các cuộc tấn công đang diễn ra, một chương trình bằng ngôn ngữ Java sẽ "hỏi" bộ định tuyến cứ mỗi 15 giây một lần để chép lại 34 chỉ số MIB. Con số 15 giây được chọn vì nó đủ nhanh để bắt được dấu vết tấn công nhưng không làm máy móc bị quá tải.



\### Cách thức hoạt động:



1\. Chiến lược theo dõi/ Hay Tại sao lại chọn 34 biến?

Tác giả chọn bộ định tuyến (router) làm điểm thu thập dữ liệu vì đây là nút giao thông chính mà mọi luồng dữ liệu đều phải đi qua.

Không có một thông số đơn lẻ nào đủ để phát hiện mọi loại tấn công.

Thay vì theo dõi toàn bộ hệ thống gây quá tải, tác giả chỉ chọn lọc ra 34 thông số (biến MIB) quan trọng và nhạy cảm nhất.

Phân bổ: 34 thông số này được chia vào 5 nhóm cốt lõi (Interface, IP, ICMP, TCP, UDP) nhằm bao quát mọi hoạt động của mạng, từ việc đếm dữ liệu ra/vào, định tuyến đường đi, cho đến ghi nhận các lỗi kết nối.

2\. Dấu hiệu nhận biết

Dữ liệu của 34 thông số này được đo bằng "bộ đếm 32" – tức là một dạng thông số chỉ cộng dồn liên tục tiến lên phía trước (từ 0 đến mức tối đa rồi mới quay vòng lại về 0).

Cách phát hiện kẻ tấn công: Các thông số này chịu ảnh hưởng trực tiếp từ lưu lượng truyền tải trên mạng. Ở trạng thái bình thường, các con số này sẽ tăng lên một cách đều đặn. Tuy nhiên, khi có các cuộc tấn công ngập lụt, kẻ gian sẽ bơm một lượng dữ liệu rác khổng lồ vào hệ thống. Hệ quả là các thông số đo lường này sẽ gia tăng với tốc độ đột biến. Bằng cách theo dõi tốc độ tăng bất thường của 34 thông số này, hệ thống có thể nhận diện được ngay khi nào mạng đang bị tấn công.





