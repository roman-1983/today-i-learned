# How to clean up Homebrew

[Homebrew][1] is a package for macOS. You can use it to install packages via commandline.

## Take a look in the cellar
Via `brew list` you can see which packages are installed.

    $ brew list
        autojump        libevent            phpunit
        composer        libpng              pv
        coreutils       libxml2             readline
        freetype        libyaml             ruby
        gettext         nmap                ssh-copy-id
        git             node                tmux
        git-flow        openssl             tree
        gnu-sed         php56               unixodbc
        htop-osx        php56-mongo         vagrant-completion
        icu4c           php56-mongodb       wget
        jpeg            php70

## Update all packages
Simply run `brew update && brew upgrade`

## Remove old versions
Run `brew cleanup -s` to remove old versions and free up some space in the cellar.

    $ brew cleanup -s
    ==> This operation has freed approximately 1.2G of disk space.

[1]: https://brew.sh