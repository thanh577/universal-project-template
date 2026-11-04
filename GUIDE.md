# Hướng dẫn sử dụng Universal Project Template

**Repository:**
<https://github.com/thanh577/universal-project-template>\
**Phiên bản hướng dẫn:** 1.0\
**Phiên bản template:** `v1.0.0`\
**Mục tiêu:** Giúp người mới bắt đầu lẫn lập trình viên có kinh nghiệm
tạo, tổ chức, phát triển và quản lý dự án phần mềm bằng Universal
Project Template, Hermes Agent, Spec Kit và Git.

------------------------------------------------------------------------

## 1. Universal Project Template là gì?

Universal Project Template là bộ khung khởi tạo dự án phần mềm có thể
tái sử dụng. Template không ép buộc dự án phải dùng Python, JavaScript,
Go hay một framework cụ thể.

Thay vì bắt đầu từ một thư mục trống, bạn có sẵn:

-   **Hermes Agent:** trợ lý AI hỗ trợ phân tích, lập kế hoạch và thực
    hiện công việc phát triển.
-   **Spec Kit:** quy trình phát triển dựa trên đặc tả, giúp làm rõ yêu
    cầu trước khi viết mã.
-   **`AGENTS.md`:** hướng dẫn để AI Agent hiểu cách làm việc trong
    repository.
-   **Constitution:** các nguyên tắc về kiến trúc, chất lượng, bảo mật
    và trách nhiệm khi tự động hóa.
-   **`docs/`:** nơi lưu tài liệu kiến trúc và quyết định kỹ thuật.
-   **`src/`, `tests/`, `scripts/`:** các thư mục khởi đầu cho mã nguồn,
    kiểm thử và tập lệnh.
-   **Git và EditorConfig:** cấu hình cơ bản để quản lý phiên bản và
    định dạng tệp nhất quán.

Template chỉ cung cấp nền móng. Nó **không tự cài đặt mọi ngôn ngữ,
framework, thư viện hoặc công cụ build** cho dự án. Bạn chọn công nghệ
theo yêu cầu thực tế rồi cài đặt các công cụ tương ứng.

### 1.1. Các thành phần phối hợp với nhau như thế nào?

  -----------------------------------------------------------------------
  Thành phần                          Vai trò
  ----------------------------------- -----------------------------------
  Bạn                                 Quyết định mục tiêu, phạm vi, ưu
                                      tiên và phê duyệt các thao tác quan
                                      trọng

  Hermes Agent                        Điều phối AI Agent, hỗ trợ đọc
                                      repository và thực hiện công việc

  Spec Kit                            Chuyển ý tưởng thành đặc tả, kế
                                      hoạch và danh sách nhiệm vụ

  `AGENTS.md`                         Đưa ra quy tắc làm việc cho AI
                                      trong repository

  Constitution                        Định nghĩa những nguyên tắc kỹ
                                      thuật dự án cần tuân thủ

  Git                                 Ghi lại lịch sử thay đổi, hỗ trợ
                                      nhánh và cộng tác

  GitHub                              Lưu repository từ xa, chia sẻ mã
                                      nguồn và làm việc nhóm
  -----------------------------------------------------------------------

Hermes Agent không thay thế Git; Spec Kit cũng không thay thế kiểm thử.
Hãy sử dụng chúng như các công cụ bổ trợ cho quy trình phát triển.

------------------------------------------------------------------------

## 2. Chuẩn bị môi trường

### 2.1. Công cụ cần có

Trên máy Ubuntu, kiểm tra các công cụ cơ bản:

``` bash
git --version
hermes --help
specify --version
gh --version
```

Ý nghĩa:

-   `git`: quản lý lịch sử mã nguồn.
-   `hermes`: khởi chạy Hermes Agent.
-   `specify`: giao diện dòng lệnh của Spec Kit.
-   `gh`: GitHub CLI, dùng để tạo và quản lý repository GitHub từ
    Terminal.

Không nhất thiết mọi dự án đều cần `gh`, nhưng công cụ này hữu ích khi
muốn tạo repository GitHub từ Terminal.

Nếu một lệnh báo `command not found`, hãy cài đặt công cụ tương ứng
trước khi tiếp tục. Cách cài đặt có thể thay đổi theo phiên bản Ubuntu
và hướng dẫn chính thức của từng dự án.

### 2.2. Kiểm tra Hermes có các kỹ năng Spec Kit

Trong cấu hình hiện tại, các kỹ năng Spec Kit được cài đặt ở cấp người
dùng, không cần sao chép vào từng repository:

``` bash
for skill in specify clarify plan tasks analyze implement checklist converge; do
    test -f "$HOME/.hermes/skills/speckit-$skill/SKILL.md" \
        && echo "OK: speckit-$skill" \
        || echo "MISSING: speckit-$skill"
done
```

