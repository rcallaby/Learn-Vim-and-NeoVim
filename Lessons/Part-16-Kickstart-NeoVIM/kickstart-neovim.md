# Kickstart NeoVim

To set up Neovim with the kickstart.nvim configuration on your system, follow these steps:

1. **Install Neovim**:
   - **Download**: Visit the [Neovim releases page](https://github.com/neovim/neovim/releases) and download the latest stable version compatible with your operating system.
   - **Install**:
     - **Windows**: Extract the downloaded zip file and add the `bin` directory to your system's `PATH`.
     - **macOS**: Use Homebrew with the command `brew install neovim`.
     - **Linux**: Follow the installation instructions specific to your distribution, as detailed in the [Neovim installation guide](https://github.com/neovim/neovim/wiki/Installing-Neovim).

2. **Set Up kickstart.nvim**:
   - **Clone the Repository**:
     - Open your terminal and execute:
       ```bash
       git clone https://github.com/nvim-lua/kickstart.nvim.git ~/.config/nvim
       ```
       This command clones the kickstart.nvim repository into your Neovim configuration directory.
   - **Launch Neovim**:
     - Start Neovim by typing `nvim` in your terminal.
     - Upon the first launch, kickstart.nvim will automatically set up the included plugins and configurations.

3. **Install a Terminal Emulator (Optional)**:
   - For an enhanced experience, consider using a feature-rich terminal emulator like [WezTerm](https://wezfurlong.org/wezterm/).
   - **Installation**:
     - **macOS**: Follow the [WezTerm installation guide for macOS](https://wezfurlong.org/wezterm/install/macos.html).
     - **Windows** and **Linux**: Refer to the [official installation instructions](https://wezfurlong.org/wezterm/).

4. **Configure Shell Integration (Optional)**:
   - To open Neovim using commands like `vi` or `vim`, set up shell aliases:
     - **macOS/Linux**:
       - Add the following lines to your shell configuration file (e.g., `~/.bashrc` or `~/.zshrc`):
         ```bash
         alias vi="nvim"
         alias vim="nvim"
         ```
       - Reload your shell configuration:
         ```bash
         source ~/.bashrc  # or ~/.zshrc
         ```
     - **Windows**: Use the `doskey` command or configure your terminal emulator to recognize `nvim` as the default editor.

5. **Explore Neovim Features**:
   - **File Browsing**:
     - Press `<Space> s` to open the file search interface provided by the Telescope plugin.
   - **Navigating Splits and Tabs**:
     - Move between split windows using `Ctrl + w` followed by `h` (left) or `l` (right).
     - Switch between tabs with `gt` (next tab) and `gT` (previous tab).
   - **Commenting Multiple Lines**:
     - Enter Visual Block mode with `Ctrl + v`, select the desired lines, press `Shift + i` to enter Insert mode, type the comment character(s), and press `Esc` to apply the comments.
