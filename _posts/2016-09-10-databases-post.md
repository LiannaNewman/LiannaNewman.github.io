---
layout: post
title:  "Diving into Databases"
date:   2016-09-10
---
In my last post I discussed how to set-up a new app in rails. Now let's talk a little about what a database is and the role it plays in an app.

The database is where we store information to use in our app. After creating an app one can create a database by entering the following code into the Terminal during your creation of the app:

{% highlight ruby %}
$ rails harry-potter-app --database postgresql
{% endhighlight %}

Note: In class we used the Postgres database, if you create your app without specifying your database the default database is MySQL.

After enter the code above and pressing "Enter", make sure you cd into app:

{% highlight ruby %}
$ cd harry-potter-app
{% endhighlight %}

Then enter the following code:

{% highlight ruby %}
$ rake db:create
{% endhighlight %}

Now that the database is created, you can add [Models](http://guides.rubyonrails.org/getting_started.html#generating-a-model). Once the models and and their attributes are created, you'll need to enter the following in terminal to create the tables in your database:

{% highlight ruby %}
$ rake db:migrate
{% endhighlight %}

You can add to, edit, and update the database using a [Controller](http://guides.rubyonrails.org/action_controller_overview.html) along with its corresponding model. The database helps us create associations between classes and is vital to functionality of many our apps.
