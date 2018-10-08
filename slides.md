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