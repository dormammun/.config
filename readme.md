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

sh -c "$(curl -Ls https://raw.githubusercontent.com/jarun/nnn/master/plugins/getplugs)"
```

# Raw configuration
## Inject Development in Windows

```sh
# Open PowerShell as Admin and Run

# Enable WSL
# For More Visit: https://learn.microsoft.com/en-us/windows/wsl/install
wsl --install

# Install Chocolatey
@"%SystemRoot%\System32\WindowsPowerShell\v1.0\powershell.exe" -NoProfile -InputFormat None -ExecutionPolicy Bypass -Command "iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))" && SET "PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin"

# Install Hyper
choco install hyper -y
```

## Hyper

```js
{
  // wls
  shell: 'C:\\Windows\\System32\\wsl.exe',
  shellArgs: [~],

    // https://github.com/ryanoasis/nerd-fonts/blob/master/patched-fonts/JetBrainsMono/font-info.md
  fontFamily: '"JetBrains Mono"',
  fontSize: 15,

  plugins: ['hyperterm-gruvbox-dark'],
}
```

## Packages

```sh
# WLS
sudo apt update && sudo apt upgrade -y

bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
echo '# Set PATH, MANPATH, etc., for Homebrew.' >> $HOME/.profile 
echo 'eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)"' >> $HOME/.profile 
eval "$(/home/linuxbrew/.linuxbrew/bin/brew shellenv)" 

brew install nvim
brew install nnn
brew install tmux

brew install autojump
brew install starship
brew install zsh-autosuggestions
brew install fzf

# WLS
brew install gcc

# MAC
brew install ripgrep
# OR
# WSL 
brew install ag

# MAC
brew install vivaldi
brew install notion
brew install spotify
brew install hyper
brew install mas
brew install --cask microsoft-edge

# MAC
brew tap homebrew/cask-fonts
brew install --cask font-jetbrains-mono

# WLS
sudo apt install zsh -y
# OR
# MAC
brew install zsh
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

curl -L https://raw.githubusercontent.com/sbugzu/gruvbox-zsh/master/gruvbox.zsh-theme > ~/.oh-my-zsh/custom/themes/gruvbox.zsh-theme
```

## ZSH
Edit `~/.zshrc`
```sh
# If you come from bash you might have to change your $PATH.
# export PATH=$HOME/bin:/usr/local/bin:$PATH

# Path to your oh-my-zsh installation.
export ZSH="$HOME/.oh-my-zsh"

# Set name of the theme to load --- if set to "random", it will
# load a random theme each time oh-my-zsh is loaded, in which case,
# to know which specific one was loaded, run: echo $RANDOM_THEME
# See https://github.com/ohmyzsh/ohmyzsh/wiki/Themes
ZSH_THEME="gruvbox"
SOLARIZED_THEME="dark"

# Set list of themes to pick from when loading at random
# Setting this variable when ZSH_THEME=random will cause zsh to load
# a theme from this variable instead of looking in $ZSH/themes/
# If set to an empty array, this variable will have no effect.
# ZSH_THEME_RANDOM_CANDIDATES=( "robbyrussell" "agnoster" )

# Uncomment the following line to use case-sensitive completion.
# CASE_SENSITIVE="true"

# Uncomment the following line to use hyphen-insensitive completion.
# Case-sensitive completion must be off. _ and - will be interchangeable.
# HYPHEN_INSENSITIVE="true"

# Uncomment one of the following lines to change the auto-update behavior
# zstyle ':omz:update' mode disabled  # disable automatic updates
# zstyle ':omz:update' mode auto      # update automatically without asking
# zstyle ':omz:update' mode reminder  # just remind me to update when it's time

# Uncomment the following line to change how often to auto-update (in days).
# zstyle ':omz:update' frequency 13

# Uncomment the following line if pasting URLs and other text is messed up.
# DISABLE_MAGIC_FUNCTIONS="true"

# Uncomment the following line to disable colors in ls.
# DISABLE_LS_COLORS="true"