Nếu một kỹ năng bị thiếu, hãy cài đặt hoặc sửa cấu hình Hermes theo
hướng dẫn của phiên bản Spec Kit/Hermes bạn đang sử dụng.

### 2.3. Kiểm tra danh tính Git

Git cần tên và email để ghi vào commit:

``` bash
git config --global user.name
git config --global user.email
```

Nếu chưa cấu hình, thiết lập thông tin của chính bạn:

``` bash
git config --global user.name "Tên của bạn"
git config --global user.email "email-của-bạn@example.com"
```

Thay các giá trị mẫu bằng tên và email bạn muốn gắn với commit. Nếu
không muốn áp dụng cho tất cả repository, bỏ `--global` và chạy lệnh
trong thư mục dự án để cấu hình riêng cho dự án đó.

Kiểm tra cấu hình:

``` bash
git config --global --list
```

> Tên và email Git không phải mật khẩu. Không đưa access token, mật khẩu
> hoặc khóa bí mật vào cấu hình Git hay commit.

------------------------------------------------------------------------

## 3. Tạo dự án mới: chọn một trong hai cách

Có hai cách khởi tạo phổ biến:

1.  Dùng script `new-project` trên máy Ubuntu. Cách này sao chép
    template cục bộ và tự khởi tạo Git.
2.  Dùng nút **Use this template** trên GitHub. Cách này tạo repository
    mới từ template trên GitHub.

Hai cách đều tạo ra dự án riêng. Sau khi tạo, thay đổi ở dự án mới
**không tự động cập nhật ngược** về template gốc.

### 3.1. Cách A --- Dùng `new-project` trên Ubuntu

Đây là cách thuận tiện khi bạn đã cài script `~/bin/new-project` theo
hướng dẫn thiết lập template.

Tạo dự án:

``` bash
new-project ten-du-an
```

Ví dụ:

``` bash
new-project expense-tracker
```

Script sẽ:

1.  Kiểm tra tên dự án.
2.  Kiểm tra thư mục đích đã tồn tại hay chưa.
3.  Sao chép nội dung template bằng `rsync`.
4.  Loại trừ Git history của template, dữ liệu Hermes cục bộ, thư mục
    phụ thuộc và một số đầu ra build.
5.  Khởi tạo repository Git mới trên nhánh `main`.
6.  Thiết lập tên và email Git lấy từ cấu hình cục bộ của repository
    template.
7.  Tạo commit đầu tiên.

Thư mục dự án được tạo bên trong `~/projects/`:

``` text
/home/ten-nguoi-dung/projects/ten-du-an/
```

Đi vào dự án:

``` bash
cd ~/projects/expense-tracker
```

Kiểm tra:

``` bash
git branch --show-current
git log -1 --oneline
git status
```

Kết quả mong đợi:

-   Nhánh hiện tại là `main`.
-   Có một commit khởi tạo dự án.
-   `working tree clean` nếu bạn chưa chỉnh sửa tệp nào.

**Lưu ý:** Script `new-project` đã khởi tạo Git và tạo commit. Không
chạy `git init` lần nữa nếu không có lý do đặc biệt.

Nếu Terminal báo `new-project: command not found`, kiểm tra:

``` bash
ls -l ~/bin/new-project
echo "$PATH"
```

Nếu `~/bin` chưa có trong `PATH`, thêm dòng sau vào `~/.bashrc`:

``` bash
export PATH="$HOME/bin:$PATH"
```

Nạp lại cấu hình:

``` bash
source ~/.bashrc
```

### 3.2. Cách B --- Dùng GitHub Template Repository

Mở repository template:

<https://github.com/thanh577/universal-project-template>

Thực hiện:

1.  Đăng nhập GitHub.
2.  Mở repository `universal-project-template`.
3.  Chọn **Use this template**.
4.  Chọn **Create a new repository**.
5.  Nhập tên repository mới, ví dụ `expense-tracker`.
6.  Chọn chủ sở hữu (Owner).
7.  Chọn Public hoặc Private theo nhu cầu.
8.  Nhấn **Create repository**.

GitHub sẽ tạo repository mới dựa trên nội dung template. Repository mới
là một dự án riêng; nó không tự động đồng bộ các commit về repository
template gốc.

Sau khi tạo, clone dự án về Ubuntu:

``` bash
cd ~/projects
gh repo clone TEN_TAI_KHOAN/expense-tracker
cd expense-tracker
```

Thay `TEN_TAI_KHOAN` bằng tên tài khoản hoặc tổ chức sở hữu repository
mới.

Kiểm tra:

``` bash
git remote -v
git branch --show-current
git status
```

