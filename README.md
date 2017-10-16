# R for Data Science

This is code and text behind the [R for Data Science](http://r4ds.had.co.nz)
book. 

The R packages used in this book can be installed via

```{r}
devtools::install_github("hadley/r4ds")
```
The site is built using [bookdown package](https://github.com/rstudio/bookdown).
To create the site, you also need:

* [pandoc](http://johnmacfarlane.net/pandoc/)

# Compiling to a Kindle eBook

This book contains HTML widgets, so you'll need to install webshot and PhantomJS
to convert those to still images. See https://bookdown.org/yihui/bookdown/html-widgets.html

```{r}
install.packages("webshot")
webshot::install_phantomjs()
```
