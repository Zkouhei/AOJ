# [4.  Computation ](http://judge.u-aizu.ac.jp/onlinejudge/topic.jsp?cid=ITP1#problems/ITP1_4)

## [A. A / B Problem ](http://judge.u-aizu.ac.jp/onlinejudge/description.jsp?id=ITP1_4_A)

- 問題:2つの整数 を読み込んで、以下の値を計算するプログラムを作成
    - a ÷ b : d (整数)
    - a ÷ b の余り : r (整数)
    - a ÷ b : f (浮動小数点数)
- 入力:1行に2つの整数 a, b
- 出力:d, r, f を空白で区切って1行に出力
- 解法:整数はMath.floor,parseInt等を使用,あまりは剰余演算(%)
- [solution](http://judge.u-aizu.ac.jp/onlinejudge/solution.jsp?pid=ITP1_4_A#10)

```js
'use strict';
(function(stdin) {
  var inputs = stdin.toString().trim().split('\n');
  var cols   = inputs[0].split(' ').map(Number);

  (function(a,b) {
  // ここに処理を書く
  })(cols[0],cols[1]);

}(require('fs').readFileSync('/dev/stdin', 'utf8')));
```

## [B. Circle ](http://judge.u-aizu.ac.jp/onlinejudge/description.jsp?id=ITP1_4_B)

- 問題:半径 r の円の面積と円周の長さを求めるプログラムを作成
- 入力:1つの実数 r 
- 出力:面積と円周の長さを1つの空白で区切って1行に出力
- 解法:円の面積および円周の公式どおり(π は Math.PI)
- [solution](http://judge.u-aizu.ac.jp/onlinejudge/solution.jsp?pid=ITP1_4_B#10)

```js
'use strict';
(function(stdin) {
  var inputs  = stdin.toString().trim().split('\n');

  (function(r) {
  // ここに処理を書く

  })(parseInt(inputs[0],10));

}(require('fs').readFileSync('/dev/stdin', 'utf8')));
```

## [C. Simple Calculator ](http://judge.u-aizu.ac.jp/onlinejudge/description.jsp?id=ITP1_4_C)

- 問題:２つの整数 a, b と１つの演算子 op を読み込んで、a op b を計算するプログラムを作成
- 入力:a op b
    - op が '?' のとき 入力の終わり
- 出力:各データセットについて、計算結果を１行に出力して下さい。
- 解法:
- [solution](http://judge.u-aizu.ac.jp/onlinejudge/solution.jsp?pid=ITP1_4_C#10)

```js
'use strict';
(function(stdin) {
  var EOF = /\w*\s\?\s\w*/;
  var inputs  = stdin.toString().trim().split('\n');
  var matrics = inputs.slice(0, inputs.indexOf(EOF)).map(function(v) {
    return v.split(' ');
  });

  (function(matrics) {
  // ここに処理を書く

  })(matrics);

}(require('fs').readFileSync('/dev/stdin', 'utf8')));
```

## [D. Min, Max and Sum ](http://judge.u-aizu.ac.jp/onlinejudge/description.jsp?id=ITP1_4_D)

- 問題:n 個の整数 ai(i=1,2,...n)を入力し、それらの最小値、最大値、合計値を求めるプログラムを作成
- 入力:1行目に整数の数 n が与えられます。2行目に n 個の整数 ai が空白区切
- 出力:最小値、最大値、合計値を空白区切りで１行に出力。
- 解法:Math.max(),Math.max.apply(null,Array)
- [solution](http://judge.u-aizu.ac.jp/onlinejudge/solution.jsp?pid=ITP1_4_D#10)

```js
'use strict';
(function(stdin) {
  var inputs = stdin.toString().trim().split('\n');
  var cols   = inputs[1].split(' ', inputs[0]).map(Number);

  (function(data) {
    console.log(
      data.reduce(min)
      , data.reduce(max)
      , data.reduce(sum)
    );

    function min(a, b) {
      return Math.min(a, b);
    }
    function max(a, b) {
      return Math.max(a, b);
    }
    function sum(a, b) {
      return a + b;
    }

  })(cols);

}(require('fs').readFileSync('/dev/stdin', 'utf8')));
```