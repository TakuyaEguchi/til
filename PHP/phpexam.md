# PHP技術者認定[初級]試験

## 1.PHPの概要

- プログラムをコンパイルせずに実行できる**サーバサイドスクリプト言語**
- JavaScriptは**クライアントサイドスクリプト言語**
- 使用に**ライセンス料は不要**
- クロスプラットフォームに対応
- **CGI**規格をサポートするWebサーバであれば使用OK
- PHPのタグは\<?php ?>で記述する

``` PHP
<head><title>hello PHP</title>
</head>
<body>
<?php
    echo 'Hello PHP World!' . "\n";
?>
</body>
```

- コメントは#または//複数行コメントは/\*&nbsp;*/で囲む
- 大文字と小文字は区別しないが変数名は区別する
- ホワイトスペースは半角スペース、タブ、改行

## 2.テキストと数の操作

- 変数名には$をつける

### 二重引用符を使うと変数名は変数が値に置き換わる

``` PHP
<?php
$str = 'World!';
echo "Hello, $str"; // Hello World!
echo 'Hello, $str'; // Hello $str
// " "の変数展開は区別しにくいので{ }で括るとわかりやすい
echo "Hello,{$str}"; // Hello World!
?>
```

### printf()はフォーマットされた文字列を出力する[*](https://www.php.net/manual/ja/function.printf.php)

``` PHP
<?php
$price = 5;
$off = 0.79;

printf('Price : $%.2f', $price - $off); // Price$4.21
?>
```

### 文字関連の関数(1)

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
?>
```

### 文字関連の関数(2)

- ucwords()関数は文字列中の単語の最初の文字を大文字にする
- strtolower()関数はすべて小文字にする
- strtoupper()関数はすべて大文字にする

``` PHP
<?php
print ucwords(strtolower('SATO ICHIRO')); // Sato Ichiro

print strtolower('SATO ICHIRO'); // 1 sato ichiro
print ucwords('sato ichiro'); // 2 Sato Ichiro
?>
```

### 文字列結合演算子「.」

```PHP
<?php
print 1 * 8 . 3 * 4; // (1 * 8) をして、(3 * 4)をして文字列結合 812
?>
```

### 変数名の指定

- 変数名の先頭文字はアルファベットかアンダースコア
- 2文字目以降はアルファベットか数字かアンダースコア

### 変数名の大文字・小文字区別

- 「==」は大文字と小文字を**区別する**。一致するときは「1」を返す
- strcasecmt()関数は大文字と小文字を**区別しない**。一致する場合は「0」を返す

``` PHP
<?php
print 'Hello' == 'Hello'; // true(1)
print 'Hello' == 'HELLO'; // false 表示なし
print strcasecmp('Hello' , 'Hello'); // 一致:0
print strcasecmp('Hello','HELLO'); // 一致:0
?>
```

### ヒアドキュメント

- 変数を含む文字列を定義したりyすつりょくしたりするために使われる構文
- 「<<<」と区切り文字ではじめ、終了するときは区切り文字を行頭に記述する

```PHP
<?php
echo "Print string1 : \"PHP\" <br>";
echo <<<_DATA_
Print string2 : "PHP" <br>
_DATA_;
?>
```

### ++演算子, --演算子 代入演算子

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
?>
```

## 3.ロジック：判定と繰り返し

### 真偽値

- ほとんどのスカラー値はtrue
- 0と0.0、空の文字列、0だけを含む文字列はfalse

``` PHP
<?php

if('abc'){
    print 'abcは' . true; // abcはtrue
}else{
    print false;
};

if(0){
    print true;
}else{
    print false; // 0はfalse
}

if(0.0){
    print true;
}else{
    print false; // 0.0はfalse
}

if(40){
    print '40は' . true; // 40はtrue
}else{
    print false;
}

if('phptest' . '@exeample.com'){
    print "'phptest' . '@exeample.com'は" . true; // 'phptest' . '@exeample.com'はtrue 
}else{
    print false;
}

if(4-7+3){
    print true;
}else{
    print false; // 0なのでfalse
}
?>

```

### 等価演算子

| 比較演算子 | 役割                                 |
| ---------- | ------------------------------------ |
| ==         | 等しい（データ型まで判定しない）     |
| ===        | 値及びデータ型が等しい               |
| !=         | 等しくない（データ型まで判定しない） |
| !==        | 値またはデータ型が等しくない         |

``` PHP
<?php

$data = '10';

if($data == 10){
    print "1"; // データ型まで判定しないので表示される
}

if($data === 10){
    print "2"; // データ型が一致しないので表示されない
}
?>
```

### abs()関数

- abs()関数は引数の絶対値を返す

``` PHP
<?php

if(abs(-100) > abs(-50)){
    print "AAA"; // 100 > 50の判定となるので表示される
}

if("abc" > "xyz"){
    print "BBB"; // アルファベット順で比較しfalseなので表示されない
}elseif("567" < "890"){
    print "CCC"; // 「567」<「890」の比較し、trueなので表示
}
?>
```

### 文字列と数値の比較[*](https://zenn.dev/ymkn8crz/articles/361492876c2c56)

- PHP7は**文字列が数値に変換**される
- PHP8は**数値が文字列に変換**される

