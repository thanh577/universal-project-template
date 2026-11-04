# Universal Project Template

Bộ khung nền tảng có thể tái sử dụng cho các dự án phần mềm, không phụ thuộc vào ngôn ngữ lập trình hoặc công nghệ cụ thể.

## Giới thiệu

Universal Project Template cung cấp cấu trúc khởi đầu thống nhất cho dự án phần mềm, kết hợp Hermes Agent, Spec Kit, Git và các nguyên tắc kỹ thuật có thể tùy chỉnh theo từng dự án.

## Thành phần

- **Spec Kit:** Phát triển phần mềm theo phương pháp đặc tả trước khi triển khai.
- **Hermes Agent:** Hỗ trợ phân tích, lập kế hoạch và thực hiện công việc phát triển thông qua các kỹ năng được cài đặt ở cấp người dùng.
- **Constitution:** Quy định các nguyên tắc về kiến trúc, chất lượng, bảo mật và trách nhiệm.
- **AGENTS.md:** Hướng dẫn chung dành cho AI Agent làm việc trong repository.
- **docs/, src/, tests/, scripts/:** Cấu trúc ban đầu cho tài liệu, mã nguồn, kiểm thử và tự động hóa.
- **Git Ignore và EditorConfig:** Cấu hình quản lý tệp và định dạng nhất quán.

## Bắt đầu nhanh

### Tạo dự án trên Ubuntu bằng script `new-project`

```bash
new-project ten-du-an
cd ~/projects/ten-du-an
hermes
```

Bắt đầu quy trình đặc tả trong Hermes:

```text
/speckit-specify
```

### Tạo dự án từ GitHub

1. Mở [Universal Project Template](https://github.com/thanh577/universal-project-template).
2. Chọn **Use this template** → **Create a new repository**.
3. Đặt tên repository mới và chọn quyền truy cập.
4. Clone repository mới về máy rồi bắt đầu phát triển.

## Hướng dẫn sử dụng chi tiết

Xem **[GUIDE.md — Hướng dẫn sử dụng Universal Project Template](GUIDE.md)** để biết:

- Cài đặt và kiểm tra môi trường.
- Tạo dự án bằng Terminal hoặc GitHub.
- Giải thích cấu trúc thư mục.
- Ví dụ xây dựng ứng dụng Expense Tracker bằng Python.
- Sử dụng Hermes Agent, Spec Kit và sub-agent.
- Quy trình Git từ cơ bản đến nâng cao.
- Bảo mật, cập nhật template, checklist và xử lý lỗi.

## Cấu trúc dự án

- `.specify/`: Đặc tả, mẫu tài liệu, script và hiến chương dự án.
- `.hermes/`: Cấu hình Hermes Agent ở cấp dự án nếu cần; được loại trừ khỏi Git.
- `docs/`: Tài liệu kiến trúc và quyết định kỹ thuật.
- `scripts/`: Tập lệnh phát triển và tự động hóa.
- `src/`: Mã nguồn ứng dụng.
- `tests/`: Kiểm thử tự động.
- `AGENTS.md`: Hướng dẫn dành cho AI Agent.
- `GUIDE.md`: Hướng dẫn sử dụng template chi tiết.

## Lựa chọn công nghệ

Template không áp đặt ngôn ngữ lập trình hoặc framework cụ thể. Hãy chọn công nghệ theo yêu cầu thực tế của từng dự án và ghi lại các quyết định quan trọng trong tài liệu đặc tả, kế hoạch triển khai hoặc ADR.

## Yêu cầu

Cài đặt các công cụ phù hợp với công nghệ được chọn. Môi trường phát triển cần có:

- Git.
- Hermes Agent.
- Spec Kit CLI và các kỹ năng Spec Kit tương ứng trong Hermes.

GitHub CLI (`gh`) là tùy chọn, hữu ích khi quản lý repository GitHub từ Terminal.

## Repository

- GitHub: https://github.com/thanh577/universal-project-template
- Phiên bản nền tảng: `v1.0.0`
