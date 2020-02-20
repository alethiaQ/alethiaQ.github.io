---
layout: post
title:      "React vs AngularJS"
date:       2020-02-20 18:13:06 -0500
permalink:  react_vs_angularjs
---


During the course of my job search, there seemed to be an even distribution of companies hiring Javascript experienced employees using React or AngularJS. At Flatiron, we are taught React (because it is awesome and statistically more popular) and although I may not have experience with Angular, I wanted to be able to atleast highlight the differences and similarities between the two. Basically, to show I am aware and willing to learn, and be able to answer some questions about Angular using my React knowledge and highlighting what may be contrasting or similar to what I already know. So I decided to do some research of my own comparing the two; even though both are JavaScript children.. the differences outweight the similarities by a long shot. 

Off the bat, the biggest difference between the two- 
**Angular is a full framework** and **React is a javascript library**. What this means is Angular is a full-fledged MVC framework (think Rails for Ruby) written in typescript, comes with a lot of its own functionality, contains rules for structuring, and is a lot less flexible. React, being a Javascript view library, is much more flexible, has no real structuring rules, and requires additional libraries to add functionality. 

## Angular (framework) vs React (library)
### Angular 
* Provides routing via @angular/router 
* Packaged ajax requests- @angular/HTTP
* Builds forms with @angular/forms
* Includes Testing capabilities
* Built-in state management 
* Access to Templates

### React 
* No native routing- Popular library is React-Router 
* 3rd party state management- Usually through Redux or MobX
* JSX instead of templates 
* Only unit-testing capabilities, for other functionality Enzyme is popular
* Fetch is used for Ajax requests 

Beyond the big differences between framework and library (like the ones listed above), there are still more key comparisons to be highlighted.  

![img](https://i.imgur.com/NjIQpBD.png)

## React 
* Uses Virtual DOM - quicker 
* "Smaller" - easier to learn
* JSX (Javascript/HTML mashup) - easier to learn
* One way Data-binding (more on this below) - requires callbacks or state management 
* Easily scalable 

## Angular 
* Regular DOM - slower 
* Framework - larger more complicated to learn at first
* Typescript - more to learn
* Two-way Data-Binding - seamless transactions 
* Easily scalable 

### Data-binding 
To explain this as simply as I can, think about when an element or state is changed (a user likes a post, information is updated, ect) and how these changes are implemented on a UI element or in the model state. When a user inputs information how does state reflect these changes, contrastingly, when state is changed how does a UI element correspond. 
In **one-way binding** (React), when model-state is set/updated, the UI is automatically updated and rendered. In contrast, when a user enters data that is to be reflected in state, **additional functionality is required**; a callback function must take care of setting/changing state before rerendering. 
In **two-way binding** (Angular) both transactions are handled effortlessly. A user can input information and state will update correspondingly. Additionally, when model state is changed, the UI element will reflect as such. Both are in communication with eachother, without the need of callbacks or additional functionality, hence two-way binding. 

React and Angular are both widely used and powerful technologies for single-page-applications. Both can be used to accomplish the same tasks, although React will need some help from other libraries. I wouldn't say one it better than the other, it just depends on preference. 
