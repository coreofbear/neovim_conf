# Setting up Neovim on Windows

## Basic installation
1) Install Neovim `winget install Neovim.Neovim`
2) Install vim-plug plugin manager
```
iwr -useb https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim |
ni "$(@($env:XDG_DATA_HOME, $env:LOCALAPPDATA)[$null -eq $env:XDG_DATA_HOME])/  nvim-data/site/autoload/plug.vim" -Force
```
3) Create empty nvim configuration file
`mkdir ~/AppData/Local/nvim`
`touch ~/AppData/Local/nvim/init.vim`
4) Add wrapper lines for vim-plug plugins list
```
call plug#begin('~/AppData/Local/nvim/plugged')
" add the plugin you want to use here.
call plug#end()
```
5) Type `:PlugStatus` in nvim for checking vim-plug

## Setting up LSP:
1) Add `Plug 'neovim/nvim-lspconfig'` to the init.vim plugins list
2) Install clangd LSP server `scoop install clangd`
3) Copy configuration from https://github.com/neovim/nvim-lspconfig in the init.vim
4) Set up clangd support with `require'lspconfig'.clangd.setup{}` 

## Different plugins
