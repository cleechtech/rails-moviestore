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

### Add movies to database
Add [movies.csv](https://raw.githubusercontent.com/Azzurrio/moviestore/master/db/seeds_data/movies.csv) to **db/seeds_data/movies.csv**.

Then in **db/seeds.rb**

```
require 'csv'
CSV.foreach(Rails.root.join("db/seeds_data/movies.csv"), headers: true) do |row|
  Movie.find_or_create_by(title: row[0], release_year: row[1], price: row[2], description: row[3], imdb_id: row[4], poster_url: row[5])
end
```
Run `$ rake db:seed`.

### Add routes

In **config/routes.rb** set up home route and resources for show and index.

```
Rails.application.routes.draw do
  resources :movies, only: [:show, :index]

  root 'movies#index'
end
```

Delete the html bits in **app/views/movies/index.html.erb** that reference editing, deleting or creating new movies.