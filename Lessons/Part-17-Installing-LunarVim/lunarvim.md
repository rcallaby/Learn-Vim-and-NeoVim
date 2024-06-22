# LunarVIM

### Step 1: Installation
1. **Pre-requisites**:
   - Install Neovim (>= 0.5.0).
   - Install a package manager like `apt`, `brew`, `yum`, etc.
   - Install `git`.

2. **Install LunarVim**:
   - Open your terminal.
   - Execute the following command:
     ```sh
     LV_BRANCH='release-1.3/neovim-0.7' bash <(curl -s https://raw.githubusercontent.com/LunarVim/LunarVim/master/utils/installer/install.sh)
     ```

### Step 2: Basic Usage
1. **Opening LunarVim**:
   - Launch LunarVim by typing `lvim` in your terminal.

2. **File Explorer**:
   - Use `Space + e` to open the file explorer.

3. **Fuzzy Finder**:
   - Use `Space + p + f` to open the fuzzy finder.

4. **Integrated Terminal**:
   - Open terminal with `Space + t + t`.

### Step 3: Configuration
1. **Open Config File**:
   - Use `:e ~/.config/lvim/config.lua` to edit the configuration file.

2. **Add Plugins**:
   - Add plugins in the `config.lua` file under the `lvim.plugins` section.
   - Example:
     ```lua
     lvim.plugins = {
       {"folke/tokyonight.nvim"},
       {"nvim-treesitter/nvim-treesitter", run = ":TSUpdate"}
     }
     ```

3. **Keybindings**:
   - Define custom keybindings in the `config.lua` file.
   - Example:
     ```lua
     lvim.keys.normal_mode["<C-s>"] = ":w<cr>"
     ```

### Step 4: Advanced Usage
1. **Language Servers (LSP)**:
   - Install and configure language servers for code intelligence.
   - Example for Python:
     ```lua
     require("lvim.lsp.manager").setup("pyright")
     ```

2. **Formatters and Linters**:
   - Configure formatters and linters.
   - Example for Python:
     ```lua
     local formatters = require "lvim.lsp.null-ls.formatters"
     formatters.setup {
       { command = "black", filetypes = { "python" } },
     }
     ```

3. **Autocommands**:
   - Add custom autocommands in the `config.lua` file.
   - Example:
     ```lua
     vim.api.nvim_create_autocmd("BufWritePre", {
       pattern = { "*.lua", "*.py" },
       command = "lua vim.lsp.buf.formatting_sync()"
     })
     ```

### Step 5: Additional Resources
1. **Documentation**:
   - Visit the [LunarVim Documentation](https://www.lunarvim.org/docs) for comprehensive details.

2. **Community Support**:
   - Join the [LunarVim Discord](https://discord.gg/lunarvim) for community help and support.

