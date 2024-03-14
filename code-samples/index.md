---
title: Code samples
summary: Used for testing code highlighting.
tags: [invisible]
date: 2024-03-14
lastmod: 2024-03-14
draft: true
---

## Bash

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

## C

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

## C++

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

## CSS

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

## Go

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

## HTML

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

## INI

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

## Java

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

## JavaScript

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

## JSON

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

## PHP

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

## Python

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

## Rust

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

## Scala

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

## Swift

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

## TOML

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

## TypeScript

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

## XML

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

## YAML

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

## References

- [GitHub - TheRenegadeCoder/sample-programs: Sample Programs in Every Programming Language](https://github.com/TheRenegadeCoder/sample-programs)
- [软件开发|JSON、XML、TOML、CSON、YAML 大比拼](https://linux.cn/article-10664-1.html)
- [inih/examples/test.ini at master · benhoyt/inih · GitHub](https://github.com/benhoyt/inih/blob/master/examples/test.ini)
- [Simple HTML Pages - javatpoint](https://www.javatpoint.com/simple-html-pages)
- [Starting with HTML + CSS](https://www.w3.org/Style/Examples/011/firstcss.en.html)
