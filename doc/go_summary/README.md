## Go知识总结



### 1. Go之`for-range`
`for-range`其实是for循环的语法糖，内部还是调用的for循环，初始化时会拷贝待遍历的列表（如：slice、array、map）。

```
for _, v := range arr {
  fmt.println(v)
}
```
每次遍历的v都是对同一个变量的遍历赋值，也就是说，如果直接对v取地址，最终得到的始终时同一个地址，而对应的值则是最后赋给v的值。


### 2.在windows中编译Linux的可执行文件  
```bash
SET CGO_ENABLED=0 
SET GOOS=linux 
SET GOARCH=amd64 
go build  test.go
```
注意：只能使用cmd。


### 3.Go之`select`

如果多个case同时就绪时，select会随机地选择一个执行，这样来保证每一个channel都有平等的被select的机会。