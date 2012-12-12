Core Data Buildpack
===================

This is a [Heroku buildpack](http://devcenter.heroku.com/articles/buildpacks) for generating a REST web service from a Core Data model. It uses [rack-core-data](https://github.com/mattt/rack-core-data). 

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

This buildpack will detect your app if it includes a Core Data model (`.xcdatamodel`) file. Using [rack-core-data](https://github.com/mattt/rack-core-data), a REST web service that communicates with a [Heroku Postgres](https://postgres.heroku.com) dev database is generated according to the attributes and relationships of each entity in the data model:

<table>
  <thead><tr>
    <th>Core Data Model</th>
    <th>API Endpoints</th>
  </tr></thead>
  <tbody><tr>
    <td><img src="http://heroku-mattt.s3.amazonaws.com/core-data-diagram.png"/></td>
    <td><ul>
      <li><tt>GET /artists</tt></li>
      <li><tt>POST /artists</tt></li>
      <li><tt>GET /artists/1</tt></li>
      <li><tt>PUT /artists/1</tt></li>
      <li><tt>DELETE /artists/1</tt></li>
      <li><tt>GET /artists/1/songs</tt></li> 
    </ul></td>
  </tr></tbody>
</table>

Limitations
-----------

**The Core Data Buildpack is designed to encourage rapid prototyping, but should not be used on its own in production applications.**

Rather, you are encouraged to create an application using [Rack::CoreData](https://github.com/mattt/rack-core-data) directly, which allows you to extend the Core Data scaffolding with [Rack](http://rack.github.com) applications, such as [Rails](http://rubyonrails.org) or [Sinatra](http://www.sinatrarb.com), and middleware. Here's an example `config.ru` file: 

### config.ru

```ruby
require 'bundler'
Bundler.require

DB = Sequel.connect(ENV['DATABASE_URL'])

run Rack::CoreData('./Example.xcdatamodeld')
```

---

## Contact

Mattt Thompson

- http://github.com/mattt
- http://twitter.com/mattt
- mattt@heroku.com

## License

Core Data Buildpack is available under the MIT license. See the LICENSE file for more info.
