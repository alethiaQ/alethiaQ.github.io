---
layout: post
title:      "Asynchronus Behavior"
date:       2020-02-20 21:19:08 +0000
permalink:  asynchronus_behavior
---


> Asynchronous programming is an approach to writing computer programs so that events happen outside of the main program flow, in the same overlapping time frame. These types of programs are called "non-blocking," because the program can continue without being "blocked" by waiting for events like user input or network activity. This general paradigm of computing is called asynchrony. - What is Asynchronous?
https://www.computerhope.com/jargon/a/asynchro.htm

It's one thing to understand Asynchrony in concept, but it is a bit more difficult to grasp in practice. Between code reviews and job interviews, questions about Asynchronus programming have come up almost every time so it is **vital** we have a solid understanding of what it is and how it works. 
To understand what asynchronus programming is, it may be easier to think about what it is *not*. It is not task-to-task, linear, one after the other programming; that is **synchronus programming**. Think of synchrony as a straight line, where one task begins, gets worked through, finishes, **THEN** the next task is begun.  **Asynchronus** programming is basically the opposite. Say we have a webpage, like instagram or twitter; there are 'like'-buttons, ads, posts, ect. The ads are constantly appearing/changing, we are able to engage in functionality (liking, sharing, retweeting), and new stuff is popping up.. all seemingly without a page refresh. Because of asynchronus programming, we are able to make all of this happen. The idea is functions are dealt with as they come, regardless of what else is going on. For example, a fetch call to grab the next ad might be getting taken care of at the same time your like on someones post is triggering an event. Many things happening at the same time, without pause or disturbance, creating a seamless user experience.. 

Imagine if the page refreshed everytime a new ad appeared and we are shot back to the top of our feed, or if someone likes a post, dragging it back to the top of the chain- away from where we are. This is what twitter/instagram would be like without asynchronus programming. It would be awful, and probably unsuccessful. That is why asynchornus development is so important today. 

But enough of why it matters and what it is in concept, lets focus on it in practice. 
Say we have a function: 

``` fetchList = () => { 
    console.log("a")
		fetch("http:/somesite")
		.then( r=> console.log("b"))
		.then( data => console.log("c", data)
		console.log("d") ```
	What would be rendered in the console? **Before scrolling down, take a moment to think about it and write your answers down**
		Keep in mind ![Imgur](https://i.imgur.com/PeIJu3h.jpg?1)
		
		The console would render:  a, d, b, c 
		Because asynchronus programming is an impatient guy, he isn't going to wait for the fetch to be resolved or rejected before jumping down past it and its .then methods, to the final console.log 
		
Now what about: 
``` 
   console.log("a")
		fetch("http:/somesite")
		.then( r=> console.log("b"))
		.then( data => console.log("c", data)
		
		for (let i = 0; i <= 50; i++) {
		console.log(i)
		} ```
		

	The console would return: a, 1...50, b, c 
	You may be wondering why the for-loop did all of its buisness before moving on, seems a little.. synchronus. Well thats because its a synchonus function within our asynchronus code. Although our code is working asynchronously generally, our program will hit the loop asynchronously (before the promise is resolved),  wait until the synchronus bit is complete, then continue on in its normal fashion. It's a bit confusing.. but just think about it like normal function execution, when our engine enters into any function it's not going to just stop midway and complete another task, it will see it all the way through, unless told other wise. Since our example lives within the same scope, it behaves this way. It enters the for-loop, does the work required inside, then exits out and handles unfinished business (in this case .then() methods belonging to our fetch object).  
		
		




