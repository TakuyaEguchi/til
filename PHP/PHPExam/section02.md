# 2.テキストと数の操作

- 変数名には$をつける

## 二重引用符を使うと変数名は変数が値に置き換わる

``` PHP
<?php
$str = 'World!';
echo "Hello, $str"; // Hello World!
echo 'Hello, $str'; // Hello $str
// " "の変数展開は区別しにくいので{ }で括るとわかりやすい
echo "Hello,{$str}"; // Hello World!
```

## printf()はフォーマットされた文字列を出力する[*](https://www.php.net/manual/ja/function.printf.php)

``` PHP
<?php
$price = 5;
$off = 0.79;

printf('Price : $%.2f', $price - $off); // Price$4.21
```

## 文字関連の関数(1)

| 関数          | 役割                         |
| ------------- | ---------------------------- |
| strlen()      | 文字列の長さを調べる         |
| substr()      | 文字列の一部を取り出す       |
| str_replace() | 一部の文字列を置き換える     |
| trim()        | 文字列の前後の空白を取り除く |

``` PHP
<?php
$string = '  aaabbb  ';

// strlen():文字列の長さを調べる
echo strlen($string); // 10

// substr():文字列の一部を取り出す
echo substr($string,0,5); //  aaa：最初の5文字を取り出す

// str_replace():一部の文字列を置き換える
echo str_replace('aaa','AAA',$string); //   AAAbbb $string変数のaaaをAAAに置換

// 文字列の前後の空白を取り除く
echo trim($string); // AAAbbb 前後の空白を取り除く
```

## 文字関連の関数(2)

- ucwords()関数は文字列中の単語の最初の文字を大文字にする
- strtolower()関数はすべて小文字にする
- strtoupper()関数はすべて大文字にする

``` PHP
<?php
print ucwords(strtolower('SATO ICHIRO')); // Sato Ichiro

print strtolower('SATO ICHIRO'); // 1 sato ichiro
print ucwords('sato ichiro'); // 2 Sato Ichiro
```

## 文字列結合演算子「.」

```PHP
<?php
print 1 * 8 . 3 * 4; // (1 * 8) をして、(3 * 4)をして文字列結合 812
```

## 変数名の指定

- 変数名の先頭文字はアルファベットかアンダースコア
- 2文字目以降はアルファベットか数字かアンダースコア

## 変数名の大文字・小文字区別

- 「==」は大文字と小文字を**区別する**。一致するときは「1」を返す
- strcasecmt()関数は大文字と小文字を**区別しない**。一致する場合は「0」を返す

``` PHP
<?php
print 'Hello' == 'Hello'; // true(1)
print 'Hello' == 'HELLO'; // false 表示なし
print strcasecmp('Hello' , 'Hello'); // 一致:0
print strcasecmp('Hello','HELLO'); // 一致:0
```

## ヒアドキュメント

- 変数を含む文字列を定義したりyすつりょくしたりするために使われる構文
- 「<<<」と区切り文字ではじめ、終了するときは区切り文字を行頭に記述する

```PHP
<?php
echo "Print string1 : \"PHP\" <br>";
echo <<<_DATA_
Print string2 : "PHP" <br>
_DATA_;
```

## ++演算子, --演算子 代入演算子

- ++$aは+1してからその行を実行
- $a++はその行を実行してから+2
- $a += 2;は$a = $a + 2と同じ意味

``` PHP
<?php
$number = 0;

$number += 1; // 1
$number += 2; // 3
$number += 3; // 6
$number += 4; // 10
$number += 5; // 15
++$number; // 16
print 'number : ' . $number; // number : 16
```
