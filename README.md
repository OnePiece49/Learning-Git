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
git config --global alias.viet `!git add -A && git commit -m`
```