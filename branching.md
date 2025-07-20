# Branching & Merging

### branching

`git branch vduczz` - create new branch `vduczz`  
`git checkout vduczz`, `git switch vduczz` - switch to vduczz branch  
`git checkout -b vduczz`, `git switch -C vduczz` - create (if not exist) and switch to branch `vduczz`  
`git branch -d vduczz` - delete branch `vduczz`

### branch comparing

`git log branch1..branch2` - list all commits that in the `branch1` and not in the `branch2`  
`git diff branch1..branch2` - show differences between `branch1` and `branch2`

### stashing

Khi cần chuyển branch, cần lưu lại những thay đổi ở branch hiện tại nhưng chưa muốn commit -> lưu thay đổi vào stash, trả repo về trạng thái chưa thay đổi. Khi quay lại branch, có thể lấy lại những thay đổi bằng cách truy vấn stash.  
`git stash push -m 'message'` - save all changes into stash (chỉ áp dụng với tracked files)  
`git stash list` - list all stashes of branch  
`git stash show stash@{i}` - show stash[i]  
`git stash apply stash@{i}` - apply stash[i] to the working directory  
`git stash pop stash@{i}` - apply and drop stash[i]  
`git stash drop stash@{i}` - drop stash[i]  
`git stash clear` - delete all the stashes

### merging

`git merge other-branch` - merging `other-branch` into current branch:

- if merge no conflict: Git tự động gộp và tạo merge commit.
- if merge conflict: change/review conflicting files -> `git add <file>` -> `git commit`

`git merge --no-ff other-branch` - luôn tạo ra một commit merge mỗi khi merge branch.  
`git merge --squash other-branch` - gộp other-branch vào branch hiện tại nhưng không thêm lịch sử commit của other-branch, chỉ tạo 1 đại diện cho tất cả bằng lệnh `git commit -m 'message'`  
`git merge --abort` - bỏ merge nếu có conflict.

### view the merged branches

`git branch --merged` - list all branches that merged into current branch  
`git branch --no-merged` - show unmerged branches

### rebasing

`git rebase main` - chuyển nhánh làm việc hiện tại lên đầu master (cắt những commit của master dán vào cuối commit đầu tiên sau rẽ nhánh), cụ thể:

- nếu dùng `git merge master`

```
A---B---C
 \       \
  D---E---M   feature
```

- nếu dùng `git rebase master`

```
A---B---C
          \
           D'---E'   feature
```

Những thay đổi mới nhất ở commit C sẽ được áp dụng lên nhánh feature, nhánh làm việc hiện tại vẫn là nhánh feature và nhánh master không bị ảnh hưởng. Nếu có conflict, cần làm các bước sau:

- Mở file xung đột và fix.
- `git add <conflict_file>`
- `git rebase --continue`

`git rebase --abort` - hủy rebase vì conflict, ...

### cherry-pick

`git cherry-pick <commit>` - áp dụng commit từ 1 nhánh khác vào nhánh hiện tại (tạo commit mới có nội dung tương tự commit chỉ định).  
Khi xảy ra conflict, cần:

- mở file và fix.
- `git add <file>`
- `git cherry-pick --continue`

`git cherry-pick --abort` - hủy cherry-pick
