---
title: "Mô Hình Client – Server Trong Lập Trình Mạng"
description: "Giải thích chi tiết mô hình Client-Server, vai trò của mỗi bên và cách hoạt động trong Java Networking."
date: 2025-12-25
draft: false
tags: ["Java", "Networking", "Client-Server"]
categories: ["Java"]

cover:
  # image: "/images/client-server-model.jpg"
  alt: "Mô hình Client-Server"
  caption: "Kiến trúc Client – Server cơ bản"
---

## Mô hình Client – Server là gì?

Mô hình Client – Server là kiến trúc phổ biến nhất trong lập trình mạng, trong đó:

- **Client**: Ứng dụng khởi tạo kết nối, gửi yêu cầu (request).
- **Server**: Ứng dụng lắng nghe kết nối, xử lý yêu cầu và trả về phản hồi (response).

## Cách hoạt động

1. Server khởi động và mở một port để lắng nghe.
2. Client kết nối đến địa chỉ IP + port của Server.
3. Sau khi kết nối thành công, hai bên có thể trao đổi dữ liệu.
4. Kết nối có thể duy trì lâu dài hoặc đóng sau mỗi lần giao tiếp.

## Ưu điểm

- Quản lý tập trung (Server kiểm soát dữ liệu và logic chính).
- Dễ mở rộng (thêm nhiều Client mà không ảnh hưởng Server).
- Bảo mật tốt hơn (Server kiểm soát truy cập).

## Ví dụ thực tế

- Trình duyệt web (Client) ↔ Web Server
- Ứng dụng chat (Client) ↔ Server chat
- Game online multiplayer

Bài tiếp theo sẽ đi sâu vào cách Java hiện thực hóa mô hình này qua **Socket TCP**.