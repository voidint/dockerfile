### 使用方式
```
# docker build -t grub-crypt:1.0 .
# docker run -it grub-crypt:1.0 // 等价于加上"--sha-512"选项
# docker run -it grub-crypt:1.0 --sha-512
# docker run -it grub-crypt:1.0 --sha-256
# docker run -it grub-crypt:1.0 --md5
```