
```bash
# 初始化 Git 仓库
$ git init git-lfs-demo
$ cd git-lfs-demo
# 初始化 Git LFS 配置文件，会在当前目录生成 ..gitattributes 文件，该文件记录仓库中的哪些文件被 Git LFS 跟踪
$ git lfs install
# 将 images 文件夹中的所有文件交给 Git LFS 管理，该命令执行后，在 .gitattributes 文件中就会添加相应的记录
$ git lfs track images/*
$ git add .
$ git commit -m 'Initial commit'
$ git remote add origin git@github.com:4demo/git-lfs-demo.git
$ git push -u origin master
```

克隆仓库到本地，并查看被 Git LFS 管理的文件内容
```bash
$ git clone git@github.com:4demo/git-lfs-demo.git
$ cd git-lfs-demo
$ cat images/GitHub.jpg
version https://git-lfs.github.com/spec/v1
oid sha256:83725d67429b6992643f9fa688967b7a98fe2736b368631733e208b79d6fbc7b
size 51695
```

从上面的输出可以看出，远程仓库中存储的实际是原文件的一个指针文件，指针文件中记录了 Git LFS 服务版本、原文件的标识、以及原文件的大小。

那如何才能得到原文件呢？只需要执行下面的命令

```bash
$ git lfs pull
```