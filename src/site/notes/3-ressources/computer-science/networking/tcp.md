---
{"dg-publish":true,"permalink":"/3-ressources/computer-science/networking/tcp/","tags":["knowledge/computer-science/networking"],"created":"","updated":""}
---

# Transmission Control Protocol
TCP is a fundamental communication protocol used in computer networks to ensure reliable and ordered data transmission between devices. It operates at the transport layer of the Internet Protocol Suite and is responsible for establishing, maintaining, and terminating connections between two endpoints (typically applications running on devices).

TCP provides a connection-oriented, reliable, and error-checked data transfer mechanism. When data is sent over a TCP connection, it breaks it down into smaller packets and sends them separately. It also includes features for flow control, acknowledgment of received data, and retransmission of lost packets, ensuring that data arrives intact and in the correct order. If any packets are lost or corrupted during transmission, TCP will retransmit them to maintain data integrity.

This protocol's reliability and error-handling capabilities make it suitable for applications where data integrity is crucial, such as web browsing, email communication, file transfer, and other important data exchanges over the internet. However, the additional overhead of managing connections and ensuring reliability comes at the cost of some performance compared to UDP (User Datagram Protocol), another transport layer protocol that sacrifices reliability for reduced latency.