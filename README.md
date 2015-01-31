
## What is SILE?

SILE is a typesetting system. Its job is to produce beautiful printed documents. It’s similar to TeX, but with some ideas borrowed from InDesign, and written with modern technologies in mind.

## What can I do with it (that I can’t do with TeX)?

First, have a look at the [show-off file][showoff]

SILE allows you to

* Produce complex document layouts using frames.

* Easily extend the typesetting system in a high-level programming language. (Lua)

* Directly process XML to PDF without the use of XSL stylesheets.

* Typeset text on a grid.

## Getting and installing sile in Ubuntu 14.04 LTS 64-bit

Copy-paste each command one by one into the Terminal:

cd

sudo rm -rf sile

sudo apt-get purge sile

sudo apt-get update

sudo apt-get purge lua5.2 

sudo apt-get install build-essential fontconfig libfreetype6 pango-graphite

sudo apt-get install gcc g++ libfreetype6-dev libglib2.0-dev libcairo2-dev

sudo apt-get install autoconf automake libtool pkg-config ragel gtk-doc-tools

sudo apt-get install checkinstall liblualib50-dev liblua5.1-0-dev

sudo apt-get install gobject-introspection

sudo apt-get install libgirepository1.0-dev 

sudo apt-get install lua5.1 luarocks unp libharfbuzz-bin gir1.2-harfbuzz-0.0

sudo apt-get install lua-lgi lua-lpeg libtext-bidi-perl libtext-lorem-perl

sudo luarocks install stdlib

sudo luarocks install lpeg

sudo luarocks install luaexpat

sudo luarocks install lgi

sudo luarocks install inspect

sudo luarocks install luaepnf

sudo luarocks install luarepl

sudo luarocks install cassowary

git clone https://github.com/behdad/harfbuzz

cd harfbuzz/

sudo ./autogen.sh

sudo make

sudo checkinstall

* type 3 and hit <ENTER> to modify version number

* enter 0.9 as version number and hit <ENTER>

apt-cache show harfbuzz

* output of apt-cache show harfbuzz should be something like this:

*Package: harfbuzz

*Status: install ok installed

*Priority: extra

*Section: checkinstall

*Installed-Size: 936

*Maintainer: root@root

*Architecture: amd64

*Version: 0.9-1

*Provides: harfbuzz

*Description: Package created with checkinstall 1.6.2

*Description-md5: 556b8d22567101c7733f37ce6557412e


cd

git clone https://github.com/simoncozens/sile.git

cd sile

sudo sh bootstrap.sh

sudo ./configure

sudo make

sudo checkinstall

* type 3 and hit <ENTER> to modify version number

* enter 0.91 as version number and hit <ENTER>

apt-cache show sile

* output of apt-cache show sile should be something like this:

*Package: sile

*Status: install ok installed

*Priority: extra

*Section: checkinstall

*Installed-Size: 9220

*Maintainer: root@root

*Architecture: amd64

*Version: 0.91-1

*Provides: sile

*Description: Package created with checkinstall 1.6.2

*Description-md5: 556b8d22567101c7733f37ce6557412e

* PDF manual:  https://raw.githubusercontent.com/simoncozens/sile/master/documentation/sile.pdf

sile examples/rotate.sil




## Getting and installing

SILE can be downloaded from [its home page][1], or directly from [the release page][2].

SILE is written in the Lua programming language, so you will need a Lua version 5.1 installation. It also relies on external libraries to access fonts and write PDF files. Its preferred combination of libraries is [harfbuzz][] and a PDF creation library extracted from TeX. It should be possible to harfbuzz from your operating system's package manager. (For Harfbuzz to work you will also need freetype2 and fontconfig installed.) If this is not possible, SILE will attempt to use the GNOME Pango/Cairo libraries. 

You also need to install the following Lua libraries using [luarocks][] (downloading luarocks if you do not already have it installed).

* `lpeg` 
* `luaexpat`
* `lgi` (required for Pango-Cairo only)

Once your dependencies are installed, run

* ./configure ; make install

(If you are running SILE from git, first run `bootstrap.sh` and then
configure and make. I don't guarantee that SILE will work from the
repository, although it probably ought to.)

This will place the SILE libraries and executable in a sensible location.

Now try `sile examples/test.sil`.

## Finding out more

Please read the [full SILE manual][3] for more information about what SILE is and how it can help you. There are example documents (source and PDF) in the examples/ directory. There's also an [FAQ][faq] available.

## Contact

Please report bugs and send patches and pull requests at the [github repository][4]. For questions, please contact the author, Simon Cozens <simon@simon-cozens.org>.

## License terms

SILE is distributed under the [MIT licence][5].

[1]: http://www.sile-typesetter.org/ 
[2]: https://github.com/simoncozens/sile/releases
[3]: https://raw.githubusercontent.com/simoncozens/sile/master/documentation/sile.pdf
[4]: https://github.com/simoncozens/sile
[5]: http://choosealicense.com/licenses/mit/
[faq]: https://github.com/simoncozens/sile/wiki/faq
[showoff]: https://raw.githubusercontent.com/simoncozens/sile/master/examples/showoff.pdf
[roadmap]: https://github.com/simoncozens/sile/blob/master/ROADMAP
[luarocks]: http://luarocks.org/en/Download
[harfbuzz]: http://www.freedesktop.org/wiki/Software/HarfBuzz/