Repository được clone đã có remote `origin` trỏ về repository mới trên
GitHub.

> Nếu bạn đã tạo dự án bằng script `new-project`, không cần tạo lại dự
> án bằng GitHub Template. Hãy làm theo mục 7.2 để kết nối thư mục hiện
> có với một repository GitHub mới.

------------------------------------------------------------------------

## 4. Hiểu cấu trúc thư mục

Cấu trúc cơ bản:

``` text
ten-du-an/
├── .github/
│   └── workflows/
├── .specify/
│   ├── memory/
│   │   └── constitution.md
│   ├── scripts/
│   ├── templates/
│   └── workflows/
├── docs/
│   ├── architecture/
│   └── decisions/
├── scripts/
├── src/
├── tests/
├── .editorconfig
├── .env.example
├── .gitignore
├── AGENTS.md
└── README.md
```

  -----------------------------------------------------------------------
  Đường dẫn                           Dùng để làm gì?
  ----------------------------------- -----------------------------------
  `.github/workflows/`                Chứa quy trình tự động của GitHub
                                      Actions; ban đầu có thể chỉ là thư
                                      mục trống

  `.specify/memory/constitution.md`   Các nguyên tắc kỹ thuật của dự án

  `.specify/templates/`               Mẫu đặc tả, kế hoạch, tasks và
                                      checklist

  `.specify/scripts/`                 Script phục vụ quy trình Spec Kit

  `.specify/workflows/`               Cấu hình quy trình Spec Kit

  `docs/architecture/`                Mô tả kiến trúc, thành phần, luồng
                                      dữ liệu và tích hợp

  `docs/decisions/`                   Lưu các quyết định kiến trúc/kỹ
                                      thuật (ADR)

  `scripts/`                          Script chạy, build, kiểm tra, triển
                                      khai hoặc bảo trì

  `src/`                              Mã nguồn chính

  `tests/`                            Kiểm thử tự động

  `AGENTS.md`                         Hướng dẫn cho AI Agent

  `.env.example`                      Danh sách biến môi trường mẫu,
                                      không chứa bí mật

  `.gitignore`                        Những tệp/thư mục Git không nên
                                      theo dõi

  `.editorconfig`                     Quy tắc định dạng tệp dùng chung

  `README.md`                         Giới thiệu, cài đặt, chạy và sử
                                      dụng dự án
  -----------------------------------------------------------------------

Một số ngôn ngữ hoặc framework có quy ước thư mục riêng. Bạn có thể điều
chỉnh cấu trúc để phù hợp với công nghệ đã chọn, nhưng nên cập nhật
README và tài liệu kiến trúc khi thay đổi.

------------------------------------------------------------------------

## 5. Ví dụ thực tế: tạo một ứng dụng Expense Tracker bằng Python

Phần này minh họa toàn bộ quy trình với một dự án cụ thể. Đây là ví dụ
để học cách sử dụng template; template không bắt buộc các dự án khác
phải dùng Python.

### 5.1. Mô tả ý tưởng

Ta muốn xây dựng ứng dụng dòng lệnh quản lý thu chi cá nhân, có tên
`expense-tracker`.

Chức năng dự kiến:

-   Thêm khoản thu hoặc chi.
-   Liệt kê các giao dịch.
-   Xem tổng thu, tổng chi và số dư.
-   Lọc giao dịch theo khoảng thời gian.
-   Lưu dữ liệu trên máy bằng SQLite.
-   Có kiểm thử tự động.
-   Chạy được trên Ubuntu.

### 5.2. Tạo dự án

``` bash
new-project expense-tracker
cd ~/projects/expense-tracker
```

Mở Hermes Agent:

``` bash
hermes
```

### 5.3. Bắt đầu bằng Spec Kit

Không nên yêu cầu AI viết toàn bộ ứng dụng ngay từ một câu ngắn. Hãy mô
tả mục tiêu, người dùng, chức năng, giới hạn và điều kiện hoàn thành.

Trong Hermes, bắt đầu bằng:

``` text
/speckit-specify
```

Ví dụ yêu cầu gửi cho Hermes:

``` text
Tôi muốn xây dựng ứng dụng Expense Tracker dạng CLI bằng Python.

Mục tiêu:
- Quản lý thu nhập và chi tiêu cá nhân.
- Chạy trên Ubuntu 24.04 trở lên.
- Dữ liệu lưu cục bộ bằng SQLite.
- Không cần tài khoản, đăng nhập hoặc kết nối Internet.

Chức năng:
1. Thêm giao dịch thu hoặc chi.
2. Xem danh sách giao dịch.
3. Sửa và xóa giao dịch.
4. Lọc giao dịch theo ngày và loại giao dịch.
5. Báo cáo tổng thu, tổng chi và số dư.
6. Xuất báo cáo CSV.

Yêu cầu:
- Giao diện dòng lệnh dễ sử dụng.
- Có kiểm thử tự động.
- Có hướng dẫn cài đặt và sử dụng.
- Không lưu dữ liệu bí mật.
- Thiết kế đơn giản, dễ bảo trì.

Hãy làm rõ các yêu cầu còn thiếu trước khi lập kế hoạch.
Chưa viết mã nguồn ở giai đoạn này.
```

