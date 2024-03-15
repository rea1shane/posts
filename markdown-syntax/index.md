---
title: Markdown 语法
summary: 一些基本的示例。
tags: [markdown]
date: 2020-10-02
lastmod: 2024-03-14
---

Markdown 是一种轻量级标记语言，它允许人们使用易读易写的纯文本格式编写文档。

## Heading 标题

`H1` - `H6` 代表六个级别的章节标题，`H1` 是最高的章节级别，`H6` 是最低的。语法：

```
# H1

## H2

### H3

#### H4

##### H5

###### H6
```

效果：

# H1

## H2

### H3

#### H4

##### H5

###### H6

## Paragraph 段落

{{< admonition note >}}
不同的段落之间需要有一行空行，如果没有空行的话会被视为同一段落，回车符会被视为空格。
{{< /admonition >}}

语法：

```
不同的段落之间需要有一行空行。

如果没有空行的话会被视为同一段落
回车符会被视为空格
```

效果：

不同的段落之间需要有一行空行。

如果没有空行的话会被视为同一段落
回车符会被视为空格

## Blockquote 块引用

块引用表示从其他来源引用的内容。语法：

```
> > 引用的引用。
>
> 引用。
```

效果：

> > 引用的引用。
>
> 引用。

## Footnote 脚注

语法：

```
这是一个脚注。[^1]

[^1]: 这是脚注的内容。

这是另一个脚注。[^2]

[^2]: 这是另一个脚注的内容。
```

效果：

这是一个脚注。[^1]

[^1]: 这是脚注的内容。

这是另一个脚注。[^2]

[^2]: 这是另一个脚注的内容。

## Table 表格

表格可以使用冒号 `:` 来定义表格的对齐方式。语法：

```
| Name  | Age |   Skin | Describe |
|:----- |:---:| ------:| -------- |
| Bob   | 27  |  white | tall     |
| Alice | 23  | yellow | fat      | 
```

效果：

| Name  | Age |   Skin | Describe |
|:----- |:---:| ------:| -------- |
| Bob   | 27  |  white | tall     |
| Alice | 23  | yellow | fat      |

## Code 代码

### Inline code 行内代码

语法：

```
`This is Inline Code`
```

效果：

`This is Inline Code`

### Code block 代码块

#### 通过反引号声明

语法：

    ```
	package main
	
	import "fmt"
	
	func main() {
		// hi
		fmt.Println("Hello, World!")
	}
    ```

效果：

```
package main

import "fmt"

func main() {
	// hi
	fmt.Println("Hello, World!")
}
```

可以在前面的三个反引号后声明代码的语言种类，语法：

	```go
	package main
	
	import "fmt"
	
	// calculateSquares calculates the sum of the squares of the digits of the given number
	// and sends the result to the squareop channel.
	func calculateSquares(number int, squareop chan int) {
		sum := 0
		for number != 0 {
			digit := number % 10
			sum += digit * digit
			number /= 10
		}
		squareop <- sum
	}
	
	// calculateCubes calculates the sum of the cubes of the digits of the given number
	// and sends the result to the cubeop channel.
	func calculateCubes(number int, cubeop chan int) {
		sum := 0
		for number != 0 {
			digit := number % 10
			sum += digit * digit * digit
			number /= 10
		}
		cubeop <- sum
	}
	
	func main() {
		number := 589
		sqrch := make(chan int)
		cubech := make(chan int)
	
		// Start two goroutines to calculate the sum of squares and cubes of the digits.
		go calculateSquares(number, sqrch)
		go calculateCubes(number, cubech)
	
		// Receive the results from the channels and add them.
		squares, cubes := <-sqrch, <-cubech
		fmt.Println("Final result", squares+cubes)
	}
	```

效果：

