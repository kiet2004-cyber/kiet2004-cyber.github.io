---
title: "Java Socket TCP Là Gì?"
description: "Giải thích rõ ràng về Socket trong Java, sự khác biệt giữa ServerSocket và Socket, và cách TCP đảm bảo truyền dữ liệu đáng tin cậy."
date: 2025-12-25
draft: false
tags: ["Java", "Socket", "TCP", "Networking"]
categories: ["Java"]

cover:
  # image: "/images/java-socket-tcp.jpg"
  alt: "Java Socket TCP"
  caption: "Socket TCP trong Java"
---

## Socket là gì?

Socket là điểm cuối (endpoint) của một kết nối mạng hai chiều giữa hai chương trình.

Trong Java:
- `ServerSocket`: Dùng phía Server để chờ kết nối từ Client.
- `Socket`: Dùng phía Client để kết nối, hoặc phía Server sau khi accept kết nối.

## TCP là gì và tại sao quan trọng?

TCP (Transmission Control Protocol) là giao thức hướng kết nối, đảm bảo:

- Dữ liệu đến đúng thứ tự
- Không mất gói tin
- Kiểm soát lưu lượng (flow control)
- Xử lý lỗi tự động

Phù hợp cho các ứng dụng cần độ tin cậy cao: chat, tải file, web...

## Cấu trúc cơ bản

```java
// Server
ServerSocket server = new ServerSocket(8080);
Socket clientSocket = server.accept(); // Chờ client kết nối

// Client
Socket socket = new Socket("127.0.0.1", 8080);