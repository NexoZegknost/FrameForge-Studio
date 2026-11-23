# Hướng dẫn hình minh họa

Prompt không nói gì về hình thì Gemini Notebook tự vẽ hình trang trí cho đẹp, không bám kỹ thuật. Mỗi prompt cần một khối **"Hình minh họa"** chỉ rõ loại hình cho từng bước của chuỗi giải thích.

## 1. Chọn loại hình theo nội dung
| Nội dung | Loại hình yêu cầu |
|---|---|
| Dòng chảy, truyền động, chuỗi tác động | sơ đồ khối có mũi tên chỉ chiều dòng chảy / chiều tác động |
| Một bước biến đổi | hình trạng thái **trước và sau** của bước đó, đặt cạnh nhau |
| Hai hay nhiều đối tượng, phương án, giai đoạn | bảng so sánh, mỗi cột một đối tượng, mỗi hàng một tiêu chí |
| Công thức | công thức hiển thị đầy đủ, chú thích từng đại lượng và đơn vị |
| Số liệu theo thời gian, theo điều kiện | biểu đồ có trục, đơn vị, giá trị lấy từ tài liệu |
| Cấu tạo | hình cắt hoặc sơ đồ cấu tạo có nhãn tên từng bộ phận |
| Văn học, lịch sử | trục thời gian, sơ đồ quan hệ nhân vật/lực lượng, trích dẫn nguyên văn |

## 2. Quy tắc chung
- Dùng **đúng tên gọi, ký hiệu, số liệu trong tài liệu**; không thay bằng hình ảnh tượng trưng (bóng đèn, bánh răng chung chung, người đang suy nghĩ…).
- Hình vẽ có sẵn trong tài liệu: yêu cầu vẽ lại theo mô tả bằng lời đã rút ở điểm neo.
- Mỗi bước của chuỗi giải thích có ít nhất một hình; hình phải đổi theo bước, không lặp một hình cho cả video.
- Nhãn trên hình bằng tiếng Việt, ký hiệu giữ nguyên như tài liệu.

## 3. Khối đưa vào prompt
```
Hình minh họa:
- Mỗi bước có sơ đồ khối với mũi tên chỉ chiều tác động, hoặc hình trạng thái trước/sau.
- [Bảng so sánh … khi có hai đối tượng trở lên.]
- Dùng đúng tên gọi, ký hiệu, số liệu trong tài liệu; không dùng hình tượng trưng.
- Công thức hiển thị kèm chú thích từng đại lượng và đơn vị.
```
Chỉ giữ những dòng hợp với cụm; thêm dòng riêng cho hình quan trọng của cụm (ví dụ "vẽ lại Hình 2.3 theo mô tả: …").