Spec Kit sẽ hỗ trợ hình thành tài liệu đặc tả. Đọc và kiểm tra tài liệu
được tạo; sửa những điểm chưa đúng với nhu cầu thực tế.

### 5.4. Làm rõ yêu cầu

Dùng kỹ năng/lệnh làm rõ tương ứng:

``` text
/speckit-clarify
```

Hãy trả lời các câu hỏi của AI. Ví dụ, cần quyết định:

-   Tiền tệ mặc định là VND hay cho phép nhiều loại tiền?
-   Có cho phép giao dịch âm không?
-   Xóa giao dịch có cần xác nhận không?
-   Ngày tháng nhập theo định dạng nào?
-   Có cần phân loại chi tiêu không?
-   Dữ liệu lưu ở vị trí nào?

Không nên bỏ qua các câu hỏi ảnh hưởng đến dữ liệu, bảo mật hoặc hành vi
của ứng dụng.

### 5.5. Lập kế hoạch kỹ thuật

Sau khi đặc tả đủ rõ:

``` text
/speckit-plan
```

Ví dụ các quyết định kỹ thuật có thể gồm:

-   Python phiên bản phù hợp với môi trường mục tiêu.
-   SQLite để lưu dữ liệu.
-   Một thư viện CLI hoặc thư viện chuẩn Python.
-   `pytest` để kiểm thử nếu dự án lựa chọn công cụ này.
-   Cấu trúc module và cách xử lý lỗi.

Đây chỉ là lựa chọn minh họa. Hãy để yêu cầu thực tế quyết định công
nghệ, không chọn thư viện chỉ vì ví dụ có nhắc đến.

### 5.6. Tạo danh sách nhiệm vụ

``` text
/speckit-tasks
```

Kiểm tra danh sách nhiệm vụ:

-   Nhiệm vụ có đủ nhỏ để thực hiện và kiểm tra không?
-   Có nhiệm vụ kiểm thử không?
-   Có tài liệu hướng dẫn không?
-   Có xử lý lỗi và dữ liệu đầu vào không?
-   Thứ tự phụ thuộc giữa các nhiệm vụ có hợp lý không?

### 5.7. Phân tích trước khi triển khai

``` text
/speckit-analyze
```

Yêu cầu Hermes kiểm tra sự nhất quán giữa đặc tả, kế hoạch và tasks.
Giải quyết những điểm mâu thuẫn hoặc thiếu trước khi triển khai.

### 5.8. Triển khai

Khi đã thống nhất kế hoạch và phạm vi:

``` text
/speckit-implement
```

Theo dõi thay đổi của Agent. Yêu cầu Agent:

-   Làm theo từng nhiệm vụ.
-   Viết kiểm thử phù hợp.
-   Không tuyên bố kiểm thử thành công nếu chưa thực sự chạy.
-   Không tự ý xóa dữ liệu quan trọng hoặc triển khai lên môi trường
    thật.
-   Báo rõ file đã thay đổi, lệnh đã chạy và vấn đề còn tồn tại.

### 5.9. Kiểm tra sau triển khai

Dùng checklist:

``` text
/speckit-checklist
```

Chạy các lệnh kiểm thử/build thực tế theo công nghệ của dự án. Với
Python, ví dụ:

``` bash
python3 --version
python3 -m pytest
```

Lệnh `pytest` chỉ chạy được khi dự án đã cài và cấu hình pytest. Nếu
chưa có, hãy bổ sung công cụ kiểm thử theo kế hoạch.

### 5.10. Cập nhật tài liệu dự án

Khi chức năng đã ổn định:

-   Cập nhật README với cách cài đặt, chạy và ví dụ lệnh.
-   Cập nhật `docs/architecture/` nếu kiến trúc thay đổi.
-   Thêm ADR vào `docs/decisions/` khi có quyết định kỹ thuật quan
    trọng.
-   Cập nhật `.env.example` nếu dự án có biến môi trường.
-   Đảm bảo không đưa dữ liệu cá nhân hoặc bí mật vào repository.

------------------------------------------------------------------------

## 6. Sử dụng Hermes Agent và AGENTS.md hiệu quả

### 6.1. Trước khi giao việc

Từ thư mục gốc của dự án, khởi chạy:

``` bash
hermes
```

