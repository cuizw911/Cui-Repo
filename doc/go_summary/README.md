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


### 4.go build参数
``` 
禁用编译器优化和内联优化
go build -gcflags="-N -I"
```

### 5. go test
```
go test 默认执行当前目录下以xxx_test.go的测试文件。
go test -v 可以看到详细的输出信息。
go test -v xxx_test.go 指定测试单个文件，但是该文件中如果调用了其它文件中的模块会报错。
go test -v xxx_test.go Testxxx   指定某个测试函数运行
go test -cover ./... 测试覆盖率
```
