# Heroku buildpack: geckodriver

This buildpack installs
[`geckodriver`](https://github.com/mozilla/geckodriver/)
 (the Selenium driver for Firefox) in a Heroku slug.
 
 This buildpack only installs the `geckodriver` binary. To use Selenium with Firefox
 on Heroku, you'll also need Firefox. This is the suggested buildpack:
 
 - [firefox-buildpack](https://github.com/buitron/firefox-buildpack) 

# Usage

Example usage:

```shell
$ heroku create [appname] --buildpack http://github.com/buitron/geckodriver-buildpack

# or if your app is already created:
$ heroku buildpacks:add http://github.com/buitron/geckodriver-buildpack

$ git push heroku master
```


## Configuring the downloaded version of geckodriver.

By default, this buildpack will download the latest release, which is provided
by [Mozilla](https://github.com/mozilla/geckodriver/releases/).

You can control the specific version by setting the `GECKODRIVER_VERSION`
variable to an explicit version e.g. `0.23.0`.

## Note

If you're using [heroku-buildpack-multi](https://devcenter.heroku.com/articles/using-multiple-buildpacks-for-an-app) to include other buildpacks, you should set environment variable by your own to include following paths.

    PATH="/usr/local/bin:/usr/bin:/bin:/app/.geckodriver/bin"
    LD_LIBRARY_PATH="/usr/local/lib:/usr/lib:/lib:/app/.geckodriver/bin"


<!-- ## Releasing a new version

Make sure you publish this buildpack in the buildpack registry

`heroku buildpacks:publish heroku/geckodriver master` -->