# Uncomment the following line to disable auto-setting terminal title.
# DISABLE_AUTO_TITLE="true"

# Uncomment the following line to enable command auto-correction.
# ENABLE_CORRECTION="true"

# Uncomment the following line to display red dots whilst waiting for completion.
# You can also set it to another string to have that shown instead of the default red dots.
# e.g. COMPLETION_WAITING_DOTS="%F{yellow}waiting...%f"
# Caution: this setting can cause issues with multiline prompts in zsh < 5.7.1 (see #5765)
# COMPLETION_WAITING_DOTS="true"

# Uncomment the following line if you want to disable marking untracked files
# under VCS as dirty. This makes repository status check for large repositories
# much, much faster.
# DISABLE_UNTRACKED_FILES_DIRTY="true"

# Uncomment the following line if you want to change the command execution time
# stamp shown in the history command output.
# You can set one of the optional three formats:
# "mm/dd/yyyy"|"dd.mm.yyyy"|"yyyy-mm-dd"
# or set a custom format using the strftime function format specifications,
# see 'man strftime' for details.
# HIST_STAMPS="mm/dd/yyyy"

# Would you like to use another custom folder than $ZSH/custom?
# ZSH_CUSTOM=/path/to/new-custom-folder

# Which plugins would you like to load?
# Standard plugins can be found in $ZSH/plugins/
# Custom plugins may be added to $ZSH_CUSTOM/plugins/
# Example format: plugins=(rails git textmate ruby lighthouse)
# Add wisely, as too many plugins slow down shell startup.
plugins=(
	docker
	docker-compose
	yarn
	tmux
	git
	vi-mode
	autojump
	web-search
	zsh-navigation-tools
	zsh-interactive-cd
	colored-man-pages
)
source /opt/homebrew/share/zsh-autosuggestions/zsh-autosuggestions.zsh

source $ZSH/oh-my-zsh.sh

# User configuration

# export MANPATH="/usr/local/man:$MANPATH"

# You may need to manually set your language environment
# export LANG=en_US.UTF-8

# Preferred editor for local and remote sessions
# if [[ -n $SSH_CONNECTION ]]; then
#   export EDITOR='vim'
# else
#   export EDITOR='mvim'
# fi

# Compilation flags
# export ARCHFLAGS="-arch x86_64"

# Set personal aliases, overriding those provided by oh-my-zsh libs,
# plugins, and themes. Aliases can be placed here, though oh-my-zsh
# users are encouraged to define aliases within the ZSH_CUSTOM folder.
# For a full list of active aliases, run `alias`.
#
# Example aliases
# alias zshconfig="mate ~/.zshrc"
# alias ohmyzsh="mate ~/.oh-my-zsh"

eval "$(starship init zsh)"

bindkey '^y' autosuggest-accept

alias fm="nnn"
alias fms="nnn -S"

alias sn='nvim -u ~/.config/svim/main.vim'
alias e='nvim'
alias ec='nvim ~/.config/nvim/init.vim'

alias ez='nvim ~/.zshrc'
alias sz='source ~/.zshrc'

alias et='nvim ~/.config/tmux/.tmux.conf'
alias st='tmux source ~/.config/tmux/.tmux.conf'

alias eh='nvim ~/.config/Hyper/.hyper.js'

alias memcl='sudo purge'
alias cl='clear'

alias lz='lazygit'
alias gs='git status'
alias gl='git log'
alias glo='git log --onelnie'
alias gm='git commit'
alias gsi='git switch'
alias gst='git stash'
alias gcl='git clone'
alias ga='git add'
alias gaa='git add .'

export NNN_PLUG='j:autojump;'
```

Create file in `~/.config/starship.toml`
```toml
add_newline = true

[shell]
disabled = false
zsh_indicator = "🐙"

[memory_usage]
disabled = false
threshold = 50
format = "$symbol via [${ram_pct} | ${ram}]($style)"

