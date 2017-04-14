---
layout: post
title: "Understanding Database Associations Through a Followings Model"
categories:
  - Rails
  - SQL
  - Mac
tags:
  - Rails
  - SQL
---
# Still In Progress
This blog isn't finished and is still in progress.

SQL databases are extremely important in building software applications. They allow us to persist data in our application. If we can't persist data, then you'd have to recreate your profile every time you log into Facebook. Using Rails Active Record, I'll show you how to make a simple table, all the way to an entire `Followings` table you would usually see in Instagram. Where you have many followers and you can also follow many people.

I'm a fan of getting started quickly ( so I'm not bored to death ). Lets create a new Rails project. I like using atom as my editor, you can replace `atom` on line 3 with the editor you use.

```shell
$ rails new project-name
$ cd project-name
$ atom .
```

## Creating a Table

Usually you have one application and that application has one database, which then contains multiple tables, where those tables then have columns and rows. If it helps, you can imagine and excel sheet. Columns and rows would be the fields you'd like the table to have. So for example in my database, I might make a `users` table  to keep track of all of the users and then create a `posts` table to keep track of all posts.  So I have one database with two tables.

If you wanted to create a table for a user, you'd do the following. Now if I wanted to save a field/column, then you'd simply add `t.type :field_name` inside the `create_table` block. In this example, I want the user to have an `username` field and an `age` field.

```ruby
class CreateUsers < ActiveRecord::Migration
  def change
    create_table 'users' do |t|
      t.string :username
      t.integer :age
    end
  end
end
```

You can see easily that posts would simply just be replacing the users

## Associations

Now my `users` table probably has an association with my `posts` table because an user can have multiple posts and a post can only have one user. If I was a user named John, then John can have a million posts, but these posts can only belong to John since he posts them.
