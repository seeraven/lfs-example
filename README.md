# lfs-example

An example repository containing files stored with the git-lfs extension
as a test for https://github.com/seeraven/gitcache.


## Commands used to Create this Repository

    git clone https://github.com/seeraven/lfs-example.git
    cd lfs-example
    git lfs install
    git lfs track "*.png"
    git config -f .lfsconfig lfs.fetchinclude "included/**"
    git config -f .lfsconfig lfs.fetchexclude "excluded/**"
    mkdir included excluded
    convert -background lightblue -fill blue -pointsize 72 label:Included included/second.png
    convert -background lightblue -fill red -pointsize 72 label:Included included/second.png
    convert -background lightblue -fill blue -pointsize 72 label:Excluded excluded/first.png
    convert -background lightblue -fill red -pointsize 72 label:Excluded excluded/second.png


## Result

    $ rm -rf lfs-example
    $ git clone https://github.com/seeraven/lfs-example.git
    $ file included/*
    included/first.png:  PNG image data, 271 x 70, 16-bit/color RGB, non-interlaced
    included/second.png: PNG image data, 271 x 70, 16-bit/color RGB, non-interlaced
    $ file excluded/*
    excluded/first.png:  ASCII text
    excluded/second.png: ASCII text
    $ git lfs pull --include "excluded/*" --exclude ""
    $ file excluded/*
    excluded/first.png:  PNG image data, 293 x 70, 16-bit/color RGB, non-interlaced
    excluded/second.png: PNG image data, 293 x 70, 16-bit/color RGB, non-interlaced
    $
