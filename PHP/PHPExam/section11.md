# 11.他のWebサイトやサービスとのやり取り

## cURL

- cURL関数によりHTTPリクエストとレスポンスを柔軟に利用することができる

```PHP:sample.php
<?php

$url = "https://www.yahoo.co.jp/";

//cURLセッションを初期化する
$ch = curl_init();

//URLとオプションを指定する
curl_setopt($ch, CURLOPT_URL, $url);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);

//URLの情報を取得する
$res =  curl_exec($ch);

//結果を表示する
var_dump($res);

//セッションを終了する
curl_close($conn);

```

## curl_getinfo()

- 引数に指定したcURLのハンドルをもとにリクエストに関する情報を返す
