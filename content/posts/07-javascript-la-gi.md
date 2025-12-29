---
title: "JavaScript Là Gì? Giới Thiệu Cơ Bản"
description: "Tìm hiểu JavaScript – ngôn ngữ lập trình phía client phổ biến nhất thế giới, vai trò của nó trong web development và cách bắt đầu."
date: 2025-12-25
draft: false
tags: ["JavaScript", "Frontend", "Web Development"]
categories: ["JavaScript"]
---

JavaScript (thường viết tắt là **JS**) là một trong ba ngôn ngữ cốt lõi của web hiện đại (cùng với HTML và CSS). Đây là ngôn ngữ lập trình chạy trực tiếp trên trình duyệt, giúp tạo ra các trang web tương tác, động và sống động.

<grok-card data-id="f4afb6" data-type="image_card"  data-arg-size="LARGE" ></grok-card>


*<p style="text-align:center; font-size:0.9rem; opacity:0.8;">Logo chính thức của JavaScript</p>*

## JavaScript dùng để làm gì?

- **Thao tác với trang web**: Thay đổi nội dung, kiểu dáng mà không cần reload trang.
- **Xử lý sự kiện người dùng**: Click, scroll, nhập form, keyboard...
- **Giao tiếp với server**: Gửi/nhận dữ liệu qua AJAX/Fetch API (ví dụ: tải dữ liệu realtime).
- **Xây dựng ứng dụng web đầy đủ**: Với Node.js, JS còn chạy được phía server.

Ngày nay, hầu hết các website lớn (Facebook, Netflix, YouTube, Google) đều sử dụng JavaScript nặng nề.

## Cách JavaScript hoạt động trong trình duyệt

Trình duyệt có một **JavaScript Engine** (như V8 của Chrome) để biên dịch và thực thi code JS.

<grok-card data-id="2fd2ca" data-type="image_card"  data-arg-size="LARGE" ></grok-card>


*<p style="text-align:center; font-size:0.9rem; opacity:0.8;">Sơ đồ kiến trúc trình duyệt và cách JavaScript được thực thi</p>*

## Ví dụ đơn giản đầu tiên

```html
<!DOCTYPE html>
<html>
<head>
    <title>Hello JS</title>
</head>
<body>
    <h1 id="title">Chào mừng bạn!</h1>
    <button onclick="changeText()">Click tôi</button>

    <script>
        function changeText() {
            document.getElementById("title").innerText = "Bạn đã click nút!";
            alert("Hello from JavaScript!");
        }
    </script>
</body>
</html>