# commit & restore

### Khởi tạo repository

Khởi tạo repo tại thư mục đang đứng: `git init`  
Tạo file `.gitignore` để ẩn các file quan trọng/ riêng tư: `echo "" > .gitignore`

### Xem trạng thái các file:

Xem trạng thái đầy đủ:  
`git status`  
Xem trạng thái ngắn gọn:
`git status -s`

### Stage aera ?

Stage Area (Index) là khu vực trung gian giữa thư mục làm việc hiện tại (Working Directory) và khu vực lưu trữ (Repo/HEAD). Ứng với từng khu vực, file sẽ có các trạng thái khác nhau:

- Modified: chỉnh sửa, chưa add.
- Staged: đã add, chờ commit
- Committed: file đã lưu vào repo (ở 1 commit nào đó)

=> Stage: Khu vực chuẩn bị các file để commit giúp chọn lọc những file cần thiết, gom nhiều file trong cùng 1 commit. Đơn giản hơn, stage giúp giữ lại phiên bản đã chỉnh sửa của một số file được chỉ định trên máy (Working Directory) thông qua `git add` và chưa commit. Sửa, add, ... cho tới khi commit.

### add modified files into stage

`git add file1.a file2.b file3.c` - add các file được chỉ định  
`git add *.js` - add theo pattern \*.js  
`git add .` - add tất cả các file trong thư mục hiện tại vào stage

### remove, rename, move files:

`git rm -rf .git` - xóa repo (không theo dõi thư mục hiện tại nữa)  
`git rm file.abc` - xóa `file.abc` ở cả directory và staging  
`git rm --cached file.abc` - xóa file `file.abc` khỏi staging  
`git mv file1.a file2.b` - đổi tên / di chuyển file 1 thành / sang file2

### commit file

#### với staged file:

`git commit -m 'message'` - commit all staged files với thông điệp message  
`git commit` - mở editor để viết message nếu message dài.

#### với unstaged file:

`git commit -am 'message'` - commit tất cả các tracked file (các file đã xuất hiện ở commit nào đó), bỏ qua staging (không áp dụng với untracked file)

### view change

`git diff` - working directory vs staging  
`git diff --cached` or `git diff --staged` - staging vs repo

### view commit history

`git log` - full commit history  
`git log --oneline` - brief commit history  
`git log --reverse` - oldest to lastest.

#### view detail a commit

`git show <hash>` - xem commit cụ thể thông qua mã HASH của commit đó  
`git show HEAD` - view lastest commit  
`git show HEAD~2` - HEAD trỏ tới commit mới nhất, HEAD~1 -> lùi 1 bước, HEAD~2 -> lùi 2 bước, ...  
`git show HEAD:file.js` - xem chi tiết file.js ở lần commit gần nhất.

### unstaging file

`git restore --staged file.a` - loại bỏ `file.a` ở stage, giữ nguyên file ở working directory.

### discard local changes

`git restore file1.a file2.b` - hủy thay đổi đối với các file được chỉ định trong working directory về giống phiên bản trong staging / commit gần nhất (nếu staging trống)  
`git restore .` - hủy thay đổi tất cả các file trong working directory  
`git clean -fd` - delete untracked files/directory.

### restore an earlier version of a file

`git restore --source=HEAD file.a` - khôi phục `file.a` về phiên bản của nó ở commit gần nhất HEAD.
