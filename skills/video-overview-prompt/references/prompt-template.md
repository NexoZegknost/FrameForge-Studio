# Khung prompt cho một video (một cụm nguyên lý)

Điền phần [ ] theo nội dung thực tế. Giữ nguyên các câu cố định.

```
Đóng vai một giảng viên [môn/lĩnh vực]. Video này CHỈ giải thích [tên nguyên lý/cơ chế]
trong tài liệu; bỏ qua các phần khác.

Cách giải thích (theo đúng thứ tự):
1. Cấu tạo: [các thành phần chính tham gia]
2. Đầu vào / điều kiện ban đầu: [...]
3. Diễn biến từng bước, mỗi bước nói rõ vì sao xảy ra:
   - Bước 1: [...]
   - Bước 2: [...]
4. Kết quả / đầu ra: [...]
5. Nếu thay đổi [yếu tố] thì điều gì xảy ra: [phản ví dụ, trường hợp đặc biệt]

Bắt buộc giải thích: [quy trình, công thức kèm ý nghĩa từng đại lượng, số liệu kèm đơn vị,
hình vẽ mô tả bằng lời — rút từ tài liệu, xem references/anchor-extraction.md]

Hình minh họa:
- Mỗi bước có sơ đồ khối với mũi tên chỉ chiều tác động, hoặc hình trạng thái trước/sau.
- [Bảng so sánh … khi có hai đối tượng trở lên.]
- Dùng đúng tên gọi, ký hiệu, số liệu trong tài liệu.
- Công thức hiển thị kèm chú thích từng đại lượng.

Yêu cầu:
- Trình bày bằng giọng miền Nam (Nam Bộ), văn phong gần gũi như một buổi giảng bài thực tế.
- Với mỗi bước, đưa ra ví dụ minh họa cụ thể, dễ hình dung.
- Giải thích cặn kẽ, tránh rút gọn hay lướt qua.
```

## Chuỗi giải thích năm bước
Danh sách tên mục khiến Gemini Notebook nói mỗi mục vài câu. Chuỗi cố định buộc video đi qua cơ chế từ đầu đến cuối:

| Bước | Điền gì | Lấy từ đâu |
|---|---|---|
| 1. Cấu tạo | các thành phần, bộ phận, đối tượng tham gia | phần mô tả, hình vẽ cấu tạo trong tài liệu |
| 2. Đầu vào | điều kiện ban đầu, trạng thái xuất phát, dữ kiện | giả thiết, điều kiện áp dụng |
| 3. Từng bước | mỗi bước một dòng, kèm **vì sao** bước đó xảy ra | phần trình bày quy trình, lập luận |
| 4. Đầu ra | kết quả, sản phẩm, trạng thái cuối | kết luận, công thức kết quả |
| 5. Thay đổi một yếu tố | điều gì khác đi nếu đổi một điều kiện; phản ví dụ, trường hợp đặc biệt | lưu ý, ngoại lệ, bài tập trong tài liệu; không có thì chọn yếu tố quan trọng nhất của bước 2 |

Điền bằng nội dung của tài liệu, không để trống dấu [...]. Bước nào tài liệu không có thì ghi "theo tài liệu" thay vì tự bịa.

**Bài không có cơ chế kỹ thuật** (văn học, lịch sử, xã hội) dùng chuỗi tương ứng: bối cảnh → nhân vật, lực lượng tham gia → diễn biến từng giai đoạn kèm nguyên nhân → kết quả → ý nghĩa, và điều gì khác đi nếu một điều kiện thay đổi.

Video sau trong bộ có thể thêm một câu nối: "Người xem đã biết [nội dung video trước], không giải thích lại."
