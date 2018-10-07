# Patterns

A list of patterns I learned that come around useful. Incomplete and wildy
unorganised.

## Returning early from controller actions
There are certain situations in which you might want to return early from a
controller actions, for example, if you want to make sure a user is allowed to
see a certain resource. If a user is not allowed to see said resource, you may
want to redirect them somewhere else. `redirect_to` does not stop the execution
of a function though, so this has to be done manually.  
The most basic way to do that is to use `and return`, however,
`validate_access_rights and return` does not read very well.

Robert Pankowecki introduces 4 possible ways to return early in [his
article](https://blog.arkency.com/2014/07/4-ways-to-early-return-from-a-rails-controller/),
the most elegant of which is the foruth: `extracted_method; return if
performed?`.

```ruby
class Controller
  def show
    verify_something; return if performed?
    @instance_var = Model.find(params[:id])
  end

  private

  def verify_something
    if not_valid?
      redirect_to some_path and return
    end
  end
```

__Further Reading__  
* [Rails redirect_to documentation](https://api.rubyonrails.org/classes/ActionController/Redirecting.html#method-i-redirect_to)
* [preformed? documentation](https://apidock.com/rails/ActionController/Metal/performed%3F)

## Memoization
The basic idea here is to cache results of methods to that these methods do not
have to be executed over and over again, yielding the same results.  
Basic memoization can look like this:

```ruby
class Article < ActiveRecord::Base
  def comments
    @comments ||= article.comments
  end
end
```
*Obviously, this example is very constructed and just used to display the
syntax*

__Further Reading__  
* [4 Simple Memoization Patterns in Ruby (And One Gem)](https://www.justinweiss.com/articles/4-simple-memoization-patterns-in-ruby-and-one-gem/)