[git_branch]
symbol = "🌿 "

[nodejs]
symbol = "🍩 "
```

Run
```sh
git config --global user.name "Dormammun"
git config --global user.email "khoteiv.dev@gmail.com"
git config --global core.editor nvim
```

## Install Mac Apps
```sh
mas install 441258766 # Magnet
mas install 526298438 # Lightshot Screenshot
mas install 1084211765 # OS Cleaner
mas install 1176895641 # Spark
mas install 1005088137 # Mate Translate(khoteiv.bill@gmail.com)
```

*Alfred*
```
khoteiv.bill@gmail.com

A4SLMTBlNjI2NzM1MDFmAeiE3y8R2kld7A9foz/1JfhEShlpjL
NK9WgsbB0+HpGqoBB40M/vx+MQPOsxKzvzYH/IM86q5+uHHMcP
a5WFi1gC1uQU0SeGd3GrwAkV5OSDM9xupug4pysXBw1MjgNo3P
oz3qkC/lAJTF52f6m4ouJDQspBkrPA4YGGbGnb6ZFJ2/4un12+
```

## VIM
Edit `~/.config/nvim/init.vim`
```sh
"dein Scripts-----------------------------
" Required:
set runtimepath+=/Users/dormammun/.config/nvim/.cache/dein/repos/github.com/Shougo/dein.vim

" Required:
call dein#begin('/Users/dormammun/.config/nvim/.cache/dein')

" Let dein manage dein
" Required:
call dein#add('/Users/dormammun/.config/nvim/.cache/dein/repos/github.com/Shougo/dein.vim')

call dein#add('sheerun/vim-polyglot')

call dein#add('scrooloose/nerdtree')
let g:NERDTreeWinPos = "right"

call dein#add('morhetz/gruvbox')
colorscheme gruvbox

call dein#add('neoclide/coc.nvim', {'build': 'yarn start'})
let g:coc_global_extensions = [
  \'coc-json',
  \'coc-tsserver',
  \'coc-sh',
  \'coc-sql',
  \'coc-tabnine',
  \'coc-prettier',
  \'coc-css',
  \'coc-html-css-support',
  \'coc-emmet',
  \'coc-eslint',
  \'coc-highlight',
  \]
autocmd CursorHold * silent call CocActionAsync('highlight')
function! ShowDocumentation()
  if CocAction('hasProvider', 'hover')
    call CocActionAsync('doHover')
  else
    call feedkeys('K', 'in')
  endif
endfunction

call dein#add('easymotion/vim-easymotion')

call dein#add('tpope/vim-surround')

call dein#add('liuchengxu/vim-which-key')
nmap <silent> <leader> :WhichKey ','<CR>
nmap <silent> s :WhichKey 's'<CR>
nmap <silent> <Space> :WhichKey '<Space>'<CR>

call dein#add('Raimondi/delimitMate')

call dein#add('mhinz/vim-startify')

call dein#add('junegunn/vim-easy-align')

call dein#add('nvim-lua/plenary.nvim')
call dein#add('nvim-telescope/telescope.nvim')
call dein#add('fannheyward/telescope-coc.nvim')

call dein#end()

" If you want to install not installed plugins on startup.
if dein#check_install()
  call dein#install()
endif

"End dein Scripts-------------------------
set nocompatible           " disable compatibility to old-time vi
set showmatch              " show matching
set ignorecase             " case insensitive
set hlsearch               " highlight search
set incsearch              " incremental search
set tabstop=2              " number of columns occupied by a tab
set softtabstop=2          " see multiple spaces as tabstops so <BS> does the right thing
set expandtab              " converts tabs to white space
set shiftwidth=2           " width for autoindents
set autoindent             " indent a new line the same amount as the line just typed
set number                 " add line numbers
set wildmode=longest,list  " get bash-like tab completions
filetype plugin indent on  " allow auto-indenting depending on file type
syntax on                  " syntax highlighting
set mouse=a                " enable mouse click
                           " set clipboard=unnamedplus   " using system clipboard
