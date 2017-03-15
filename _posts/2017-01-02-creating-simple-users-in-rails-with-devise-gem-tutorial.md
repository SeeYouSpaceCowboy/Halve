---
layout: post
title: "Creating Simple Users in Rails with Devise Gem Tutorial"
categories:
  - Rails
  - Devise
tags:
  - Rails
  - Gems
  - Mac
---

Prerequisite: Ruby, Rails, Active Record CRUD

When you finally get Ruby, understand a bit of Rails and start writing small websites with RESTful & CRUD conventions, you start to feel pretty good that you can show something off. Though that showcase still doesn’t feel very personal to someone just yet, until they start to make their own profile.

Here’s a tutorial using the Devise gem doing just that. We’ll make a simple blog app. We won’t be making the entire blog app in part I but will complete it in Part II. I would like us to focus just on how to create the profile, not the blog for this part. So instead we’ll kind of cut the blog short so that when someone logs in, it just displays a welcome index page with their e-mail they signed up with displayed. This way you can have a full user profile and have a platform for a full website if you’d like. In part II we’ll complete the blog and focus on how to make our blog unique to our individual user. Lets get started.

## Setting Up Devise Gem and Creating a User

Go to the directory where you want to have this project created and open terminal, then type :

```shell
$ rails new simple-user-profile
```

Now add the Devise gem to the Gemfile :

```ruby
gem 'devise'
```

Then the following in our terminal :

```ruby
# -- Install devise gem
$ bundle
$ rails g devise:install

# -- creates devise User model
$ rails g devise User
```

In terminal you’ll see a set of instructions from the devise gem. We only have to add the following line of code to the `config/environments/development.rb` path :

```ruby
config.action_mailer.default_url_options = { host: 'localhost', port: 3000 }
```

Migrate the database :

```shell
$ rake db:migrate
```

At this point you actually have a devise user profile and log in. If you’d like to try it out, start the rails server with :

```shell
$ rails s
```

Then go to `localhost:3000/users/sign_up` in your browser to see the sign in. It should automatically display the Ruby on Rails page. Lets change that into our index page next.

## Displaying a Welcome Index Page

Now that we have our Devise gem working properly, lets set up a welcome index page for our user in their blog (this could be anything, recipes, journal, etc. not just blog)

Lets create a Blog model and controller:

```shell
$ rails g model Blog
$ rails g controller blogs
```

Lets go into our User model created by our devise gem and our Blog model then set our associations.
Our User model has many blogs and our blog model belongs to a user.

Here is our User in `app/models/user.rb` :

```ruby
class User < ActiveRecord::Base
    has_many :blogs

    # Include default devise modules. Others available are:
    # :confirmable, :lockable, :timeoutable and :omniauthable
    devise :database_authenticatable, :registerable,
       :recoverable, :rememberable, :trackable, :validatable
end
```

Here is our Blog in `app/models/blog.rb` :
```ruby
class Blog < ActiveRecord::Base
    belongs_to :user
end
```

Our blog will have a title and a body. Lets set those in our migration `db/migrate/(date)_create_posts.rb` :
```ruby
class CreateBlogs < ActiveRecord::Migration
  def change
    create_table :blogs do |t|
      t.belongs_to :user
      t.string :title
      t.string :body
      t.timestamps
    end
  end
end
```
Lets migrate :
```shell
$ rake db:migrate
```
This is where if we were to create a full blog, we would have all our RESTful methods here, but since that’s not our focus for this part, we’ll simply create a welcome index page with the user email displayed :
```ruby
class BlogsController < ApplicationController
  # before any blog action happens, it will authenticate the user
  before_action :authenticate_user!
  def index
    @user = current_user.email
  end
  #Other Restful methods show, new, edit, create, update, destroy
end
```
We have to set routes in our configs folder :
```ruby
Rails.application.routes.draw do
  root 'blogs#index'

  devise_for :users

  resources :users do
    resources :blogs
  end
end
```
All we need is for our user to be able to see a page after they log in, since we have our index method in our controller, we need to edit our index blogs view :
```html
<h1>Welcome !</h1>
<p><%= @user %></p>
```
Now when you log in, you should see your e-mail. Hopefully, you now know how to make a user and are able incorporate users in other works. Take this project and make this into anything you like. If you liked this tutorial, follow me for when I finish and publish Part II or bookmark this page and I’ll link it here. Thanks for reading!
