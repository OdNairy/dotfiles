# dotfiles

    cd ~
    git clone git://github.com/r-plus/dotfiles.git
    ln -s dotfiles/.vimrc .vimrc
    ln -s dotfiles/.bashrc .bashrc
    ln -s dotfiles/.bash_profile .bash_profile
    ln -s ~/dotfiles/.ssh/config ~/.ssh/config
    mkdir -p ~/.vim/bundle
    mkdir -p ~/.vim/view
    mkdir -p ~/.vim/swap
    git clone git://github.com/Shougo/neobundle.vim.git ~/.vim/bundle/neobundle.vim

### mod remote (for author)

    cd ~/dotfiles
    git remote rm origin
    git remote add origin git@github.com:r-plus/dotfiles.git

### Add mail address for github identity
Add `git config --global user.email hogehoge@gmail.com` to `.bashrc`

### Vim-Plugins

* Install | :NeoBundleInstall
* Update | :NeoBundleUpdate
* Remove | :NeoBundleClean

### vimproc
`cd ~/.vim/bundle/vimproc/; make -f ~/.vim/bundle/vimproc/make_mac.mak`

### lynx setup for Lion

    /opt/local/etc/lynx.cfg (MacPorts)
    /usr/local/etc/lynx.cfg (homebrew)

Add this line.  `CHARACTER_SET:utf-8` 

### get vim-ref ref file.

    wget --no-check-certificate https://raw.github.com/gist/2762277/c8cf993bec75b819759fad524b7b6b4661d41209/alc.vim .vim/bundle/vim-ref/autoload/ref/alc.vim
    // or
    curl -o .vim/bundle/vim-ref/autoload/ref/alc.vim -k https://raw.github.com/gist/2762277/c8cf993bec75b819759fad524b7b6b4661d41209/alc.vim

-----
## for Windows KaoriYa-vim(used mingw and minsys)
### First, install mingw, minsys and git.
http://git-scm.com/    
http://sourceforge.net/projects/mingw/files/

if you using proxy, set below (bash)

    export HTTP_PROXY=http://PROXY_HOSTorIP:PORT
    export HTTPS_PROXY=http://PROXY_HOSTorIP:PORT
    // or
    git config --global http.proxy http://PROXY_HOSTorIP:PORT

proxy setting for cmd.exe

    proxycfg -u
    // or
    netsh winhttp import proxy source=ie

then clone neobundle and dotfiles. (Required `git` package for cygwin) If you see the certificate error, try `http` or `git` protocol.

    cd ; mkdir -p .vim/bundle; mkdir -p .vim/swap
    git clone https://github.com/Shougo/neobundle.vim.git .vim/bundle/neobundle.vim
    git clone https://github.com/r-plus/dotfiles.git

and https protocol to replace the git protocol in `.vimrc` (many company blocking git protocol)   
`$HOMEPATH/_vimrc` is for KaoriYa-vim/gvim, `~/.vimrc` for cygwin's one.

    ln -s dotfiles/.vimrc _vimrc
    ln -s dotfiles/_gvimrc _gvimrc

install plugins! (Please use correct vim that can be used `git(git.exe)`)

    :NeoBundleInstall

make the vimproc.dll (You should use `MinGW Shell`(not `Git Bash` or `cmd.exe`))

    cd .vim/bundle/vimproc; make -f make_mingw32.mak

### Lynx for Windows
[Lynx for Win32 - http://lynx-win32-pata.sourceforge.jp/index-ja.html](http://lynx-win32-pata.sourceforge.jp/index-ja.html)

### vimdiff for Windows
* Download diff `Binaries` and `Dependencies` from [DiffUtils for Windows](http://gnuwin32.sourceforge.net/packages/diffutils.htm)
* Put dlls and exes to vim directory.
