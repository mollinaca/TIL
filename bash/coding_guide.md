# bash コーディング規約

## reference
[Google - Shell Style Guide](https://google.github.io/styleguide/shell.xml)  
[Qiita - bashコーディング規約](https://qiita.com/mashumashu/items/f5b5ff62fef8af0859c5)  
[Qiita - Googleの肩に乗ってShellコーディングしちゃおう](https://qiita.com/laqiiz/items/5f72ca668f1c58176644)  
[M3 Tech Blog - bashスクリプティング研修の資料を公開します](https://www.m3tech.blog/entry/2018/08/21/bash-scripting)  


## templete

```bash:templete.sh
#!/bin/bash
# Description :
#  This is ShellScript templete
set -uC
script_dir=$(dirname $(readlink -f $0))
cd "${script_dir}"

# 設定など
source ./setting.ini

# グローバル定数
readonly DEBUG=false
readonly LOG_DIR=./log

################
# function
################

function echo_dbg() {
    echo "'+%Y/%m/%d %H:%m:%S' [dbg] ${1}" 1>&2
    return 0
}

function usage() {
  # パラメータの詳細を必ず明記すること
  cat <<EOS >&2
Usage: $0 [-o OUTPUT_FILE] [-a] INPUT_FILE
  INPUT_FILE      入力ファイル
  -o OUTPUT_FILE  出力ファイル
  -a              オプション。〜〜を〜〜として動作します
EOS
  exit 1
}

function parse_args() {
  while getopts "o:a" OPT; do
    case $OPT in
      o) OUTPUT_FILE=$OPTARG ;;
      a) FLAG=1 ;;
      ?) usage;;
    esac
  done

  shift $((OPTIND - 1))

  INPUT_FILE=${1:-}

  if [[ "$INPUT_FILE" == "" ]]; then
    usage
  fi
}

################
# main
################

if [[ "${BASH_SOURCE[0]}" == "${0}" ]]; then
  parse_args "$@"
  main "$OUTPUT_FILE" "$INPUT_FILE" "$FLAG"
fi

exit 0

```

## shebang

## doc

## 命名規約

### 定数

### 変数

### 関数

## オプション解析