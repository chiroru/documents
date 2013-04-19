### 認証

認証を行っていないクライアントは、1時間に60リクエストで制限される。
これ以上のリクエストを送るには認証しておく必要がある。

認証を行うには以下を実行する。

 $ curl -k -u chiroru https://api.github.com/users/chiroru

上記の方法は単純で便利ですが、認証の方式としてはベーシック認証となります。
GitHubのユーザー名とパスワードが漏えいする可能性があるので基本認証は理想的ではありません。

APIを使用して個人情報を読み書きする必要のあるアプリケーションでは、OAuthを使用する必要があります。

ユーザ名とパスワードを用いた認証の代わりに、OAuthではトークンを使用します。
トークンは、以下の二つの大きな機能を提供します。

* Revokableアクセス：ユーザーが任意の時点でサードパーティ製のアプリに許可を取り消すことができます
* 限定的なアクセス：ユーザはトークンが前に提供することを特定のアクセスを確認することができます

$ curl -k -u chiroru -d '{"scopes": ["repo"]}' https://api.github.com/authorizations
Enter host password for user 'chiroru':
{
  "id": 2321536,
  "url": "https://api.github.com/authorizations/2321536",
  "app": {
  "name": "GitHub API",
  "url": "http://developer.github.com/v3/oauth/#oauth-authorizations-api"
},
  "token": "4a295cf8fa367ab2924250c591a99c560cc16f3c",
  "note": null,
  "note_url": null,
  "created_at": "2013-04-18T02:05:17Z",
  "updated_at": "2013-04-18T02:05:17Z",
  "scopes": [
    "repo"
  ]
}




