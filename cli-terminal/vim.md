# vim



fix tab sizing:

```
:set tabstop=4
```















































***

## Neovim

`Lazyvim` and `Nvim Kikstart` are a good way to begin your neovim journey.

### LazyVim

Official Documentation:

[https://www.lazyvim.org/installation](https://www.lazyvim.org/installation)

Using profiles lets you easily switch between using your own config and others like lazyvim:

```
git clone https://github.com/LazyVim/starter ~/.config/LazyVim
rm -rf ~/.config/LazyVim/.git
NVIM_APPNAME=LazyVim nvim
```

if you want to quickly open lazyvim from now on you can add this to your bashrc:

```
alias vl="NVIM_APPNAME=LazyVim nvim"
```

after reloading you bashrc from now on typing vl will launch lazy vim :smile:



## commands

:set foldlevel=3







## Combos

| Keyboard | Effect      |   |
| -------- | ----------- | - |
| za       | toggle fold |   |
|          |             |   |
|          |             |   |

* `zm` → fold **one more level** globally
* `zr` → open **one more level** globally
* `zM` → fold **everything**
* `zR` → open **everything**





































### Kickstart Nvim

Official Repo:

[https://github.com/nvim-lua/kickstart.nvim](https://github.com/nvim-lua/kickstart.nvim)

you just need the `init.lua` and copy it into `~/.config/nvim/init.lua`&#x20;

(you have to create the nvim folder if it doest exist.)











