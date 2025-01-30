# Color schemes


## Install

Vim color schemes are stored in *.vim* files, e.g. *mariana.vim*.
To manually install a color theme, get the file from a git repository 
(typically in the *colors/* directory) 
and copy it to the folder *~/.vim/colors/*


## Available colorschemes

To view current colorscheme:
```vim
:colorscheme
```

In order to cycle through all available colorschemes,
add a space to the command above and press "tab"
(multiple times to cycle)

## Set color scheme

```vim
:colorscheme solarized
:set background=dark    # optional, for colorschemes with light/dark options
```
(to make it permanent, put these commands in the *.vimrc* file)

## Examples

Interesting color themes:
- [Iceberg](https://github.com/cocopon/iceberg.vim) 
- [Solarized] (https://github.com/altercation/vim-colors-solarized)
    (if colors appear weird, see *Troubleshooting* below)
- [Awesome vim color schemes](https://github.com/rafi/awesome-vim-colorschemes)
- [Ocean Next](https://github.com/mhartington/oceanic-next)
- [Nord](https://github.com/nordtheme/vim)

## Troubleshooting

If the colors render weirdly, it can be due to problems with the terminal color palette
(some themes are designed for GUI vim and not terminal vim, see e.g. list here:
https://github.com/rafi/awesome-vim-colorschemes)

Try reducing the color palette with
```vim
:set termguicolors
```
or try cancelling the previous setting using
```vim
:set notermguicolors
```


## Documentation

See e.g.
https://www.linode.com/docs/guides/vim-color-schemes/
