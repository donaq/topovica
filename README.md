# Topovica

It's an acronym for "The Only Parts Of Vimperator I Care About". This project exists because as of version [57](https://www.mozilla.org/en-US/firefox/57.0/releasenotes/), the [Vimperator](http://vimperator.org/) extension will no longer work. Over the years, I have acquired significant muscle memory in browsing with Vimperator and, while there are other extensions that present similar interfaces, they are just different enough to be jarring. Instead of retraining, it's probably more fun to reimplement the subset of Vimperator that I am used to, so that's what I am going to do.

## Currently implemented

### Command mode

#### Page Movements

`h`,`j`,`k`,`l` &rarr; left, down, up and right, respectively 

`CTRL-D`, `CTRL-U` &rarr; 10x `j` and 10x `k`, respectively

`gg`, `G` &rarr; top of page, bottom of page

`ge`, `gE` &rarr; moves to the next and previous scrollable elements, respectively. (impacts `h`,`j`,`k`,`l`)

`/` &rarr; search page for text matches

#### Tab movements

`gt`, `gT`, `g^`, `g$` &rarr; next tab, previous tab, first tab, last tab, respectively

`:buffer`, `b` &rarr; brings up the buffer selector interface. typing will search buffers for matching indexes or titles, displaying them as hints. `Tab` or `Shift+Tab` cycles between hints. Pressing `Enter` jumps to the first match if no hint is selected, else to the selected hint

#### Tab creation/deletion

`d` &rarr; delete: close tab

`u` &rarr; undo: restore most recently deleted tab

#### Navigation

`:open`, `:o`, `o` &rarr; opens a url or does a search in the current tab. hints work the same way as `:buffer`

`:tabnew` &rarr; opens a url or does a search in a new tab. hints work the same way as `:buffer`

`CTRL-I`, `CTRL-O` &rarr; forward and back

`f`, `F` &rarr; displays indexes for links: typing in those indexes follows the link in the current tab or a new tab, respectively

`r`, `R` &rarr; hard and soft (use cache) refresh the page, respectively. yes, why shouldn't the default behaviour be hard refresh? =)

#### Misc

`y` &rarr; copies the current url to the clipboard

### Insert mode

We currently detect insert mode when currently focused element is `input`, `textarea` or `select`

## Credits

I referred to existing projects when I encountered functionality I couldn't figure out how to implement.

- `:open`: [vim-vixen](https://github.com/ueokande/vim-vixen)

## Known issues

1. `ge` and `gE` do not work with frames. Also somewhat wonky. The check for scrollable elements is not perfect.

2. `CTRL-O` sometimes lands you in the previous page with `:open` activated if you don't release the "O" button quickly enough.

3. `:open` and `:tabnew` occasionally cause an "undefined" hint to be displayed. This is irritating but doesn't really affect my usage, so I don't care. Feel free to suggest a patch if you can be arsed to find out why.

## License

[MIT](LICENSE)
