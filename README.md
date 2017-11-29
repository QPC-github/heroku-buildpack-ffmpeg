Heroku buildpack: FFMpeg
=======================

This is a [Heroku buildpack](http://devcenter.heroku.com/articles/buildpacks) for using [ffmpeg, ffprobe, ffserver, ffmpeg-10bit and qt-faststart ](http://www.ffmpeg.org/) in your project, It will install all components of FFMPEG extension which we install in our local computer.  
It doesn't do anything else, so to actually compile your app you should use [heroku-buildpack-multi](https://github.com/ddollar/heroku-buildpack-multi) to combine it with a real buildpack.


Usage
-----

    # Ruby buildpack
    $ cat .buildpacks
    https://github.com/laddhadhiraj/heroku-buildpack-ffmpeg
    https://github.com/heroku/heroku-buildpack-ruby

    # for new project
    $ heroku create --buildpack https://github.com/ddollar/heroku-buildpack-multi

    # for existing project
    $ heroku buildpacks:set https://github.com/ddollar/heroku-buildpack-multi

    $ heroku config:set FFMPEG_BIN_URL="http://johnvansickle.com/ffmpeg/releases/ffmpeg-release-64bit-static.tar.xz"

    $ git push heroku master

    # verify and profit!
    $ heroku run "ffmpeg -version"
    $ heroku run "ffprobe -version"
    $ heroku run "ffserver -version"
    $ heroku run "ffmpeg-10bit -version"
    $ heroku run "qt-faststart -version"
