# Editors & IDEs

<!-- INDEX_START -->

- [Editors](#editors)
  - [ViM](#vim)
  - [Neovim](#neovim)
  - [GNU Emacs](#gnu-emacs)
  - [Nano](#nano)
- [IDEs](#ides)
  - [IntelliJ IDEA](#intellij-idea)
  - [PyCharm](#pycharm)
  - [RubyMine](#rubymine)
  - [VS Code](#vs-code)
  - [Eclipse](#eclipse)
- [Editor Config](#editor-config)
- [Misc Eclipse IDE Notes](#misc-eclipse-ide-notes)
  - [Eclipse Plugins](#eclipse-plugins)

<!-- INDEX_END -->

## Editors

### ViM

Vi iMproved.

- `vi` was the core editor available on every unix system
- `vim` means `vi` improved
- highly configurable but steep learning curve
- basic knowledge of `vi` is a core skill for all unix / linux server administrators
- tonnes of plugins, highly extensible and widely used
- see my advanced [.vimrc](https://github.com/nholuongut/devops-bash-tools/blob/master/configs/.vimrc) for all
  sorts of trips & tricks, hotkey linting and building, plugins etc.

See [vim.md](vim.md) for more details.

### Neovim

<https://github.com/neovim/neovim>

Fork of vim above.

- more actively developed
- asynchronous plugins
- extensible in Lua instead of vimscript
- config can be in lua and vimscript
- better external UI support
- built-in terminal

### GNU Emacs

- advanced highly customizable programming editor written by unix veteran by Richard Stallman in 1976
- steep learning curve like vim
- git integration via Magit
- can run shell commands and interact with system processes directly from Emac
- modes for different programming languages and tasks:
  - major modes provide features specific to a language or type of file (e.g., Python mode, HTML mode)
  - minor modes add additional functionalities, such as enabling version control, spell-checking, or syntax highlighting
- integration with external tools: Emacs supports a wide array of external tools, such as Git (via Magit), debuggers, shells, email clients, and more. You can run shell commands and interact with system processes directly from Emacs
- people used to joke that Emacs stood for *"Eight Megabytes and Constantly Swapping"* thinking it was resource hungry
  - contrast to today with [IntelliJ](intellij.md) sucking up 8GB of RAM!
- extensible via Emacs Lisp (Elisp)

### Nano

<https://www.nano-editor.org/>

Simple lightweight text editor for beginners.

Easier to use than vim or emacs.

Developed as an alternative to the pico text editor which was not entirely open source.

## IDEs

### IntelliJ IDEA

<https://www.jetbrains.com/idea/>

State of the art modern popular IDE - proprietary but has a free version.

- fast & slick
- feature rich
- highly extensible with tonnes of plugins
  - (see [IntelliJ](intellij.md) page for many good ones)
- built-in terminal
- resource intensive - just buy a more powerful machine like my M3 Max, it's worth it

The best of the best in my opinion.

See the [IntelliJ IDEA](intellij.md) page for more.

### PyCharm

<https://www.jetbrains.com/pycharm/>

Python-focused version of the grand daddy IntelliJ IDEA.

### RubyMine

<https://www.jetbrains.com/ruby/>

Ruby-focused version of the grand daddy IntelliJ IDEA.

Unfortuntely, this is proprietary paid for only and doesn't have a free version like [PyCharm](#pycharm).

### VS Code

<https://code.visualstudio.com/>

Microsoft's Visual Studio Code is a free modern popular open-source IDE with plugins.

- IntelliSense - code completion
- remote development extensions enable developers to work seamlessly on remote machines or containers, enhancing the
  flexibility for those who work in cloud-based or server environments
- built-in terminal
- not quite as feature rich as Visual Studio

Not as good as IntelliJ in my opinion.

See the [VS Code](vs-code.md) page for more details.

### Eclipse

<https://www.eclipse.org/>

Old open source IDE.

Most people prefer IntelliJ as it's much faster and slicker.

## Editor Config

- `.editorconfig` - standard config file that many editors will read, including [GitHub](github.md) for displaying the `README.
  md` in the repo home page
  - see my [.editorconfig](https://github.com/nholuongut/devops-bash-tools/blob/master/configs/.editorconfig)

## Misc Eclipse IDE Notes

I haven't used eclipse enough to warrant its own page, so here are some minor bits.

`F3` on a class to go it it's definition

Next / Previous Tab - `Fn`-`Ctrl`-`Left` / `Fn`-`Ctrl`-`Right`

| Shortcut                                                     | Description                                      |
|--------------------------------------------------------------|--------------------------------------------------|
| `sysout` -> `Ctrl`-`Space`                                   | Fills in the common `System.out.println` in Java |
| Right-click -> `Source` -> `Generate Getters & Setters`      |                                                  |
| default package -> Right-click -> `Export` -> `Java` -> `JAR file` |                                                  |

Eclipse -> Preferences (Mac):

- Window
  - Preferences
    - Maven
      - untick - `Do not automatically update dependencies from remote repositories`
      - tick   - `Download repository index updates on startup`

Eclipse JSONTools validation plugin (Help -> MarketPlace), but needs files to be .json (not .template from CloudFormation)

IntelliJ also has JSON error validation, but it's not as good as it's hard to see underscores not the big red cross eclipse puts in the left column.

### Eclipse Plugins

- CheckStyle
- Cucumber
- PMD
- Findbugs
- CodeTemplates
- Mylyn

**Ported from various private Knowledge Base pages 2013+**
