# Views
Everything that is remotely connected to views in a Rails application.

## Table of Contents
* [Forms](#forms)
  * [Form Basics](#form-basics)
* [Partials](#partials)
    * [Default values for partial locals](#default-values-for-parial-locals)

## Forms

### Form basics

Generating basic forms be done with the `form_tag`, however, this will lead to a
lot of manual work that rails can handle. Should you be in a situation where
you cannot use the form builder and need to build a form by hand, railsgiudes
[has you
covered](http://guides.rubyonrails.org/form_helpers.html#dealing-with-basic-forms).  
The following will handle the creation of forms with the form builder.

Often times when working on a rails application and dealing with forms, chances
are you want to modify or create a resoucrce (in the 'new' and 'edit' view for
example). To make that easier, we can make use of the form builder, by using
`form_for` to generate our form.  
Let's assume we have an `Article` model that has fields for a title and content.
We can than pass an instance of that model to `form_for`, which will yield a
form builder object (passed to the block as `f` in the example below) which will
handle a lot of work for us.

```ruby
= form_for @article, url: {action: "create"} do |f|
  = f.text_field :title
  = f.text_field :content
  = f.submit "Create"
  ```

If we had defined artilces as a resouce in our routes, we could even use

```ruby
= form_for @article do |f|
  = f.text_field :title
  = f.text_field :content
  = f.submit "Create"
  ```

and rails will figure out if we are generating a new record or modifying an
exiting.

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
