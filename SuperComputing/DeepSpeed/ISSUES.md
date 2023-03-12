# 常见问题及解决

<br>

## 如何让多台LINUX主机无密码ssh连接？

### TODO

使用`sudo su`时，是在`root`用户下进行的操作，`ssh-keygen -t rsa`操作的`.ssh`目录默认是放在`/root/.ssh`目录下的，如果是指定用户，则默认的操作目录是`~/.ssh`。区别在于，我们通过ssh无密码能够链接的节点也不一样：`root@ip`和`username@ip`的区别。

- [ ] deepspeed的多节点调用是在哪种用户下调用的，或者两个用户都可以？

### Ref:
1. [ubuntu设置远程无密码登录ssh秘钥认证](https://blog.csdn.net/xyh930929/article/details/84531081)
2. [多台Linux主机无需密码直接连接的SSH配置](https://blog.csdn.net/hq86937375/article/details/69218201)

