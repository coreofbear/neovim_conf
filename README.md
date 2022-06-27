# Setting up Neovim on Windows
Setting up Neovim guide for Embedded C development on Windows 10

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

## Setup LSP (Language Server Processor):
1) Add `Plug 'neovim/nvim-lspconfig'` to the init.vim plugins list
2) Type `:PlugInstall` in nvim for install the plugin
3) Install clangd LSP server `scoop install clangd`
4) Copy configuration from [nvim-lspconfig](https://github.com/neovim/nvim-lspconfig) in the init.vim
5) Set up clangd support with `require'lspconfig'.clangd.setup{}` 

## Set up Treesitter (improved syntax highlight)
1) Add `Plug 'nvim-treesitter/nvim-treesitter', {'do': ':TSUpdate'}` to the init.vim plugins list
2) Type `:PlugInstall` in nvim for install the plugin
3) Type `:TSInstall c` in nvim for install C language support
4) Add configuration from [nvim-treesitter](https://github.com/nvim-treesitter/nvim-treesitter) in the init.vim

## Color theme
List with some Neovim themes which I like
- [Tokyo Night theme](https://github.com/folke/tokyonight.nvim)
- [GitHub theme](https://github.com/projekt0n/github-nvim-theme)

## Usage

### JSON compilation database generation
clangd relies on compile_commands.json JSON compilation database. 
It can be exported with CMake with flag `-DCMAKE_EXPORT_COMPILE_COMMANDS` or can be created with [Bear](https://github.com/rizsotto/Bear) utility.
