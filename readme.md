/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

brew bundle --file .Brewfile

ln -s .zshrc ~/.zshrc
ln -s .zprofile ~/.zprofile
ln -s .zshev ~/.zshev
