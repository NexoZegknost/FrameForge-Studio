---
name: video-overview-prompt
description: >-
  Tạo 'steering prompt' (kèm gợi ý cấu hình Format và Visual Style) để dán vào
  tính năng Video Overview của Gemini Notebook (trước đây là NotebookLM), nhằm
  tạo video minh họa bài giảng - đóng vai giảng viên, giọng miền Nam, nội dung
  đầy đủ chi tiết bám sát bài ghi gốc, có ví dụ minh họa phong phú, giải thích
  cặn kẽ. LUÔN dùng skill này khi người dùng đưa một bài ghi, giáo án hoặc nội
  dung bài học chi tiết (dán văn bản hoặc tải file) và muốn tạo prompt cho
  video minh họa, làm video bài giảng bằng Gemini Notebook hoặc NotebookLM,
  hoặc nhắc đến 'videoOverviewPrompt', 'steering prompt', 'video overview', 'prompt video' - kể cả
  khi họ không dùng đúng từ 'skill'.
---

# videoOverviewPrompt — Tạo prompt Video Overview cho Gemini Notebook

## Mục đích
Biến một bài ghi/giáo án chi tiết thành một **steering prompt** hoàn chỉnh để dán vào ô tùy chỉnh khi tạo Video Overview trên Gemini Notebook, giúp video sinh ra: đóng vai giảng viên, nói giọng miền Nam, nội dung đầy đủ - chi tiết - bám sát bài gốc, có ví dụ minh họa phong phú, giải thích cặn kẽ.

## Quy trình

### Bước 1: Lấy nội dung bài ghi
- Nếu người dùng dán trực tiếp văn bản trong chat → dùng luôn nội dung đó.
- Nếu người dùng tải lên file (.docx, .pdf, ...) → dùng skill đọc file tương ứng (docx / pdf / file-reading) để trích xuất toàn bộ nội dung trước khi làm tiếp. KHÔNG suy đoán nội dung khi chưa đọc file.
- Nếu bài ghi quá sơ sài để rút ra đề cương rõ ràng, hỏi lại người dùng thay vì tự bịa nội dung.

### Bước 2: Trích xuất đề cương & chủ đề
Đọc kỹ bài ghi, xác định:
- Tên chủ đề / môn học chính (để điền vào vai "giảng viên [môn]")
- Đề cương các mục/luận điểm chính, theo đúng thứ tự trình bày trong bài ghi
- Các ví dụ/dẫn chứng đã có sẵn trong bài (nếu có), để prompt yêu cầu giữ lại và bổ sung thêm

### Bước 3: Soạn Steering Prompt
Viết theo khung cố định sau, điền phần [ ] theo nội dung thực tế, **giữ nguyên các yêu cầu bắt buộc** (vai giảng viên, giọng miền Nam, đầy đủ chi tiết, ví dụ phong phú, giải thích cặn kẽ):

```
Đóng vai một giảng viên [môn/lĩnh vực], hãy giải thích chi tiết về [tên chủ đề].

Yêu cầu:
- Trình bày bằng giọng miền Nam (Nam Bộ), văn phong gần gũi như một buổi giảng bài thực tế.
- Nội dung cần đầy đủ, chi tiết, bám sát toàn bộ các ý sau (không được bỏ sót):
  1. [luận điểm/mục 1]
  2. [luận điểm/mục 2]
  3. ...
- Với mỗi luận điểm, đưa ra ví dụ minh họa cụ thể, phong phú, dễ hình dung.
- Giải thích cặn kẽ, tránh rút gọn hay lướt qua, đảm bảo người xem hiểu vấn đề như đang đọc trọn bài ghi gốc.
```

Không chép nguyên văn toàn bộ bài ghi vào prompt — chỉ liệt kê đề cương/luận điểm chính, vì Gemini Notebook sẽ tự lấy nội dung chi tiết từ nguồn (source) đã có sẵn trong notebook. Giữ prompt gọn và rõ ràng.

### Bước 4: Gợi ý cấu hình khác
Luôn kèm theo prompt các gợi ý sau:
- **Format**: Explainer (không chọn Brief — vì cần chi tiết đầy đủ)
- **Visual Style**: chọn theo tính chất nội dung
  - Nội dung văn học/cảm xúc/lịch sử → Heritage hoặc Watercolor
  - Nội dung khoa học/kỹ thuật/logic → Whiteboard hoặc Classic
  - Không chắc → Whiteboard (phong cách giáo dục trung tính)
- **Language**: Tiếng Việt

### Bước 5: Trình bày kết quả
Đưa cho người dùng:
1. Đoạn prompt hoàn chỉnh trong khối code (để copy dễ dàng)
2. Gợi ý cấu hình (Format, Visual Style kèm lý do ngắn gọn, Language)
