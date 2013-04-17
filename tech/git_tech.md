### リモートブランチ

## 紐づいているリモートリポジトリを確認する

 $ git remote
 origin

 $ git remote -v
 origin  https://github.com/SpringSource/spring-mvc-showcase.git (fetch)
 origin  https://github.com/SpringSource/spring-mvc-showcase.git (push)

「-v」オプションを指定するとURLも確認できる。

## リモートリポジトリを追加する

書式は以下の通り。 
 git remote add ショートネーム（リポジトリのエイリアスのようなもの） URL

 git remote add chiroru https://github.com/chiroru/spring-mvc-chat.git
 git push chiroru master

※ push した際には指定したブランチ名に内容が反映される。ローカルとリモートの
　ブランチ名は一致しない。

### 参考

* http://www.backlog.jp/git-guide/
* http://git-scm.com/book/ja/%E4%BD%BF%E3%81%84%E5%A7%8B%E3%82%81%E3%82%8B



