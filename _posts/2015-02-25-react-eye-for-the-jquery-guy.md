---
layout: post
title: React Eye for the jQuery Guy (or Lady!)
tags:
  - javascript
  - react
---

React is the bees knees [1]. If you're familiar with React, I would suggest checking out the docs and watching Pete Hunt's talk, [Rethinking Best Practices](https://www.youtube.com/watch?v=x7cQ3mrcKaY).

Since I got into web development I've spent *a lot* of time with jQuery.
I got pretty good at it, learned all the tricks of the trade.
But over the last couple years, I've had more time than most to learn about React and I began my education at Facebook (straight from the source!).
I had to unlearn familiar jQuery patterns in favor of the alternatives React provides.

## Wait what day is it?

When you're writing React, every day is hump day [1] because everyday is so much more delightful than the ones you knew before!
And also because props should be named according to JS DOM conventions rather than HTML conventions.

{% highlight js %}
<button
  onMouseDown={handleMouseDown} // correct!
  onMouseup={handleMouseUp} // not quite...
/>
{% endhighlight %}

It's `lowerCamelCase` all day every day and when you forget it can be a real pain to track down.

## The DOM is not a data store

Actually, it kind of is but we rarely need to use it that way with React.
In my experience, passing data to event handlers using data attributes is a common pattern.

{% highlight html %}
<button class="delete-button" data-user-id="12345">
  Delete User
</button>
{% endhighlight %}

{% highlight js %}
$('.delete-button').click(function(event) {
  deleteUserById(
    $(event.target).data('user-id')
  );
});
{% endhighlight %}

My first instict was to do the same in my components.

{% highlight js %}
React.createClass({
  handleDelete: function(event) {
    deleteUserById(
      $(event.target).data('user-id')
    );
  },
  render: function() {
    return (
      <button
        data-user-id={12345}
        onClick={this.handleDelete}>
        Delete User
      </button>
    );
  }
});
{% endhighlight %}

## Make refs, not DOM queries

`this.refs`

## Clean up!

This isn't completely new if you're familiar with Backbone or other clientside JS frameworks, but cleaning up after yourself is important.
React manages DOM event listeners automatically which is awesome!
But anything you setup yourself in `componentDidMount` should be cleaned up.
Otherwise you'll inevitably end up with problems...

{% highlight js %}
Uncaught Error: Invariant Violation: replaceState(...): Can only update a mounted or mounting component.
{% endhighlight %}

`componentWillUnmount` 

## tl;dr

So just remember:

1. Props are always `lowerCamelCase` to match the DOM API spec.
2. Use [partially applied functions](http://lostechies.com/derickbailey/2012/07/20/partially-applied-functions-in-javascript/) instead of data attributes.
3. Prefer [`this.refs`](http://facebook.github.io/react/docs/more-about-refs.html) over DOM queries.
4. Always cleanup listeners in [`componentWillUnmount`](http://facebook.github.io/react/docs/component-specs.html#unmounting-componentwillunmount).

Now go write some React!

---

[1] Bees.

![BEES](http://i.imgur.com/qrLEV.gif)

[2] Hump Day!

![HUMP DAY](http://cl.ly/image/272O0H1j401A/hump-day_1370620934_epiclolcom.gif)