Yêu cầu Agent đọc các tài liệu nền tảng trước khi làm việc:

``` text
Hãy đọc AGENTS.md, .specify/memory/constitution.md,
README.md và các tài liệu đặc tả/kế hoạch/tasks hiện có.

Tóm tắt:
1. Mục tiêu dự án.
2. Kiến trúc hiện tại.
3. Các nguyên tắc bắt buộc.
4. Công việc đang làm dở.
5. Những điểm chưa rõ.

Chưa chỉnh sửa file cho đến khi tôi yêu cầu.
```

### 6.2. Giao việc rõ ràng

Một yêu cầu tốt thường có:

1.  **Mục tiêu:** muốn đạt được điều gì?
2.  **Phạm vi:** file, module hoặc chức năng nào liên quan?
3.  **Ràng buộc:** công nghệ, tương thích, bảo mật, hiệu năng?
4.  **Điều kiện hoàn thành:** kiểm tra bằng cách nào?
5.  **Giới hạn hành động:** thao tác nào phải hỏi trước?

Ví dụ:

``` text
Hãy triển khai chức năng lọc giao dịch theo khoảng ngày.

Yêu cầu:
- Tuân thủ đặc tả và kế hoạch hiện tại.
- Không thay đổi định dạng dữ liệu đã lưu nếu không cần thiết.
- Bổ sung kiểm thử cho ngày bắt đầu, ngày kết thúc và khoảng rỗng.
- Chạy các kiểm thử liên quan.
- Báo cáo file đã thay đổi và kết quả kiểm thử.

Không xóa dữ liệu người dùng hoặc thực hiện thao tác phá hủy.
```

### 6.3. Dùng sub-agent khi phù hợp

Nếu môi trường Hermes của bạn có các sub-agent, có thể giao những nhiệm
vụ tách biệt như:

-   Researcher: tìm hiểu thư viện hoặc phương án kỹ thuật.
-   Explorer: khảo sát cấu trúc repository.
-   Developer: triển khai chức năng.
-   Tester: thiết kế và chạy kiểm thử.
-   Reviewer: rà soát thay đổi.
-   Documenter: cập nhật tài liệu.

Hãy kiểm tra tên agent và quyền của chúng trong cấu hình Hermes thực tế.
Không giả định mọi dự án đều có cùng bộ agent hoặc cùng quyền truy cập.

### 6.4. Các thao tác cần kiểm soát

Yêu cầu Agent hỏi trước khi:

-   Xóa dữ liệu quan trọng hoặc thư mục không thể khôi phục.
-   Thay đổi schema hoặc thực hiện migration có rủi ro.
-   Triển khai lên production.
-   Công khai repository hoặc phát hành package.
-   Gửi dữ liệu ra dịch vụ bên ngoài.
-   Phát sinh chi phí.
-   Truy cập hoặc tiết lộ thông tin bí mật.

------------------------------------------------------------------------

## 7. Sử dụng Git trong dự án

Git giúp lưu lại lịch sử thay đổi. GitHub là dịch vụ lưu repository từ
xa. Hai khái niệm này liên quan nhưng không giống nhau.

### 7.1. Những khái niệm cần biết

  Khái niệm           Giải thích
  ------------------- -----------------------------------------------------
  Repository (repo)   Kho chứa mã nguồn và lịch sử Git
  Working tree        Các file hiện tại trong thư mục dự án
  Commit              Một mốc ghi nhận thay đổi
  Branch              Nhánh phát triển độc lập
  `main`              Nhánh chính của dự án
  Remote              Repository từ xa, thường đặt trên GitHub
  `origin`            Tên remote mặc định thường dùng
  Push                Đẩy commit từ máy lên remote
  Pull                Lấy và tích hợp thay đổi từ remote
  Clone               Sao chép repository từ xa về máy
  Tag                 Nhãn đánh dấu một commit, thường dùng cho phiên bản
  Merge               Tích hợp thay đổi từ nhánh này vào nhánh khác
  Pull Request (PR)   Đề xuất tích hợp thay đổi trên GitHub

### 7.2. Kết nối dự án tạo bằng `new-project` với GitHub

Script `new-project` chỉ tạo repository Git cục bộ. Nếu muốn lưu dự án
lên GitHub, hãy tạo repository từ thư mục dự án.

Ví dụ dự án `expense-tracker`:

``` bash
cd ~/projects/expense-tracker
gh auth status
```

Tạo repository GitHub mới và push:

``` bash
gh repo create expense-tracker \
    --private \
    --source=. \
    --remote=origin \
    --push
```

Ở ví dụ này repository được tạo ở chế độ Private. Nếu muốn công khai,
thay `--private` bằng `--public`.

Kiểm tra:

``` bash
git remote -v
git status
```

