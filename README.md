# go2go
learning golang

##概述
- 使用var定义变量,支持类型推断；在函数内部可省略var
- 表达式
```go
    if x > 0 {
        ...
    } else if x <0 {
        ...
    } else{
        ...
    }

    switch{
        case x > 0:
            ...
        case x < 0:
            ...
        default:
            ...
    }

    for i := 0; i < 5; i++{
        ...
    }

    for x < 5 {
        ...
    }

    for {
        ...
    }

    x := []int{100, 101, 102}
    for i,n := range x{
        println(i, ":", n)
    }
```
```
    0:100
    1:101
    2:102
```

- 函数
    - 函数可以有多个返回值
    ```go
    func div(a,b int)(int,error){
        if b ==0{
            return 0, errors.New("division by zero")
        }
        return a/b, nil
    }

    a,b := 10,2
    c,err := div(a,b)
    fmt.Println(c,err)
    ```
    - 函数是第一类型，可以作为参数或者返回值
    ```go
    func test(x int) func(){
        return func(){
            println(x)
        }
    }

    x := 100
    f := test(x)
    f()
    ```
    - 用defer定义**延迟调用**，无论函数是否出错，它都确保结束前被调用
    ```go
    func test(a,b int){
        defer println("dispose")

        println(a/b)
    }

    test(10,0)
    ```
    ```
    dispose
    panic: runtime error: integer divide by zero
    ```
- 数据
    - 切片