``` PHP
<?php

if('9crz' < 88){
    print 'answer7'; // PHP7は 9 < 88で比較
}else {
    print 'answer8'; // PHP8は '9crz' < '88'で比較
}
```

### strcmp()関数

- アルファベット順で引数を比較
- 1番目の引数が2番目の引数より大きい場合は正の値
- 1番目の引数が2番目の引数より小さい場合は負の値

```PHP
<?php

if(strcmp("54321","6789") > 0){
    print "Over";
}else{
    print "Under"; // 1番目の引数が2番目の引数より小さいので負の値を返す
}
```

### 宇宙演算子<=>

- 演算子の左の値が右の値より小さい場合は負の値「-1」大きい場合は正の値「1」等しい場合は「0」

```PHP
<?php

$ans = 2 <=> 22.5; // -1

if($ans > 0){
    print "Over";
}else{
    print "Under"; // falseなのでUnderが表示
}
```

### 論理演算子

- 「式 && 式」両方の式がtrueの場合は全体がtrue
- 「式 || 式」片方の式がtrueの場合は全体がtrue

### while文,for文

- Javaと同様の使い方

## 4.データのグループ：配列の操作

### 配列の作成方法

- $配列名 = array(値1,値2, ...);
- $配列名[キー] = 値;

```PHP
<?php
$numbers = array(10,20,30);
$numbers[] = 40; // 添字3に追加
$numbers[] = 50; // 添字4に追加
print $numbers[4]; // 50が表示
```

### 連想配列

- 文字列をキーとした配列を連想配列という
- array()のときは =>で区切る

```PHP
<?php
$colors['sea'] = 'blue';
$colors['left'] = 'green';
$colors['night'] = 'black';

$scores = array('国語' => 80,
                '数学' => 90,
                '英語' => 75);

```

### 配列の要素の追加

- 配列は順序情報を持つハッシュとして実装されている
- キーは省略可能（要素追加時は末尾に追加）
- 配列コピーはメモリ参照

### 配列とforeach文

- 配列の順番は、要素が追加された順番と同じ
  
```PHP
<?php
$colors[0] = 'red';
$colors[1] = 'yellow';
$colors[3] = 'orange';
$colors[2] = 'blue';

foreach ($colors as $color){
    // 格納された順番に表示
    print "$color "; // red yellow orange blue
}

foreach($colors as $key => $value){
    print "$key: $value"; // 0: red 1: yellow 3: orange 2: blue
}
```

### 配列の並べ替え

| 関数         | 並べ替えの基準 | 意味                                                             |
| ------------ | -------------- | ---------------------------------------------------------------- |
| sort($ary)   | 値             | 配列$aryの値を昇順に並べ替える                                   |
| asort($ary)  | 値             | 連想配列$aryの値を、キーと要素の関係を保持しつつ昇順に並べ替える |
| ksort($ary)  | キー           | 連想配列$aryの値を、キーと要素の関係を保持しつつ昇順に並べ替える |
| rsort($ary)  | 値             | 配列$aryの値を降順に並べ替える                                   |
| arsort($ary) | 値             | 配列$aryの値を降順に並べ替える                                   |
| krsort($ary) | キー           | 連想配列$aryの値を、キーと要素の関係を保持しつつ降順に並べ替える |

| 関数              | 意味                                       |
| ----------------- | ------------------------------------------ |
| count($var)       | $varの要素数を返す                         |
| explode($d,$str)  | 文字列$strを文字列$dで分割し、配列を返す   |
| implode($d,$ary)  | 配列$aryを文字列$dで連結し、文字列を返す   |
| unset($ary[$key]) | 配列$aryのキー$keyに対応する要素を削除する |

### var_dump()関数

- 変数や配列に関する情報を出力
- 引数を指定すると、配列の各要素の情報を得る

## 5.ロジックのグループ：関数とファイル

### 関数の宣言

```PHP
<?php

// 関数の宣言　場所はどこでも可
function add($data1, $data2){
    $sum = $data1 + $data2;
    return $sum; // 戻り値がない場合はreturn不要
}

print add(10,20); // 30
```

### 関数の引数

- デフォルト値を使うことができる
- 呼び出しの際に引数が設定されていれば優先
- デフォルト値に変数は指定できない

```PHP
<?php
function message($message, $name = "Hanako"){
    print "$message, $name";
}

message("Hello", "taro"); // Hello,Taro
message("Hello"); // Hello,Hanako
```

### スコープ

- 関数の内部で変数の値を変更しても、関数の外部にある変数には影響を与えない
- グローバル変数：関数の外部で定義された変数
- ローカル変数：関数内で定義された変数
- globalキーワードを付けるとローカル変数ではなくグローバル変数として扱われる
- $GLOBALSに変数をキー指定するとグローバル変数として扱われる

```PHP
<?php

$num1 = 100;
$num2 = 200;
foo();

funtion foo(){
    print $num1; // ローカル変数として未定義なのでエラー
    global $num2;
    print num2; // グローバル変数として扱うので「200」と表示
}
```

```PHP
<?php

$num = 100;
foo();

funtion foo(){
    print $GLOBALS['num']; // グローバル変数numを参照するので「100」と表示する
}
```
