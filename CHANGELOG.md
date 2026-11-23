# Lịch sử phiên bản

Mỗi phiên bản là một commit gắn tag `vMAJOR.MINOR.PATCH` (bản thử nghiệm: `-beta.N`); số phiên bản cũng nằm trong `.claude-plugin/plugin.json` và README. Tag và bản phát hành do GitHub Actions tự tạo khi commit đổi phiên bản lên nhánh mặc định.

## 0.2.2
- Quy trình phát hành: khi không gắn được tag cho một commit cũ (GitHub không cho token của Actions tạo ref trỏ tới commit có workflow khác bản hiện tại), workflow thử tạo tag qua API, nếu vẫn không được thì báo cảnh báo và tiếp tục với các phiên bản còn lại thay vì dừng hẳn.
- Hỗ trợ secret tuỳ chọn `RELEASE_TOKEN` (PAT có quyền contents và workflows) để gắn tag cho mọi commit đổi phiên bản.

## 0.2.1
- Quy trình phát hành tự động (`.github/workflows/release.yaml`) làm lại theo SlideWright:
  - mỗi lần đẩy lên nhánh mặc định, mọi commit có đổi `version` trong `plugin.json` mà chưa có tag được gắn tag `vX.Y.Z`, kể cả các phiên bản cũ (0.1.0 → 0.2.0);
  - mỗi tag chưa có bản phát hành được đóng gói thành `frameforge-studio-X.Y.Z.plugin` và đăng lên mục Releases, ghi chú lấy từ mục tương ứng trong CHANGELOG;
  - vẫn phát hành được bằng cách đẩy tag tay: số phiên bản được đồng bộ vào `plugin.json`, README, CHANGELOG (tự sinh mục từ commit nếu chưa viết), commit `chore(release)` rồi dời tag;
  - không phụ thuộc tên nhánh `main`, dùng nhánh mặc định của kho; số phiên bản có hậu tố (`-beta.N`) được đánh dấu là bản thử nghiệm.

## 0.2.0
Thêm skill đầu tiên: **videoOverviewPrompt** (`video-overview-prompt`), chuyển từ skill cá nhân `gemini-notebook-video-prompt`.
- Biến bài ghi, giáo án (dán văn bản hoặc tải file) thành steering prompt cho Video Overview của Gemini Notebook (NotebookLM): vai giảng viên, giọng miền Nam, bám sát đề cương bài gốc, ví dụ minh họa phong phú, giải thích cặn kẽ.
- Kèm gợi ý cấu hình: Format (Explainer), Visual Style theo tính chất nội dung, Language (Tiếng Việt).

## 0.1.2
- Thêm quy trình phát hành tự động bằng GitHub Actions (`.github/workflows/release.yaml`): đẩy tag `vX.Y.Z` thì đồng bộ số phiên bản vào `plugin.json`, README, CHANGELOG (tự sinh mục từ commit nếu chưa viết), đóng gói tệp `.plugin` và đăng bản phát hành lên mục Releases.
- Số phiên bản có hậu tố (ví dụ `-beta.1`) tự được đánh dấu là bản thử nghiệm.

## 0.1.1
- Thêm README (giới thiệu, cài đặt, cấu trúc thư mục) và CHANGELOG.

## 0.1.0
- Khởi tạo plugin: manifest `.claude-plugin/plugin.json`, marketplace `.claude-plugin/marketplace.json`, `.gitignore`.
