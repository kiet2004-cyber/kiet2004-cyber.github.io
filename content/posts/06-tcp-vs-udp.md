---
title: "Xử Lý Nhiều Client Cùng Lúc Với Multithreading"
description: "Nâng cấp Server TCP để hỗ trợ nhiều Client kết nối đồng thời bằng cách sử dụng Thread trong Java."
date: 2025-12-25
draft: false
tags: ["Java", "Multithreading", "Socket", "Networking"]
categories: ["Java"]
---

Trong bài trước, chúng ta đã xây dựng một Server TCP đơn giản chỉ xử lý được **một Client** tại một thời điểm. Nếu Client thứ hai kết nối, nó phải chờ đến khi Client đầu tiên ngắt kết nối.

Bài này sẽ nâng cấp Server để hỗ trợ **nhiều Client đồng thời** bằng cách sử dụng **Multithreading** – một kỹ thuật rất quan trọng trong lập trình mạng.

![Minh họa Multithread Server](https://media.geeksforgeeks.org/wp-content/uploads/20220502163844/MultiThreadedServer-660x396.png)
*<p style="text-align:center; font-size:0.9rem; opacity:0.8;">Sơ đồ Server TCP đa luồng xử lý nhiều Client cùng lúc (Nguồn: GeeksforGeeks)</p>*

## Mục tiêu

- Server chấp nhận nhiều kết nối từ các Client.
- Mỗi Client được xử lý trong một **luồng riêng** (Thread).
- Server tiếp tục lắng nghe kết nối mới ngay cả khi đang xử lý Client cũ.

## Cách hoạt động

1. Server mở `ServerSocket` và chờ kết nối (vòng lặp vô hạn).
2. Khi một Client kết nối → tạo một Thread mới để xử lý Client đó.
3. Thread riêng: nhận tin nhắn từ Client, trả phản hồi, rồi đóng kết nối.
4. Server quay lại chờ Client mới.

## Code Server (Multithreaded)

```java
import java.io.*;
import java.net.*;

public class MultiThreadServer {
    public static void main(String[] args) {
        try (ServerSocket serverSocket = new ServerSocket(8080)) {
            System.out.println("Server đang chạy trên port 8080...");

            // Vòng lặp vô hạn để chấp nhận nhiều Client
            while (true) {
                Socket clientSocket = serverSocket.accept();
                System.out.println("Client mới đã kết nối!");

                // Tạo Thread mới để xử lý Client này
                new Thread(() -> handleClient(clientSocket)).start();
            }
        } catch (IOException e) {
            e.printStackTrace();
        }
    }

    // Hàm xử lý từng Client trong Thread riêng
    private static void handleClient(Socket clientSocket) {
        try {
            BufferedReader in = new BufferedReader(
                new InputStreamReader(clientSocket.getInputStream()));
            PrintWriter out = new PrintWriter(clientSocket.getOutputStream(), true);

            String message = in.readLine();
            if (message != null) {
                System.out.println("Nhận từ Client: " + message);
                out.println("OK - Server đã nhận: " + message);
            }

            clientSocket.close();
            System.out.println("Kết nối với Client đã đóng.");
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}