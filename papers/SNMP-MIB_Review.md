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

