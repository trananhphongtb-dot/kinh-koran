# Kinh Koran — APK scaffold

App tra cứu + trắc nghiệm Kinh Koran đa ngữ (10 ngôn ngữ), đủ 114 surah / 6.236 câu,
đọc song song 2 ngôn ngữ, nghe tự động đọc, chạy offline.

- **App ID:** `com.tranphong.quran`
- **App name:** Kinh Koran
- **Version:** 1.0 (versionCode 1)
- **Web source:** bản web `kinh-koran` (đã xuất ra `www/index.html`, gồm cả mục Nghe
  và bản sửa đối chiếu mặc định tắt)
- **Keystore:** `keystore/quran-release.keystore` (alias `quran`, SHA-1
  `19:4E:D2:75:02:65:23:03:7C:63:8D:0A:F4:A4:A3:89:85:8C:4E:15`, hết hạn 2056).
  Mật khẩu trong `keystore/storepass.txt` / `keypass.txt` — KHÔNG đưa vào repo.
- **Repo GitHub:** `trananhphongtb-dot/kinh-koran` (public)

## Workflows

- `build-apk.yml` — push lên main → build debug APK (`quran-apk`).
- `build-aab.yml` — chạy tay (workflow_dispatch) → build + ký AAB (`quran-aab`),
  dùng 4 secrets: `KEYSTORE_BASE64`, `KEY_ALIAS` (= quran), `KEYSTORE_PASSWORD`,
  `KEY_PASSWORD`.

## Lưu ý phiên bản (bài học từ app Kinh Thánh)

Capacitor KHÔNG lấy versionName từ package.json — file `android/app/build.gradle`
sinh ra luôn có versionName mặc định `"1.0"`. Khi nâng phiên bản, sửa literal
trong sed của CẢ HAI workflow: sed luôn thay `"1.0"` (mẫu mặc định) thành
version mới, không nối chuỗi từ version cũ.
