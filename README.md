# 1. URL（Uniform Resource Locator）とは
インターネット上のリソース（ウェブページ、画像、動画など）のアドレスや位置を示すために使用される一意の識別子。<br>
URLは、プロトコル（`http://`や`https://`など）、ドメイン名（ウェブサイトのアドレス）、パス（ファイルの場所やディレクトリの階層）、クエリ文字列（追加のパラメータやデータ）などの要素から構成される。
# 2. クエリ文字列とは
URLに付加されるパラメータやデータを表す文字列のこと。<br>
URLの末尾に「?」を付けて、その後にキーと値のペアを「キー=値」の形式で指定する。<br>
複数のキーと値は「&」で区切られる。<br>
<br>
例： `https://example.com/search?q=keyword&page=1`<br>
<br>
「q」がキーで「keyword」が値、「page」がキーで「1」が値
# 3. パスパラメーター（パス変数）とは
URL内の一部として指定されるパラメーターのこと。<br>
<br>
例：　`https://example.com/users/{user_id}`<br>
<br>
上記のURLでは、{user_id}の部分がパスパラメーター。この部分には、実際のユーザーIDが指定される。
# 4. クエリ文字列とパスパラメーターの違いについて
クエリ文字列はリソースへの追加情報や要求の詳細を指定するために使用され、パスパラメーターはリソースの一部を識別するために使用される。
# 5. HTTPメソッドについて
クライアントがサーバーに対してどのような操作を要求するかを示すために使用される。
|  HTTPメソッド  |  意味  |
|  ---- | ----  |
|  GET |リソースの取得|
| POST |リソースの作成または処理の実行|
| PUT	|ソースの置き換え|
| PATCH	|リソースの一部の変更|
| DELETE |リソースの削除|
# 6. HTTPステータスコードについて
HTTPステータスコードはリクエストやレスポンスに対する処理結果を示す3桁の数字で、各ステータスコードには特定の意味がある。<br>
クライアントとサーバー間の通信において、リクエストやレスポンスが適切に処理されたかどうかを示す重要な情報となる。
|HTTPステータスコード|意味|詳細|
|-----|-----|-----|
|200|OK |リクエスト成功|
|201|Created|新規リソースを作成|
|400|Bad Request|リクエストが不正な形式|
|404|Not Found|リクエストされたリソースが不明|
|500|Internal Server Error|サーバー内部でエラーが発生||
# 7. HTTPメッセージについて
## (1) リクエストヘッダーとは
HTTPリクエストのメタデータ[^1]を含む部分で、リクエストの属性や設定をサーバーに伝える役割を持つ。

   ```
   GET /api/users HTTP/1.1
   Host: example.com
   User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/89.0.4389.114 Safari/537.36
   Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
   Accept-Language: en-US,en;q=0.9
   Cookie: sessionId=abc12345; lang=en
   ```

この例では、クライアントがexample.comのAPIエンドポイント「/api/users」にGETリクエストを送信している。<br>
リクエストヘッダーには、User-Agentで使用されるブラウザ情報、Acceptで受け入れ可能なコンテンツタイプ、<br>
CookieでクライアントのセッションIDと言語設定が含まれている。
   
## (2) リクエストボディとは
HTTPリクエストのコンテンツを含む部分で、クライアントからサーバーに送信されるデータ本体を格納する。

   ```
   POST /api/users HTTP/1.1
   Host: example.com
   Content-Type: application/json
   Content-Length: 49

   {"username": "john_doe", "email": "john.doe@example.com"}
   ```

この例では、クライアントがexample.comのAPIエンドポイント「/api/users」にJSON形式のデータを含むPOSTリクエストを送信している。<br>
リクエストヘッダーには、Content-Typeでデータの形式がJSONであることを示し、Content-Lengthでデータの長さを指定している。

## (3) レスポンスヘッダーとは
HTTPレスポンスのメタデータ[^1]を含む部分で、レスポンスの属性や設定をクライアントに伝える役割を持つ。

   ```
   HTTP/1.1 200 OK
   Date: Sat, 17 Jul 2023 12:34:56 GMT
   Content-Type: application/json
   Content-Length: 87

   ```

この例では、サーバーがクライアントに対して「200 OK」のステータスコードで応答している。<br>
レスポンスヘッダーには、Dateでレスポンスが生成された日時、Content-TypeでコンテンツタイプがJSONであること、<br>
Content-Lengthでデータの長さが87バイトであることが含まれている。

## (4) レスポンスボディとは
HTTPレスポンスのコンテンツを含む部分で、サーバーからクライアントに送信されるデータ本体を格納する。

   ```
   HTTP/1.1 200 OK
   Date: Sat, 17 Jul 2023 12:34:56 GMT
   Content-Type: text/html
   Content-Length: 84

   <!DOCTYPE html>
   <html>
   <head>
       <title>Example Page</title>
   </head>
   <body>
       <h1>Hello, World!</h1>
   </body>
   </html>
   ```
この例では、サーバーがクライアントに対して「200 OK」のステータスコードで応答している。<br>
レスポンスヘッダーには、Dateでレスポンスが生成された日時、Content-TypeでコンテンツタイプがHTMLであること、<br>
Content-Lengthでデータの長さが84バイトであることが含まれている。<br>
レスポンスボディにはHTML形式のデータが含まれており、ブラウザによって表示されるコンテンツが定義されている。


   [^1]:メタデータ：「データに関するデータ」を指す用語で、データ自体の説明や特性、属性、構造、関係などを表す情報のことを意味する。

*****
   【参考】
   MDN：https://developer.mozilla.org/ja/docs/Glossary/Request_header
