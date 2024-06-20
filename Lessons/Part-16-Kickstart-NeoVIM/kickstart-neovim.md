# Kickstart NeoVim
 

## Step-by-Step Guide to Kickstart Neovim

#### 1. **Prerequisites**
   - **Neovim Installation**: Ensure you have Neovim installed. You can download it from [neovim.io](https://neovim.io/).
   - **Git**: Make sure Git is installed to clone repositories.

#### 2. **Setup `kickstart.nvim`**
   - **Clone the Repository**:
     ```sh
     git clone https://github.com/nvim-lua/kickstart.nvim.git ~/.config/nvim
     ```
   - **Initialize Neovim**: Open Neovim to start the configuration setup.
     ```sh
     nvim
     ```

#### 3. **Modularizing Configuration**
   - **Directory Structure**:
     - Create a directory structure under `~/.config/nvim/lua/` to organize your configurations. 
     - Example:
       ```
       ~/.config/nvim/lua/
       ├── plugins.lua
       ├── lsp-config.lua
       ├── treesitter.lua
       ├── mappings.lua
       └── init.lua
       ```
   - **Splitting `init.lua`**:
     - Move specific configurations from `init.lua` to separate files in the `lua` directory.
     - Load these files in `init.lua` using `require`.
     ```lua
     require('plugins')
     require('lsp-config')
     require('treesitter')
     require('mappings')
     ```

#### 4. **Managing Plugins**
   - **Install Plugin Manager**:
     - Use `Lazy.nvim` for plugin management. Add the following to your `plugins.lua`:
     ```lua
     local lazypath = vim.fn.stdpath("data") .. "/lazy/lazy.nvim"
     if not vim.loop.fs_stat(lazypath) then
       vim.fn.system({
         "git",
         "clone",
         "--filter=blob:none",
         "https://github.com/folke/lazy.nvim.git",
         "--branch=stable",
         lazypath,
       })
     end
     vim.opt.rtp:prepend(lazypath)

     require("lazy").setup({
       -- List your plugins here
     })
     ```
   - **Add Plugins**:
     - Example plugins:
     ```lua
     require("lazy").setup({
       'nvim-treesitter/nvim-treesitter',
       'neovim/nvim-lspconfig',
       'hrsh7th/nvim-cmp',
       -- add more plugins as needed
     })
     ```

#### 5. **Configuring LSP (Language Server Protocol)**
   - **Install `mason.nvim` for LSP management**:
     ```lua
     require("mason").setup()
     require("mason-lspconfig").setup({
       ensure_installed = { "lua-language-server", "pyright", "tsserver" }
     })
     ```
   - **LSP Configuration**:
     ```lua
     local lspconfig = require('lspconfig')
     lspconfig.pyright.setup({})
     lspconfig.tsserver.setup({})
     -- Add more LSP configurations as needed
     ```

#### 6. **Tree-sitter Setup**
   - **Install and Configure Tree-sitter**:
     ```lua
     require'nvim-treesitter.configs'.setup {
       ensure_installed = { "lua", "python", "javascript" },
       highlight = { enable = true },
     }
     ```

#### 7. **Key Mappings**
   - **Configure Key Mappings**:
     - Use `which-key.nvim` for better key mapping hints.
     ```lua
     require("which-key").setup({})
     vim.api.nvim_set_keymap('n', '<leader>ff', ':Telescope find_files<CR>', { noremap = true })
     vim.api.nvim_set_keymap('n', '<leader>fg', ':Telescope live_grep<CR>', { noremap = true })
     -- Add more mappings as needed
     ```

#### 8. **Additional Configurations**
   - **Setup Autocommands**:
     ```lua
     vim.api.nvim_exec([[
       augroup MyAutoCmd
         autocmd!
         autocmd BufWritePost *.lua source <afile> | PackerCompile
       augroup END
     ]], false)
     ```
   - **Configure Status Line**:
     - Use `lualine.nvim` for a better status line.
     ```lua
     require('lualine').setup {
       options = {
         theme = 'gruvbox'
       }
     }
     ```

### Final Thoughts
This modular approach allows for better organization, easier debugging, and scalable configurations. By following these steps, you can efficiently kickstart your Neovim setup using `kickstart.nvim` and customize it to fit your workflow perfectly.

