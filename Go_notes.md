# Go 语言语法学习笔记

## 基础语法

### 1. `package` 和 `import`

- 每个 Go 文件都需要一个 `package` 声明。
- `import` 用于导入其他包。

```go
package main

import (
	"fmt"
	"math/rand"
)
```

### 2. 主函数 `main`

- 程序的入口函数为 `func main()`。

```go
func main() {
	fmt.Println("Hello, World!")
}
```

### 3. 变量声明与 `var` 的作用

- **Go 的特点**：

  - 使用 `var` 声明变量，支持显式类型和自动类型推导。
  - 声明的变量会被初始化为**零值**。
  - 支持批量声明多个变量。

- **语法示例**：
  ```go
  var x int        // 显式声明类型
  var y = 42       // 自动类型推导
  var z, w = 10, 5 // 批量声明多个变量
  ```

---

## 数据类型

### 1. 基本数据类型

| 数据类型  | 描述   |
| --------- | ------ |
| `int`     | 整型   |
| `float64` | 浮点型 |
| `string`  | 字符串 |
| `bool`    | 布尔值 |

```go
var a int = 42
var b float64 = 3.14
var c string = "Go语言"
var d bool = true
```

### 2. 类型推导

- 使用 `:=` 自动推导变量类型。

```go
x := 10       // // 等价于 var x int = 10
name := "Alice"  // 等价于 var name string = "Alice"
```

---

## 控制结构

### 1. 条件语句

```go
if a > b {
	fmt.Println("a 大于 b")
} else {
	fmt.Println("a 不大于 b")
}
```

### 2. 循环语句

- Go 中只有 `for` 一种循环结构。

```go
for i := 0; i < 10; i++ {
	fmt.Println(i)
}

// 类似 while 的写法
n := 0
for n < 5 {
	fmt.Println(n)
	n++
}
```

---

## 函数

### 1. 定义函数

- 使用 `func` 关键字定义函数。

```go
func add(a int, b int) int {
	return a + b
}
```

### 2. 返回多个值

```go
func swap(x, y string) (string, string) {
	return y, x
}
```

---

## 数组与切片

### 1. 数组

```go
var arr [5]int = [5]int{1, 2, 3, 4, 5}
```

### 2. 切片

- 切片是数组的动态视图。

```go
s := []int{1, 2, 3}
s = append(s, 4)
fmt.Println(s) // 输出: [1 2 3 4]
```

---

## Map (字典)

- 使用键值对存储数据。

```go
m := make(map[string]int)
m["Alice"] = 25
m["Bob"] = 30
fmt.Println(m["Alice"])
```

---

## Goroutines 与 Channels

### 1. Goroutines

- 使用 `go` 关键字启动并发任务。

```go
func sayHello() {
	fmt.Println("Hello")
}

go sayHello()
```

### 2. Channels

- 用于 Goroutines 之间的通信。

```go
ch := make(chan int)
go func() {
	ch <- 42
}()

value := <-ch
fmt.Println(value) // 输出: 42
```

---

## 错误处理

- 使用 `error` 类型和 `errors.New` 函数。

```go
import (
	"errors"
	"fmt"
)

func divide(a, b int) (int, error) {
	if b == 0 {
		return 0, errors.New("除数不能为0")
	}
	return a / b, nil
}
```

---

## 面向对象编程

### 1. 定义结构体

```go
type Person struct {
	Name string
	Age  int
}
```

### 2. 方法

```go
func (p Person) SayHello() {
	fmt.Printf("Hello, my name is %s!\n", p.Name)
}
```

### 3. 接口

```go
type Animal interface {
	Speak() string
}

type Dog struct {}

func (d Dog) Speak() string {
	return "Woof!"
}
```

---

## 工具与命令

### 1. 格式化代码

```bash
go fmt
```

### 2. 运行程序

```bash
go run main.go
```

### 3. 编译程序

```bash
go build
```

---

## 常用标准库

| 包名       | 功能           |
| ---------- | -------------- |
| `fmt`      | 格式化输入输出 |
| `math`     | 数学运算       |
| `time`     | 时间处理       |
| `net/http` | HTTP 网络请求  |

```go
import (
	"fmt"
	"time"
)

func main() {
	now := time.Now()
	fmt.Println("当前时间:", now)
}
```
