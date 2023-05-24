```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

brew bundle --file .Brewfile

ln .zshrc ~/.zshrc
ln .zprofile ~/.zprofile
ln .zshev ~/.zshev
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
sz


ln -s Hyper/.hyper.js ~/.hyper.js

git clone https://github.com/tmux-plugins/tpm ~/.config/tmux/plugins/tpm
ln ./tmux/.tmux.conf ~/.tmux.conf
st
Ctrl-b I
```
