
# スクリプトが置いてあるディレクトリの絶対パス

```
script_dir_path=$(dirname $(readlink -f $0))
```

### ref
https://qiita.com/m-yamashita/items/889c116b92dc0bf4ea7d#実行されている自分自身のディレクトリを取得する
