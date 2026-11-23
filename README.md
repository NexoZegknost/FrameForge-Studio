<h1 align="center">FrameForge - Studio</h1>

Plugin cho Claude giúp làm video tiếng Việt. Gói plugin hiện có một skill: **videoOverviewPrompt** (prompt cho Video Overview của Gemini Notebook).

Phiên bản hiện tại: **0.3.8** · [Lịch sử thay đổi](CHANGELOG.md)

## Tính năng

- **Bộ prompt Video Overview cho Gemini Notebook (videoOverviewPrompt):** từ bài ghi hoặc giáo án, soạn bộ steering prompt để Gemini Notebook (NotebookLM) tạo video bài giảng giải thích sâu nguyên lý, cơ chế:
  - chia bài thành các cụm nguyên lý, mỗi video một cụm, đánh số theo thứ tự xem;
  - mỗi video giải thích theo chuỗi cấu tạo → đầu vào → từng bước (kèm lý do) → kết quả → điều gì thay đổi khi đổi một yếu tố;
  - bắt buộc nêu quy trình, công thức, số liệu, hình vẽ của tài liệu; hướng dẫn hình minh họa kỹ thuật; chặn kiểu nói chung chung;
  - kèm gợi ý Format, Visual Style, Language, lưu ý giọng đọc và hạn mức tạo video mỗi ngày.

## Cách dùng

Nói với Claude bằng ngôn ngữ tự nhiên; skill tự chạy khi bạn nhắc đến "videoOverviewPrompt", "prompt video", "video overview", "steering prompt" hoặc muốn làm video bài giảng bằng Gemini Notebook/NotebookLM.

| Yêu cầu | Kết quả |
|---|---|
| "Tạo prompt video overview cho bài ghi này" (kèm `.docx`/`.pdf` hoặc dán văn bản) | Bảng kế hoạch bộ video, mỗi video một prompt trong khối code, gợi ý cấu hình |

Tải bài ghi lên làm nguồn của notebook trước, rồi tạo từng video theo thứ tự, mỗi lần dán một prompt vào ô tùy chỉnh của Video Overview.

## Cài đặt

**Claude Code**

```
/plugin marketplace add NexoZegknost/FrameForge-Studio
/plugin install frameforge-studio@frameforge-studio
```

**Ứng dụng Claude (Cowork):** tải tệp `.plugin` ở mục Releases của kho này, mở tệp và bấm chấp nhận.

Sau khi cài, mở một phiên trò chuyện mới để plugin được nạp.

## Cấu trúc

```
.claude-plugin/        manifest plugin và marketplace
skills/<skill-name>/   mỗi skill một thư mục (SKILL.md, references/, scripts/, assets/)
.github/workflows/      phát hành tự động (tag vX.Y.Z, tệp .plugin, Releases)
CHANGELOG.md           lịch sử phiên bản
```

## Lưu ý

- Báo lỗi hoặc góp ý qua mục Issues của kho.
