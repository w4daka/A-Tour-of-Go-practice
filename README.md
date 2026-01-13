# A-Tour-of-Go-practice

## Overview

This repository is a for tracking my progress in "A Tour of Go"

## Progress

2026/01/10 "Welcome" did

2026/01/11 "Basics-Packages" did

## 学んだこと

### welcome

welcomeディレクトリに**Hello_world.go**と**time.go**を配置したときに

**Hello_world.go**は

```go
package main

import "fmt"

func main() {
	fmt.Println("Hello, 世界")
}

```

という形

**time.go**を

```go
package main

import (
	"fmt"
	"time"
)

func main() {
	fmt.Println("Welcome to the playground!")

	fmt.Println("The time is", time.Now())
}

```

という形
それぞれのmainに

```
main redeclared in this blockcompilerDuplicateDecl
Hello_world.go(5, 6): other declaration of main
```

という警告が出た。これは一つのディレクトリは一つのパッケージとして扱うからである解決するにはディレクトリ構成をのようにすればよい。やる。

```
welcome/
├── hello/
│   └── Hello_world.go
└── time/
    └── time.go
```

### Basics

#### Packages

Goのプログラムはmainパッケージから始まる

#### Imports

factoredインポートステートメントのほうがよりよいスタイル。

#### Exported names

`math.pi`だと、以下のようなエラーが出る。

```
undefined: math.pi (but have Pi)
```
`math.Pi`に変えるとエラーが解消される。これは、小文字で始まる文字は外部のパッケージからアクセスすることはできないからである。

#### Functions

変数名は**後ろ**に型名を書くことに注意する。

#### Functions continued

関数が2つ以上の引数が同じ型である場合には、最後の型を残して省略して記述できる。今回の例では
```
x int, y int
```
を
```
x, y int
```
と書くことができる。

#### Multiple results

Goの関数は複数の戻り値を返すことができる。
このときのコードの`a, b =swap("hello", "world")`という行の`:=`がわからなかった。この`:=`はGo言語における**短縮変数宣言(Short Variable Declearation)**である。

これは以下二つの役割を同時にはたしている。


1. **変数の宣言**:新しい変数`a`と`b`を作成する

2. **初期化**:右辺の`swap("hello", "world)`の戻り値を左辺の変数に代入する

**`var`を使った場合との比較**

```go
var a, b string = swap("hello", "world")
```

または

```go
var a, b string
a, b = swap("hello", "world")
```

よって、`:=`を使うことで`var`キーワードや型の記述を省略できるというメリットがある。