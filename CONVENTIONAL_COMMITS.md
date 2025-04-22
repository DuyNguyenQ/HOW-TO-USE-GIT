# Conventional Commits
Thường mỗi dự án đều sẽ được đặt ra một tiêu chuẩn chung cho các commit message trong dự án của mình, mục đích dễ thấy nhất. Mọi người trong cùng 1 dự án cũng như người mới có thể hình dung được bao quát được nội dung code thay đổi làm công việc chính là gì, tiện cho việc review đánh giá cũng như tìm kiếm. Lưu giữ đầy đủ thông tin có thể tìm kiếm và kiểm chứng được các thay đổi.

```
Dòng 1: Tóm tắt nội dung thay đổi trong commit.
Dòng 2: Dòng trống.
Dòng 3 trở đi: Lý do đã thay đổi.
```

## General Structure:
Cấu trúc chung của một commit mesage theo conventional có dạng:
```
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```

**Trong đó**:
- Các thành phần type, description là bắt buộc cần có trong commit message, optional là tuỳ chọn, có hoặc không có cũng được.
- `type`: Từ khoá để phân loại commit là feature, fix bug, refactor...
- `scope`: Cũng được dùng để phân loại commit, nhưng khác với type nó giúp trả lời câu  hỏi: commit này refactor|fix cái gì? được đặt trong dấu ngoặc đơn ngay sau type. ex: `feat(authentication):`, `fix(homescreen):`...
- `description`: mô tả một cách ngắn gọn về nội dung commit.
- `body`: là mô tả dài và chi tiết hơn, cần thiết khi description chưa thể nói rõ hết được.
- `fotter`: một số thông tin mở rộng như số ID của pull request, issue.. được quy định theo conventional. 
```
ex: feat: add hat wobble
    ^--^  ^------------^
    |     |
    |     +-> Summary in present tense.
    |
    +-------> Type: chore, docs, feat, fix, refactor, style, or test.
```

## Types:
- `feat`: Những thay đổi cho tính năng mới.
- `fix`: Những thay đổi liên quan đến sửa lỗi trong ứng dụng, hệ thống.
- `docs`: Những thay đổi liên quan đến sửa đổi document trong repo.
- `style`: Những thay đổi không làm thay đổi ý nghĩa của code như căn hàng, xuồng dòng ở cuối file…
- `refactor`: Tối ưu source code, có thể liên quan logic…Ví dụ như xoá code thừa, tối giản code, đổi tên biến …
- `perf`: Thay đổi giúp tăng hiệu năng.
- `test`: Thêm hoặc sửa các testcase trong hệ thống.
- `build`: Thay đổi liên quan đến hệ thống hoặc các thư viên bên ngoài (Ảnh hưởng đến tiến trình build).
- `ci`: Thay đổi liên quan đến cấu hình CI…
- `chore`: Những sửa đổi nhỏ nhặt không liên quan tới code.
- `BREAKING CHANGE`: Nhưng commit mới footer là BREAKING CHANGE thể hiện những thay đổi gây ảnh hướng lớn đến source code ví dụ thay đổi kiểu dữ liệu, cách lấy dữ liệu… => Qua đó cảnh báo mọi người để tránh phát sinh các vấn đề.
