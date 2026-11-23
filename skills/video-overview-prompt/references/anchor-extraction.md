# Rút điểm neo bắt buộc giải thích

Đề cương chỉ cho biết bài nói về gì. **Điểm neo** là những chi tiết cụ thể mà video bắt buộc phải nêu và giải thích; thiếu chúng, video chỉ nói được ý chung.

## 1. Bốn loại điểm neo
| Loại | Rút gì | Ví dụ |
|---|---|---|
| Quy trình | các bước vận hành theo đúng thứ tự, điều kiện chuyển bước | "Kỳ nạp → kỳ nén → kỳ nổ → kỳ xả" |
| Công thức, định luật, quy tắc | biểu thức đầy đủ, ý nghĩa và đơn vị từng đại lượng, điều kiện áp dụng | "η = 1 − 1/ε^(γ−1); ε là tỉ số nén, không đơn vị" |
| Số liệu, thông số | giá trị kèm đơn vị và ngữ cảnh | "tỉ số nén xăng 8 – 12, diesel 14 – 22" |
| Hình vẽ, sơ đồ | mô tả lại bằng lời: có những khối nào, nối với nhau ra sao, chiều mũi tên, nhãn | "Hình 2.3: piston nối thanh truyền, thanh truyền nối trục khuỷu; mũi tên chỉ piston đi xuống ở kỳ nạp" |

Hình vẽ phải được mô tả lại bằng lời trong prompt, vì Gemini Notebook có thể không đọc được hình trong file PDF quét hoặc ảnh chụp.

## 2. Cách rút
1. Đọc hết tài liệu, đánh dấu mọi quy trình, công thức, số liệu, hình vẽ.
2. Giữ **đúng tên gọi, ký hiệu, đơn vị** như trong tài liệu; không đổi sang ký hiệu khác, không làm tròn số.
3. Ghi kèm vị trí (mục, trang, số hình) để người dùng đối chiếu.
4. Gán mỗi điểm neo vào cụm nguyên lý dùng đến nó (Bước 3 của skill). Một điểm neo dùng ở nhiều cụm thì giải thích ở cụm đầu, các cụm sau chỉ nhắc lại.
5. Không bịa điểm neo: tài liệu không có công thức thì không thêm công thức.

## 3. Đưa vào prompt
Mỗi prompt có một dòng liệt kê điểm neo của cụm:

```
Bắt buộc giải thích: [quy trình …]; [công thức … (ý nghĩa từng đại lượng)]; [số liệu … kèm đơn vị]; [hình … mô tả bằng lời].
```

Cụm có nhiều điểm neo thì xuống dòng, mỗi điểm neo một gạch đầu dòng.
