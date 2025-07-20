### clone a repo

`git clone <URL>`

### fetching

`git fetch origin master` - lấy nhánh master từ remote origin về.  
`git fetch` / `git fetch origin` - lấy tất cả các nhánh, commits, tag từ origin  
`git merge origin/<branch>` - áp dụng nhánh `branch` vào nhánh hiện tại ở local.

### pulling

`git pull` - lấy nhánh tương ứng ở remote origin và merge vào nhánh local hiện tại.

### pushing

`git push origin <branch>` - đẩy nhánh `branch` từ local lên remote origin.  
`git push` đẩy nhánh hiện tại lên remote origin

### sharing tags

`git push origin v1.0` - đẩy tag `v1.0` lên remote.  
`git push origin --delete v1.0` - xóa tag `v1.0` trên remote

### sharing branches

`git branch -r` - liệt kê các nhánh của remote mà local đang theo dõi. ex: main của remote đang được theo dõi bởi main của local  
`git branch -vv` - liệt kê các nhánh local (+ commit mới nhất trên nhánh local) kèm thèo thông tin nhánh remote tương ứng  
`git push -u origin <branch>` - push branch lên remote
`git push -d origin <branch>` - delete branch trên remote

### managing remotes

`git remote` - hiển thị danh sách các remote ứng với local repo  
`git remote add <name> <URL>` - tạo remote mới ứng với `URL` và gọi là `name`  
`git remote rm <name>` - xóa remote `name`