```go
package main

import "fmt"

// calculateSquares calculates the sum of the squares of the digits of the given number
// and sends the result to the squareop channel.
func calculateSquares(number int, squareop chan int) {
	sum := 0
	for number != 0 {
		digit := number % 10
		sum += digit * digit
		number /= 10
	}
	squareop <- sum
}

// calculateCubes calculates the sum of the cubes of the digits of the given number
// and sends the result to the cubeop channel.
func calculateCubes(number int, cubeop chan int) {
	sum := 0
	for number != 0 {
		digit := number % 10
		sum += digit * digit * digit
		number /= 10
	}
	cubeop <- sum
}

func main() {
	number := 589
	sqrch := make(chan int)
	cubech := make(chan int)

	// Start two goroutines to calculate the sum of squares and cubes of the digits.
	go calculateSquares(number, sqrch)
	go calculateCubes(number, cubech)

	// Receive the results from the channels and add them.
	squares, cubes := <-sqrch, <-cubech
	fmt.Println("Final result", squares+cubes)
}
```

更多语言的代码示例详见 [附录](#附录)。

#### 通过四个空格或一个制表符声明

语法：

```
	package main
	
	import "fmt"
	
	func main() {
		// hi
		fmt.Println("Hello, World!")
	}
```

效果：

	package main
	
	import "fmt"
	
	func main() {
		// hi
		fmt.Println("Hello, World!")
	}

## List 列表

### Ordered list 有序列表

语法：

```
1.  First item
	1.  Sub 1
	2.  Sub 2
	3.  Sub 3
2.  Second item
3.  Third item
```

或者：

```
1.  First item
	1.  Sub 1
	1.  Sub 2
	1.  Sub 3
1.  Second item
1.  Third item
```

效果：

1.  First item
	1.  Sub 1
	1.  Sub 2
	1.  Sub 3
1.  Second item
1.  Third item

### Nested list 无序列表

语法：

```
-   Fruit
    -   Apple
    -   Orange
    -   Banana
-   Dairy
    -   Milk
    -   Cheese
```

效果：

-   Fruit
    -   Apple
    -   Orange
    -   Banana
-   Dairy
    -   Milk
    -   Cheese

## Image 图片

语法：

```
![图片加载失败时显示的文字](assets/example.png "鼠标悬浮时的提示")
```

效果：

![图片加载失败时显示的文字](assets/example.png "鼠标悬浮时的提示")

GIF 同理，语法：

```
![GIF 加载失败时显示的文字](assets/example.gif "鼠标悬浮时的提示")
```

效果：

![GIF 加载失败时显示的文字](assets/example.gif "鼠标悬浮时的提示")

## Dividing line 分割线

语法：

```
---
```

效果：

---

## 其他

| 名称  | 语法                                                     | 效果                                                   |
| --- | ------------------------------------------------------ | ---------------------------------------------------- |
| 粗体  | `**bold**`                                             | **bold**                                             |
| 斜体  | `_italics_`                                            | _italics_                                            |
| 粗斜体 | `_**text**_`                                           | _**text**_                                           |
| 删除线 | `~~delete~~`                                           | ~~delete~~                                           |
| 缩写  | `<abbr title="Graphics Interchange Format">GIF</abbr>` | <abbr title="Graphics Interchange Format">GIF</abbr> |
| 下标  | `H<sub>2</sub>O`                                       | H<sub>2</sub>O                                       |
| 上标  | `X<sup>n</sup> + Y<sup>n</sup> = Z<sup>n</sup>`        | X<sup>n</sup> + Y<sup>n</sup> = Z<sup>n</sup>        |
| 按键  | `<kbd>Ctrl</kbd> + <kbd>Alt</kbd> + <kbd>Delete</kbd>` | <kbd>Ctrl</kbd> + <kbd>Alt</kbd> + <kbd>Delete</kbd> |
| 标记  | `<mark>mark</mark>`                                    | <mark>mark</mark>                                    |

## 相关链接

- [Basic Syntax | Markdown Guide](https://www.markdownguide.org/basic-syntax/)
- [styleguide/style.md at gh-pages · google/styleguide · GitHub](https://github.com/google/styleguide/blob/gh-pages/docguide/style.md)
- [styleguide/markdown.md at master · fex-team/styleguide · GitHub](https://github.com/fex-team/styleguide/blob/master/markdown.md)

## 附录

不同语言的代码示例，部分取自 [Sample Programs in Every Language](https://github.com/TheRenegadeCoder/sample-programs) 仓库。

### Bash

```bash
#!/bin/bash

count=$1

[[ $count =~ ^[0-9]+$ ]] || {
    echo "Usage: please input the count of fibonacci numbers to output"
    exit 1
}

n=1
n_minus_1=1
[[ $count < 1 ]] && exit 0

echo "1: 1"
for i in $(seq 2 $count); do
    echo "$i: $n"
    tmp=$n
    n=$(($n + $n_minus_1))
    n_minus_1=$tmp
done
```

### C

```c
#include <stdio.h>
#include <errno.h>
#include <inttypes.h>
#include <string.h>

/*
 * This limit is chosen because fib(93) is the first number that is
 * still small enough to fit into a 64 bit integer.
 */
#define LIMIT 93

void fibonacci(int n)
{
    unsigned long long first = 0;
    unsigned long long second = 1;
    unsigned long long result = 0;

    for (int i = 1; i <= n; i++)
    {
        result = first + second;
        first = second;
        second = result;
        printf("%d: %llu\n", i, first);
    }
}

int main(int argc, char **argv)
{
    uintmax_t n;

    if (argc < 2 || strcmp(argv[1], "") == 0)
    {
        fprintf(stderr, "Usage: please input the count of fibonacci numbers to output\n");
        return 1;
    }

    errno = 0;
    n = strtoumax(argv[1], NULL, 10);
    if (n == 0 && strcmp(argv[1], "0") != 0 || (n == UINTMAX_MAX && errno == ERANGE))
    {
        fprintf(stderr, "Usage: please input the count of fibonacci numbers to output\n");
        return 1;
    }

    if (n > LIMIT)
    {
        fprintf(stderr, "n cannot be larger than %d\n", LIMIT);
        return 1;
    }

    fibonacci(n);
    return 0;
}
```

### C++

```cpp
#include <iostream>
#include <cstdlib>
using namespace std;

int main(int argc, char *argv[])
{
    if (argc < 2 || std::string(argv[1]) == "")
    {
        cout << "Usage: please input the count of fibonacci numbers to output" << endl;
        return 1;
    }

    int n = atoi(argv[1]);
    if (n == 0 && std::string(argv[1]) != "0")
    {
        cout << "Usage: please input the count of fibonacci numbers to output" << endl;
        return 1;
    }
    int first = 0;
    int second = 1;
    int result = 0;

    for (int i = 1; i <= n; ++i)
    {
        result = first + second;
        first = second;
        second = result;
        cout << i << ": " << first << endl;
    }
    return 0;
}
```

### CSS

```css
body {
    padding-left: 11em;
    font-family: Georgia, "Times New Roman", Times, serif;
    color: purple;
    background-color: #d8da3d
}

ul.navbar {
    position: absolute;
    top: 2em;
    left: 1em;
    width: 9em
}

h1 {
    /* Set title font */
    font-family: Helvetica, Geneva, Arial, SunSans-Regular, sans-serif
}
```

### Go

```go
package main

import (
   "fmt"
   "os"
   "strconv"
)

func fibonacci(n int, c chan int) {
   x, y := 1, 1
   for i := 0; i < n; i++ {
      c <- x
      x, y = y, x+y
   }
   close(c)
}

func exitWithError() {
   fmt.Println("Usage: please input the count of fibonacci numbers to output")
   os.Exit(1)
}

func main() {
   if len(os.Args) != 2 {
      exitWithError()
   }

   n, err := strconv.Atoi(os.Args[1])
   if err != nil {
      exitWithError()
   }

   c := make(chan int, n)

   go fibonacci(cap(c), c)
   i := 1
   for v := range c {
      fmt.Printf("%d: %d\n", i, v)
      i++
   }
}
```

### HTML

```html
<Html>

<Head>
    <title>
        Example of anchor or hyperlink
    </title>
</Head>

<Body>
    <!-- In this example we use the anchor tag for linking one page to another by using the href attribute which specify the url of the second page which you want to link.-->
    <center>
        Click on <a href="https://www.javatpoint.com/html-favicon"> this link </a> for reading about HTML favicon in JavaTpoint.
    </center>
</Body>

</Html>
```

### INI

```ini
; Test config file for ini_example.c and INIReaderTest.cpp

[protocol]               ; Protocol configuration
version=6                ; IPv6

[user]
name = Bob Smith         ; Spaces around '=' are stripped
email = bob@smith.com    ; And comments (like this) ignored
active = true            ; Test a boolean
pi = 3.14159             ; Test a floating point number
trillion = 1000000000000 ; Test 64-bit integers
```

### Java

```java
public class Fibonacci {

    public static void main(String[] args) {
        try {
            int n = Integer.parseInt(args[0]);
            int first = 0;
            int second = 1;
            int result = 0;
            for (int i = 1; i <= n; i++) {
                result = first + second;
                first = second;
                second = result;
                System.out.println(i + ": " + first);
            }
        } catch (Exception e) {
            System.out.println("Usage: please input the count of fibonacci numbers to output");
            System.exit(1);
        }
    }

}
```

### JavaScript

```javascript
function fibonacci(num) {
    let n = Number(num);
    let first = 0;
    let second = 1;
    let result = 0;
    for (let i = 1; i <= n; i++) {
        result = first + second;
        first = second;
        second = result;
        console.log(i + ": " + first);
    }
}

num = process.argv[2];

if (num && !isNaN(num)) {
    fibonacci(num);
} else {
    console.log("Usage: please input the count of fibonacci numbers to output")
}
```

### JSON

```json
{
    "books": [
        {
            "id": "bk102",
            "author": "Crockford, Douglas",
            "title": "JavaScript: The Good Parts",
            "genre": "Computer",
            "price": 29.99,
            "publish_date": "2008-05-01",
            "description": "Unearthing the Excellence in JavaScript"
        }
    ]
}
```

### PHP

```php
<?php

if ($argc < 2 || !is_numeric($argv[1]) || intval($argv[1]) < 0) {
    die("Usage: please input the count of fibonacci numbers to output");
}

$input = intval($argv[1]);

$a = 0;
$b = 1;
$fibonacci = 0;

for ($index = 1; $index <= $input; $index++) {
    $fibonacci = $a + $b;
    $a = $b;
    $b = $fibonacci;
    echo "$index: $a\n";
}
```

### Python

```python
import sys

def fibonacci(n):
    fib = fibs()
    for i in range(1, n + 1):
        print(f"{i}: {next(fib)}")

def fibs():
    first = 1
    second = 1
    yield first
    yield second
    while True:
        new = first + second
        yield new
        first = second
        second = new

def main(args):
    try:
        fibonacci(int(args[0]))
    except (IndexError, ValueError):
        print("Usage: please input the count of fibonacci numbers to output")
        sys.exit(1)

if __name__ == "__main__":
    main(sys.argv[1:])
```

### Rust

```rust
use std::env::args;
use std::process::exit;
use std::str::FromStr;

const LIMIT: i32 = 93;

fn usage() -> ! {
    println!("Usage: please input the count of fibonacci numbers to output");
    exit(0);
}

fn parse_int<T: FromStr>(s: &str) -> Result<T, <T as FromStr>::Err> {
    s.trim().parse::<T>()
}

fn fibonacci(terms: i32) {
    if terms > LIMIT {
        println!("The number of terms you want to calculate is too big!");
        println!("The limit is {}.", LIMIT);
    } else {
        let mut a = 0u64;
        let mut b = 1u64;
        for i in 1..(terms + 1) {
            (a, b) = (b, a + b);
            println!("{i}: {a}");
        }
    }
}

fn main() {
    let mut args = args().skip(1);

    // Exit if 1st command-line argument not an integer
    let mut input_num: i32 = args
        .next()
        .and_then(|s| parse_int(&s).ok())
        .unwrap_or_else(|| usage());

    // Show request number of Fibonacci numbers
    fibonacci(input_num);
}
```

### Scala

```scala
import scala.util.{Try, Success, Failure}

object Fibonacci {

  def fibonacci(n: Int) = {
    var a = 0
    var b = 1
    for (i <- 1 to n) {
      println(s"$i: $b")
      val c = a + b
      a = b
      b = c
    }
  }

  def main(args: Array[String]) = {
    Try(args(0).toInt) match {
      case Failure(_) => println("Usage: please input the count of fibonacci numbers to output")
      case Success(n) => fibonacci(n)
    }
  }

}
```

### Swift

```swift
import Foundation

func fibonacciProgram(_ n: Int) {
    var f1=0, f2=1, fib=1
    for i in 0..<n {
        print("\(i+1): \(fib)")
        fib = f1 + f2
        f1 = f2
        f2 = fib
    }
}

func fibonacciRecursive(_ n: Int) -> Int {
    if (n == 0) {
        return 0
    } else if (n == 1) {
        return 1
    }
    return fibonacciRecursive(n-1) + fibonacciRecursive(n-2)
}

/*
    Check if there is exactly one argument and if it can be parsed as an integer
*/
guard CommandLine.argc == 2, let number = Int(CommandLine.arguments[1]) else {
    print("Usage: please input the count of fibonacci numbers to output")
    exit(0)
}

fibonacciProgram(number)
```

### TOML

```toml
[[books]]
id = 'bk101'
author = 'Crockford, Douglas'
title = 'JavaScript: The Good Parts'
genre = 'Computer'
price = 29.99
publish_date = 2008-05-01T00:00:00+00:00
description = 'Unearthing the Excellence in JavaScript'
```

### TypeScript

```typescript
function fibonacci(num: number) {

  let n = Number(num);
  let elementOne: number = 0;
  let elementTwo: number = 1;
  let result: number = 0;

  for (let i: number = 1; i <= n; i++) {
    result = elementOne + elementTwo;
    elementOne = elementTwo;
    elementTwo = result;
    console.log(`${i}: ${elementOne}`);
  }

}

let num_str = (process.argv.length >= 3) ? process.argv[2] : ""
let num: number = parseInt(num_str);
if (isNaN(num)) {
  console.log("Usage: please input the count of fibonacci numbers to output")
  process.exit(0)
}

fibonacci(num);
```

### XML

```xml
<book id="bk101">
    <author>Gambardella, Matthew</author>
    <title>XML Developer's Guide</title>
    <genre>Computer</genre>
    <price>44.95</price>
    <publish_date>2000-10-01</publish_date>
    <description>An in-depth look at creating applications with XML.</description>
</book>
```

### YAML

```yaml
books:
  - id: bk102
    author: Crockford, Douglas
    title: "JavaScript: The Good Parts"
    genre: Computer
    price: 29.99
    publish_date: !!str 2008-05-01
    description: Unearthing the Excellence in JavaScript
```

### diff

```diff
  - name: Deploy
    uses: peaceiris/actions-gh-pages@v3
    if: github.ref == 'refs/heads/main'
    with:
-     github_token: ${{ secrets.GITHUB_TOKEN }}
+     personal_token: ${{ secrets.GH_PAGES_TOKEN }}
+     external_repository: rea1shane/posts
      publish_dir: ./public
```