filetype plugin on
set cursorline             " highlight current cursorline
set ttyfast                " Speed up scrolling in Vim
set backupdir=~/.cache/vim " Directory to store backup files.
set timeoutlen=500         " Wait before map sequence to complete
set updatetime=200         " Time to save swap file
set scrolloff=8            " Screen lines visible below the cursor
set splitright             " New window on right of current
set splitbelow             " New window on below of current
set jumpoptions=view       " ???
set signcolumn=yes         " ???

let mapleader = ","

" -Vim-
nmap <silent> sc :source $MYVIMRC<CR>
nmap <silent> sec :e $MYVIMRC<CR>
" -Vim#End-

" -View-
nmap <silent> sft :NERDTree<CR>
nmap <silent> sfT :NERDTreeToggle<CR>
nmap <silent> sfo :NERDTreeFind<CR>
" -View#End-

" -Edit-
nmap <silent> <Space>fS :wa<CR>
nmap <silent> <Space>fs :w<CR>
" -Edit#End-

" -Navigation-
nmap sfw :lua require'telescope.builtin'.grep_string{}<CR>
nmap sfi :lua require'telescope.builtin'.current_buffer_fuzzy_find{}<CR>

nmap <leader>F :lua require'telescope.builtin'.live_grep{}<CR>
nmap <leader>o :lua require'telescope.builtin'.find_files{}<CR>
nmap <leader>b :lua require'telescope.builtin'.buffers{}<CR>
nmap <leader>sm :lua require'telescope.builtin'.marks{}<CR>
nmap <leader>sR :lua require'telescope.builtin'.registers{}<CR>
" TODO: fix
nmap <leader>se :Telescope coc mru<CR>

let g:startify_session_persistence = 1
let g:startify_session_autoload = 1
let g:startify_update_oldfiles = 1
let g:startify_change_to_vcs_root = 1
nmap <silent> <leader>S :SSave <CR>
nmap <silent> <leader>L :SLoad <CR>
" -Navigation#End-

" -Buffers & Tabs-
nmap <silent> stT :BuffergatorToggle<CR>
nmap <silent> stt :BuffergatorOpen<CR>
nmap <silent> stn :tabnew<CR>
nmap <silent> stc :tabclose<CR>

nmap <silent> <Space>bd :bd<CR>
nmap <silent> <Space>bD :%bd<CR>
nmap <silent> <Space>bN :enew<CR>

