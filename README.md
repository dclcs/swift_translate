# swift_translate
### The Basics

#### A. 变量和常量

- fundamental types
  - Integers : `Int`
  - Floating-point values : `Double` and `Float`
  - Boolean values : `Bool`
  - texual data : `String`
  - Three primary type
    - `Array`, `Set`, `Dictionary`

- 常量和变量

  - 常量的值一旦被定义好就不会被改变

  - 变量的值可以变化

  - 常量和变量的声明

    ```swift
    let maximumNumberOfLoginAttempts = 10
    var currentLoginAttempt = 0
    ```

  - 可以在一行声明多个常量和变量，通过逗号分隔

    ```swift
    var x = 0.0, y = 0.0, z = 0.0
    ```

- 类型标注（Type Annoation）

  - 可以在变量名后加上冒号来标记变量的类型

  ```swift
  var welcomeMessage : String
  welcomeMessage = "Hello World"
  
  var green, red, blue : Double 
  ```

  

- 变量和常量的命名

  - 常量名和变量名可以是任意的Unicode字符

  ```swift
  let π = 3.14159
  let 你好 = "你好世界"
  let 🍘🍜 = "dogcow"
  ```

  - 变量名/常量名不能包含空白，数学符号，箭头，Unicode的标量字符
  - 变量名/常量名可以以数字开头

- 打印变量和常量

  ```swift
  //print(_:seperator:terminator:)
  print(friendlyWelcome)
  
  print("The current value of friendlyWelcome is \(friendlyWelcome)")
  ```

  

#### B. 注释

```swift
// this is a comment
/*This is also a comment*/
```

#### C.分号

Swift 不需要在语句后面加上分号，但是如果你想在一行写多个语句，需要用分号隔离

#### D. 整数

- Swift 提供8、16、32 和 64 的有符号和无符号整数，

- 整数边界

  ```swift
  let minValue = UInt8.min
  let maxValue = UInt8.max
  ```

- Int

  - 在一个32bit机器上， `Int`和`Int32`的大小一样
  - 在一个64bit机器上， `Int`和`Int64`的大小一样
  - 所以你的代码一般要写`Int`

#### E. 浮点数

- `Double` 代表64位浮点数
- `Float` 代表32位浮点数