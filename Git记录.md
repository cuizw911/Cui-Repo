### 查看当前的git分支是基于哪个分支创建的

1.在命令行，切换到要查询的分支下

2.输入：

```
git reflog --date=local --all | grep 要查询的分支名称
```