nmap ]b :bnext<CR>
nmap [b :bprev<CR>

nmap <silent> sG :split<CR>
nmap <silent> sg :vsplit<CR>
nmap <silent> so :only<CR>
nmap <silent> sO :q<CR>
" -Buffers & Tabs#End-

" -Selection-
xmap if <Plug>(coc-funcobj-i)
omap if <Plug>(coc-funcobj-i)
xmap af <Plug>(coc-funcobj-a)
omap af <Plug>(coc-funcobj-a)
xmap ic <Plug>(coc-classobj-i)
omap ic <Plug>(coc-classobj-i)
xmap ac <Plug>(coc-classobj-a)
omap ac <Plug>(coc-classobj-a)
" -Selection#End-

" -Code-
nmap <silent> K :call ShowDocumentation()<CR>
nmap <leader>ss :Telescope coc document_symbols<CR>
nmap <leader>sS :Telescope coc workspace_symbols<CR>
nmap <leader>a :Telescope coc line_code_actions<CR>
nmap <leader>A :Telescope coc file_code_actions<CR>
nmap <leader>sd :Telescope coc diagnostics<CR>
nmap <leader>sD :Telescope coc workspace_diagnostics<CR>

nmap <leader>dd <Plug>(coc-diagnostic-next)
nmap <leader>dD <Plug>(coc-diagnostic-prev)
nmap <leader>dE <Plug>(coc-diagnostic-prev-error)
nmap <leader>de <Plug>(coc-diagnostic-next-error)
nmap <leader>di <Plug>(coc-diagnostic-info)
nmap <leader>r <Plug>(coc-rename)
xmap <leader>il <Plug>(EasyAlign)

" Use tab for trigger completion with characters ahead and navigate
" NOTE: There's always complete item selected by default, you may want to enable
" no select by `"suggest.noselect": true` in your configuration file
" NOTE: Use command ':verbose imap <tab>' to make sure tab is not mapped by
" other plugin before putting this into your config
inoremap <silent><expr> <TAB>
      \ coc#pum#visible() ? coc#pum#next(1) :
      \ CheckBackspace() ? "\<Tab>" :
      \ coc#refresh()
inoremap <expr><S-TAB> coc#pum#visible() ? coc#pum#prev(1) : "\<C-h>"

" Make <CR> to accept selected completion item or notify coc.nvim to format
" <C-g>u breaks current undo, please make your own choice
inoremap <silent><expr> <CR> coc#pum#visible() ? coc#pum#confirm()
                              \: "\<C-g>u\<CR>\<c-r>=coc#on_enter()\<CR>"

function! CheckBackspace() abort
  let col = col('.') - 1
  return !col || getline('.')[col - 1]  =~# '\s'
endfunction
inoremap <silent><expr> <C-e> coc#pum#visible() ? coc#pum#cancel() : "\<C-e>"
inoremap <silent><expr> <C-y> coc#pum#visible() ? coc#pum#confirm() : "\<C-y>"
" -Code#End-

" -GoTo-
nmap gr :Telescope coc references<CR>
nmap gd :Telescope coc definitions<CR>
nmap gD :Telescope coc declarations<CR>
nmap gy :Telescope coc type_definitions<CR>
nmap gi :Telescope coc implementations<CR>

nmap <silent> gc `.
nmap gw <Plug>(easymotion-s)
" -GoTo#End-
```

Edit:
`nvim ~/.config/nvim/coc-settings.json`
```json
{
  "suggest.autoTrigger": "none",
  "diagnostic.enableHighlightLineNumber": false,
  "diagnostic.enableMessage": "jump"
}
```

## Tmux
```
set -g @plugin 'tmux-plugins/tmux-sensible'
set -g @plugin 'christoomey/vim-tmux-navigator'
set -g @plugin 'catppuccin/tmux'
set -g @plugin 'tmux-plugins/tmux-yank'
set -g @plugin 'tmux-plugins/tmux-resurrect'
set -g @plugin 'tmux-plugins/tmux-continuum'
#set -g @plugin 'caiogondim/maglev'
#set -g @plugin 'tmux-plugins/tmux-pain-control'
#set -g @plugin 'tmux-plugins/tmux-copycat'
#set -g @plugin 'tmux-plugins/tmux-open'
#set -g @plugin 'tmux-plugins/tmux-battery'
#set -g @plugin 'tmux-plugins/tmux-cpu'
#set -g @plugin 'tmux-plugins/tmux-net-speed'
set -g @plugin 'tmux-plugins/tpm'
run '~/.config/tmux/plugins/tpm/tpm'

set -g @catppuccin_window_tabs_enabled on
set -g @catppuccin_flavour 'frape'

set -g escape-time 10
set-option -sa terminal-overrides ",xterm*:Tc"
set -g mouse on
set -g status-interval 5

set -g base-index 1
set -g pane-base-index 1
set-window-option -g pane-base-index 1
set-option -g renumber-windows on

set-window-option -g mode-keys vi
bind-key -T copy-mode-vi v send -X begin-selection
bind-key -T copy-mode-vi V send -X select-line
bind-key -T copy-mode-vi y send -X copy-pipe-and-cancel 'xclip -in -selection clipboard'

set-option default-terminal "screen-256color"
set-option -g allow-rename off

bind s choose-tree -sZ -O name

set -g @resurrect-capture-pane-contents 'on'
set -g @continuum-boot 'on'
```
