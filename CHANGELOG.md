# Lịch sử phiên bản

Mỗi phiên bản là một commit gắn tag `vMAJOR.MINOR.PATCH` (bản thử nghiệm: `-beta.N`); số phiên bản cũng nằm trong `.claude-plugin/plugin.json` và README.

## 0.1.2
- Thêm quy trình phát hành tự động bằng GitHub Actions (`.github/workflows/release.yaml`): đẩy tag `vX.Y.Z` thì đồng bộ số phiên bản vào `plugin.json`, README, CHANGELOG (tự sinh mục từ commit nếu chưa viết), đóng gói tệp `.plugin` và đăng bản phát hành lên mục Releases.
- Số phiên bản có hậu tố (ví dụ `-beta.1`) tự được đánh dấu là bản thử nghiệm.

## 0.1.1
- Thêm README (giới thiệu, cài đặt, cấu trúc thư mục) và CHANGELOG.

## 0.1.0
- Khởi tạo plugin: manifest `.claude-plugin/plugin.json`, marketplace `.claude-plugin/marketplace.json`, `.gitignore`.
