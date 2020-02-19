---
layout: post
title:      "Functional -> Class Component"
date:       2020-02-19 13:53:29 -0500
permalink:  functional_-_class_component
---


**Often, there comes a time in our 'React career' when we have to differentiate, decide, and alternate between functional components and class components. Both are essential parts of building a React application, but the two have very important differences that I will aim to highlight here. **

While building my single-page-application with React and Redux, I needed to revisit a functional component and transform it into a class component. Before I explain why and how I did so, lets refresh on the **main** differences between the two. 

### Functional 
- Plain old JavaScript function that returns a React element 
- Is **stateless** (pretending hooks don't exist) 
- Only needs an implicit or explicit return 
- Unable to use lifecycle methods 

### Class Component
- Can have **state** 
- Requires a render() method 
- Has access to lifecycle methods
- returns JSX wrapped in a single element 

 *aside: in order for a component to have access to lifecycle methods, it needs a render() method.* 
 
 In my case, the functional comp., GiftList, returned a list of gifts. Each gift object had price, name, category, url, to, and like attributes. I wanted to add a 'sort' functionality feature that would sort my gift list by price. 
The idea seems simple to implement at first;  just add a sort method in my functional component that when a button is clicked it gets invoked. Easy enough. While that concept is still correct, the entire process is a bit more dynamic.  

### Functionality/Process
- When the component mounts, we want the unsorted list to render automatically
- User pressed 'sort' button 
- Event listener attached to button invokes 'handleClick' method
- 'handleClick' method signals to our program that we want to sort our list
- sort method NON-DESTRUCTIVELY arranges our gift objects appropriately 
- new collection of objects is rendered

<iframe width="560" height="315" src="https://www.youtube.com/embed/uYbXFVQpF8c" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

To accomplish this goal, I first thought "what do I need to add to keep track of whether to render sorted or not" and obviously, the best way would be to have a little piece of state that marks one or the other. For this purpose in particular, a boolean piece of state made the most sense and would be easiest to change back and forth. In order to have state in the component, I needed to transform it into a class component. This can be accomplished either by importing { Component} from 'react' or extending React.Component when defining my class, and moving all the 'return' logic into a render method (which also gives us access to lifecycle methods) . Next, I explictly created a constructor method to access my passed in props and declared my piece of state. 
``` 
 constructor(props) {
        super(props);
        this.state = {
            sorted: false
        };
    };
		
		```
		
The 'sorted' property of the components state held a boolean value that was set to false upon construction. In the fourth step of our process, the first step in handling our event, we toggle our state: 
```
  handleClick = () => {
        this.setState(prevState => ({
            sorted: !prevState.sorted
        }));
    };		

```

		and this **signals** we want to sort our state because in the render() method, what gets rendered **depends** on the status of our state. 

```
		  const renderList = () => {
            let gifts;
            let sorted = this.state.sorted
            if (sorted) {
                gifts = this.sortList()
            }
            else {
                gifts = this.props.gifts
            }
						
						```
						
						
						**If** sorted == true, we use the sortList() method to make a new collection of arranged gift objects from the props passed in. 
				
``` 
    sortList = () => { 
            let gifts = this.props.gifts
            return (
                [...gifts].sort((a, b) =>
                    parseInt(b.price) - parseInt(a.price)
                ));
    };
		
		```

