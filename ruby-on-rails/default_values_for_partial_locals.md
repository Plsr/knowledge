# Default values for partial locals

First things first: I feel like setting default values for locals in partials
should not be happening in any production application. I think this kind of ligic does
not belong into the view, especially not in a partial.  
Nonetheless, there are situations where it is needed to set the value of a
local in the partial. This happened for example in a heavily mocked prototype
that was just used for internal demoing pruposes. Thinking about it now, I feel
like I could probably have found a better solution for this as well, without too
much effort. But nonetheless, should I ever again need to do this, I'll write it
down here.

The approach is rather simple: Every local passed to a partial can be accessed
via the `local_assigns` hash. So basicalli all we have to do is to check if the
key we want to set a default value is present and set the default value if it's
not the case.  
There are multiple approaches to this, but I liked the following the most for
its reability (even though it's kind of long):

```ruby
- default_value = "default_value" if local_assigns[:default_value].nil?
```
