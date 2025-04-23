# How To Use Git
## Contents:
- [<u>How To Use Git</u>](#how-to-use-git)
  - [<u>Popular Git Commands</u>](#popular-git-commands)
    - [<u>Basic Commands</u>](#basic-commands)
    - [<u>Branch And Merge</u>](#branch-and-merge)
    - [<u>Remote Repositories</u>](#remote-repositories)
    - [<u>History Commits</u>](#history-commits)
    - [<u>Revert</u>](#revert)
    - [<u>Staging</u>](#staging)
    - [<u>Tagging</u>](#tagging)
    - [<u>Collaboration</u>](#collaboration)
  - [<u>Conflicts</u>](#conflicts)
    - [<u>Resolve Conflicts Git Merge</u>](#resolve-conflicts-git-merge)
    - [<u>Resolve Conflicts Github Pull Request</u>](#resolve-conflicts-github-pull-request)
  - [<u>Overview Of Git Flow</u>](#overview-of-git-flow)
    - [<u>Main Branches</u>](#main-branches)
    - [<u>Supporting Branches</u>](#supporting-branches)
    - [<u>Git Flow Process</u>](#git-flow-process)
    - [<u>Version Tags</u>](#version-tags)
- [<u>How To Write README</u>](#how-to-write-readme)
- [<u>Conventional Commits</u>](#conventional-commits)


## Popular Git Commands:
### Basic Commands:
#### `git init`: Khởi tạo một Git repo mới trong thư mục hiện tại.
```
git init
```

#### `git clone`: Sao chép một Git repo từ một máy chủ từ xa(remote).
```
git clone https://github.com/user/repo.git
```

#### `git status`: Hiển thị trạng thái hiện tại của thư mục dang làm việc(working directory) và khu vực staging(khu vực được chuẩn bị commit).
```
git status
```

#### `git add`: Thêm các thay đổi(tệp hoặc thư mục) vào khu vực staging.
```
git add file.txt
git add .    # thêm tất cả các file thay đổi
```

#### `git restore`: Lệnh này được sử dụng để khôi phục hoặc loại bỏ các thay đổi trong working directory và staging area.
```
# Lệnh này sẽ loại bỏ <file> khỏi staging area mà không loại bỏ các thay đổi
git restore --staged <file> 
# Lệnh này sẽ loại bỏ mọi thay đổi đã thực hiện trên <file> kể từ lần commit cuối cùng 
git restore <file> 
```

#### `git commit`: Ghi lại các thay đổi đã được staged vào repo với một msg tương ứng.
```
git commit -m "feat: added server"
git commit --amend -m "feat: add server"  # Ghi đè lên commit cuối cùng 
```

#### `git push`: Đẩy các commit từ local lên remote repo.
```
git push origin <branch_name>
git push -u origin <branch_name>  # Push lần đầu
```

#### `git pull`: Kéo các thay đổi từ remote repo về nhánh local branch.
```
git pull origin <branch_name>
```

### Branch And Merge:
#### `git branch`: Liệt kê, tạo mới, hoặc xoá branchs.
```
git branch  # Liệt kê tất cả các nhánh
git branch <branch_name>  # Tạo một nhánh mới có tên brand_name
git branch -d <branch_name>  # Xoá một nhánh tên branch_name
```

#### `git checkout`: Chuyển sang một nhánh khác.
```
git checkout <branch_name>  # Chuyển sang nhánh branch_name
git checkout -b <branch_name>  # Tạo và chuyển sang nhánh branch_name
```

#### `git merge`: Hợp nhất một nhánh vào nhánh hiện tại.
```
git checkout main
git merge <feature_branch> # Merge nhánh feature_branch vào nhánh main
```

### Remote Repositories:
#### `git remote`: Quản lý các kết nối với remote repo.
```
git remote -v  # Liệt kê các kết nối từ xa
git remote add origin https://github.com/user/repo.git  # Thêm một remote mới
git remote set-url origin https://github.com/user/new_repo.git  # Thay đổi URL của remote repo
```

#### `git fetch`: Cập nhật các thay đổi đã diễn ra trên remote repo về local (chỉ fetch history còn muốn tải các remote update thì cần dùng lệnh pull trên branch tương ứng).
```
git fetch origin
```

### History Commits:
#### `git log`: Hiển thị lịch sử commit.
```
git log
```

#### git diff: Hiển thị thay đổi giữa các commits, branches, hay the working directory.
```
git diff  # Các thay đổi chưa được staged 
git diff --staged  # Các thay đổi đã được staged để commit
git diff <branch_1> <branch_2>  # So sánh hai branch
```

### Revert:
#### `git revert`: Hoàn tác một commit cụ thể bằng cách tạo một commit mới để đảo ngược nó.
```
git revert commit-sha
```

#### `git reset`: (Cẩn trọng khi sử dụng vì có thể mất dữ liệu đã cập nhập trước đó). Reset lại khu vực staging hoặc di chuyển con trỏ nhánh(branch pointer).
```
git reset file.txt  # Huỷ staged một tệp
git reset --hard HEAD^  # Trở về commit trước đó
```

### Staging:
#### `git stash`: Tạm thời lưu các thay đổi chưa sẵn sàng để commit.
```
git stash  # Lưu trữ các thay đổi hiện tại
git stash pop  # Áp dụng lại các thay đổi đã lưu trữ và xoá chúng khỏi stash
git stash list  # Liệt kê tất cả các thay đổi đã lưu trữ
```

### Tagging:
#### `git tag`: Tạo các tag để đánh dấu các commit cụ thể, thường dùng cho các bản phát hành(releases).
```
git tag v1.0  # Tạo một lightweight tag
git tag -a v1.0 -m "Version 1.0"  # Tạo một chú thích tag
git push origin v1.0  # Đẩy tag lên remote repo
```

### Collaboration:
#### `git rebase`: Áp dụng lại các commit trên một nhánh khác lên nhánh hiện tại, hữu ích để làm thẳng hàng, tuyến tính hoá lịch sử commit của các nhánh hiện tại, đồng bộ hoá với các thay đổi từ nhánh khác.
```
git checkout <feature_branch>
git rebase main
```

#### `git cherry-pick`: Áp dụng một commit cụ thể từ một nhánh khác.
```
git cherry-pick commit-sha
```


## Conflicts:
### Resolve Conflicts Git Merge:
- Nhận dạng conflict: Sau khi thực hiện một lệnh merge, Git có thể sẽ thông báo cho bạn về xung đột(thường xảy ra khi repo, branches được team nhiều người cùng thao tác cập nhập sử đổi) `git status`. Lệnh này sẽ được liệt kê các file có xung đột(Conflicts).
- Mở các file bị conflict: Tìm đến các đoạn được đánh dấu xảy ra xung đôt `(<<<<<<<, =======, >>>>>>>)` trong các file:
  + `<<<<<<<` chỉ ra sự bắt đầu của thay đổi của bạn
  + `=======` phân tách thay đổi của bạn và thay đổi từ nhánh khác
  + `>>>>>>>` chỉ ra sự kết thúc của thay đổi từ nhánh khác
- Xử lý xung đột(Resolve the conflict): Chỉnh sửa conflict file bằng cách kết hợp các thay đổi hoặc chọn một update phù hợp nào đó. Xoá cá kí hiệu đánh dấu conflict, và hoàn thành bẳn chỉnh sửa.
- Lưu lại các file conflicts sau khi đã hoàn tất chỉnh sửa `git add <file>`.
- Tiếp tục hoàn thành merge trước đó `git commit`.
- Nếu quá trình merge bị gián đoạn bạn có thể cần dùng `git merge --continue`.
- Kiểm tra lại trạng thái code đã merge: Đảm bảo rằng merge đã thành công và không còn xung đột nào `git status`.
- Cập nhập các thay đổi lên remote repo(Push the changes) nếu cần `git push origin <branch_name>`

### Resolve Conflicts Github Pull Request:
- Navigate to the Pull Request: Truy cập vào Repo trên github, và tìm pull request có xung đột.
- Check Conflict Details: Github sẽ hiển thị thông báo cho biết nhánh có xung đột. Nhấn vào nút Reslove Conflict để
xem các file có xung đột.
- Reslove Conflicts in the Github Editor: Với mỗi một file có xung đột, chỉnh sửa nội dụng để giải quyết sự khác
biệt trực tiếp trong trình chỉnh sửa web của github. Xoá các dấu hiệu xung đột `(<<<<<<<, =======, >>>>>>>)` và đảm bảo code là chính xác.
- Mark as Resolved: Sau khi giải quyết xung đột cho tất cả các file, nhấn Mark as resolved.
-  Commit the Changes: Nhấn nút Commit merge để tạo một commit, bạn có thể tiếp tục Merge pull request vào nhánh đích.
  
## Overview Of Git Flow:
Git Flow là một chiến lược branching để quản lý phát triển tính năng, phát hành và sửa lỗi theo cách có cấu trúc
và mở rộng. Nó giúp các nhóm quản lý việc phát triển song song, cộng tác hiệu quả và xử lý phát hành và sửa lỗi
một cách suôn sẻ. Dưới đây là tổng quan về Git Flow.

### Main Branches:
- main(or master): Branch sẵn sàng cho production, chứa mã ổn định đã được deploy. Tất cả các bản phát hành(releases)
được đánh tag tại đây.
- develop: Branch phát triển chính nơi mã mới nhất cho bản phát hành tiếp theo được tích hợp. Các tính năng và sửa lỗi
được hợp nhất vào develop.

### Supporting Branches:
Git flow sử dụng cấc nhánh bổ sung cho phát triển tính năng, sửa lỗi và phát hành. Mỗi nhánh có vai trò cụ thể:
- Feature Branches(feature/):
  + Dùng để phát triển các tính năng mới
  + Được tạo từ develop và hợp nhất lại vào develop khi hoàn thành
  + Ví dụ: `feature/new-login`

- Release Branches(release/):
  + Dùng để chuẩn bị bản phát hành mới(new release)
  + Được tạo từ develop khi hoàn tất tính năng, cho phép thử nghiệm cuối cùng, sửa lỗi và gắn phiên bản(tag version)
trước khi hợp vào main
  + ví dụ: `release/v1.0`

- Hotfix Branches(hotfix/):
  + Dùng để sửa lỗi nghiêm trọng trên production
  + Được tạo từ main và hợp nhất lại vào cả main và develop để đảm bảo sửa lỗi áp dụng cho cả hai nhánh
  + Ví dụ: `hotfix/fix-payment-bug`
  
### Git Flow Process:
- Phát triển tính năng: Phát triển tạo nhánh feature/ từ develop để làm việc trên tính năng mới. Sau khi hoàn thành,
tính năng sẽ được hợp nhất vào develop

- Phát hành: Khi develop ổn định và sẵng snagf phát hành, một nhánh release./ được tạo để kiểm tra và điều chỉnh cuối
cùng. Khi đã sẵn sàng sẽ được hợp nhất vào main (for production) và develop (for develop).

- Sửa lỗi Hotfixes: Nếu phát hiện lỗi nghiêm trọng trên production, một nhánh hotfix/ được tạo từ main, sửa lỗi, và
sau đó hợp nhất vào cả main và develop để giữ cả hai nhánh được cập nhập

### Version Tags:
Sau khi hợp nhất một release/ hoặc hotfix/ vào main, bạn cần gắn tag cho commit với một số phiên bản tương ứng(ex: v1.0)
để đánh dấu bản phát hành(release).

Tóm tắt các lệnh Git Flow quan trọng:
- Bắt đầu một tính năng mới.
```
# Tạo một nhánh tên feature/abc từ nhánh develop và chuyển sang nhánh feature/abc
git checkout -b feature/abc develop
```

- Hoàn thành một tính năng.
```
# Chuyển sang nhánh develop và merge nhánh feature/abc vào develop
git checkout develop && git merge feature/abc
``` 

- Khởi tạo một bản phát hành release.
```
# Tạo và chuyển sang bản phát hành từ nhánh develop
git checkout -b release/v1.0 develop
``` 

- Hoàn tất bản release.
```
#  Chuyển sang nhánh main và merge nhánh release/v1.0 vào main
git checkout main && git merge release/v1.0
```

- Khởi tạo một hotfix khi có lỗi.
```
# Tạo một nhánh tên hotfix/fix-bug từ nhánh main và chuyển sang nhánh hotfix/fix-bug
git checkout -b hotfix/fix-bug main
```

- Hoàn thành hotfix.
```
# Chuyển sang nhánh main và merge nhánh hotfix/fix-bug vào main
git checkout main && git merge hotfix/fix-bug
```

# How To Write README:
[<ins>See More</ins>](WRITE_READ_ME.md)
# Conventional Commits:
[<ins>See More</ins>](CONVENTIONAL_COMMITS.md)