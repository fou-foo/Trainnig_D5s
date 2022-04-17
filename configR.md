update.packages(ask = FALSE, checkBuilt = TRUE)
#write('PATH="${RTOOLS40_HOME}\\usr\\bin;${PATH}"', file = "~/.Renviron", append = TRUE)
tinytex::tlmgr_update()
tinytex::reinstall_tinytex()
options(tinytex.verbose = TRUE)

https://yihui.org/tinytex/r/#debugging
https://cran.rstudio.com/bin/windows/Rtools/rtools40.html