---
title: "DOM Và Event Cơ Bản Trong JavaScript"
description: "Hướng dẫn thao tác với DOM (Document Object Model) và xử lý sự kiện người dùng bằng JavaScript thuần, không cần thư viện."
date: 2025-12-25
draft: false
tags: ["JavaScript", "DOM", "Event", "Frontend"]
categories: ["JavaScript"]
---

Sau khi hiểu **JavaScript** là gì, chúng ta sẽ đi sâu vào phần quan trọng nhất khiến trang web trở nên **tương tác**: **DOM** và **Event**.

DOM giúp JavaScript "nhìn thấy" và thay đổi cấu trúc HTML, còn Event giúp bắt các hành động của người dùng như click, nhập liệu...

<grok-card data-id="00f4b6" data-type="image_card"  data-arg-size="LARGE" ></grok-card>


*<p style="text-align:center; font-size:0.9rem; opacity:0.8;">Cấu trúc cây DOM của một trang HTML đơn giản (Nguồn: W3Schools)</p>*

## DOM là gì?

**Document Object Model** (Mô hình Đối tượng Tài liệu) là cách trình duyệt biểu diễn trang HTML dưới dạng **cây đối tượng**.

- Mỗi thẻ HTML là một **node** (nút).
- JavaScript có thể truy cập, thêm, sửa, xóa các node này.

Ví dụ: Thẻ `<h1>` trở thành một object mà bạn có thể thay đổi nội dung.

## Các phương thức DOM phổ biến

| Phương thức                  | Mô tả                                      | Ví dụ |
|------------------------------|--------------------------------------------|-------|
| `document.getElementById()`  | Lấy phần tử theo ID                        | `document.getElementById("title")` |
| `document.querySelector()`   | Lấy phần tử đầu tiên khớp CSS selector     | `document.querySelector(".button")` |
| `element.innerHTML`          | Đọc/ghi nội dung HTML bên trong            | `element.innerHTML = "<strong>Mới</strong>"` |
| `element.textContent`        | Đọc/ghi chỉ text (an toàn hơn)             | `element.textContent = "Hello"` |
| `element.style.property`     | Thay đổi CSS inline                        | `element.style.color = "red"` |
| `document.createElement()`   | Tạo phần tử mới                            | `let btn = document.createElement("button")` |

<grok-card data-id="49bb87" data-type="image_card"  data-arg-size="LARGE" ></grok-card>


*<p style="text-align:center; font-size:0.9rem; opacity:0.8;">Ví dụ trước/sau khi thao tác DOM (Nguồn: Medium)</p>*

## Event là gì và cách xử lý

**Event** là các sự kiện xảy ra trên trang: click chuột, nhấn phím, load trang, submit form...

JavaScript có thể **lắng nghe** (listen) và **phản hồi** các event này.

### Cách thêm Event Listener

```javascript
// Cách hiện đại (khuyến nghị)
element.addEventListener("click", function() {
    alert("Bạn đã click!");
});

// Hoặc dùng arrow function
element.addEventListener("click", () => {
    console.log("Click rồi!");
});