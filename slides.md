## Ruby and Ruby on Rails
A quick overview

---

## Ruby

![RubyLogo](images/ruby-logo-R.png)
*[The Official Ruby Logo](https://www.ruby.or.jp/en/about/logo) by Ruby Association is used with permission*

note:
* Ruby's philosophy is to be pleasant to work with
* This means: concise, Principle of Least Astonishment, etc

--

## Ruby At A Glance

* Interpreted instead of complied
* Dynamic language
* Still Object Oriented, Garbage Collected

note:
* Interpreted - slower, but more flexibility
* No static type checking - can get up and running faster

--

## Show Me Some Code!

```ruby
# Say hi to everybody 
def say_hi( names )
  if names.nil?
    puts "..."
  elsif names.respond_to?("each")
    # @names is a list of some kind, iterate!
    names.each do |name|
      puts "Hello #{name}!"
    end
  else
    puts "Hello #{names}!"
  end
end

say_hi nil
say_hi "Brian"
say_hi ["Brian", "Matt" ]
```

note:
* Notes here

---

## Ruby on Rails

![RailsLogo](images/rails-logo.svg)
*[The Official Ruby Logo](https://rubyonrails.org) by David Heinemeier Hansson is used with permission*

note:
* Its an MVC-style Web Application framework that gives you everything to rapidly build a site
* Convention over configuration - quicker setup

--

## What's In The Box?

* Web Server (duh)
* Routing
* Pre-configured Database/ORM
* Web Pages written in ERuby (hmtl.erb) files
* Scaffolding for fast development

note:
* Puma webserver, but is customizable like everything
* Database is sqlite by default, also postgres, mysql

--

## Scaffolding/Generators

* Scafolding - build everything
```ruby
rails generate scaffold Post name:string title:string content:text
```
* Generator - more focused building
```ruby
rails generate controller Greetings hello
```

note:
* Creates Model, database migrations, unit test code, CRUD pages, controller 
* Similar to .net MVC scaffolding in Visual Studio
* Can use scaffolding to build a lot of stuff
* Generator is used for finer grained stuff. Can customize/create your own.
* This example creates a Greeting class with a hello method

--

## ORM/Data Access

ActiveRecord ORM

```ruby
class Product < ApplicationRecord
end
...
#Create
product = Product.create(name: 'Board Game', price: 49.99)
#Read/Query
products = Product.all
board_game = Product.find_by(name: 'Board Game')
products = Product.where("price > ?", 25)
#Delete
board_game.destroy
```

note:
* Convention Over Configuration - minimal work if you "play by the rules"
* Create Product model with `Products` backend table

--

## Database Migrations

* Auto created for you with generator/scaffolding
* Timestamped
* Rake (Ruby Make) runs the migrations via `rake db:migrate`

```ruby
class CreateBoardGames < ActiveRecord::Migration[5.0]
  def change
    create_table :board_games do |t|
      t.string :name
      t.decimal :price
 
      t.timestamps
    end
  end
end
```

note:
* Very similar to EntityFramework
* Rails Generator can be used to create migrations

--

## View/ERB Files

```erb
<% @board_games.each do |game| %>
    <tr>
    <td><%= game.name %></td>
    <td><%= game.price %></td>
    <td><%= link_to "Show", game %></td>
    <td><%= link_to "Edit", edit_game_path(game) %></td>
    <td><%= link_to "Destroy", game, method: :delete, data: { confirm: "Are you sure?" } %></td>
    </tr>
<% end %>
```

note:
* If you have route and controller defined, view auto-hooks up to Model
* Helper methods like `edit_game_path for finding the path

--

## Testing With Minitest

```ruby
require 'test_helper'
 
class ProductTest < ActiveSupport::TestCase
  test "product with name and price is valid" do
    product = Product.new(name: 'Product', price: 1.99)
    assert product.valid?
  end
  
  test "should not save product without name" do
    product = Product.new
    assert_not product.save, "Saved the product without a title"
  end
end
```

note:
* Rails comes with `Minitest` built in
* Rails includes helpers for testing controllers and views (not shown)

--

## Test Data Using Fixtures

```yml
banana:
  name: Banana 
  price: 10
pixel3:
  name: Pixel3
  price: 799
# Insert 100 products
<% 100.times do |n| %>
product_<%= n %>:
  username: <%= "product#{n}" %>
  price: <%= n %>
<% end %>
```

note:
* Test data is in Fixture files for each model type
* You can reference them by name in your tests
* YAML files are pre-processed with ERB so you can use ruby to generate data

---

## Live Demo