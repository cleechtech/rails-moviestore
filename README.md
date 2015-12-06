ROR Shopping Cart
===

Following along the [Sitepoint tutorial](http://www.sitepoint.com/build-online-store-rails/)

```
$ rails new rails-moviestore --database=postgresql
$ cd rails-moviestore
$ rails g scaffold movie title release_year:integer price:float description:text imdb_id poster_url --skip-stylesheets
$ rake db:create
$ rake db:migrate
```
