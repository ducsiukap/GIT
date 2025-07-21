### Undoing commit - remove or roll back an older commit - `git reset`

|          command           |         commit          |            staging             |             working directory              |
| :------------------------: | :---------------------: | :----------------------------: | :----------------------------------------: |
| `git reset --soft HEAD~n`  | remove n-lastest commit | all change in n-lastest commit |            current working dir             |
| `git reset --mixed HEAD~n` | remove n-lastest commit |  empty (use `git add` to add)  |            current working dir             |
| `git reset --hard HEAD~n`  | remove n-lastest commit |             empty              | roll-back wd to lastest commit after reset |

##### Note

- `HEAD~n` - n-lastest commits, `HEAD^n` - n-th parents commit (with merge commit)

- `--soft`, `--mixed` cơ bản là giống nhau, chỉ khác
  nhau việc `--soft` tự động add thay đổi trong khi việc đó phải làm thủ công thông qua `git add` đối với `--mixed`. Việc này không quá ảnh hưởng do `working directory` vẫn là phiên bản mới nhất(phiên bản trước reset).

- cẩn thận khi dùng `--hard` vì nó xóa sạch những thay đổi mới nhất trước reset, kể cả ở `working directory`. Nó đưa mọi thứ về commit "mới nhất" sau reset.

#

### Reverting commits - `git revert` - tạo commit mới nhằm quay lại commit cũ mà không làm mất lịch sử commit.

`git revert <commit>` - loại bỏ những thay đổi ở commit được chỉ định.  
`git revert HEAD~n..` - loại bỏ thay đổi ở n commit mới nhất.  
`git revert --no-commit HEAD~3..` - chỉ cần tạo 1 commit sau khi revert xong, không cần commit ở mỗi bước trong quá trình revert.

##### Giả sử ta có lịch sử commit:

```
A -> B -> C -> D -> E (HEAD, main)
```

khi này:

- `git revert HEAD~2` or `git revert <Hash C>`: tạo 1 commit mới hủy bỏ tất cả các thay đổi của commit C và giữ nguyên các thay đổi ở commit D, E. Cụ thể:

```
A -> B -> C -> D -> E -> C' (B + D + E) (HEAD, main)
```

- `git revert HEAD~2..`: tạo lần lượt các commit mới nhằm hủy các thay đổi ở 2 commit mới nhất (E và D)

```
A -> B -> C -> D -> E -> E'(D) -> D'(C) (HEAD, main)
```

- `git revert --no-commit HEAD~2..`: hủy tất cả các thay đổi ở 2 commit mới nhất. Ở mỗi lần rollback, không cần commit mà chỉ cần commit sau khi thực hiện xong revert.

```
A -> B -> C -> D -> E -> F (E' -> D' = C) (HEAD, main)
```

=> `git revert <commit>` dễ xảy ra conflict hơn so với `git revert <commit>..`

#

### Recovering lost commits - `git reflog` - ghi lại mọi hoạt động của HEAD tại local và hoàn toàn cục bộ (chỉ lưu tại local).

`git reflog` - liệt kê mọi hoạt động của HEAD, kể cả commit, checkout, reset, .....

```
8fec23c (HEAD -> main, origin/main) HEAD@{0}: commit: add branching, colaboration
2d303ad HEAD@{1}: checkout: moving from vduczz to main
2d303ad HEAD@{2}: checkout: moving from main to vduczz
2d303ad HEAD@{3}: checkout: moving from vduczz to main
2d303ad HEAD@{4}: checkout: moving from main to vduczz
2d303ad HEAD@{5}: commit: add setupGit, snapshots and browsing history
e64d96d HEAD@{6}: checkout: moving from main to main
e64d96d HEAD@{7}: checkout: moving from main to main
e64d96d HEAD@{8}: commit (initial): add cheatsheet
```

#### khi này, muốn quay lại trạng thái nào của HEAD, có thể sử dụng: `git checkout <hash>` or `git reset --hard <hash>`. Trong đó, `<hash>` có thể là:

- `HEAD@{i}`
- `hash` của `HEAD@{i}`.

ex: sử dụng `git reset --hard 2d303ad` hay `git reset --hard HEAD@{5}` đều đưa `HEAD` về trạng thái của `HEAD@{5}`.

#### Điều này cực kì hữu ích trong các trường hợp muốn cứu lại các commit, công việc đã mất.

`git reflog show <branch>` - hiển thị hoạt động của branch cụ thể

#

### `git commit --amend` - modify last commit.

`git commit --amend` - loại bỏ commit cuối cùng (mới nhất), thêm những thay đổi ở commit đó vào `staging area` hiện tại (lúc này, `staging area` gồm file đã được add sau commit mới nhất và thay đổi của commit mới nhất), giữ nguyên `working dir` hiện tại. (tương tự `git reset --soft HEAD^1`). Điểm khác biệt là lệnh này tự động mở `editor` để tạo commit thay thế commit hiện tại (sửa message của commit).

### Interactive rebasing

[git interactive rebase - Undo, Edit & Squash git commits with a single command](https://www.youtube.com/watch?v=42392W7SgnE)
