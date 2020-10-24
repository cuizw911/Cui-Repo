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

### 6.protoc命令

protoc的命令格式为 protoc [optinon] PROTO_FILES （最后是待编译的proto文件）
```bash
$ protoc --go_out=plugins=grpc:./go/ ./proto/helleworld.proto
```
* --go_out 为输出目录。

```bash
$ protoc -I=proto --go_out=plugins=grpc:./go/ ./proto/helleworld.proto
```
* -I 相当于--proto_path的缩写，指定查找proto文件的目录。可以多次指定，执行时将按顺序查找。   
* 简单来说，就是如果多个proto文件之间有互相依赖，生成某个proto文件时，需要import其他几个proto文件，这时候就要用-I来指定搜索目录。   
* 如果没有指定，则在当前目录查找。   
* -I参数起作用后，生成的目录将不包括-I指定的目录。

### 7.beego打包部署（windows）
1) 利用bee工具打包成exe可执行文件。命令：bee pack -be GOOS=windows

2) 利用[nssm](https://www.cnblogs.com/TianFang/p/7912648.html)工具将exe打包成windows服务，然后启动服务即可。
