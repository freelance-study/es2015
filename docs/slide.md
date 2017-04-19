class: center, middle

# ES2015について

---

# Agenda

1. Introduction
1. let、constによる変数宣言
1. アロー関数による関数宣言
1. モジュール化
1. 分割代入
1. クラス宣言

---

# Introduction

- ブラウザ対応状況
 - http://caniuse.com/#search=es6


- ES2015で可能となる新たなシンタックス
 - let、constによる変数宣言
 - アロー関数による関数宣言
 - モジュール化
 - 分割代入
 - クラス宣言


---

## let、constによる変数宣言

- ES5までは関数スコープのみしか存在しなかったが、ES2015では`let`や`const`により定義された変数は、ブラケット`{}`によるブロックスコープが可能となった。


        var x = 'foo';
        if (true) {
          var x = 'bar';
          console.log(x); // bar
        }
        console.log(x); // bar  <- 値が書き換わっている


        let x = 'foo';
        if (true) {
          let x = 'bar';
          console.log(x); // bar
        }
        console.log(x); // foo  <- 値が書き換わっていない

- `let`で宣言した変数は再代入を可能とするが、`const`で宣言した変数は再代入を不可とする。

---

## アロー関数による関数宣言
Arrow Functions

- `this`は関数が定義されたスコープにおける`this`を引き継ぐ

```javascript
        // アロー関数を使わない場合
        var num = 100;
        let counter = {
          num: 10,
          count: function() {
            setTimeout(function() {
              this.num++;
              console.log(this.num);  // 101  <- thisはグローバルオブジェクトを指している
            }, 100);
          }
        };
        counter.count();
```
---
```javascript
        // アロー関数を使う場合
        var num = 100;
        let counter = {
          num: 10,
          count: function() {
            setTimeout(() => {
              this.num++;
              console.log(this.num);  // 11 <- thisはcounterオブジェクトを指している
            }, 100);
          }
        };
        counter.count();
```
---

## モジュール化
Module

- JSファイルを分けて開発する機能
- これまではcommon.js等のライブラリを使用していた。  
node.jsではrequire関数に相当する
- ES2015ではimport/exportを使用する

---

### 使い方  

- 基本的にはexport defaultを使う
- 受け取り側はimportを使う

```javascript
// my-module.js
export default function myDefault() {}
```

```javascript
import myDefault from 'my-module';
myDefault();
```

---

- メンバーを指定してインポートするときは名前指定を使う

```javascript
// my-module.js
export function foo() {}
export function bar() {}
```

```javascript
import {foo, bar} from 'my-module';
```

※デフォルト指定されたメンバーを名前指定でインポートしようとするとエラーになる

---

## 分割代入
Destructing Assignment

配列かオブジェクトからデータを取り出して別個の変数に代入することができる。

```javascript
var a, b;
[a, b] = [1, 2];

console.log(a);     // 1
console.log(b);     // 2
```

---

代入時に足りない分は`undefined`に、余った分は切り捨てられる。

配列の分割代入

```javascript
var foo = ["one", "two", "three"];
var [x, y] = foo;

console.log(x);     // "one"
console.log(y);     // "two"
```

オブジェクトの分割代入

```javascript
var o = {p: 42, q: true};
var {p, q} = o;

console.log(p); // 42
console.log(q); // true
```
