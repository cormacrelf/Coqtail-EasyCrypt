# Coqtail

[![Code style: black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/ambv/black)
[![Build Status](https://travis-ci.com/whonore/Coqtail.svg?branch=master)](https://travis-ci.com/whonore/Coqtail)

## Interactive Coq Proofs in Vim

Coqtail enables interactive Coq proof development in Vim similar to
[CoqIDE](https://coq.inria.fr/refman/practical-tools/coqide.html)
or [ProofGeneral](https://proofgeneral.github.io/).

It supports:
- Coq 8.4 - 8.9
- Having multiple Coq buffers open
- Python 2 and 3

## Installation and Requirements

As a [vim package](https://vimhelp.org/repeat.txt.html#packages):

```sh
mkdir ~/.vim/pack/coq/start
git clone https://github.com/let-def/vimbufsync.git ~/.vim/pack/coq/start/vimbufsync
git clone https://github.com/whonore/coqtail.git ~/.vim/pack/coq/start/coqtail
vim +helptags\ .vim/pack/coq/start/coqtail/doc +q
```

Using
[pathogen](https://github.com/tpope/vim-pathogen):

```
cd ~/.vim/bundle && git clone https://github.com/whonore/coqtail.git
```

Using
[Vundle](https://github.com/VundleVim/Vundle.vim):

```
Plugin 'whonore/coqtail' (in .vimrc)
:PluginInstall
```

Using
[VimPlug](https://github.com/junegunn/vim-plug):

```
Plug 'whonore/coqtail' (in .vimrc)
:PlugInstall
```

Coqtail requires:
- Vim compiled with either `+python` or `+python3`
- [vimbufsync](https://github.com/let-def/vimbufsync)
- [Coq 8.4](https://coq.inria.fr/coq-84),
  [8.5](https://coq.inria.fr/coq-85),
  [8.6](https://coq.inria.fr/coq-86),
  [8.7](https://coq.inria.fr/coq-87),
  [8.8](https://github.com/coq/coq/releases/tag/V8.8.1), or
  [8.9](https://github.com/coq/coq/releases/tag/V8.9.0)

If you are using pathogen, documentation can be generated by
`:call pathogen#helptags()`. Alternatively, you can do `:helptags
{path-to-coqtail}/doc`.

## Usage

Coqtail provides the following commands (see `:help coqtail` for more details):

| Command | Mapping | Description |
|---|---|---|
| **Starting and Stopping** | |
| `CoqStart` | `<leader>cc` | Launch Coqtail for the current buffer. |
| `CoqStop` | `<leader>cq` | Quit Coqtail for the current buffer. |
| **Movement** | |
| `{n}CoqNext` | `<leader>cj` | Check the next `n` (1 by default) sentences with Coq. |
| `{n}CoqUndo` | `<leader>ck` | Step back `n` (1 by default) sentences. |
| `{n}CoqToLine` | `<leader>cl` | Check/rewind all sentences up to line `n` (cursor position by default). `n` can also be `$` to check the entire buffer.|
| `CoqToTop` | `<leader>cT` | Rewind to the beginning of the file. Similar to `1CoqToLine`, but `CoqToLine` only rewinds to the end of the line. |
| `CoqJumpToEnd` | `<leader>cG` | Move the cursor to the end of the checked region. |
| `CoqGotoDef[!] <arg>` | `<leader>cg` | Populate the quickfix list with possible locations of the definition of `<arg>` and try to jump to the first one. |
| **Queries** | |
| `Coq <args>` | | Send arbitrary queries to Coq (e.g. `Check`, `About`, `Print`, etc.). |
| `Coq Check <arg>` | `<leader>ch` | Show the type of `<arg>` (the mapping will use the term under the cursor). |
| `Coq About <arg>` | `<leader>ca` | Show information about `<arg>`. |
| `Coq Print <arg>` | `<leader>cp` | Show the definition of `<arg>`. |
| `Coq Locate <arg>` | `<leader>cf` | Show where `<arg>` is defined. |
| `Coq SearchAbout <args>` | `<leader>cs` | Show theorems about `<args>`. |

The mappings shown above are set by default, but you can disable them all and
define your own by setting `g:coqtail_nomap = 1` in your .vimrc.
Alternatively, you can choose to only remap specific commands and the defaults
will still be used for the rest.

Coqtail also comes with an ftdetect script for Coq, as well as modified
versions of Vincent Aravantinos'
[syntax](http://www.vim.org/scripts/script.php?script_id=2063) and
[index](http://www.vim.org/scripts/script.php?script_id=2079) scripts for Coq.
These scripts are used by default but can be disabled by setting
`g:coqtail_nosyntax = 1` and `g:coqtail_noindent = 1` respectively.

## Thanks

Parts of Coqtail were originally inspired by/adapted from
[Coquille](https://github.com/the-lambda-church/coquille)
(MIT License, Copyright (c) 2013, Thomas Refis).
