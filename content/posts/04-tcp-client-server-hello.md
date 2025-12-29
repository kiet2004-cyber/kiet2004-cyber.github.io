---
title: "Xây Dựng TCP Client – Server Đơn Giản Với Java"
description: "Hướng dẫn từng bước xây dựng ứng dụng TCP cơ bản: Client gửi tin nhắn, Server nhận và trả lời."
date: 2025-12-25
draft: false
tags: ["Java", "Networking", "Socket", "TCP"]
categories: ["Java"]
---

Trong bài này, chúng ta sẽ xây dựng một ứng dụng TCP Client-Server đơn giản nhất để hiểu rõ cách giao tiếp mạng trong Java: Client gửi "Hello", Server nhận và trả về "OK".

![Mô hình TCP Client-Server cơ bản](https://scaler.com/topics/images/tcp-ip-ports-and-sockets.webp)
*<p style="text-align:center; font-size:0.9rem; opacity:0.8;">Sơ đồ minh họa Client kết nối đến Server qua Socket</p>*

## Mục tiêu

- Server lắng nghe trên port 8080
- Client kết nối và gửi tin nhắn
- Server nhận tin, xử lý và trả phản hồi

## Code Server

```java
import java.io.*;
import java.net.*;

public class TcpServer {
    public static void main(String[] args) throws IOException {
        ServerSocket serverSocket = new ServerSocket(8080);
        System.out.println("Server đang chạy trên port 8080...");

        Socket clientSocket = serverSocket.accept();
        System.out.println("Client đã kết nối!");

        BufferedReader in = new BufferedReader(
            new InputStreamReader(clientSocket.getInputStream()));
        PrintWriter out = new PrintWriter(clientSocket.getOutputStream(), true);

        String message = in.readLine();
        System.out.println("Nhận từ Client: " + message);

        out.println("OK - Server đã nhận: " + message);

        clientSocket.close();
        serverSocket.close();
        System.out.println("Kết nối đã đóng.");
    }
}