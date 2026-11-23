<h1 align="center">FrameForge - Studio</h1>

Plugin cho Claude giúp làm video tiếng Việt. Các skill trong gói được bổ sung dần theo từng phiên bản.

Phiên bản hiện tại: **0.1.2** · [Lịch sử thay đổi](CHANGELOG.md)

## Tính năng

Đang dựng khung, chưa có skill.

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
.github/workflows/      phát hành tự động khi đẩy tag vX.Y.Z
CHANGELOG.md           lịch sử phiên bản
```

## Lưu ý

- Báo lỗi hoặc góp ý qua mục Issues của kho.
