# R for Data Science

This is code and text behind the [R for Data Science](http://r4ds.had.co.nz)
book. 

The site is built using [bookdown package](https://github.com/rstudio/bookdown).
To create the site, you also need:

* [pandoc](http://johnmacfarlane.net/pandoc/)

The R packages used in this book can be installed via

```{r}
install.packages("packrat")
packrat::on()
```

# Compiling to a Kindle eBook

## Requirements

This book contains HTML widgets, so you'll need to install webshot and PhantomJS
to convert those to still images. See https://bookdown.org/yihui/bookdown/html-widgets.html

```{r}
install.packages("webshot")
webshot::install_phantomjs()
```

Take note of where webshot installed phantomjs to, and make sure that the `phantomjs`
binary winds up on your `$PATH`! You should be able to do this from within R and see
the installed phantomjs version:

```{r}
> system("phantomjs --version")
2.1.1
```

## Compiling

```{r}
bookdown::render_book("index.rmd", output_format="bookdown::epub_book")
# And then either:
bookdown::kindlgen(...)
# ... or ...
bookdown::calibre(...)
```
