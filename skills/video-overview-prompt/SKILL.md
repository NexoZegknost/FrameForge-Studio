---
name: video-overview-prompt
description: Tạo bộ steering prompt cho tính năng Video Overview của Gemini Notebook (trước đây là NotebookLM) để làm video bài giảng giải thích sâu nguyên lý, cơ chế — chia bài thành các cụm nguyên lý, mỗi video một cụm theo chuỗi cấu tạo → đầu vào → từng bước → kết quả, bắt buộc nêu công thức, số liệu, thuật ngữ, hình vẽ của tài liệu, hướng dẫn hình minh họa kỹ thuật, chặn kiểu nói chung chung, văn phong giảng viên gần gũi kiểu Nam Bộ; kèm gợi ý Format, Visual Style, Language và lưu ý hạn mức. LUÔN dùng skill này khi người dùng đưa bài ghi, giáo án hoặc nội dung bài học chi tiết (dán văn bản hoặc tải file) và muốn tạo prompt cho video minh họa, làm video bài giảng bằng Gemini Notebook hoặc NotebookLM, hoặc nhắc "videoOverviewPrompt", "steering prompt", "video overview", "prompt video" — kể cả khi không nói từ "skill".
---

# videoOverviewPrompt — Bộ prompt Video Overview cho Gemini Notebook

Mục tiêu: biến một bài ghi, giáo án chi tiết thành **bộ steering prompt** dán vào ô tùy chỉnh khi tạo Video Overview, để video **giải thích được cách thức hoạt động và nguyên lý**, không nói chung chung. Mỗi prompt tạo **một video đi sâu vào một cụm nguyên lý**: video Explainer chỉ dài vài phút, ôm cả bài thì nội dung bị dàn mỏng. Viết **tiếng Việt chuẩn, đủ dấu**. Đường dẫn `references/` tính từ thư mục skill này (`${CLAUDE_PLUGIN_ROOT}/skills/video-overview-prompt/`; không có biến thì `find / -path "*video-overview-prompt/references/prompt-template.md" 2>/dev/null | head -1`).

Tạo danh sách công việc (task list) theo các bước để người dùng theo dõi.

| Tệp | Dùng ở bước |
|---|---|
| `references/anchor-extraction.md` | 2 — rút điểm neo |
| `references/series-planning.md` | 3 — chia cụm nguyên lý |
| `references/prompt-template.md` | 4 — khung prompt và chuỗi giải thích |
| `references/visual-guidelines.md` | 4 — khối hình minh họa |
| `references/gemini-settings.md` | 6, 7 — cấu hình, giọng đọc, hạn mức, giới hạn |

## Bước 1 — Lấy nội dung bài ghi
| Có gì | Làm |
|---|---|
| Văn bản dán trong chat | dùng luôn |
| `.docx` | đọc bằng skill docx |
| `.pdf` có lớp chữ | đọc bằng skill pdf |
| PDF quét, ảnh chụp | đọc từng trang dạng ảnh (OCR); hình vẽ trong trang ghi lại để mô tả ở Bước 2 |
| Định dạng khác (`.pptx`, `.md`, link) | đọc bằng skill hoặc công cụ tương ứng có trong phiên |

Không suy đoán nội dung khi chưa đọc xong file. Bài ghi quá sơ sài, không rút được đề cương và điểm neo rõ ràng thì hỏi lại người dùng thay vì tự bịa.

## Bước 2 — Trích xuất đề cương, chủ đề và điểm neo
Đọc kỹ bài ghi, xác định:
- Tên chủ đề / môn học chính (để điền vào vai "giảng viên [môn]")
- Đề cương các mục/luận điểm chính, theo đúng thứ tự trình bày trong bài ghi
- Các ví dụ/dẫn chứng đã có sẵn trong bài (nếu có), để prompt yêu cầu giữ lại và bổ sung thêm
- **Điểm neo bắt buộc giải thích** (cách rút: `references/anchor-extraction.md`):
  - quy trình, các bước vận hành;
  - công thức, định luật, quy tắc;
  - số liệu, thông số kỹ thuật;
  - hình vẽ, sơ đồ có sẵn trong tài liệu — mô tả lại bằng lời, vì Gemini Notebook có thể không đọc được hình trong file PDF quét.

  Giữ đúng tên gọi, ký hiệu, đơn vị như tài liệu và ghi kèm vị trí (mục, trang, số hình).

## Bước 3 — Chia bài thành các cụm nguyên lý
Mỗi cụm là **một nguyên lý, cơ chế hoặc quy trình hoàn chỉnh** mà một video vài phút giải thích trọn vẹn được. Quy tắc chia: xem `references/series-planning.md`. Tóm tắt:
- Một cụm = một cơ chế; không gộp hai cơ chế độc lập vào một video.
- Sắp theo **thứ tự xem**: khái niệm nền và cụm được cụm khác dùng lại đứng trước.
- Mỗi mục trong đề cương thuộc đúng một cụm; mục chỉ mang tính dẫn nhập thì ghép vào cụm đầu tiên dùng đến nó.
- Bài chỉ có một nguyên lý → một video; không chia nhỏ cho đủ số.
- Mỗi điểm neo gán vào cụm đầu tiên dùng đến nó.

