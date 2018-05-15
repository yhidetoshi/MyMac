## ZSH

- zsh(oh-my-zsh)
  - `$ brew update`
  - `$ brew install zsh`
  - `$ curl -L https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh | sh`

- zpreztoをダウンロード
  - https://github.com/sorin-ionescu/prezto

- pecoをインストール
  - `$ brew install peco`

#### pecoの設定
- zshにてコマンド検索の実行をできるようにする(.zshrcに追記する)
```
# for peco (brew install peco)
function select-history() {
    local tac
    if which tac > /dev/null; then
        tac="tac"
    else
        tac="tail -r"
    fi
    BUFFER=$(fc -l -n 1 | eval $tac | peco --query "$LBUFFER")
    CURSOR=$#BUFFER
    zle -R -c
}
    zle -N select-history
    bindkey '^r' select-history
```
