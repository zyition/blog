# Change `/etc/apt/source.list`

```
deb http://cn.archive.ubuntu.com/ubuntu/ xenial main restricted universe multiverse
deb http://cn.archive.ubuntu.com/ubuntu/ xenial-security main restricted universe multiverse
deb http://cn.archive.ubuntu.com/ubuntu/ xenial-updates main restricted universe multiverse
deb http://cn.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
##測試版源
deb http://cn.archive.ubuntu.com/ubuntu/ xenial-proposed main restricted universe multiverse
# 源碼
deb-src http://cn.archive.ubuntu.com/ubuntu/ xenial main restricted universe multiverse
deb-src http://cn.archive.ubuntu.com/ubuntu/ xenial-security main restricted universe multiverse
deb-src http://cn.archive.ubuntu.com/ubuntu/ xenial-updates main restricted universe multiverse
deb-src http://cn.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
##測試版源
deb-src http://cn.archive.ubuntu.com/ubuntu/ xenial-proposed main restricted universe multiverse
# Canonical 合作夥伴和附加
# deb http://archive.canonical.com/ubuntu/ xenial partner
# deb http://extras.ubuntu.com/ubuntu/ xenial main
```

# Update
```
apt update
apt upgrade
```

# Config dircolors to fix terminal color issue
refer to https://github.com/seebi/dircolors-solarized#installation

```
wget -O .dir_colors https://raw.githubusercontent.com/seebi/dircolors-solarized/master/dircolors.256dark
```

# autojump
`apt install autojump`

enable autojump plugin in zshrc

# ZSH
* `apt install zsh`

* install oh-my-zsh
```
sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

## Conf
```
ZSH_THEME="pygmalion"

[[ -z "$TMUX" && -n "$USE_TMUX" ]] && {
    [[ -n "$ATTACH_ONLY" ]] && {
        tmux a 2>/dev/null || {
            cd && exec tmux
        }
        exit
    }

    tmux new-window -c "$PWD" 2>/dev/null && exec tmux a
    exec tmux
}

unsetopt BG_NICE

# fix terminal color issue
if [ -f ~/.dir_colors ]; then
  eval `dircolors ~/.dir_colors`
  fi
```


# Tmux
apt install tmux

install .tmux.conf
```
cd
git clone https://github.com/gpakosz/.tmux.git
ln -s -f .tmux/.tmux.conf
cp .tmux/.tmux.conf.local .
```

set -g mouse on
disable battery plugin

# VIM
config by vim-bootstrap
add below lines into ~/.vimrc.local
```
set nobomb
set nobinary
```

# Configure ssh
ssh-keygen

generate .ssh/config with mode 600
```
Host vps
        Hostname <Your VPS Host>
        Port <Port>
        User <Username>
```

# Link some dirs in windows
ln -s /mnt/c/<path-in-windows> <target-path>

# wsl-terminal conf
```
shell=/bin/zsh
use_tmux = 1
```

Run tools/write-distro-guids-to-config-file.js to generate the distro_guid config. then enable it

# mintty config
To fix color issue uncheck `允许粗体字颜色` if your mintty version <= 2.8.1
