# R for Data Science

This is code and text behind the [R for Data Science](http://r4ds.had.co.nz)
book. 

The site is built using [bookdown package](https://github.com/rstudio/bookdown).
To create the site, you also need:

* [pandoc](http://johnmacfarlane.net/pandoc/)

# Compiling to a Kindle eBook

If you find this book useful, then consider supporting the author by buying the
official Kindle ebook (or a print copy of the book) rather than compiling it yourself:

http://a.co/27uQJ8E

That said, `bookdown` supports compilation to the `.mobi` format supported by Kindle,
via an intermediate conversion to `.epub`.

## Requirements

I've recorded the specific version numbers of all the package requirements via
packrat. So first, set that up:

```{r}
# Install packrat (if you haven't already)
install.packages("packrat")

# Activate packrat (will automatically download and install dependencies)
packrat::on()
```

### Calibre and/or KindleGen

To convert from `.epub` to `.mobi` you'll need either the open-source "Calibre" program,
or the free-as-in-beer Amazon "KindleGen" utility. See the Bookdown documentation for
details on obtaining these: https://bookdown.org/yihui/bookdown/e-books.html#mobi

On Ubuntu, Calibre is easily available as an apt package:

```
sudo apt install calibre
```

### Webshot & PhantomJS

This book contains HTML widgets, so you'll need to install the R "Webshot" package,
and the (non-R) PhantomJS program to convert those to still images.
See https://bookdown.org/yihui/bookdown/html-widgets.html

Webshot will have been installed via packrat. PhantomJS can be installed via
Webshot:

```{r}
webshot::install_phantomjs()
```

Take note of where webshot installed PhantomJS, and make sure that the `phantomjs`
command winds up on your `$PATH`! If it's set up correctly, you should be able to
execute `phantomjs` from withi R and see the installed version number:
the installed phantomjs version:

```{r}
> system("phantomjs --version")
2.1.1
```

If you see an error instead of the PhantomJS version number, you need to add the
`phantomjs` binary to your `$PATH`. Details vary depending on your operating system.

## Compiling

Bookdown can compile to the Kindle-compatible `.mobi` format by first generating
an `.epub` file, and then using either Calibre or KindleGen to convert it to `.mobi`.
It may be worth comparing the output from both programs to see which one does a
better conversion. KindleGen seems to be more likely to crash than Calibre.

```{r}
# First generate the .epub file:
bookdown::render_book("index.rmd", output_format="bookdown::epub_book")

# Then generate the .mobi file with one of these:

## Kindlegen: Generates a file called "_book/_main.mobi"
bookdown::kindlegen("_book/_main.epub")


## Calibre: The second parameter is the output filename.
bookdown::calibre("_book/_main.epub", "_book/fromcalibre.mobi")
```

## Getting it onto your Kindle

See https://www.amazon.com/gp/sendtokindle
