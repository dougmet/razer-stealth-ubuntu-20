# Setting Up R

## Installing R

Ubuntu 20 brilliantly defaults to R 4.0 -- pretty recent! But it won't stay recent so best to add the R apt repo.

```sh
sudo vim /etc/apt/sources.list
```

add

```
# R CRAN
deb https://cloud.r-project.org/bin/linux/ubuntu focal-cran40/
```

And put the public key in for secure apt

```sh
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E298A3A825C0D65DFD57CBB651716619E084DAB9
```

But check instructions on the r-project website if you're not sure.

```sh
sudo apt update
suso apt install r-base-dev
```

## R Binary Pacakges

Doug: Look into this some time: https://launchpad.net/~c2d4u.team/+archive/ubuntu/c2d4u4.0+

## RStudio Package Manager

To use binary R packages and save yourself a bunch of time us the RStudio Package Manager instead of the normal R binaries. To do this add the following to the file: `/usr/lib/R/etc/Rprofile.site`

```
local({
    r <- getOption("repos")
    r["REPO_NAME"] <- "https://packagemanager.rstudio.com/all/__linux__/focal/latest"
    options(repos = r)

    options(HTTPUserAgent = sprintf("R/%s R (%s)", getRversion(), paste(getRversion(), R.version$platform, R.version$arch, R.version$os)))
})

```

Note the `focal` in there. That means Ubuntu 20.

## Common R Dependencies

