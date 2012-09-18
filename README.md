Core Data Buildpack
===================

> This is still in early stages of development, so proceed with caution when using this in a production application.
Any bug reports, feature requests, or general feedback at this point would be greatly appreciated.

This is an example [Heroku buildpack](http://devcenter.heroku.com/articles/buildpacks).

Usage
-----

    $ ls
    Example.xcdatamodel

    $ heroku create --stack cedar --buildpack http://github.com/mattt/heroku-buildpack-core-data.git

    $ git push heroku master
    ...
    -----> Heroku receiving push
    -----> Fetching custom buildpack
    -----> Core Data detected

---

## Contact

Mattt Thompson

- http://github.com/mattt
- http://twitter.com/mattt
- mattt@heroku.com

## License

Core Data Buildpack is available under the MIT license. See the LICENSE file for more info.
