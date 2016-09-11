---
layout: post
title:  "Hacking Hashes"
date:   2016-09-10
---
One of the really difficult concepts I had trouble grasping in class was Hashes. Hashes are made up of keys and values and look similar to arrays. Take a look at the hash below:

{% highlight ruby %}
$ hash = {"Wizard" => "Harry Potter"}
{% endhighlight %}

In the example above, the name of the hash is "hash", the key of the hash pair is "Wizard" and the key's value is "Harry Potter".

If we wanted to find the value of "Wizard," we would call the key on the hash like so:

{% highlight ruby %}
$ hash["Wizard"]
$ => "Harry Potter"
{% endhighlight %}

The tricky part for me, was implementing this concept into my rails app to use in the various controller methods that required it. For example, let's say we have a Wizard Controller with an update method:

{% highlight ruby %}
class Wizard < ApplicationController
  def update
  end
end
{% endhighlight %}

On the 'edit.html.erb' view page, let's say the Wizard model has a first name and last name that we want to update:

{% highlight ruby %}
  <%= form_tag("/wizards/#{@wizard.id}/edit}", method: "patch") do %>
  <div>
    <%= label_tag(:first_name) %>
    <%= text_field_tag(:first_name, @wizard.first_name) %>
  </div>
  <div>
    <%= label_tag(:last_name) %>
    <%= text_field_tag(:last_name, @wizard.last_name) %>
  </div>
  <div>
    <%= submit_tag("Update Wizard Info") %>
  </div>
  <%= end %>
{% endhighlight %}


We'll need to first find the 'id' of the Wizard, in order to access the names, which is where the hashes come into play:

{% highlight ruby %}
class WizardController < ApplicationController
  def update
    @wizard = Wizard.find_by(id: params[:id])
    @wizard.update(
       first_name: params[:first_name],
       last_name: params[:last_name]
       )
    end
  end
end
{% endhighlight %}

Now let's break down the code above. The update method, allows use to make changes to the Wizard attributes by first seeking the 'id' using `find_by` which consists of a hash where we've labeled the key `id:` and its corresponding value `params[:id]`. Keep in mind we don't know the Wizard 'id' so `id` and `params[:id]` serve as placeholders that will allow us to call an id on Wizard, and receive the corresponding information. Once we know the `id:`, we are able to make changes to the Wizard's information, using the hash combinations `first_name: params[:first_name]`and
`last_name: params[:last_name]`.

This concept and use of hashes is still tricky, but it gets clearer the more I do it.
