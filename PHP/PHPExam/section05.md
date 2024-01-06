# 5.ロジックのグループ：関数とファイル

## 関数の宣言

```PHP
<?php

// 関数の宣言　場所はどこでも可
function add($data1, $data2){
    $sum = $data1 + $data2;
    return $sum; // 戻り値がない場合はreturn不要
}

print add(10,20); // 30
```

## 関数の引数

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

## スコープ

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
