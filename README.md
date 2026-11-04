# Universal Project Template

Bộ khung nền tảng có thể tái sử dụng cho các dự án phần mềm, không phụ thuộc vào ngôn ngữ lập trình hoặc công nghệ cụ thể.

## Thành phần

- **Spec Kit:** Phát triển phần mềm theo phương pháp đặc tả trước khi triển khai (Specification-Driven Development).
- **Hermes Agent:** Tích hợp Hermes Agent thông qua các kỹ năng (Skills) được cài đặt ở cấp hệ thống.
- **Constitution:** Quy định các nguyên tắc về kỹ thuật phần mềm, kiến trúc và bảo mật.
- **AGENTS.md:** Tệp hướng dẫn chung dành cho các AI Agent tham gia phát triển dự án.
- **Thư mục tài liệu, mã nguồn, kiểm thử và tập lệnh:** Cung cấp cấu trúc tổ chức thống nhất cho dự án.
- **Git Ignore và EditorConfig:** Cấu hình chung nhằm quản lý tệp và duy trì định dạng mã nguồn nhất quán.

## Yêu cầu

Cài đặt và cấu hình các công cụ cần thiết tương ứng với công nghệ được lựa chọn cho từng dự án.

Các công cụ sau cần có sẵn trong môi trường phát triển:

- Spec Kit CLI.
- Hermes Agent.

## Khởi tạo dự án mới

1. Sao chép hoặc nhân bản bộ khung này vào thư mục dự án mới.
2. Cập nhật tệp README.md để mô tả mục đích, chức năng và hướng dẫn sử dụng của dự án.
3. Đọc và rà soát `AGENTS.md` cùng `.specify/memory/constitution.md`.
4. Mở thư mục dự án bằng Hermes Agent.
5. Bắt đầu quy trình Spec Kit bằng lệnh `/speckit-specify`.
6. Tiếp tục các giai đoạn làm rõ yêu cầu, lập kế hoạch, tạo danh sách công việc và triển khai.

## Cấu trúc dự án

- `.specify/`: Chứa các bản đặc tả, mẫu tài liệu, tập lệnh và hiến chương dự án.
- `.hermes/`: Chứa cấu hình Hermes Agent ở cấp dự án nếu cần; thư mục này được loại trừ khỏi Git.
- `docs/`: Chứa tài liệu kiến trúc và tài liệu kỹ thuật.
- `scripts/`: Chứa các tập lệnh phục vụ phát triển và tự động hóa.
- `src/`: Chứa mã nguồn của ứng dụng.
- `tests/`: Chứa các bài kiểm thử tự động.
- `AGENTS.md`: Chứa hướng dẫn dành cho các AI Agent tham gia phát triển dự án.

## Lựa chọn công nghệ

Bộ khung này không áp đặt bất kỳ ngôn ngữ lập trình hoặc framework cụ thể nào.

Hãy lựa chọn công nghệ dựa trên yêu cầu thực tế của từng dự án. Các quyết định về công nghệ cần được mô tả rõ ràng trong tài liệu đặc tả và kế hoạch triển khai.
