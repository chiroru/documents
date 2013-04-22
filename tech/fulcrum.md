### Fulcrum
Pivotal Trackerのクローン。

## インストール手順

以下コマンドを実行し必要なパッケージがインストールされているか確認する。

 yum list  git libxml2 libxml2-devel libxslt-devel

インストールされていなければインストールする。

 git clone https://github.com/malclocke/fulcrum.git

Gemfileを編集し、MySQLに接続する設定に変更する。

 group :production do
   gem 'mysql2'
   gem 'therubyracer'
 end

 bundle install --without development test --no-deployment

MySQLにスキーマを作成する。

 GRANT ALL PRIVILEGES ON `fulcrum%`.* TO 'fulcrum'@'localhost' IDENTIFIED BY 'fulcrum', 'fulcrum'@'%' IDENTIFIED BY 'fulcrum';
 flush privileges;

 create database fulcrum;

Fulcrumのコンフィグレーションを行う。

config/database.ymlを作成、設定する。 config/database.yml.mysqlをコピーして作成するとよい。

config/fulcrum.rbを作成。

マイグレーションの実行。

RAILS_ENV=production bundle exec rake fulcrum:setup db:setup

今回は Apache + Passenger でサã=acp#onPopupPost()
ディレクトリで動かすので、application.rb を変更します。

$ vi config/application.rb

Application クラスの下辺りに以下のように relative_url_root を追記します。

module Fulcrum
  class Application < Rails::Application
      config.action_controller.relative_url_root = '/fulcrum' # 追記

      また、サブディレクトリ以下で動かす場合、そのままだと project.js が動作しないのでこれも修正します。

      $ vi app/assets/javascripts/models/project.js

      以下のように、30行目の「return '/projects/' + this.id;」となっている部分にサブディレクトリ名である「fulcrum」を追加しておきます。

      29   url: function() {
      30     return '/fulcrum/projects/' + this.id; # /fulcrum を追記
      31   },

      assets:precompile を実行しておきます。

      $ RAILS_ENV=production bundle exec rake assets:precompile

## パスワードの設定

 # rails console
 ※ consoleからのアクセス時は、development環境の設定が使われるためconfig/database.ymlのdevelopment設定を正しく行う。
 > User.first.confirm!
 > User.first.update_attributes!(:password => 'pass')

## 参考
* http://d.hatena.ne.jp/akishin999/20130130/1359501604
* http://wholemeal.co.nz/projects/fulcrum.html


