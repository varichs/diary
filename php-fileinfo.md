# 前因

使用的是阿里云1核1G的机器，源码编译安装PHP7.2的时候， 添加--fileinfo会导致内存不足，中断编译；
而后用到此扩展，继续从源码中编译添加此扩展，依旧因为内存不足报错中断

```shell
dd if=/dev/zero of=/swap bs=1024 count=1M
mkswap /swap
swapon /swap
echo "/swap  swap  swap  sw  0  0" >> /etc/fstab
```

通过swap临时解决

## 新的问题，添加扩展后无法加载，提示找不到

在扩展源码目录中

```shell
make clean
phpize
./configure --prefix= --with-php-config=php-config
make && make install

```

重新添加就好