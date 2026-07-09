# Hướng dẫn chạy dự án

## 1. Dự án này dùng gì?

- Đây là một **Hugo static site**.
- Theme đang dùng: `hugo-theme-learn`.
- Theme được quản lý qua **git submodule** tại `themes/hugo-theme-learn`.
- CI của dự án đang build bằng **Hugo Extended 0.134.3**.

## 2. Yêu cầu trước khi chạy

- Cài `git`
- Cài **Hugo Extended**

> Ghi chú: trong repo không có `package.json`, `yarn.lock`, `pnpm-lock.yaml` hay `go.mod`, nên dự án này **không cần npm / yarn / pnpm** để chạy.

## 3. Chuẩn bị source

Nếu bạn clone repo bằng git, hãy bảo đảm submodule được tải đầy đủ:

```powershell
git submodule update --init --recursive
```

## 4. Cài Hugo

### Một cách cài tham khảo trên Windows

```powershell
winget install --id Hugo.Hugo --exact --accept-source-agreements --accept-package-agreements
```

Sau đó kiểm tra lại:

```powershell
hugo version
```

> Lưu ý: CI đang dùng **Hugo Extended 0.134.3**, nên nếu cần đồng nhất tuyệt đối với môi trường deploy thì ưu tiên dùng đúng phiên bản này. Trong lần kiểm tra này, lệnh `winget` chưa cài xong thành công do lỗi quyền trên máy.

## 5. Chạy dự án ở môi trường local

Theo cấu hình hiện tại của repo, lệnh local phù hợp là:

```powershell
hugo server -D
```

Theo mặc định của Hugo, sau đó bạn có thể mở trình duyệt tại:

```text
http://localhost:1313
```

## 6. Build dự án

Lệnh build mà CI đang dùng là:

```powershell
hugo --minify
```

File build sẽ được tạo trong thư mục:

```text
public/
```

## 7. Những gì tôi đã xác nhận từ repo

- File cấu hình chính: `config.toml`
- Theme: `themes/hugo-theme-learn`
- Submodule: `.gitmodules`
- Workflow build/deploy: `.github/workflows/hugo.yml`
- Lệnh CI đang dùng: `hugo --minify`

## 8. Ghi chú về lần kiểm tra này

Trong môi trường kiểm tra hiện tại:

- `git` có sẵn
- `winget` có sẵn
- `hugo` ban đầu **chưa được cài**
- Đã thử cài Hugo bằng `winget`, nhưng bị lỗi quyền khi tạo symlink vào PATH
- Vì vậy, trong phiên kiểm tra này tôi **chưa xác minh được local serve/build chạy thành công bằng Hugo trên máy hiện tại**

Lỗi ghi nhận được:

```text
create_symlink: Access is denied.
```

Nếu bạn gặp lỗi tương tự trên Windows, hãy mở terminal bằng quyền phù hợp hoặc cài Hugo Extended theo cách thủ công từ trang release chính thức của Hugo, rồi chạy lại `hugo version` để xác nhận.
