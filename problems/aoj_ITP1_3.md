# [3. Repetitive Processing ](http://judge.u-aizu.ac.jp/onlinejudge/topic.jsp?cid=ITP1#problems/ITP1_3)

## [A. Print Many Hello World ](http://judge.u-aizu.ac.jp/onlinejudge/description.jsp?id=ITP1_3_A)

- 問題:1000 個の "Hello World" を出力するプログラムを作成して下さい。
- 入力:なし
- 解法:1000回 print する
- **解法:Loop(for or while)文 を使う**
- [solution](http://judge.u-aizu.ac.jp/onlinejudge/solution.jsp?pid=ITP1_3_A#10)


## [B. Print Test Cases ](http://judge.u-aizu.ac.jp/onlinejudge/description.jsp?id=ITP1_3_B)

- 問題:データ x ごとに,Case i: x のように出力して下さい：
- 入力:xが0のとき入力の終わりを示す複数行からなるデータセット
- 解法:Loop(for,while)文 を使う
- 解法:配列のMap,forEachを使う
- [solution](http://judge.u-aizu.ac.jp/onlinejudge/solution.jsp?pid=ITP1_3_B#10)

```js
// Array.forEach() を 使ったパターン
'use strict';
(function(stdin) {
  var EOF    = '0';
  var inputs = stdin.toString().trim().split('\n');

  (function(array) {

    array.forEach(function(x, index) {
      console.log('Case', index + ':', x);
    });

  })(inputs.slice(0, inputs.indexOf(EOF)));

}(require('fs').readFileSync('/dev/stdin', 'utf8')));
```

## [C. Swapping Two Numbers ](http://judge.u-aizu.ac.jp/onlinejudge/description.jsp?id=ITP1_3_C)

- 問題:2つの整数 x, y を読み込み、それらを値が小さい順に出力
- 入力:各データセットは空白で区切られた2つの整数 x, y を含む1行から構成
- 解法:Loop(for,while)文 もしくは配列のMap,forEachを使う
- 解法:大小の比較は if文,Math.max() Math.min(),もしくはarray.sort()を使う
- [solution](http://judge.u-aizu.ac.jp/onlinejudge/solution.jsp?pid=ITP1_3_C#10)

```js
// Arrays.sortを使って並べ替え
'use strict';
(function(stdin) {
  var EOF = '0 0';
  var inputs = stdin.toString().trim().split('\n');
  var matrics = inputs.slice(0, inputs.indexOf(EOF)).map(function(v) {
    return v.split(' ').map(Number);
  });

  (function(matrics) {

    matrics.map(function(v) {
      return v.sort(function(a, b) {
        return a - b;
      });
    })
    .forEach(function(v) {
      console.log(v[0], v[1]);
    });

  })(matrics);

}(require('fs').readFileSync('/dev/stdin', 'utf8')));
```

```js
'use strict';
// Math.max Math.min を使ったパターン
(function(stdin) {
  var EOF     = '0 0';
  var inputs  = stdin.toString().trim().split('\n');
  var matrics = inputs.slice(0, inputs.indexOf(EOF)).map(function(v) {
    return v.split(' ').map(Number);
  });

  (function(matrics) {

    matrics.map(function(v) {
      return [
        Math.min(v[0], v[1])
        , Math.max(v[0], v[1])
      ];
    })
    .forEach(function(v) {
      console.log(v[0], v[1]);
    });

  })(matrics);

}(require('fs').readFileSync('/dev/stdin', 'utf8')));
```


## [D. How Many Divisors? ](http://judge.u-aizu.ac.jp/onlinejudge/description.jsp?id=ITP1_3_D)

- 問題:3つの整数 a,b,c を読み込み、a から b までの整数の中に、c の約数がいくつあるかを求める
- 入力:a,b,c が1つの空白区切りで1行
- 解法:約数の判定は ( c % n === 0) を使う
- [solution](http://judge.u-aizu.ac.jp/onlinejudge/solution.jsp?pid=ITP1_3_D#10)

```js
'use strict';
(function(stdin) {

  var inputs = stdin.toString().split('\n');
  var cols   = inputs[0].split(' ').map(Number);
  (function(numbers, divisable) {

    console.log(numbers.filter(divisable).length);

  })(range(cols[0], cols[1]), isDivisable(cols[2]));

  function range(n, m) {
    var array = [];

    for (var i = n; i < m + 1; i++) {
      array.push(i);
    }
    return array;
  }

  function isDivisable(diviser) {
    return function(n) {
      return diviser % n === 0;
    };
  }

}(require('fs').readFileSync('/dev/stdin', 'utf8')));
```