Nếu repository đã được tạo trên GitHub bằng giao diện web, không chạy
lại lệnh tạo repository. Khi đó hãy kết nối remote hiện có, ví dụ:

``` bash
git remote add origin https://github.com/TEN_TAI_KHOAN/expense-tracker.git
git push -u origin main
```

Thay `TEN_TAI_KHOAN` bằng tài khoản hoặc tổ chức thực tế. Nếu `origin`
đã tồn tại, kiểm tra bằng `git remote -v` trước khi thêm; không thêm
trùng remote.

### 7.3. Quy trình làm việc cơ bản hằng ngày

Kiểm tra trạng thái trước khi làm:

``` bash
git status
```

Xem các file thay đổi:

``` bash
git diff
```

Đưa file vào vùng chuẩn bị commit:

``` bash
git add README.md
```

Hoặc đưa tất cả thay đổi phù hợp vào vùng chuẩn bị:

``` bash
git add -A
```

Kiểm tra những gì sắp commit:

``` bash
git diff --cached
```

Tạo commit:

``` bash
git commit -m "feat: add transaction filtering"
```

Đẩy lên GitHub:

``` bash
git push
```

Nếu đây là lần đầu push một nhánh mới:

``` bash
git push -u origin ten-nhanh
```

**Quy tắc quan trọng:** Không commit file bí mật, token, mật khẩu, khóa
riêng, database chứa dữ liệu cá nhân hoặc file build không cần thiết.
`.gitignore` hỗ trợ bỏ qua file, nhưng không thay thế việc kiểm tra
trước khi commit.

### 7.4. Quy ước commit gợi ý

Có thể dùng quy ước Conventional Commits:

  Tiền tố       Dùng khi
  ------------- -------------------------------------------
  `feat:`       Thêm chức năng
  `fix:`        Sửa lỗi
  `docs:`       Thay đổi tài liệu
  `refactor:`   Tái cấu trúc, không đổi hành vi mong muốn
  `test:`       Thêm hoặc sửa kiểm thử
  `build:`      Thay đổi hệ thống build hoặc phụ thuộc
  `ci:`         Thay đổi CI/CD
  `chore:`      Công việc bảo trì khác

Ví dụ:

``` bash
git commit -m "feat: add monthly expense report"
git commit -m "fix: handle invalid transaction date"
git commit -m "docs: update installation guide"
git commit -m "test: cover empty transaction list"
```

Commit nên nhỏ, tập trung vào một mục đích và có nội dung dễ hiểu.

### 7.5. Làm việc bằng branch

Không nhất thiết phải phát triển trực tiếp trên `main`. Với một chức
năng mới:

``` bash
git switch main
git pull
git switch -c feature/monthly-report
```

Sau khi sửa mã nguồn và kiểm thử:

``` bash
git status
git add -A
git diff --cached
git commit -m "feat: add monthly report"
git push -u origin feature/monthly-report
```

Mở GitHub repository và tạo Pull Request từ `feature/monthly-report` vào
`main`.

Sau khi review và kiểm thử đạt yêu cầu, merge PR. Cập nhật máy local:

``` bash
git switch main
git pull
```

Tên branch gợi ý:

-   `feature/ten-chuc-nang`
-   `fix/mo-ta-loi`
-   `docs/cap-nhat-huong-dan`
-   `refactor/ten-module`

Dự án cá nhân nhỏ có thể làm trực tiếp trên `main`, nhưng vẫn nên commit
thường xuyên và kiểm tra kỹ trước khi push.

### 7.6. Đồng bộ thay đổi từ GitHub

Lấy thay đổi mới nhất:

``` bash
git pull
```

Đẩy commit local:

``` bash
git push
```

Xem remote:

``` bash
git remote -v
```

Xem lịch sử:

``` bash
git log --oneline --decorate -10
```

Xem nhánh:

``` bash
git branch
```

Nếu Git báo có xung đột (conflict), đừng xóa file hoặc chạy lệnh reset
một cách tùy tiện. Mở các file được báo conflict, chọn nội dung đúng,
kiểm tra lại, rồi tạo commit hoàn tất việc tích hợp.

### 7.7. Tag và phát hành phiên bản

Khi có một mốc ổn định, có thể tạo tag:

``` bash
git tag -a v0.1.0 -m "Expense Tracker v0.1.0"
git push origin v0.1.0
```

Xem tag:

``` bash
git tag
```

Tag là nhãn trỏ đến một commit. Tạo tag không tự động kiểm thử, build
hay phát hành ứng dụng. Chỉ đánh dấu phiên bản sau khi đã kiểm tra nội
dung và trạng thái dự án.

### 7.8. Một số lệnh Git cần thận trọng

Các lệnh sau có thể làm mất thay đổi:

