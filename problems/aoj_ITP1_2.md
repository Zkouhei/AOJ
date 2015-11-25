# [2. Branch on Condition](http://judge.u-aizu.ac.jp/onlinejudge/topic.jsp?cid=ITP1#problems/ITP1_2)

## [A. Small, Large, or Equal](http://judge.u-aizu.ac.jp/onlinejudge/description.jsp?id=ITP1_2_A)

- 問題:a と b の大小関係を出力するプログラム
- 入力:2つの整数 a,b
- 解法:a,bを比較してその結果を返す
- [solution](http://judge.u-aizu.ac.jp/onlinejudge/solution.jsp?pid=ITP1_2_A#10)

```js
'use strict';
(function(stdin) {
  var inputs = stdin.toString().trim().split('\n');
  var params = inputs[0].split(' ').map(Number);

  (function(a, b) {
    // ここに処理を書く

  }(params[0], params[1]));

}(require('fs').readFileSync('/dev/stdin', 'utf8')));
```

## [B. Range](http://judge.u-aizu.ac.jp/onlinejudge/description.jsp?id=ITP1_2_B)

- 問題:a < b < cの条件を満たすならば"Yes"を、満たさないならば"No"
- 入力:3つの整数 a,b,c 
- 解法:a,b,c の大小を比較してその結果を返す
- [solution](http://judge.u-aizu.ac.jp/onlinejudge/solution.jsp?pid=ITP1_2_B#10)

```js
'use strict';
(function(stdin) {
  var inputs = stdin.toString().trim().split('\n');
  var params = inputs[0].split(' ').map(Number);

  (function(a, b, c) {
    // ここに処理を書く

  }(params[0], params[1], params[2]));

}(require('fs').readFileSync('/dev/stdin', 'utf8')));
```

## [C. Sorting Three Numbers](http://judge.u-aizu.ac.jp/onlinejudge/description.jsp?id=ITP1_1_C)

- 問題:3つの整数を読み込み,昇順で返す
- 入力:3つの整数 a,b,c
- 解法: if文で分岐して結果を返す
- **解法:配列をソートして結果を返す**
- [solution](http://judge.u-aizu.ac.jp/onlinejudge/solution.jsp?pid=ITP1_2_C#10)


```js
'use strict';
(function(stdin) {
  var inputs = stdin.toString().trim().split('\n');
  var params = inputs[0].split(' ').map(Number);

  (function(a, b, c) {
    // ここに処理を書く

  }(params[0], params[1], params[2]));

}(require('fs').readFileSync('/dev/stdin', 'utf8')));
```
> Array.protorype.sort() を使う場合

```js
'use strict';
(function(stdin) {
  var inputs = stdin.toString().trim().split('\n');
  var params = inputs[0].split(' ').map(Number);

  (function(array) {
    // ここに処理を書く

  })(params);

}(require('fs').readFileSync('/dev/stdin', 'utf8')));
```

## [D. Circle in a Rectangle](http://judge.u-aizu.ac.jp/onlinejudge/description.jsp?id=ITP1_2_D)

- 問題:長方形の中に円が含まれるかを判定するプログラム
- 入力:5つの整数 W,H,x,y,r
- 解法:W <= x + r, H <= y + r, 0 <= x - r, 0 <= y - r 
- [solution](http://judge.u-aizu.ac.jp/onlinejudge/solution.jsp?pid=ITP1_2_D#10)

```js
'use strict';
(function(stdin) {
  var inputs = stdin.toString().trim().split('\n');
  var params = inputs[0].split(' ').map(Number);

  (function(W, H, x, y, r) {
    // ここに処理を書く

  }(params[0], params[1], params[2], params[3], params[4]));

}(require('fs').readFileSync('/dev/stdin', 'utf8')));
```
> オブジェクトを使った解法

```js
'use strict';
(function(stdin) { 
  var inputs = stdin.toString().trim().split('\n');
  var params = inputs[0].split(' ').map(Number);
  var Circle = function(x, y, r){
    this.left   = x - r;
    this.right  = x + r;
    this.top    = y + r;
    this.bottom = y - r;
  };

  Circle.prototype.within = function(h,w) {
    return [this.bottom, this.left, h - this.top , w - this.right ]
        .every(function(v) {
          return v >= 0;
        });
  };

  (function(H,W,circle) {

    console.log(['No','Yes'][Number(circle.within(H,W))]);

  })(params[0],params[1],new Circle(params[2],params[3],params[4]); 

}(require('fs').readFileSync('/dev/stdin', 'utf8')));
```