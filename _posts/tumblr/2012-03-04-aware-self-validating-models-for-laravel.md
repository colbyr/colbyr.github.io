---
layout: post
title: 'Aware: Self-validating Models for Laravel'
tags:
- laravel
- budles
- development
---
Last night, I submitted a [brand new
bundle](http://bundles.laravel.com/bundle/aware) for [Laravel
PHP](http://laravel.com)! Aware is an extension of Taylor Otwell's [Eloquent
ORM](http://bundles.laravel.com/bundle/eloquent), which allows you to define
models with built-in validation.

Aware use's Laravel's Validator class so it's easy to define validation rules:

{% highlight php %}
<?php

class User extends Aware {

  /**
   * Aware validation rules
   */
  public static $rules = array(
    'name' => 'required',
    email => 'required|email'
  );

}
{% endhighlight %}

Aware models validate automatically when the save method is called:

{% highlight php %}
<?php

$user = new User();
$user->name = 'Colby';
$user->email = 'crabideau5691';
$user->save(); // returns false

$user->email = 'crabideau5691@gmail.com';
$user->save(); // returns true
{% endhighlight %}

If a model is invalid, you can access the errors from the validator like so:

{% highlight php %}
<?php

$user->errors->all();
{% endhighlight %}

For more detailed documentation and to browse the source check out the [github
repo](https://github.com/crabideau5691/aware).
