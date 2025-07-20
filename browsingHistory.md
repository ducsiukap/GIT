# Browsing History - view commit history in repo

### View commit history

`git log` - xem log đầy đủ  
`git log --stat` - commit history + list of modified files in each commit  
`git log --patch` - commit history + diff  
`git log file.a`, `git log --stat file.a`, `git log --patch file.a` - chỉ log thông tin liên quan tới `file.a`, trong các commit mà `file.a` bị thay đổi.

### Filtering history

`git log -n` - show n-lastest commit  
`git log --author="vduczz"` - only show commits of `vduczz`  
`git log --before="2025-02-02"`, `git log --after="2025-02-02"` - show only the commits before/after a period of time  
`git log --grep="text"` - show only commits whose message contains the message "text"  
`git log -S"Text"` - tìm commit có chưa "Text" trong phần thay đổi (Thêm/xóa) của file.  
`git log hash1..hash2` - hiển thị các commits có mã hash từ sau hash1 (không gồm hash1) tới hash2 (gồm cả hash2)

### Formating the log output

`git log --pretty=format:"pattern"` - log theo pattern, trong đó:

- `%H` : mã hash đầy đủ của commit
- `%h` : mã hash rút gọn của commit
- `%an` : author's name
- `%ae` : author's email
- `%s` : commit's message
- `%ad` : commit's date

### View a commit

`git show hash` - xem commit có mã hash tương ứng  
`git show HEAD`, `git show HEAD~n` - xem commit gần nhất / commit thứ n+1 gần nhất  
`git show hash:file.abc` - xem nội dung file `file.abc` trong commit có mã hash tương ứng.

### Comparing commits

`git diff hash1 hash2` - so sánh toàn bộ các file và show phần khác nhau của 2 commit có mã hash là hash1 và hash2  
`git diff hash1 hash2 file.abc` - so sánh `file.abc` ở 2 commit có mã hash1 và hash2

### Checkout a commit

`git checkout <hash>` - quay về commit có mã hash  
Nếu có bất cứ thay đổi nào ở commit cũ, cần tạo nhánh mới sau đó mới commit! `git checkout -b new-branch`
`git checkout main` - quay về nhánh chính.

```
A --- B --- C  (main)
       \
        D --- E  (new-branch)
```

### Finding a bad commit (bug)

`git bisect start` - khởi động quá trình bisect, cần chỉ ra 2 commit (khoảng cách tìm kiếm):

- `git bisect bad` - đánh dấu commit hiện tại là lỗi (có bug)
- `git bisect good <commit>` - đánh dấu commit cụ thể không có lỗi.

Sau đó, Git thực hiện tìm kiếm nhị phân, lấy phần tử ở giữa để bạn đánh dấu => thu hẹp phạm vi tìm kiếm:

- `git bisect bad` - đánh dấu commit đang xét là bad
- `git bisect good` - đánh dấu commit đang xét là good

=> Kết thúc quá trình bisect, git xác định được commit đầu tiên gây lỗi (commid cũ nhất được đánh dấu bad).  
`git bisect reset` - kết thúc phiên git bisect

### Finding contributors.

`git shortlog` - tóm tắt lịch sử commit (message) và nhóm theo tác giả

### Finding the authors of lines

`git blame file.abc` - show tác giả của từng dòng trong file `file.abc`

### Tagging the commit

`git tag v1.0` - gắn tag `v1.0` cho commit mới nhất (HEAD)  
`git tag <tag> <commit>` - gắn tag chỉ định cho commit chỉ định.
`git tag -d v1.0` - xóa tag `v1.0`  
`git tag` - liệt kê tất cả các tag.  
Sử dụng tag như là mã hash của commit nó được gắn.
