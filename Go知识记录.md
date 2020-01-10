### 1. Go之`for-range`
`for-range`其实是for循环的语法糖，内部还是调用的for循环，初始化时会拷贝待遍历的列表（如：slice、array、map）。
```
for _, v := range arr {
  fmt.println(v)
}
```
每次遍历的v都是对同一个变量的遍历赋值，也就是说，如果直接对v取地址，最终得到的始终时同一个地址，而对应的值则是最后赋给v的值。
