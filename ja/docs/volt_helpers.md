
## ロギング

Volt はロギングのためのヘルパーを提供しています。```Volt.logger``` を実行すると、Ruby の logger のインスタンスを返します。詳細は [ここ](http://www.ruby-doc.org/stdlib-2.1.3/libdoc/logger/rdoc/Logger.html) を参照してください。

```ruby
Volt.logger.info("Some info...")
```

logger を変更したい場合は以下のようにします:

```ruby
Volt.logger = Logger.new
```

## アプリケーションの構成

Volt は他の多くのフレームワークと同様に、環境 (environment) フラグによっていくつかのデフォルト設定を変更することができます。Volt の環境を設定するには VOLT_ENV 環境変数を使用します。

アプリケーションの ```config``` フォルダーにあるすべてのファイルは、Volt の起動時にすべて読み込まれます。これは Rails の ```initializers``` フォルダーに似ています。

Volt には、初めからいくつかのデフォルト構成が設定されているため、すぐに使用を開始することができます。データベースやアプリケーション名などの構成は config/app.rb ファイルで設定することができます。以下が、現時点で用意されている構成オプションです:

| オプション名 | デフォルト値           | 詳細                                                          |
|-----------|---------------------------|---------------------------------------------------------------|
| app_name  | 現在のフォルダー名        | ロギングなどの用途で内部的に使用されます。|
| db_driver | 'mongo'                   | 現在サポートしているドライバーは mongo のみですが、近いうちに追加される予定です。|
| db_name   | "#{app_name}_#{Volt.env}  | mongo のデータベース名です。|
| db_host   | 'localhost'               | mongo のデータベースのためのホスト名です。|
| db_port   | 27017                     | mongo のデータベースのためのポートです。|
| compress_deflate | false              | true の場合、アプリケーションサーバーで圧縮を行います。(ただ、これは本来は Nginx などに任せた方が良いでしょう)。 |