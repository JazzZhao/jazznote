## 初次使用gitbash
1. 首先需要在Git网站上面注册自己的帐号
2. 安装gitbash软件并初始用户配置

```java
git config --global user.name "userName"
git config --global user.email "userName@hot.com"
```

该配置会写入`gitconfig`文件中

3. 在gitbash中生成git私钥

```java
ssh -keygen -t rsa -C "userName@hot.com"
```

然后用编辑器打开id_rsa.pub,复制里面的内容到git网站中的ssh设置中

