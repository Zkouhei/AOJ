# [1. Getting Started](http://judge.u-aizu.ac.jp/onlinejudge/topic.jsp?cid=ITP1#problems/ITP1_1)

## [A. Hello World](http://judge.u-aizu.ac.jp/onlinejudge/description.jsp?id=ITP1_1_A)

- 問題:Hello Worldの出力
- 入力:なし
- 解法:console.log()で出力
- [solution](http://judge.u-aizu.ac.jp/onlinejudge/solution.jsp?pid=ITP1_1_A#10)

```js
'use strict';
(function() {
  //ここに処理を書く

}()); 
```

> 引数を渡して処理

```js
'use strict';
(function(word) {
  //ここに処理を書く

}('Hello World')); 
```

## [B. X Cubic](http://judge.u-aizu.ac.jp/onlinejudge/description.jsp?id=ITP1_1_B)

- 問題:xの3乗を出力
- 入力:1つの整数 x 
- 解法:xを3回かける
- **解法:Math.pow()**
- [solution](http://judge.u-aizu.ac.jp/onlinejudge/solution.jsp?pid=ITP1_1_B#10)

```js
'use strict';
(function(stdin) { 
  var inputs = stdin.toString().trim();
  var param = parseInt(inputs,10);
  (function(x) {
    //ここに処理を書く

  }(param)); 
}(require('fs').readFileSync('/dev/stdin', 'utf8')));
```

## [C. Rectangle](http://judge.u-aizu.ac.jp/onlinejudge/description.jsp?id=ITP1_1_C)

- 問題:長方形の面積と周の長さを求める
- 入力:2つの整数 a,b
- 解法:面積は a * b, 周の長さは (a + b) * 2
- [solution](http://judge.u-aizu.ac.jp/onlinejudge/solution.jsp?pid=ITP1_1_C#10)


```js
'use strict';
(function(stdin) { 
  var inputs = stdin.toString().trim();
  var params = inputs.split(' ').map(Number);
  (function(a,b) {
    //ここに処理を書く

  }(params[0],params[1])); 
}(require('fs').readFileSync('/dev/stdin', 'utf8')));
```

## [D. Watch](http://judge.u-aizu.ac.jp/onlinejudge/description.jsp?id=ITP1_1_D)

- 問題:秒単位の時間 S を h:m:s の形式へ変換
- 入力:S
- 解法:h = S / 60 * 60, m = (S - h * 60) / 60, s = S - (h * 60) - (m * 60) 
- **解法:h = S / (60 * 60) , m = S % (60 * 60) / 60, s = S % 60**
- [solution](http://judge.u-aizu.ac.jp/onlinejudge/solution.jsp?pid=ITP1_1_D#10)

```js
'use strict';
(function(stdin) { 
  var inputs = stdin.toString().trim();
  var param = parseInt(inputs,10)
  (function(S) {
    //ここに処理を書く

  }(param); 
}(require('fs').readFileSync('/dev/stdin', 'utf8')));
```