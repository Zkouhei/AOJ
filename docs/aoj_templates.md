# AOJにおけるのデータの取り出し方(JavaScript)

## 外部入力のとり方

### `fs.readFileSync()`を使う方法

こちらがシンプルかつ高速なのでおすすめ

```javascript
var stdin = require('fs').readFileSync('/dev/stdin', 'utf8');
```

### `process.stdin` を 使う方法

paizaの標準テンプレート

```javascript
process.stdin.on('data', function(chunk) {
  var inputs = chunk.toString();
  // ここに処理を書く
});
process.stdin.resume();
process.stdin.setEncoding('utf8');
```

完全にデータを受け取ってから,処理を開始したい場合

```javascript
var data = '';
process.stdin.on('end', function() {
  var inputs = data.toString();
  // ここに処理を書く
});

process.stdin.resume();
process.stdin.setEncoding('utf8');
process.stdin.on('data', function(chunk) {
  data += chunk;
});
```

プログラムの実行は ```$nodejs filename.js < datafile``` で行う

## テンプレート

> 即値実行関数を使ってデータを渡す

```javascript
'use strict';
(function(stdin) {

  var inputs  = stdin.toString().trim().split('\n');
  console.log(inputs);


}(require('fs').readFileSync('/dev/stdin', 'utf8')));
```

> 1行だけのデータを取得する場合

```javascript
'use strict';
(function(stdin) { 

  var inputs  = stdin.toString().trim().split('\n');
  var line = inputs[0];

  console.log(line);

}(require('fs').readFileSync('/dev/stdin', 'utf8')));
```

> 1行めの複数の数値データを取得する場合(配列で返す)

```javascript
'use strict';
(function(stdin) { 

  var inputs  = stdin.toString().trim().split('\n');
  var line = inputs[0];
  var cols = line.split(' ').map(Number);
  console.log(cols);


}(require('fs').readFileSync('/dev/stdin', 'utf8')));
```

> 1行めの複数の数値データを取得する場合(Paramを使用)

```javascript
'use strict';
(function(stdin) { 

  var inputs  = stdin.toString().trim().split('\n');
  var cols = inputs[0].split(' ').map(Number);
  var result = (function(a, b) {

    console.log(a,b);

  })(cols[0],cols[1]);

}(require('fs').readFileSync('/dev/stdin', 'utf8')));
```


> 複数行,複数列の数値データを取得する場合(2次元配列で返す)

```javascript
'use strict';
(function(stdin) {

  var inputs = stdin.toString().trim().split('\n');
  var matrics = inputs.map(function(v) {
    return v.split(' ').map(Number);
  });

  console.log(matrics);

}(require('fs').readFileSync('/dev/stdin', 'utf8')));

```

> 1行目にデータの数が指定されている場合(Array.slice()を使う)

```javascript
'use strict';
(function(stdin) {
  var inputs  = stdin.toString().trim().split('\n');
  // Array.shift()で1行目(m)を抜き出し
  var len = inputs.shift();
  // Array.slice(n,m)でm行目まで取得
  var lines = inputs.slice(0,len);

  console.log(lines);
 
}(require('fs').readFileSync('/dev/stdin', 'utf8')));
```

> 1行目にデータの数が指定されている場合(上記のショートVer)

```javascript
'use strict';
(function(stdin) {
  var inputs  = stdin.toString().trim().split('\n');
  var lines = inputs.lines.slice(0, lines.shift());

  console.log(lines);
 
}(require('fs').readFileSync('/dev/stdin', 'utf8')));
```

> 終了文字列が指定されている場合(Array.indexOf()を使う方法)

```javascript
'use strict';
(function(stdin) {
  // 終了文字列の指定
  var EOF = '指定文字列';
  var inputs  = stdin.toString().trim().split('\n');
  // Array.indexOfを使用して指定文字のindexを取得しArray.slice(n,m)で切り出し
  var lines = inputs.slice(0, inputs.indexOf(EOF));

  console.log(lines);

}(require('fs').readFileSync('/dev/stdin', 'utf8')));
```


> 終了文字列が指定されている場合(String.split()を使う方法)

```javascript
'use strict';
(function(stdin) {
  // 終了文字列の指定(指定文字列)
  var EOF = '指定文字列';
  var inputs  = stdin.toString().trim();
  // 終了文字列で分割し終了文字列の直前までを取得
  var lines = inputs.split(EOF, 1)[0].trim().split('\n');

  console.log(lines);

}(require('fs').readFileSync('/dev/stdin', 'utf8')));
```
> Arrow構文版

```
(stdin => {
  // Define Function

  // Declare Variable
  const inputs  = stdin.toString().trim().split('\n');

  // Main Procedure
  const result = ((lines) => {

    return lines;

  })(inputs);
  
  // Display
  console.log(result);

})(require('fs').readFileSync('/dev/stdin', 'utf8'));
```