``` bash
git reset --hard
git clean -fd
git push --force
```

Không chạy chúng chỉ vì AI Agent đề xuất mà chưa hiểu tác động. Trước
thao tác rủi ro, kiểm tra `git status`, sao lưu dữ liệu cần thiết và xác
nhận phạm vi ảnh hưởng.

------------------------------------------------------------------------

## 8. Bảo mật và quản lý cấu hình

### 8.1. Sử dụng `.env.example`

Khi dự án cần biến môi trường, ghi tên biến và giá trị minh họa trong
`.env.example`:

``` dotenv
APP_ENV=development
DATABASE_URL=sqlite:///data/app.db
API_BASE_URL=https://example.invalid
API_KEY=
```

Tạo file `.env` cục bộ để chứa giá trị thật:

``` bash
cp .env.example .env
```

Không commit `.env`. Kiểm tra `.gitignore` có quy tắc loại trừ `.env` và
các biến thể phù hợp.

### 8.2. Kiểm tra trước khi commit

``` bash
git status --short
git diff --cached
```

Nếu lỡ đưa bí mật vào commit, chỉ xóa file ở commit sau là chưa đủ vì bí
mật vẫn có thể tồn tại trong lịch sử Git. Hãy thu hồi hoặc xoay vòng
token/khóa bị lộ trước, sau đó xử lý lịch sử repository phù hợp.

### 8.3. Dữ liệu người dùng

-   Không đưa database thật có thông tin cá nhân lên repository công
    khai.
-   Không đưa log chứa token hoặc thông tin định danh vào commit.
-   Không dùng dữ liệu thật trong ví dụ tài liệu nếu không cần thiết.
-   Sao lưu dữ liệu trước migration hoặc thao tác phá hủy.

------------------------------------------------------------------------

## 9. Cập nhật template và các dự án đã tạo

Khi repository template được cập nhật, các dự án đã tạo từ template
**không tự động nhận thay đổi**.

Ví dụ, bạn bổ sung một quy tắc mới trong `AGENTS.md` của template. Dự án
`expense-tracker` sẽ không tự có quy tắc đó.

Có hai trường hợp:

### 9.1. Cập nhật template gốc

Làm việc trong repository template:

``` bash
cd ~/projects/project_template
git pull
```

Sửa tài liệu hoặc cấu hình, kiểm tra, commit và push:

``` bash
git status
git add -A
git diff --cached
git commit -m "chore: improve project template"
git push
```

Khi phát hành phiên bản mới, tạo tag mới, ví dụ `v1.1.0`:

``` bash
git tag -a v1.1.0 -m "Universal Project Template v1.1.0"
git push origin v1.1.0
```

Không di chuyển hoặc ghi đè tag cũ `v1.0.0` nếu không có lý do đặc biệt.

### 9.2. Đưa thay đổi template vào một dự án đã tạo

Không nên mặc định sao chép toàn bộ template mới đè lên dự án đang chạy.
Cách an toàn:

1.  Xem thay đổi trong template mới.
2.  Xác định file nào thực sự cần cập nhật.
3.  Kiểm tra file tương ứng trong dự án hiện tại.
4.  Chọn lọc và tích hợp thay đổi.
5.  Chạy kiểm thử.
6.  Commit riêng cho việc cập nhật nền tảng.

Đặc biệt cẩn thận với `.specify/`, `AGENTS.md`, `.gitignore`, tài liệu
kiến trúc và cấu hình build vì dự án có thể đã chỉnh sửa chúng theo nhu
cầu riêng.

------------------------------------------------------------------------

## 10. Checklist khởi tạo dự án mới

Dùng checklist này mỗi lần bắt đầu dự án.

### Trước khi phát triển

-   [ ] Tạo dự án bằng `new-project` hoặc GitHub Template.
-   [ ] Kiểm tra nhánh `main` và trạng thái Git.
-   [ ] Đọc `README.md`, `AGENTS.md` và Constitution.
-   [ ] Xác định mục tiêu và phạm vi dự án.
-   [ ] Chọn ngôn ngữ, framework và công cụ.
-   [ ] Cài đặt môi trường phát triển.
-   [ ] Cập nhật README theo dự án mới.
-   [ ] Bắt đầu Spec Kit bằng `/speckit-specify`.

### Trước khi triển khai

-   [ ] Đặc tả đã được rà soát.
-   [ ] Các điểm chưa rõ đã được làm rõ.
-   [ ] Kế hoạch kỹ thuật đã được thống nhất.
-   [ ] Tasks có thứ tự và tiêu chí hoàn thành.
-   [ ] Các rủi ro về bảo mật và dữ liệu đã được xem xét.

### Trước khi commit/push

