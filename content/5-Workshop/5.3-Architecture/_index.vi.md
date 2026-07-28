---
title : "Kiến trúc"
date : 2026-06-26 
weight : 3
chapter : false
pre : " <b> 5.3. </b> "
---

#### Sơ đồ kiến trúc

Luồng dữ liệu và phát hiện bảo mật trong workshop được mô tả như sau:

<div style="text-align: center; margin: 20px 0;">
  <a href="architecture.vi.drawio" target="_blank">
    <img src="Screenshots/Architecture.drawio.png" alt="Sơ đồ kiến trúc" style="max-width: 100%; border: 1px solid #ddd; border-radius: 4px;" />
  </a>
  <br />
  <em>
    <a href="architecture.vi.drawio" target="_blank">Mở trong draw.io</a>
    &nbsp;|&nbsp;
    <a href="https://app.diagrams.net/?grid=0&pv=0&border=10&edit=_blank#create=%7B%22type%22%3A%20%22xml%22%2C%20%22compressed%22%3A%20true%2C%20%22data%22%3A%22%207Zrdb%2BI4FIB%2Fyz5EmnlolSuBx1xot9qZ1WphNTtPI5O4ibcmRo5TYH79%2BBYgBLpMiqYQFVU0x%2Bf4OPh8PrEdG05kOHerOTZs8xnSEpHCcGLDtq1bk3%2FzUlgkJEVFpor%2Fmd7dDIXCuTOcsWEGhhPNV48IQ26ak5Ips5SCJSLKQcOtPbg1lWdV2zbFnxOlCGQUzLlQgDlUtsGXCZcnMKkoYmt%2BGdAkRwwmrKJw30XtaL66p2CRfyYpxAcMajNKCDuq3vqKIBY9g1J1R7pLDPvu5%2Btaqu4CUFiwI%2B5e9PjbzY3oA9kpESZVKv6TggFUQMqvufqnb8rWIQK4anS69i90JVtjraOkKlIoqlqGEy5FLCYLkAjtknc6L8sZJ0mpU1DmG9uSUfIEI4IJla4cy%2FXHYbDRfEEpy7mGxzTkMOHasiAFFEX8Zx6qLMon%2Bv6sWkbfpehymaPHUAJwgFEmAGRE3CTQEoaPTNwB%2Fwmc709SiofbkqmwjoWfZNPNqp2EYAwWJZrJlnnPhguCCgbp%2BJkHt9RlG%2FwZXB1lwDoM8uHo3UMyh4yKsaA9upqhtfY20PJSdyiX%2FLoshyjLdbPDuiIoVUG2cX0q4dxG83Q6vIyB5EnS%2BoFUrEQpbCL9sSPHTovjPzMjGhihaYwtIwyNUYy4PjUixwhHPJmpn2ibf0h9IExsk2kh8AouJdLYFcavGQe7OHN2H4cJTJJDQ2I29FxPcMMTYYrglvjDg8CUn%2F8ZBPYvwnCTy9ZNLHcwdM0DGHpvQeE4Es4fipKBIoEdiXPbmXMOvpOi9r%2BHTJmDhbicrzLxeLoFy9K9pbAkFU3gQyIejyEX1VXTCiZ2G6Nx7Fsy%2Bi2MHuXnBC53MDk5W9mvw8QaOA1MDmWrYZuSuuyXUjLht2qGFU9XrCMi3nFEJs5phMxU%2B63w%2B0FgWYNrC7%2FjWlcT%2FofgM%2F%2F%2Bm%2BCuCWJwZGolHZ%2BUHUTbrcjHseO60bVF3rNGVxN5ORGZUoBwx8j7L02qtePzPR4S4ZVJr%2B2nhG95fnjtacIeXjAt9xWgaVzJ9WkXWIbHHxI7rs%2BHSyacpsJpT1LLPi2eecmTiu1mxu%2FVrCMyoyP5Zd%2F5%2BaAptedvOffbU258%2B4K5GacZ75yguYSW6NTLmS4gWWaLpBY1kLdcry4JZTnJSAHweFsaNlfDW5tPRO6fiML%2FIGNrHWBQMdKMPlwh9q%2FYM7k1B1r8uqOKV3o%2FRQrrWih4n6taXi1%2B3dVtq0lpWy8NKCVLLs4wSZ6mOSpU8R3C9R0BYVEDucenkDGYQRzyOGTyxx8iXm%2Beyri9tObmnS0HYGMfgwGaQbaz0OyAOYUYMPTcbP5ioJWrqw9LxEeabcru7Lr1Y1ktiKPNPk4lBq%2FYxwmiQrRUAvS2hHvvgO8D7vUScLV%2B7AS0fWFZeeS%2BQ7sP7aAH0OqJg%2BL11atey7kwbDulWrtH2LptbP0eYCunDoeoPc90or2xP83FNIK71rOKeCFeU29FsT%2F8JF8Wxe%2BTi7cE3usn8Hoqca487fUhT%2Fs9wnbQT2ybpCp6X7tbarXfqvyl1nd2IV%2Fgi8s4yTfLPlMu%2B57fV31vSrjfJnzYA8IbNOt9jXNs8FrtN0jT%2BhyLJw%2Bv5FoMnIV0MwDzhYyOaUSuMTIl%2B5ZkP0NKeB8BbzkChu0RMLqiESDNjpyZ1C6OHLuU2vp0Z31iVFaQh0ZlyQ8%3D%22%7D" target="_blank">Mở trong diagrams.net</a>
  </em>
</div>

#### Giải thích luồng kiến trúc

1. **Lỗ hổng đầu vào** - Kẻ tấn công hoặc người dùng khai thác các cấu hình sai trên EC2, S3, hoặc IAM (ví dụ: S3 public, SSH mở toàn cầu, IAM policy `*/*`).
2. **Ghi nhận** - AWS CloudTrail ghi lại tất cả các API calls, bao gồm cả những hành động độc hại hoặc trái phép.
3. **Phát hiện** - Amazon GuardDuty phân tích hành vi và nhật ký để phát hiện các mối đe dọa và bất thường.
4. **Tổng hợp & Đánh giá** - AWS Security Hub tổng hợp các phát hiện từ GuardDuty và tự động chấm điểm tuân thủ dựa trên CIS AWS Foundations Benchmark.

#### Các dịch vụ AWS sử dụng

| Dịch vụ | Vai trò |
|---------|---------|
| **AWS CloudTrail** | Ghi nhật ký API tập trung và kiểm toán |
| **Amazon GuardDuty** | Phát hiện mối đe dọa bằng ML và thông tin tình báo |
| **AWS Security Hub** | Tổng hợp phát hiện bảo mật và đánh giá tuân thủ |
| **Amazon S3** | Lưu trữ log CloudTrail và dữ liệu có thể bị lỗ hổng |
| **Amazon EC2** | Compute instances (với cấu hình sai ban đầu) |
| **AWS IAM** | Quản lý danh tính và truy cập (bao gồm role quá hạn) |