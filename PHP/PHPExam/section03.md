# 3.ロジック：判定と繰り返し

## 真偽値

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
```

## 等価演算子

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
```

## abs()関数

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
```

## 文字列と数値の比較[*](https://zenn.dev/ymkn8crz/articles/361492876c2c56)

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

## strcmp()関数

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

## 宇宙演算子<=>

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

## 論理演算子

- 「式 && 式」両方の式がtrueの場合は全体がtrue
- 「式 || 式」片方の式がtrueの場合は全体がtrue

### while文,for文

- Javaと同様の使い方
