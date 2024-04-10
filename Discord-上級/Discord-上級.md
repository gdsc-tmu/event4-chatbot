# DiscordBotを作る(上級編)
## 上級編の内容
* ローカル環境(自分のPC上でDiscordBotの開発をする)
* DiscordBotを常時オンラインにできるようにするためには
* DiscordBotの機能を増やす

## ローカル環境(自分のPC上でDiscordBotの開発をする)

ローカル環境で開発を行うにはPythonを実行する環境を整える必要があります.ここではvenvという仮想環境を用意してその中で実行する環境を整えます。手元でPythonが動く環境がない方は今日はRepl.itを使うことをおすすめします。<br>
mac,linuxの人は
```
python3 --version
```
とコンソールで打ってpythonのバージョン表示が出るか確認しましょう.pythonのバージョンが表示されればpythonを実行する環境があります.<br>
windowsの人は同じくコマンドプロンプトで
```
python –version
```
と打って確認してください .<br>
以下pythonの実行環境があることを前提としています.

### 作業用のディレクトリを作成し移動

```
mkdir DiscordBot
cd DiscordBot
```

### pythonの仮想環境を作成

Windowsの場合
```bash
python -m venv .venv
```

Linxu/Macの場合
```bash
python3 -m venv .venv
```

### 仮想環境をアクティベート

Windowsの場合
```bash
.venv\Scripts\activate
```
Linux/Macの場合
```
source .venv/bin/activate
```
コンソール上で(.venv)といった表記が出ればOKです。

### 必要なパッケージのインストール
```
pip install discord.py python-dotenv
```
適宜必要になったらほかも入れてください

### 環境変数の設定(中級編の6に対応する内容です)
ローカル環境ではRepl.itと同じようにTOKENを管理できないので.envというファイルにTOKEN情報を書き込みます。
Windowsの場合
```
type nul > .env
```
Linux/Macの場合
```
touch .env
```
として.envファイルを作成してください.ファイルマネージャーとかFinderとかから作っても問題ないです。　

envファイルを作成したら以下を記述してださい。

```
TOKEN='Discordアカウントの準備で作成したトークンをここに'
```

※envの内容はいわゆるCredentialsなので外に漏らさないように管理しましょう。

これで環境の構築は完了です。あとはこのディレクトリ内でpythonファイルを作成しコードを書いて実行して見ましょう
コードの実行は例えばmain.pyなら
Windowsの場合
```
python main.py
```
Mac/Linuxの場合
```
python3 main.py
```
で実行できます。

### 2回目以降
２回目以降は環境の構築は不要なので作業ディレクトリに移動して
Windowsの場合
```bash
.venv\Scripts\activate
```
Linux/Macの場合
```
source .venv/bin/activate
```
で仮想環境をアクティベートしてください。

### サンプルコード
中級編と同じことができるプログラムです

```python
# インストールした discord.py を読み込む
import discord
import os
from dotenv import load_dotenv

load_dotenv()
TOKEN = os.getenv("TOKEN")
# 接続に必要なオブジェクトを生成
client = discord.Client(intents=discord.Intents.all())

@client.event
async def on_ready():
    print('We have logged in as {0.user}'.format(client))

@client.event
async def on_message(message):
    if message.author == client.user:
        return

    if message.content.startswith('$hello'):
        await message.channel.send('Hello!')

# Botの起動とDiscordサーバーへの接続
client.run(TOKEN)
```

## DiscordBotを常時オンラインにするには
中級編でやったようにRepl.it上でプログラムを実行するとBotをオンラインにしてチャットのやり取りなどができるようになります。
しかし、Repl.itを閉じたり、実行から１時間程度経つとオフラインになってしまいます。
### デプロイをする
DiscordBotを常時オンラインにするためには「デプロイ」をする必要があります。デプロイとは簡単に言うと実行ファイルをWebサーバー上に配置して、常に利用できる状態にすることです。Webサーバー利用するため多くの場合デプロイをしてサービスを稼働しつづけるためにはお金がかかるのですが、中には条件付きで無料でデプロイができるサービスもあります。
詳しくは下の記事を見たり、調べたりしてください
[クラウドサービスRenderを利用したPythonアプリの無料デプロイ方法](https://qiita.com/kakiuchis/items/0225664568ece7b7b08b)

## DiscordBotの機能を増やす
使えそうな記事を共有します

[Pythonで実用Discord Bot(discordpy解説)](https://qiita.com/1ntegrale9/items/9d570ef8175cf178468f)

[Discord Botを作ってみよう #02 - スラッシュコマンドを使ってみよう](https://qiita.com/ukwhatn/items/48953e30ed67dee6fe38)

[誰でも作れる！Discord Bot（応用編）](https://note.com/exteoi/n/n87bd4fa02c95)