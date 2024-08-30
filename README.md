# My Neovim Configuration

## Installation Steps
- Install neovim.
- Clone repository in ".config" dir.
- Open neovim. 

## MacOs
- brew install ripgrep

## Windows 🤮
- choco install rip-grep
- choco install make
- choco install mingw

- cd AppData\Local
- git clone this repo
- enter nvim
- cd %LOCALAPPDATA%\nvim-data\site\pack\packer\start\telescope-fzf-native.nvim
- make
```
AppData\Local\nvim\lua\my_config\plugins> cat .\nvim-tree.lua
local setup, nvimtree = pcall(require, "nvim-tree")
if not setup then
  return
end

-- recommended settings form nvim tree documentation
vim.g.loaded = 1
vim.g.loaded_netrwPlugin = 1


local function my_on_attach(bufnr)
  local api = require "nvim-tree.api"

  local function opts(desc)
    return { desc = "nvim-tree: " .. desc, buffer = bufnr, noremap = true, silent = true, nowait = true }
  end

  -- default mappings
  api.config.mappings.default_on_attach(bufnr)

  -- custom mappings
  vim.keymap.set('n', '<C-q>', api.node.open.vertical,        opts('Open: Vertical Split'))
end

nvimtree.setup({
  -- change folder arrow icons
  renderer = {
    icons = {
      glyphs = {
        folder = {
          arrow_closed = "->", -- arrow when folder is closed
          arrow_open = "L>", -- arrow when folder is open
        },
      },
    },
  },
  on_attach = my_on_attach,
})
```