## Bước 4 — Soạn prompt cho từng video
Mỗi cụm một prompt riêng, theo khung trong `references/prompt-template.md`, điền phần [ ] theo nội dung thực tế. Mỗi prompt phải có câu giới hạn phạm vi: **"Video này CHỈ giải thích [cơ chế X] trong tài liệu; bỏ qua các phần khác."**

Phần thân prompt đi theo **chuỗi giải thích năm bước**, không liệt kê tên mục:
1. Cấu tạo / các thành phần tham gia
2. Đầu vào (điều kiện ban đầu)
3. Từng bước biến đổi, kèm lý do vì sao diễn ra như vậy
4. Đầu ra / kết quả
5. Điều gì thay đổi nếu thay đổi một yếu tố (phản ví dụ, trường hợp đặc biệt)

Sau chuỗi giải thích, mỗi prompt có dòng **"Bắt buộc giải thích: …"** liệt kê các điểm neo của cụm.

Tiếp theo là khối **"Hình minh họa"** (chọn loại hình theo `references/visual-guidelines.md`): sơ đồ khối có mũi tên chỉ dòng chảy / chiều tác động, hình trạng thái trước và sau của mỗi bước, bảng so sánh khi có hai đối tượng trở lên, công thức kèm chú thích từng đại lượng và đơn vị; dùng đúng tên gọi, ký hiệu, số liệu trong tài liệu, không thay bằng hình tượng trưng.

Cuối prompt là khối **"Ràng buộc"** chặn kiểu nói chung chung:
- vào thẳng vấn đề sau tối đa 1–2 câu, không mở bài dài dòng;
- không dùng câu sáo rỗng ("đây là vấn đề rất quan trọng", "có vai trò to lớn");
- mỗi ý gắn với một chi tiết, số liệu hoặc thuật ngữ cụ thể lấy từ tài liệu;
- ví dụ là tình huống cụ thể có đối tượng, số liệu, kết quả, không viết kiểu "ví dụ như trong đời sống hằng ngày";
- giải thích nghĩa của mọi thuật ngữ ngay lần đầu xuất hiện.

Không chép nguyên văn bài ghi vào prompt: Gemini Notebook tự lấy nội dung chi tiết từ nguồn (source) đã có trong notebook. Prompt chỉ nêu phạm vi và cách giải thích.

## Bước 5 — Tự kiểm tra bộ prompt
Trước khi trình bày, rà từng prompt; mục nào chưa đạt thì sửa rồi mới đưa:
- [ ] Có câu "Video này CHỈ giải thích …; bỏ qua các phần khác", và chỉ một cơ chế.
- [ ] Đủ năm bước của chuỗi giải thích, không còn dấu [...] chưa điền; mỗi bước biến đổi có lý do.
- [ ] Dòng "Bắt buộc giải thích" có đủ điểm neo của cụm, đúng tên gọi, ký hiệu, số liệu, đơn vị như tài liệu.
- [ ] Khối "Hình minh họa" hợp với cụm (có bảng so sánh khi có hai đối tượng, có công thức khi cụm có công thức).
- [ ] Khối "Ràng buộc" giữ nguyên; bản thân prompt cũng không có câu sáo rỗng.
- [ ] Cả bộ phủ kín đề cương, mỗi mục thuộc đúng một video, thứ tự xem hợp lý.

## Bước 6 — Gợi ý cấu hình
Dùng chung cho cả bộ; chi tiết và lý do trong `references/gemini-settings.md`:
- **Format**: Explainer. Không chọn Short (dọc, khoảng 60 giây, chỉ một ý). Cinematic chỉ khi người dùng có gói Pro/Ultra.
- **Visual Style**: nội dung kỹ thuật, khoa học ưu tiên Whiteboard; văn học, lịch sử chọn Heritage hoặc Watercolor; không chắc thì Whiteboard. Nhắc người dùng kiểm tra lại danh sách trong giao diện.
- **Language**: Tiếng Việt.

## Bước 7 — Trình bày kết quả
Đưa cho người dùng:
1. Cách dùng: **tải bài ghi gốc lên làm nguồn (source) của notebook trước**, rồi tạo từng video theo thứ tự, mỗi lần dán một prompt vào ô tùy chỉnh của Video Overview. Prompt không chứa nội dung chi tiết, thiếu nguồn thì video không bám được tài liệu.
2. Bảng kế hoạch bộ video: số thứ tự, tên cụm, các mục đề cương thuộc cụm.
3. **Bộ prompt đánh số theo thứ tự xem**: mỗi video một khối code riêng, có tiêu đề `Video n/N — [tên cụm]` để copy dễ dàng.
4. Gợi ý cấu hình (Format, Visual Style kèm lý do ngắn gọn, Language).
5. Lưu ý ngắn:
   - giọng đọc tiếng Việt do hệ thống cố định, prompt chỉ đổi được văn phong, nên giọng có thể không phải giọng miền Nam;
   - bộ có nhiều hơn 3 video thì nhắc hạn mức khoảng 3 Video Overview/ngày của gói miễn phí và gợi ý chia ngày;
   - Video Overview chỉ dựng slide có hình và lời thuyết minh, không có hoạt hình từng bước; cơ chế cần thấy chuyển động thật thì gợi ý hoạt hình do Claude dựng hoặc Manim (toán, lý, hoá).
