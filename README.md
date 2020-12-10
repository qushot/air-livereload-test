# air-livereload-test

## .air.toml
```toml
[build]
# Just plain old shell command. You could use `make` as well.
cmd = "go build -o ./tmp/main ."
# Binary file yields from `cmd`.
bin = "tmp/main"
```
- cmd: ビルドコマンドを書く
- bin: バイナリ置く場所を指定する
- 他の設定項目は未調査

## 起動
`air -c .air.toml`

## 動作確認
1. 上記コマンドでairを起動する。
1. http://localhost:8080 にアスセスし、`Hello, World`の表示を確認する。
1. handler関数を`Hello, World2`とかに適当に書き換える。
1. air起動中の端末に`main.go has changed`とか`running...`出てくるので、再度localhostにアクセスすると表示が変わる。

### ログ
```
$ air -c .air.toml

  __    _   ___  
 / /\  | | | |_) 
/_/--\ |_| |_| \_ v1.12.1 // live reload for Go apps, with Go1.14.0

mkdir $HOME/go/src/github.com/qushot/air-livereload-test/tmp
watching .
!exclude tmp
watching tools
building...
running...
main.go has changed
building...
running...
```

## tools/tools.goについて
利用するツールの依存関係を記録するため？に、 `tools.go`ってファイルを作って、
ツールのパッケージをブランクインポートしとくといいらしい。
