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

## Ruby Slide 2

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
* Notes

--

## Ruby on Rails Slide 1

text

note:
* Notes