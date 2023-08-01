---
{"dg-publish":true,"permalink":"/3-ressources/computer-science/networking/udp/","tags":["knowledge/computer-science/networking"],"created":"","updated":""}
---

# User Datagram Protocol
UDP is another transport layer protocol in the Internet Protocol Suite that operates alongside TCP. Unlike TCP, UDP is connectionless and provides a simple, best-effort, and unreliable data transmission service.

When data is sent using UDP, it is divided into small units called datagrams, which are then transmitted independently to the destination. Unlike TCP, UDP does not establish a connection before sending data or guarantee delivery, ordering, or error checking. This means that UDP is faster and has lower overhead compared to TCP.

UDP is commonly used in scenarios where real-time communication and low latency are crucial, and it is acceptable for some data loss or out-of-order delivery. Some applications that utilize UDP include:

1. Real-time video and audio streaming: UDP is often used for live streaming, video conferencing, and online gaming, where low latency is essential, and occasional loss of a few packets is acceptable.

2. DNS (Domain Name System): UDP is the primary protocol used for DNS queries, as DNS requests and responses are usually short and need quick resolution.

3. DHCP (Dynamic Host Configuration Protocol): UDP is used for DHCP client-server communication during the process of obtaining an IP address and network configuration.

4. IoT (Internet of Things) applications: UDP is employed in IoT devices, where speed and efficiency are prioritized over reliability.

5. Broadcasts and multicasting: UDP is used for sending data to multiple recipients simultaneously.

In summary, UDP sacrifices reliability and error-checking in favor of reduced latency and lower overhead, making it suitable for real-time applications and scenarios where data loss can be tolerated.