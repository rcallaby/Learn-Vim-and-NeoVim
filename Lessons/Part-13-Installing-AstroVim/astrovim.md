# Installing and Customizing AstroVIM

 `astro.vim` is a plugin for Neovim that aims to provide an out-of-the-box experience for those who want to get started with Neovim quickly. It comes with a curated set of plugins and configurations to enhance the Neovim experience. Here's a detailed tutorial on how to install, use, and customize `astro.vim`:

### Step 1: Install Neovim

If you haven't already, you'll need to install Neovim on your system. You can find the installation instructions on the official Neovim GitHub repository: [Neovim GitHub Repository](https://github.com/neovim/neovim).

### Step 2: Install `astro.vim`

To install `astro.vim`, you'll first need to make sure you have a plugin manager for Neovim. If you don't have one, I recommend using `vim-plug`, which is a popular choice. You can find the installation instructions for `vim-plug` here: [vim-plug GitHub Repository](https://github.com/junegunn/vim-plug).

Once you have `vim-plug` installed, you can add the following line to your Neovim configuration file (usually `~/.config/nvim/init.vim` or `~/.vimrc`):

```vim
Plug 'astronauts/astro.vim'
```

After adding the line, save the file and then run the following command in Neovim:

```vim
:PlugInstall
```

This will download and install `astro.vim` along with its dependencies.

### Step 3: Basic Usage

`astro.vim` is designed to work out-of-the-box, so you should be able to start using it right away. Here are some basic commands and features:

- `Ctrl-p` opens the file finder.
- `Ctrl-n` opens the file explorer.
- `Ctrl-t` opens a new tab.
- `Ctrl-w` followed by a direction key switches between splits.
- `Ctrl-q` closes the current buffer.

### Step 4: Customization

If you want to customize `astro.vim` to better suit your preferences, you can do so by editing your Neovim configuration file.

Here's an example of how you can customize `astro.vim`:

```vim
" Set the color scheme (replace 'onedark' with your preferred scheme)
colorscheme onedark

" Customize keybindings (replace these with your preferred bindings)
nnoremap <C-s> :w<CR>
nnoremap <C-q> :q<CR>
nnoremap <C-n> :new<CR>
nnoremap <C-t> :tabnew<CR>

" Set the leader key (replace '\' with your preferred key)
let mapleader = "\<Space>"

" Enable line numbers
set number

" Enable syntax highlighting
syntax enable

" Customize the status line (replace 'lightline' with your preferred plugin)
let g:lightline = {
      \ 'colorscheme': 'onedark',
      \ 'active': {
      \   'left': [ [ 'mode', 'paste' ],
      \             [ 'gitbranch', 'filename', 'filetype' ] ],
      \   'right': [ [ 'lineinfo' ],
      \              [ 'percent' ],
      \              [ 'fileformat', 'fileencoding', 'filetype' ] ]
      \ },
      \ 'component': {
      \   'lineinfo': '%3l:%-2v [%L/%P]'
      \ }
      \ }
```

### Step 5: Save and Restart Neovim

After customizing your Neovim configuration file, save the changes and restart Neovim for the customizations to take effect.

### Additional Notes

- Remember to replace placeholders like `'onedark'` with your preferred values.
- Feel free to explore more plugins and configurations to further enhance your Neovim experience.

That's it! You should now have `astro.vim` installed, configured, and customized according to your preferences. Happy coding!