# vim_tmux_events

Fix vim-tmux-focus-events a question:

Although don't affect the use of vim, vim will report a error when the command line exists chars.

`FocusGained` and `FocusLost` autocommand events are not working in terminal vim. This plugin restores them when using vim inside Tmux.

Here's where that matters:

- [vim-fugitive](https://github.com/tpope/vim-fugitive) plugin uses
  `FocusGained` for refreshing git branch in status line
- [vim-gitgutter](https://github.com/airblade/vim-gitgutter) uses `FocusGained`
  for refreshing ... (wait for it) git gutter
- [vim-tmux-clipboard](https://github.com/roxma/vim-tmux-clipboard) uses
    `FocusGained` and `FocusLost` for refreshing clipboard.
- (get in touch if you know other popular plugins that get improved)
- [vim-tmux-focus-events](https://github.com/tmux-plugins/vim-tmux-focus-events)

Also`vim_tmux_events` makes the [autoread](http://vimdoc.sourceforge.net/htmldoc/options.html#'autoread') option work properly for terminal vim. So far, this was only working in a GUI version.

The `autoread` feature comes handy when files are changed outside vim, for example when resolving merge conflicts. When you come back to vim and try saving a changed file you'll likely be interrupted with [E813](http://vimdoc.sourceforge.net/htmldoc/editing.html#E813):

![vim E813](/vim_e813.png)

Improved `autoread` prevents this by automatically reading a file from disk if it was changed. Works only if `autoread` option is set (enable it with `set autoread` in `.vimrc`).

### Installation & Configuration

#### Vim plugin installation

```plain
```
* Vundle: `Plugin 'qeuroal/vim_tmux_events'`
* vim-plug: `Plug 'qeuroal/vim_tmux_events'`
* Pathogen: `git clone git://github.com/qeuroal/vim_tmux_events.git ~/.vim/bundle/vim_tmux_events`

#### Tmux configuration

In order for Tmux to do its magic `focus-events` option has to be set to `on`.

Enable that by installing [tmux-sensible](https://github.com/tmux-plugins/tmux-sensible) plugin, or by setting this line in `tmux.conf`:

```plain
set -g focus-events on
```

### Testing

Tested and working on:

- OS X
  - Terminal.app
  - iTerm2

- Linux
  - GNOME Terminal
  - Terminator
  - XTerm
  - Konsole
  - st

### Other goodies

- [vim-tmux](https://github.com/tmux-plugins/vim-tmux) - vim plugin for `tmux.conf`
- [tmux-resurrect](https://github.com/tmux-plugins/tmux-resurrect) - restore tmux environment after system restart

### Credits

- Big chunk of code was taken and adapted from [vitality.vim](https://github.com/sjl/vitality.vim).
- The repositories is a subbranch derived the [vim-tmux-focus-events](https://github.com/tmux-plugins/vim-tmux-focus-events).

### Other

In April 2013 [a patch was submitted](https://groups.google.com/forum/#!topic/vim_dev/ASn8QqQqVe0) to vim_dev mailing list that enables this functionality natively in vim.
Once merged, the functionality from the patch will make this plugin obsolete.
I hope that day comes soon.

### Licence

[MIT](LICENSE.md)
