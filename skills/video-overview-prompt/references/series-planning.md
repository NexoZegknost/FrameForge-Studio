# Chia bài thành bộ video theo cụm nguyên lý

Video Explainer của Gemini Notebook chỉ dài vài phút. Yêu cầu một video "bám sát toàn bộ các ý, không bỏ sót" thì mỗi ý chỉ được vài câu, video nói chung chung. Vì vậy mỗi video chỉ đi sâu vào **một cụm nguyên lý**.

## 1. Cụm nguyên lý là gì
Một cụm là một nguyên lý, cơ chế hoặc quy trình hoàn chỉnh, có:
- các thành phần tham gia,
- điểm bắt đầu (đầu vào, điều kiện ban đầu),
- diễn biến qua các bước,
- kết quả (đầu ra).

Ví dụ với bài "Động cơ đốt trong 4 kỳ": cụm 1 — cấu tạo và các bộ phận chính; cụm 2 — chu trình 4 kỳ; cụm 3 — hệ thống đánh lửa và nhiên liệu; cụm 4 — hiệu suất và các yếu tố ảnh hưởng.

## 2. Quy tắc chia
1. **Một cụm, một cơ chế.** Hai cơ chế độc lập thì tách hai video, kể cả khi bài ghi trình bày chung một mục.
2. **Thứ tự xem.** Cụm nền (khái niệm, cấu tạo) và cụm được cụm khác dùng lại đứng trước. Video sau được phép nhắc "như video trước" nhưng không giải thích lại.
3. **Phủ kín đề cương.** Mỗi mục trong đề cương thuộc đúng một cụm. Mục dẫn nhập, lịch sử, ý nghĩa ghép vào cụm đầu tiên hoặc cụm cuối, không thành video riêng nếu quá mỏng.
4. **Độ dày vừa một video.** Cụm có nhiều hơn khoảng 6 bước biến đổi hoặc 3 công thức chính thì cân nhắc tách tiếp; cụm chỉ một hai câu thì ghép với cụm liền kề.
5. **Không chia cho đủ số.** Bài chỉ có một nguyên lý thì một video.

## 3. Bài không có cơ chế kỹ thuật
Bài văn học, lịch sử, xã hội: cụm là **một luận điểm hoặc một sự kiện** trọn vẹn (một tác phẩm, một giai đoạn, một vấn đề). Quy tắc 2 – 5 giữ nguyên.

## 4. Đầu ra của bước này
Bảng kế hoạch trình cho người dùng cùng bộ prompt:

| Video | Tên cụm | Mục đề cương thuộc cụm |
|---|---|---|
| 1/N | [...] | [...] |
