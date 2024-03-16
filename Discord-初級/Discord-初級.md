# DiscordBotを作る(初級編)
## 初級編の目標
1. DiscordのBotアカウントを作成する
1. サーバーにDiscordBotを招待する

[参考リンク](https://discordpy.readthedocs.io/ja/latest/discord.html)


## DiscordBotのアカウント作成
1. [Discordのウェブサイト](https://discord.com/) にログインできていることを確認する<br>
(Discordを開くを押してDiscordのチャット画面が開けばOK、電話認証、メール認証をしていなかったら指示に従ってやる)

1. [Applicationページ](https://discord.com/developers/applications) に移動 <br>
(アカウントの認証が必要ですみたいな文言が出てきたらログインができていないので1に戻る)<bt>
![alt text](application_page.png)

1. New Application ボタンを押してアプリケーション名を記入してCreateボタンを押す<br>
(日本語や記号もOK)<br>
![alt text](name_sample.png)

1. [Applicationページ](https://discord.com/developers/applications)で作成したBotを選択

1. SETTINGSのOAuth2タブを選択し、scopesのチェックボックスのbotにチェックを入れる<br>
![alt text](bot_check.png)

1. Bot PermissionsからBotの機能に必要な権限にチェックを入れる<br>
(今回は下の画像のように入れてください)<br>
![alt text](bot_permission.png)

1. GENERATED URLのURLをコピーしてブラウザに貼り付け、Botを招待したいサーバーを選択し、「認証」をクリックするとサーバーに招待できます<br>
(Botを追加するサーバー管理権限が必要です)
![alt text](bot_invitation.png)


招待できたら初級編は終了です。
