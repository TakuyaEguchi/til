# 4.データのグループ：配列の操作

## 配列の作成方法

- $配列名 = array(値1,値2, ...);
- $配列名[キー] = 値;

```PHP
<?php
$numbers = array(10,20,30);
$numbers[] = 40; // 添字3に追加
$numbers[] = 50; // 添字4に追加
print $numbers[4]; // 50が表示
```

## 連想配列

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

## 配列の要素の追加

- 配列は順序情報を持つハッシュとして実装されている
- キーは省略可能（要素追加時は末尾に追加）
- 配列コピーはメモリ参照

## 配列とforeach文

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

## 配列の並べ替え

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
| count(\$var)       | $varの要素数を返す                         |
| explode(\$d,\$str)  | 文字列\$strを文字列$dで分割し、配列を返す   |
| implode(\$d,\$ary)  | 配列\$aryを文字列\$dで連結し、文字列を返す   |
| unset(\$ary[\$key]) | 配列\$aryのキー\$keyに対応する要素を削除する |

## var_dump()関数

- 変数や配列に関する情報を出力
- 引数を指定すると、配列の各要素の情報を得る
