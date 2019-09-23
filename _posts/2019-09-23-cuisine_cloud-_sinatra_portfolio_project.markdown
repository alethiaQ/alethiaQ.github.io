---
layout: post
title:      "Cuisine Cloud- Sinatra Portfolio Project"
date:       2019-09-23 19:49:54 +0000
permalink:  cuisine_cloud-_sinatra_portfolio_project
---


## Overview
For this assignment, we were to create our own simple Sinatra application. Using ActiveRecord associations, I needed a "User" class that sponsored a "has_many" relationship and at least one other class that "belonged_to" a user. Also, user authentication and password encryption were required. Alike any project started from scratch, I used my three phase methodolgy- Planning/Researching, Implementation, and Refactoring/CSS. 

## Planning

* **Brainstorm: Browse, write down app ideas that YOU would find useful:** <br>
Coming up with an idea for an application can be challenging, especially if you are indecisive like me. The brainstorming process always takes a little while for me, browsing the internet and visiting websites like [app ideas](https://www.ideaswatch.com/startup-ideas/app#) helps. <br>
* **Map Out Associations and Migrations**<br>
The most challenging aspect of this project for me, was setting up my relationships. It helps to think about the associations in real life situations and diagramming the relationships as well. After brainstorming and many attempts to set-up associations with various ideas, I decided to make a cook-book and recipe website. A user has_many cook-books, a cook-book belongs to a user, a cook-book has_many recipes, and a recipe belongs_to a cook-book. By association, a user has_many recipes through cook-books. ![Imgur](https://i.imgur.com/c7bs2Jl.png?1)<br>
* **Establish how you want the site to flow generally ** <br>

Imagine you are entering the site for the first time, how would you want the homepage to look.. what would you want the viewer to see after creating an account, ect. 
<br>

## Implementation 
1. After laying out the basics of my application, Cuisine Cloud,  on paper, I browsed the internet for creating a sinatra application from scratch. I found a very helpful gem 'Corneal' that laid out the foundations of a sinatra app, including an app folder, a preset environement, config.ru, and gemfile. 
2. The first step of actual development I like to begin with, is creating my migrations and models. Since I had already established my associations, it was just a matter of putting the correct columns in my tables. For Users, a username, a password, and their full name. Cook-books; a name, a description, and a user id field. Recipes; a name, ingredients, cook time, instructions, and (after messing around with my associations a little) I added a user field. 
3. From here, its just a matter of setting up your routes and views. Depending on your application, your routes and pages will differ, but for the most part when creating a user aspect of an application you will need a login and sign up feature.  With each step I load up shotgun and make sure everything is going through correctly, as in my routes are established correctly and my views are render properly. Get one piece working correctly before moving on and don't worry about it looking pretty until the end, its more important that the functionality is running smoothly, without data and pages your pretty pages will be pretty pointless. 

Cuisine Cloud Routes and Views Overview: 
* Obviously, a user will start by either creating an account or logging into their account 
* From there, they would be redirected to their "dashboard" or accountpage view 
 ![Imgur](https://i.imgur.com/5QsQpdf.png?1)<br>
With CSS from bootstrap, it translates too: ![Imgur](https://i.imgur.com/Hpzy28D.png?1)
* They then would be able to create a new cook-book or recipe
* When creating a recipe, the user must choose the cook-book the recipe belongs too.. by association the recipe will belong to the user who the cook-book belongs too 
```
 post "/recipes" do
    if logged_in?
      if params["Name"] == ""
        redirect to "/recipes/new"
      else
        @recipe = Recipe.create(params)
        @recipe.user = User.find_by(params[:user_id])
        @recipe.save
        redirect "/recipes/#{@recipe.id}"
      end
    else
      redirect to "/login"
  end
```
	I added the line @recipe.user = User.find_by in order to give the accountpage easy access to the owners recipes without repeating and complicating code 
* 	For new cook-books:

```
 patch "/cookbooks/:id" do
    if logged_in?
      if params[:name] == ""
        redirect to "/cookbooks/#{params[:id]}/edit"
      else
        @book = CookBook.find_by_id(params[:id])
        if @book && current_user.cook_books.include?(@book)
          #error message needed
          @book.update(params[:cookbook])
          @book.description = params[:cookbook][:description]
          @book.save
          redirect "/cookbooks/#{@book.id}"
        end
      end
    else
      redirect "/login"
    end
```
* Each recipe and cook-book could be edited or deleted using Rack::MethodOverride and patch methods 
Edit example : `<form action="/cookbooks/<%= @book.id %>" method="POST">
    <input type="hidden" name="_method" value="PATCH">
`
* Index or Browsing pages were implemented for both as well 
* Logout was accessible through the nav-bar 

## Refactoring/Beautify
The last step was to refactor any repetitive or ugly code, like "if logged_in ?" in majority of methods could be implemented through a helper method. After, I browsed the web and used bootstrap to easily implement CSS and make my application pretty! 

If you'd like to take a look at my repo- [Cuisine Cloud](https://github.com/alethiaQ/CuisineCloud)



