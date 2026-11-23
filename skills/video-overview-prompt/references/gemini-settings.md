# Cấu hình Video Overview và giới hạn của Gemini Notebook

Thông tin giao diện cập nhật đến tháng 11/2026. Gemini Notebook đổi giao diện thường xuyên: khi người dùng báo tên tuỳ chọn khác, làm theo giao diện họ đang thấy.

## 1. Format
| Format | Dùng khi |
|---|---|
| **Explainer** | mặc định cho bộ prompt này: giải thích có cấu trúc, đủ thời lượng cho một cụm nguyên lý |
| Short | không chọn: dạng dọc, khoảng 60 giây, chỉ nói được một ý |
| Cinematic | chỉ khi người dùng có gói Pro/Ultra và muốn hình ảnh điện ảnh hơn; nội dung vẫn theo prompt |

## 2. Visual Style
Danh sách hiện có gồm Whiteboard, Watercolor, Papercraft, Anime, Retro Print, Heritage… Nhắc người dùng kiểm tra lại danh sách trong giao diện.

| Nội dung | Gợi ý |
|---|---|
| Khoa học, kỹ thuật, toán, quy trình | **Whiteboard** (ưu tiên: nền sạch, sơ đồ và công thức rõ) |
| Văn học, lịch sử, văn hoá | Heritage hoặc Watercolor |
| Bài cho học sinh nhỏ tuổi, chủ đề nhẹ | Papercraft |
| Không chắc | Whiteboard |

Cả bộ video nên dùng chung một Visual Style để liền mạch.

## 3. Language
Tiếng Việt.

## 4. Giọng đọc
Giọng đọc tiếng Việt do hệ thống cố định. Prompt chỉ đổi được **văn phong** (cách xưng hô, từ ngữ gần gũi kiểu Nam Bộ), không đổi được giọng vùng miền. Luôn báo trước cho người dùng: giọng đọc có thể không phải giọng miền Nam.

## 5. Hạn mức
Gói miễn phí giới hạn khoảng **3 Video Overview mỗi ngày**. Bộ prompt có nhiều video hơn hạn mức thì nhắc người dùng và gợi ý lịch tạo: ví dụ 5 video → hôm nay Video 1–3, hôm sau Video 4–5.

## 6. Giới hạn không sửa được bằng prompt
Video Overview dựng **slide có hình minh họa và lời thuyết minh**, không dựng được hoạt hình chuyển động từng bước; hình do AI vẽ có thể sai chi tiết kỹ thuật. Prompt tốt làm video bớt chung chung rõ rệt, nhưng với nội dung cần thấy cơ chế vận hành thật, gợi ý thêm:
- hoạt hình do Claude dựng theo đúng nguyên lý;
- Manim cho nội dung toán, lý, hoá.
