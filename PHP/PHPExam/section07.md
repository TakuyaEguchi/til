# 7.ユーザとの情報交換：Webフォームの作成

## フォーム

- フォームとはWebアプリケーションでよく利用される、ユーザが入力するWebブラウザ上の画面
- フォームを利用するには\<form>タグを使う
- PHPでフォームデータを利用するには\$_GETや\$_POSTを使う
- フォームはユーザから送られたデータを利用してWebサーバとクライアント間の通信が発生する

### クロスサイトスクリプティング対策

- strip_tags()関数は文字列からHTMLタグを取り除く
- htmlentities()関数は特別なHTML文字をエンコードする

### $_SERVERの要素

| 要素        | 説明                                                  |
| ----------- | ----------------------------------------------------- |
| PHP_SELF    | Webサーバに要求するURLのパス名                        |
| SERVER_NAME | PHPが実行されているWebサーバの名前                    |
| SERVER_ADDR | 現在のスクリプトが実行されているWebサーバのIPアドレス |

## フォームのやり取り

- formタグのmethodでGETかPOSTを指定する
- actionでformの内容を送信する宛先を指定する
- phpで受け取るときは$_GET['name']

``` HTML:sample.html
<form method="GET" action="sample.php">
    <input type="text" name="name">
    <input type="submit" name="submit">
</form>
```

```PHP:sample.php
<?
// $_GET['name']; // 普通にform内のnameを受け取る→危険なので以下のように受け取る

// formの内容を安全に受け取る
$name = filter_input(INPUT_GET,'name',FILTER_DEFAULT);

// 受け取った後はバリデーションチェックを入れる
if(!$name){
    echo '名前を入力してください';
    exit();
}

if(strlen($name) < 10){
    echo '10文字未満で入力してください';
    exit();
}
?>

<pre><?php echo htmlspecialchars($name); ?></pre>
```

## null合体演算子??

- サブミットされたデータに値が入力されていないとき警告表示させないときに使う
- PHP7以前はisset()関数を利用している

```HTML:sample2.html
<form method="POST" action="sample2.php">
    <input type="text" name="member_id">
    <input type="submit" name="submit">
</form>
```

```PHP:sample2.php
<?
// formの内容を安全に受け取る
$id = filter_input(INPUT_POST,'member_id',FILTER_SANITIZE_NUMBER_INT);

// $idが入っていない場合は何も表示しない
echo 'ID : ' . $id ?? '';

```

### 複数の値をフォームパラメータに渡す

- 配列として渡し、foreachなどで取り出す
