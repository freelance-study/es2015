class: center, middle

# ES2015について

---

# Agenda

1. Introduction
1. let、constによる変数宣言
1. アロー関数による関数宣言
1. モジュール化

---

# Introduction

- ブラウザ対応状況
 - http://caniuse.com/#search=es6


- ES2015で可能となる新たなシンタックス
 - let、constによる変数宣言
 - アロー関数による関数宣言
 - モジュール化


---

### let、constによる変数宣言

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

### アロー関数による関数宣言

- `this`は関数が定義されたスコープにおける`this`を引き継ぐ


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

---

### モジュール化

- JSファイルを分けて開発する機能
- これまではcommon.js等のライブラリを使用していた。  
node.jsではrequire関数に相当する
- ES2015ではimport/exportを使用する
- 使い方  

```javascript:myFunc.js
export default function () {};
```

```javascript:main.js
import myFunc from 'myFunc';
myFunc();
```

- 基本的にはexport defaultを使う
- 複数のモジュールをexportするときはexportを使う
- 受け取り側はimportを使う
