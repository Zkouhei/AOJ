# JavaScript Tips

## 単純な分岐

```js
'use strict';
// 単純な分岐
var func = {
  // if文を 使って分岐
  f1:function(rain) {
    if (rain) {
      return '雨';
    } 
    return '晴れ';
  }
  // 3項演算を使って分岐
  ,f2:function(rain) {
    return rain ? '雨' : '晴れ';
  }
  // 配列とboolen -> number 変換を使って分岐
  ,f3:function(rain) {
    return ['晴れ','雨'][Number(rain)];
  }
  // オブジェクトのプロパティを使って分岐
  ,f4:function(rain) {
    return {true:'雨',false:'晴れ'}[rain];
  }
};

// 単純にcallする
console.log(func.f1(false));
console.log(func.f2(false));
console.log(func.f3(false));
console.log(func.f4(false));

// for in 文で 回す
for (var f in func) {
  console.log(func[f](false));
}

// Key(f1,f2,f3,f4)を配列にしてforEachで回す
Object.keys(func).forEach(function(f) {
  console.log(func[f](false));
});
```

## 小数を整数にする手法

```js
// 小数を整数にする手法(時間計測)
exec(_number);
exec(_parseInt);
exec(_floor);
exec(_xorxor)
exec(_orZero);
exec(_bitshiftZero);

function exec(f) {
  console.time(f.name);
  for (var i = 0; i < 100000000; i++) {
    f(3,2);
  }
  console.timeEnd(f.name);
}

function _number(n,m) {
  return Number(n / m);
}
function _parseInt(n,m) {
  return parseInt(n / m, 10);
}
function _floor(n,m) {
  return Math.floor(n / m);
}
function _xorxor(n,m) {
  return ~~(n / m);
}
function _orZero(n,m) {
  return (n / m) | 0;
}
function _bitshiftZero(n,m) {
  return (n / m) >> 0;
}
```