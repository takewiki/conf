


# conf

> Persistent Package Configuration

[![Linux Build Status](https://travis-ci.org/gaborcsardi/conf.svg?branch=master)](https://travis-ci.org/gaborcsardi/conf)
[![Windows Build status](https://ci.appveyor.com/api/projects/status/github/gaborcsardi/conf?svg=true)](https://ci.appveyor.com/project/gaborcsardi/conf)
[![](http://www.r-pkg.org/badges/version/conf)](http://www.r-pkg.org/pkg/conf)
[![CRAN RStudio mirror downloads](http://cranlogs.r-pkg.org/badges/conf)](http://www.r-pkg.org/pkg/conf)

Store the configuration of your package in the user's platform dependent
config file directory. The configuration persists across R sessions, and can
also be edited manually. Configuration files are YAML files.

## Installation


```r
devtools::install_github("gaborcsardi/conf")
```

## Usage


```r
library(conf)
```

`conf` uses the `rappdirs` package (https://github.com/hadley/rappdirs) to
determine the appropriate location of the configuration file of a package.

To determine the location of the configuration file, you can use:

```r
conf$new(package = "mypackage")$get_path()
```

```
#> [1] "/Users/gaborcsardi/Library/Application Support/r-config/mypackage/config.yaml"
```

Create a configuration file by creating a `conf` object, then setting
some configuration keys in it, and writing it out to a file:

```r
cf <- conf$new(package = "mypackage", lock = TRUE)
```




```r
cf$set("user:id", "test-user")
cf$set("user:email", "test@acme.com")
cf$set("rversion", format(getRversion()))
```


```r
cf
```

```
#> user:
#>   id: test-user
#>   email: test@acme.com
#> rversion: 3.3.3
```


```r
cf$save()
```

## License

MIT © RStudio Inc
