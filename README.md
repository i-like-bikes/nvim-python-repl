# nvim-python-repl 

[![asciicast](https://asciinema.org/a/460861.svg)](https://asciinema.org/a/460861)

A simple plugin leveraging treesitter to send expressions, statements, function
definitions and class definitions to an ipython REPL. Also supports sending selection
from visual mode. 

### Usage 

Can be installed with any plugin manager. For example, in packer you can use 

```
use "geg2102/nvim-python-repl"
```

Somewhere in your init.lua/init.vim you should place 

```
require("nvim-python-repl").setup()
```

### Keymaps

In normal mode, default keymapping for sending a treesitter object is set to
`<leader>n`. The command will send the smallest semantic unit at the cursor. If the
cursor is somewhere within an expression, the expression will be sent, even if the
expression is within a function. If the cursor is on the function definition, the entire
function will be sent. If it is on a class definition, the entire class will be sent. 

In visual mode, `<leader>n` sends visual selection to repl. 

Default keymapping for sending the entire buffer is `<leader>nr`. 

```
vim.api.nvim_set_keymap('n', [your keymap], ":SendPyObject<CR>", {noremap=true, silent=true})
``` 

```
vim.api.nvim_set_keymap('v', [your keymap], ":<C-U>SendPySelection<CR>", {noremap=true, silent=true})
```

```
vim.api.nvim_set_keymap('n', [your keymap], ":SendPyBuffer<CR>", {noremap=true, silent=true})
```

### Options
The only option for now is whether to execute the given expression on send. By default
this is set to true, but this can be toggled with `<leader>e` or `:ToggleExecuteOnSend`. You can also change  the
default behavior with 


```
require("nvim-python-repl").setup({execute_on_send=false})
```