-   [ ] Kiểm tra `git status`.
-   [ ] Kiểm tra `git diff` và `git diff --cached`.
-   [ ] Không có `.env`, token, mật khẩu hoặc dữ liệu riêng tư.
-   [ ] Kiểm thử đã chạy; báo cáo đúng kết quả thực tế.
-   [ ] Commit có thông điệp rõ ràng.
-   [ ] Push đúng repository và đúng branch.

### Trước khi phát hành

-   [ ] README có hướng dẫn cài đặt và sử dụng.
-   [ ] Kiểm thử cần thiết đã đạt.
-   [ ] Tài liệu kiến trúc được cập nhật.
-   [ ] Các thay đổi rủi ro đã được review.
-   [ ] Tag phiên bản được tạo đúng commit.
-   [ ] Có ghi chú phát hành nếu cần.

------------------------------------------------------------------------

## 11. Xử lý một số lỗi thường gặp

### `new-project: command not found`

Kiểm tra script và PATH:

``` bash
ls -l ~/bin/new-project
echo "$PATH"
```

Nếu cần, thêm `export PATH="$HOME/bin:$PATH"` vào `~/.bashrc`, rồi chạy
`source ~/.bashrc`.

### `Lỗi: Thư mục đã tồn tại`

Script không ghi đè thư mục có sẵn. Chọn tên dự án khác hoặc tự kiểm tra
thư mục cũ trước khi quyết định xử lý. Không xóa thư mục nếu chưa chắc
chắn dữ liệu bên trong không còn cần thiết.

### `Author identity unknown`

Thiết lập danh tính Git:

``` bash
git config --global user.name "Tên của bạn"
git config --global user.email "email-của-bạn@example.com"
```

### `gh: command not found`

GitHub CLI chưa được cài đặt hoặc chưa có trong PATH. Cài đặt theo hướng
dẫn chính thức của GitHub CLI dành cho hệ điều hành đang dùng.

### `Permission denied` khi push

Kiểm tra xác thực:

``` bash
gh auth status
```

Nếu chưa đăng nhập:

``` bash
gh auth login
```

Đồng thời xác nhận tài khoản có quyền ghi vào repository đích.

### Hermes không nhận ra lệnh Spec Kit

Kiểm tra Hermes đã cài các skill cần thiết ở cấp người dùng hay chưa:

``` bash
ls ~/.hermes/skills/
```

Kiểm tra chính xác từng skill bằng lệnh ở mục 2.2. Nếu skill chưa có,
cần cài đặt hoặc sửa cấu hình; không nên giả định rằng chỉ có thư mục
`.specify/` là Hermes tự nhận được mọi lệnh.

### Git báo `nothing to commit, working tree clean`

Điều này thường có nghĩa là không có thay đổi chưa commit. Nếu bạn vừa
sửa file nhưng Git không hiển thị, kiểm tra nội dung đã lưu chưa và file
có bị `.gitignore` loại trừ hay không.

------------------------------------------------------------------------

## 12. Tài nguyên

-   **Universal Project Template:**
    <https://github.com/thanh577/universal-project-template>
-   **Hermes Agent:** <https://github.com/NousResearch/hermes-agent>
-   **Spec Kit:** <https://github.com/github/spec-kit>
-   **Git documentation:** <https://git-scm.com/doc>
-   **GitHub CLI manual:** <https://cli.github.com/manual>
-   **GitHub Docs --- Template repositories:**
    <https://docs.github.com/repositories/creating-and-managing-repositories/creating-a-template-repository>

------------------------------------------------------------------------

## 13. Nguyên tắc sử dụng quan trọng

1.  Bắt đầu bằng việc hiểu vấn đề và đặc tả yêu cầu; không vội viết mã
    khi mục tiêu còn mơ hồ.
2.  Đọc và tuân thủ `AGENTS.md` cùng Constitution.
3.  Để công nghệ phục vụ yêu cầu dự án; không áp đặt một stack cho mọi
    dự án.
4.  Dùng Git thường xuyên, commit theo từng thay đổi có ý nghĩa.
5.  Kiểm tra nội dung trước khi commit và push.
6.  Không giao quyền quyết định các thao tác phá hủy hoặc phát hành quan
    trọng cho AI mà không có kiểm soát.
7.  Không coi kết quả do AI báo cáo là bằng chứng kiểm thử; phải dựa
    trên lệnh và kết quả thực tế.
8.  Cập nhật tài liệu khi kiến trúc, cách chạy hoặc cách sử dụng thay
    đổi.

**Universal Project Template là điểm khởi đầu thống nhất, không phải
khuôn mẫu cứng nhắc.** Mỗi dự án có thể điều chỉnh cấu trúc và công
nghệ, miễn là giữ được tính rõ ràng, dễ bảo trì, an toàn và có thể kiểm
chứng.
