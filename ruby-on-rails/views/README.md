# Views
Everything that is remotely connected to views in a Rails application.

## Table of Contents
* [Partials](#partials)
    * [Default values for partial locals](#default-values-for-parial-locals)

## Partials

### Default values for partial locals

First things first: I feel like setting default values for locals in partials
should not be happening in any production application. I think this kind of logic does
not belong into the view, especially not in a partial.

Nonetheless, there are situations where it is ~~needed~~ more convenient to set the value of a
local inside the partial. This happened for example in a heavily mocked prototype
that was just used for internal demoing pruposes to me lately.  
Thinking about it now, I feel like I could probably have found a better solution for this as well, without too
much effort. But nonetheless, should I ever again need to do this, I'll write it
down here.

The approach is rather simple: Every local passed to a partial can be accessed
via the `local_assigns` hash. So basically all we have to do is to check if the
key we want to set a default value is present and set the default value if it's
not the case.  
There are multiple approaches to this, but I liked the following the most for
its reability (even though it's kind of long):

```ruby
- default_value = "default_value" if local_assigns[:default_value].nil?
```

#### Further reading
* There are a lot of different approaches in [this Stack Overflow Question](https://stackoverflow.com/questions/2060561/optional-local-variables-in-rails-partial-templates-how-do-i-get-out-of-the-de)
