## Objectives

 1. Use the `collection` keyword with their partials
 2. Pass a collection to the render method 
 3. Handle empty collections

## Overview
Up until now our only way to render collections was somewhat manually.  We could iterate over an array and call the partial for each object in the array.  Let's see how rails can abstract this into a nicer syntax.

## Lesson

### Rendering Collections
Currently, our `posts#index` view is manually rendering the partial in a loop.
```erb
<% @posts.each do |post| %>
  <%= render :partial => "post", {:locals => {:post => post}} %>
<% end %>
```

Rails offers a great way to render a collection using a partial by passing the collection option to the render method.

```erb
<%= render :partial => "post", collection: @posts %>
```

Our code is tighter and both more abstract and more clear.
Another even more abstract method Rails gives us to do this is passing the array directly to the render method.

```erb
<%= render @posts %>
```

This is a bit more abstract.  Under the hood Rails uses the convention that you will have a partial with the name of the models in the collection.  Rails will even render a collection of heterogeneous models ([customer, order, customer]) calling the correct partial for each one.

### Empty Collections

What happens if the collection you pass to your render call is empty?  If you don't handle this exception the render method will return nil and nothing will appear on the screen.  A useful trick is to use the `||` operator to print something to the screen to alert the user to this.

```erb
<%= render @posts || "There are no blog posts!" %>
```

##Conclusion
As always, Rails has tried to abstract commonly used functionality into more terse and implicit code.  Experiment with these tricks in the upcoming lab.

<a href='https://learn.co/lessons/rendering-collections-reading' data-visibility='hidden'>View this lesson on Learn.co</a>
