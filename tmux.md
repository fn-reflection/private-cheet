# tmux 

## tmuxとは

tmuxはTerminal MUltipleXerの略である。その名の通りターミナルを多重化して扱うこともできるが、ターミナルのセッション情報をサーバー側で保持できるという利点があり、例えばssh接続時にクライアントが落ちてプログラムも実行停止してしまったなんてことを避けるために利用できる。

## tmuxの基本

ターミナルを1:Nのセッション(クライアント)を持ち

セッションは1:Nのウィンドウを持ち、

ウィンドウは1:Nのペインを持つ。

```
terminal-session1-window1_1-pane1_1_1
                           -pane1_1_2
        -session2-window2_1-pane2_1_1
                           -pane2_1_2
                 -window2_2-pane2_2_1
```

## tmuxコマンド

### tmux外部からの操作コマンド

| Command                  | 意味                                     |
| :----------------------- | :--------------------------------------- |
| tmux                     | セッションを作って入る                   |
| tmux new -s abc          | セッションabcを作って入る                |
| tmux a                   | 最後に入ったセッションに入る             |
| tmux a -t abc            | セッションabcに入る                      |
| tmux ls                  | セッション一覧をみる                     |
| tmux kill-session -t abc | セッションabcを消す                      |
| tmux source ~/.tmux.conf | ~/.tmux.confコンフィグファイルを読み込む |

### tmuxセッション内部からの操作コマンド

PREはtmuxのprefixキーを示す。（デフォルトはCtrl+b）

| Command        | 意味                                   |
| :------------- | :------------------------------------- |
| exit           | 今のセッションから出てセッションを消す |
| **PRE ?**      | **コマンド一覧をみる**                 |
| PRE :          | tmuxの外部コマンドが使える             |
| PRE d          | 今のセッションから出る                 |
| PRE s          | セッション一覧をみる                   |
| PRE (<br>PRE ) | セッション間を移動                     |
| PRE w          | ウィンドウ一覧をみる                   |
| PRE c          | ウィンドウを作る                       |
| PRE &          | 今のウィンドウをkillする               |
| PRE →          | ウィンドウ間を移動                     |
| PRE [0-9]      | ウィンドウ間を移動(数字指定)           |
| PRE ;          | 前のアクティブペインに移動             |
| PRE x          | ペインを消す                           |
| PRE E          | ペインを均等分割                       |
| PRE #          | バッファ一覧をみる                     |
| PRE =          | バッファ一覧から選んで貼り付け         |



## tmux.confの設定例

https://github.com/fn-reflection/dotfiles/blob/master/.tmux.conf
