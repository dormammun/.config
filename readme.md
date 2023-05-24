```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

brew bundle --file .Brewfile

rm ~/.zshrc && ln .zshrc ~/.zshrc
rm ~/.zprofile && ln .zprofile ~/.zprofile
rm ~/.zshenv && ln .zshenv ~/.zshenv
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
sz


rm ~/.hyper.js && ln Hyper/.hyper.js ~/.hyper.js

git clone https://github.com/tmux-plugins/tpm ~/.config/tmux/plugins/tpm
rm ~/.tmux.conf && ln ./tmux/.tmux.conf ~/.tmux.conf
st
Ctrl-b I
```
sh -c "$(curl -Ls https://raw.githubusercontent.com/jarun/nnn/master/plugins/getplugs)"

