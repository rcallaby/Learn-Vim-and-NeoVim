# Tutorial: Integrating Version Control (Git) with Vim

## 1. Introduction

Version control systems like Git are crucial for managing code projects efficiently. Integrating Git with Vim can streamline your workflow, allowing you to perform version control operations without leaving your text editor.

## 2. Prerequisites

Before you start, make sure you have the following installed:

- Git (https://git-scm.com/)
- Vim or NeoVim (https://www.vim.org/)

## 3. Setting Up Git

If you haven't already installed Git, download and install it from the official website. Once installed, open a terminal and run:

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

Replace "Your Name" and "your.email@example.com" with your actual name and email.

## 4. Installing Vim-Plug (Plugin Manager)

We'll use Vim-Plug as the plugin manager. Open Vim and run the following commands:

```vim
curl -fLo ~/.vim/autoload/plug.vim --create-dirs \
    https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
```

For NeoVim:

```bash
mkdir -p ~/.config/nvim/autoload
curl -fLo ~/.config/nvim/autoload/plug.vim --create-dirs \
    https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
```

## 5. Installing Plugins for Git Integration

Open your `~/.vimrc` (for Vim) or `~/.config/nvim/init.vim` (for NeoVim) and add the following lines:

```vim
call plug#begin('~/.vim/plugged')

" Plugins for Git integration
Plug 'tpope/vim-fugitive'
Plug 'airblade/vim-gitgutter'

call plug#end()
```

Save the file and restart Vim. Run `:PlugInstall` to install the plugins.

## 6. Basic Git Operations in Vim

### 6.1. Vim Fugitive (Git Wrapper)

- **`:Git`**: Opens a Git command-line interface within Vim.
- **`:Git status`**: Shows the current status of the repository.
- **`:Git add %`**: Stages the current file for commit.
- **`:Git commit`**: Commits changes with a message.
- **`:Git push`**: Pushes changes to the remote repository.

### 6.2. Vim Gitgutter (Shows Git changes)

- **`:GitGutterToggle`**: Toggles GitGutter on/off.
- Use `]c` and `[c` to navigate between changes.

## 7. Advanced Git Operations in Vim

### 7.1. Merging with Vim Fugitive

- **`:Git merge branch_name`**: Merges `branch_name` into the current branch.
- **`:Gwrite`**: Saves changes.
- **`:Gcommit`**: Commits the merge.

### 7.2. Viewing Diffs

- **`:Gdiff`**: Opens a split diff view.
- Use `dp` and `do` to put/take changes.

### 7.3. Resolving Conflicts

- **`:Gstatus`**: Opens Git status window.
- Navigate to conflicted file, press `:diffget //3` to choose local changes or `:diffget //2` for remote changes.

## 8. Conclusion

You've now successfully integrated Git with Vim. This allows for seamless version control operations within your text editor. Experiment with these commands to master Git integration in Vim.
