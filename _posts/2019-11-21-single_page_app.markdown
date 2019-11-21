---
layout: post
title:      "Single Page App "
date:       2019-11-21 01:07:43 -0500
permalink:  single_page_app
---

JS Frontend and API Backend 

## Overview: 
I created a single page app titled "He goes by Lo". Its based off the Lorax and basically, he is undercover because of current events and needs your help collecting trash (snake-game) and "growing trees" (points). In order for the points to really have a purpose, I created a user model to keep track of each players total tree score. 
**Backend- **
The purpose of the backend api was really to store user data, not so much as generate app logic. 
**Frontend- **
I have one class- a user class and 
A prototype function for the game 

## Deep-Dive into Javascript abstraction
Abstracting your own implemented logic can be a lot to wrap your head around at times, especially when you are still learning a language. Personally, I wasted a very large sum of time figuring out how to pass user data into game logical then back into user data.. and it was a mess and just as confusing as that sounds. Then a light-bulb *finally* turned on... I could use Javascripts OO Class structure. Although, I had spent weeks learning about this very idea, I still hadn't completely grasped the concept of tying api data and Javascript manipulation all together, so hopefully I can ease that confusion for anyone else struggling. 

So for my app;** In general ** (frontend and backend)  a user will have a name, email, and a tree score. 
**The Rails api's ONLY job is to store user data and render it in json when needed. That is it! **

Because I know I will be manipulating and updating that data, it is best to make a User JS Class. 
A User class with name, email, and tree constructor parameters, will make our life a lot easier when passing a user object instance around and it will clean up our code nicely (or else to find user info inorder to update it, we would either have to pass a variable around which is risky, or fetch everysingle time) 






