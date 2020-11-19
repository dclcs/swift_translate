# The Basics

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

#### F. 类型安全和类型推断

- 类型安全： Swift是一种类型安全的语言，所以你必须明确清楚代码的类型
- 类型推断： 但是，你不需要明确的给每一个变量明确类型，

```swift
let meaningOfLife = 42 // meaningOfLife 被推断出是一个整形
let pi = 3.14156 //pi 推断出是一个浮点数
```

#### G. 数值字面量

- 十进制数 ： 没有前缀
- 二进制数 ： 前缀 0b
- 八进制数 ： 前缀0o
- 十六进制数 ：0x

#### H. 数值类型转换

- 整数转换

  - 不同整数类型的变量和常量可以存储不同范围的数字。`Int8` 类型的常量或者变量可以存储的数字范围是 `-128`~`127`，而 `UInt8` 类型的常量或者变量能存储的数字范围是 `0`~`255`。如果数字超出了常量或者变量可存储的范围，编译的时候会报错：

  ```swift
  let cannotBeNegative : UInt8 = -1 //Wrong
  let notBig : UInt8 = UInt8 + 1 //Wrong
  ```

  - `SomeType(ofInitialValue)` 是调用 Swift 构造器并传入一个初始值的默认方法。在语言内部，`UInt16` 有一个构造器，可以接受一个 `UInt8` 类型的值，所以这个构造器可以用现有的 `UInt8` 来创建一个新的 `UInt16`。注意，你并不能传入任意类型的值，只能传入 `UInt16` 内部有对应构造器的值。不过你可以扩展现有的类型来让它可以接收其他类型的值（包括自定义类型）

- 整数和浮点数转换

  - 整数和浮点数的转换必须显式指定类型：

  ```swift
  let three = 3
  let pointOneFourOneFiveNine = 0.14159
  let pi = Double(three) + pointOneFourOneFiveNine
  // pi 等于 3.14159，所以被推测为 Double 类型
  ```

#### I. 类型别名

- Type aliases, 给现有类型定义另一个名字

  ```swift
  typealias AudioSample = UInt16
  var testVar = AudioSample.min
  ```

#### J. Boolean

#### K. 元组

- 定义元组

  ```swift
  let http404Error = (404, "Not Found")
  //http404Error 类型是 (Int, String)
  ```

- 元组的分解（decompose）

  ```swift
  let (statusCode, statusMessage) = http404Error
  let (justTheStatusCode, _) = http404Error
  print(\(http404Error.0))
  print(\(http404Error.1))
  ```

- 定义元组的时候给单个元素命名

  ```swift
  let http200Status = (statusCode: 200, description: "OK")
  print("The status code is \(http200Status.statusCode)")
  // 输出 "The status code is 200"
  print("The status message is \(http200Status.description)")
  // 输出 "The status message is OK"
  ```

#### L. 可选类型(Optionals)

来看一个例子。Swift 的 `Int` 类型有一种构造器，作用是将一个 `String` 值转换成一个 `Int` 值。然而，并不是所有的字符串都可以转换成一个整数。字符串 `"123"` 可以被转换成数字 `123` ，但是字符串 `"hello, world"` 不行。

下面的例子使用这种构造器来尝试将一个 `String` 转换成 `Int`：

```swift
let possibleNumber = "123"
let convertedNumber = Int(possibleNumber)
// convertedNumber 被推测为类型 "Int?"， 或者类型 "optional Int"
```

因为该构造器可能会失败，所以它返回一个*可选类型*（optional）`Int`，而不是一个 `Int`。一个可选的 `Int` 被写作 `Int?` 而不是 `Int`。问号暗示包含的值是可选类型，也就是说可能包含 `Int` 值也可能*不包含值*。（不能包含其他任何值比如 `Bool` 值或者 `String` 值。只能是 `Int` 或者什么都没有。）



- nil

  - 你可以给可选变量赋值为 `nil` 来表示它没有值：

    ```swift
    var serverResponseCode: Int? = 404
    // serverResponseCode 包含一个可选的 Int 值 404
    serverResponseCode = nil
    // serverResponseCode 现在不包含值
    ```

- If 语句以及强制解析

  - 你可以使用 `if` 语句和 `nil` 比较来判断一个可选值是否包含值。你可以使用“相等”(`==`)或“不等”(`!=`)来执行比较。

    如果可选类型有值，它将不等于 `nil`：

    ```swift
    if convertedNumber != nil {
        print("convertedNumber contains some integer value.")
    }
    // 输出 "convertedNumber contains some integer value."
    ```

  - 当你确定可选类型确实包含值之后，你可以在可选的名字后面加一个感叹号（`!`）来获取值。这个惊叹号表示“我知道这个可选有值，请使用它。”这被称为可选值的*强制解析（forced unwrapping）*：

    ```swift
    if convertedNumber != nil {
        print("convertedNumber has an integer value of \(convertedNumber!).")
    }
    // 输出 "convertedNumber has an integer value of 123."
    ```

    

- 可选绑定

  - 使用*可选绑定（optional binding）*来判断可选类型是否包含值，如果包含就把值赋给一个临时常量或者变量。可选绑定可以用在 `if` 和 `while` 语句中，这条语句不仅可以用来判断可选类型中是否有值，同时可以将可选类型中的值赋给一个常量或者变量。`if` 和 `while` 语句

  - 像下面这样在 `if` 语句中写一个可选绑定：

    ```swift
    if let constantName = someOptional {
        statements
    }
    ```

    

  - example

    ```swift
    if let actualNumber = Int(possibleNumber) {
        print("\'\(possibleNumber)\' has an integer value of \(actualNumber)")
    } else {
        print("\'\(possibleNumber)\' could not be converted to an integer")
    }
    // 输出 "'123' h
    ```

    - 这段代码可以被理解为：

      “如果 `Int(possibleNumber)` 返回的可选 `Int` 包含一个值，创建一个叫做 `actualNumber` 的新常量并将可选包含的值赋给它。”

      如果转换成功，`actualNumber` 常量可以在 `if` 语句的第一个分支中使用。它已经被可选类型 *包含的* 值初始化过，所以不需要再使用 `!` 后缀来获取它的值。在这个例子中，`actualNumber` 只被用来输出转换结果。

#### M. Error Handling

#### N. 断言和先决条件

- 使用断言进行调试

  - 你可以调用 Swift 标准库的 `assert(_:_:file:line:)` 函数来写一个断言。向这个函数传入一个结果为 `true` 或者 `false` 的表达式以及一条信息，当表达式的结果为 `false` 的时候这条信息会被显示：

  ```swift
  let age = -3
  assert(age >= 0, "A person's age cannot be less than zero")
  // 因为 age < 0，所以断言会触发
  ```

- 强制执行先决条件

  - 当一个条件可能为假，但是继续执行代码要求条件必须为真的时候，需要使用先决条件。例如使用先决条件来检查是否下标越界，或者来检查是否将一个正确的参数传给函数。

    你可以使用全局 `precondition(_:_:file:line:)` 函数来写一个先决条件。向这个函数传入一个结果为 `true` 或者 `false` 的表达式以及一条信息，当表达式的结果为 `false` 的时候这条信息会被显示

  ```swift
  // 在一个下标的实现里...
  precondition(index > 0, "Index must be greater than zero.")
  ```

  

