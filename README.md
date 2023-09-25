# Learning-Git

# I. Kết hợp lệnh

Bình thường khi ta muốn commit 1 file ta thường dùng 2 command line này

```php
git add .
git commit -m "Update sth"
```


- Ta có 1 cách đơn giản để có thể kết hợp 2 lệnh đó thông qua (Sửa cờ từ `-m` thành `-am`).

```php
git commit -am "Update sth"
```

Chú ý: Command line `git commit -am "Update sth"` chỉ đúng với những file mà đã được track trước đó (nghĩa là đã được `git add` rồi). Còn với những file vừa được tạo mới hoặc chưa được track, thì nó sẽ không đúng. Nên ta phải hiểu rằng `git commit -am "Update sth"` không tương đương với 2 lệnh ở đầu tiên, mà nó chỉ tương đương trong trường hợp tất cả các file đều đã được track.

Để kết hợp lệnh được thì ta phải sử dụng `alias` như dưới đây.

```php
git config --global alias.viet '!git add -A && git commit -m'
```

- Cờ `--global` chop phép sử dụng trên toàn bộ máy mac của mình (ứng với mọi `repo` trên máy mình) chứ ko phải riêng `repo` được alias.

Lúc này ta chỉ cần

```php
git viet "Add alias viet"
```

# II. Ghi đè message trước đó

Ta sử dụng 

```php
git commit --amend -m "Update latest message commit"
```

Sử dụng thêm cờ `--amend` ta sẽ update message của commit trước đó. Chú ý nó chỉ có tác dụng duy nhất là update message của commit trước đó thôi nhé, chứ không `track` hay `update các file vừa được modifiled`.

# III. Reset Commit

Ờ `git reset` ta có 2 cờ:
- `--solf`: Sẽ reset các commit trước đó nhưng `vẫn muốn lưu các thay đổi` của mình trên branch ta đang làm và có thể mang sự thay đổi đó sang branch khác.
- `--hard`: Sẽ reset các commit trước đó nhưng `không muốn lưu các thay đổi` (remove everything).

Ta có thể sử dụng 2 kiểu như sau:

```php
git reset --soft HEAD~2      //Reset về 2 commit trước đó
git reset --hard debf3c31b73399b101562085b80462dc931b7431
```

# IV. Watch log clearer and Read Code in github

```php
git log --graph --decorate --oneline
```

Đôi khi ta ko muốn clone project về mà chỉ muốn đọc code thì ta chỉ cần mở `repo` lên sau đó nhân phím `.`