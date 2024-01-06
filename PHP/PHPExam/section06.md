# 6.データとロジックの結合：オブジェクトの操作

## オブジェクト指向

- PHPはオブジェクト指向の機能が追加された
- オブジェクトは、データとデータを操作する関数を内部に持つ集合体
- クラスからインスタンスを作成することをインスタンス化
- クラスを定義するにはclassキーワードを利用
- メソッドもfunctionキーワードを利用
- プロパティやメソッドを利用するときは「->」を使う
- クラスからインスタンスを作成するときはnewキーワードを使う
- 静的メソッドは「クラス名::静的メソッド名()」と記述する
- コンストラクタは「__construct」で定義する

```PHP
<?php

class Super{
    private $data; // Superクラスのみ利用可
    
    public function getData(){
        return $this->data; // オブジェクト内のdataを返却
    }
    
    // インスタンス生成する際に実行される
    public function __construct($data){
        $this->data = $data; // オブジェクトのdataに引数dataを格納
    }
}

// Superクラスを継承したSubクラス
class Sub extends Super{
    private $param; // Subクラスのみ利用可
    
    public function getParam(){
        return $this->param; // オブジェクト内のparamuを返却
    }
    
    public function __construct($data,$param){
        $this->data = $data; // オブジェクトのdataに引数dataを格納
        $this->param = $param; // オブジェクトのparamに引数paramuを格納
    }
}

// ここから実行される
$obj = new Sub("Red", "Blue"); // Subクラスからインスタンスを生成し、コンストラクタを呼び出す
print "Data: " . $obj->getData() . "\n"; // getData()はSubクラスにはないのでSuperクラスを呼び出すが、$dataは値が入っていないので何も表示されない
print "Param: " . $obj->getParam(); // getParam()はSubクラスのものを呼び出し、設定されたparamが表示される："Blue"
```
