## Git常用操作汇总

* ##### 查看当前分支是基于哪个分支创建的

  切换到要查询的分支下，输入

  ```bash
  git reflog --date=local --all | grep 要查询的分支名称
  ```

  