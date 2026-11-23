<h1 align="center">FrameForge - Studio</h1>

Plugin cho Claude giúp làm video tiếng Việt. Gói plugin hiện có một skill: **videoOverviewPrompt** (prompt cho Video Overview của Gemini Notebook).

Phiên bản hiện tại: **0.2.0** · [Lịch sử thay đổi](CHANGELOG.md)

## Tính năng

- **Prompt Video Overview cho Gemini Notebook (videoOverviewPrompt):** từ bài ghi hoặc giáo án, soạn steering prompt để Gemini Notebook (NotebookLM) tạo video bài giảng: vai giảng viên, giọng miền Nam, đủ ý theo đề cương bài gốc, nhiều ví dụ minh họa; kèm gợi ý Format, Visual Style và Language.

## Cách dùng

Nói với Claude bằng ngôn ngữ tự nhiên; skill tự chạy khi bạn nhắc đến "videoOverviewPrompt", "prompt video", "video overview", "steering prompt" hoặc muốn làm video bài giảng bằng Gemini Notebook/NotebookLM.

| Yêu cầu | Kết quả |
|---|---|
| "Tạo prompt video overview cho bài ghi này" (kèm `.docx`/`.pdf` hoặc dán văn bản) | Steering prompt trong khối code và gợi ý cấu hình |

Dán prompt vào ô tùy chỉnh khi tạo Video Overview trong notebook đã có sẵn tài liệu nguồn.

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
