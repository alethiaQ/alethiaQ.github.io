---
layout: post
title:      "Simple CLI Project Start to Run-"
date:       2019-08-12 16:19:20 -0400
permalink:  stranger_things_directory_cli_ruby_gem
---

## Complete CLI-project methodology and implementation

Beginning any project with a blank page is always daunting, even more so when you have the freedom to pick any topic. In this case, I had to create a CLI ruby gem with scraped data from any web-page. After many attempts, I finally found a webpage that interested me and was laid out well enough to scrape from. I chose two FANDOM Stranger things wiki articles, one containing trending characters, and the other about show locations.  


**Getting Started**
The best way to organize my thoughts and ensure I stay on task- is to invision the big picture first, then work down to the "nitty-gritty". 

Using a simple list, such as the ones below, I was able to imagine how I wanted my program to look, how I wanted the user to interact with it, and map how I wanted my data to be broken down. 

**How I want my program to run overall: **
* Welcome message
* Output to user Category options (Location list, Character List) 
* Output selected list- Allow user to choose item to learn more about 
* Output item 
* Start from top
* Exit program when user enters exit

**Basic CLI Project design steps and notes: **
* Gem bundle creator (after research)
* Create execution file 
* Create CLI logic file in lib that the exe file calls to run the program 
* Use "fake" practice data to make sure the exe file works 
* Stub out fake data with real data from different files
* Discover objects as I go
* Refactor

After brief research, I decided to use bundlers 'bundle gem new 'gem-name'' to create my projects' directory infrastructure. This creates our new app with the appropriate gemfile, environment, and other necessary files. 

![img](https://i.imgur.com/U3PI436.png[/img])

Once my files were set up,  I used basic test data directly within the file  to map out the flow of the entire app from start to finish before we subsitute with real data. 

### Creating objects, Getting our Real Data 

The goal of scraping our wiki page is to gather elements that hold value and use them to create relevant objects with various attributes. 

**Location Object should have**
* name 
* description
* type of location
* inhabitants
* area in proximity 
* webpage url 

**Character Object should have**
* name
* age
* gender
* status (dead or alive) 
* occupation
* portrayed by 
* residence
* family

# **Scraping**
Scraping can seem like a daunting and tideous task at first, but once you get the hang of accessing data you want, the process can be almost effortless and easy. 

To begin, I opened the webpage I intended to use with nokogiri and open uri, added a binding.pry command, and tested various iterations to reach the values relevant to their corresponding attribute. This is probably the hardest part of scraping, but just keep trying and implementing different css selectors until you find something that works, no harm will be done because you are just in pry! 
```
def open_page
    Nokogiri::HTML(open("https://strangerthings.fandom.com/wiki/Category:Characters"))
		binding.pry
end
```

In order to keep my program stratified and concise, separted by function and implementation, I decided to create a scraper for the location homepage and character homepage. Since each webpage held individual items (characters and locations) each having their own url, I needed my program to scrape down to each url piece by piece, then send the information from that webpage to another file that parsed that page, collecting each objects attributes one by one, for each url. 
**To visual this: **

![img](https://i.imgur.com/tdOIj6l.png?1[/img])

**Method Breakdown:**
1. The first method opens the main webpage that leads to each characters own page ![img](https://i.imgur.com/iIigJrX.png?1[/img])
2. The second method parses the HTML page down to where each characters url is listed ![img](https://i.imgur.com/nK8htMR.png?1[/img])
3. The third method sends each list item containing the characters name and url, to a character.rb file that creates a character object for each and grabs data to create all the attributes needed for every object
![img](https://i.imgur.com/riTakz2.png?1[/img])

*Notice how most methods scrape an individual piece of data, rather than having one method that scrapes all attributes in one*

I followed the same process for my location items and scraper, allowing my program to be concise and run quicker and smoother. Once I had all the data I needed scraped and accessible through my objects, I had to refactor my cli.rb file to grab the information from my objects, know which object was needed when picked (done so by a class variable @@all that kept each objects information, and a self.find method to access the class variable and find the specific instance based on index), and present an objects' attributes in an aesthetic way. Alike my scraper and object files, my cli file needed to have methods that focused on an individual task. By doing so, my methods were able to call on eachother and there was no need to use a loop to keep the program running. 

![img](https://i.imgur.com/9rIwz0I.png?1[/img])
![img](https://i.imgur.com/o31P2wQ.png?1[/img])
![img](https://i.imgur.com/8RpHzRG.png?1[/img])

Once I cleaned up my code, added a fun ASCII space image, and pushed my gem to Ruby Gems, my project was finished and the final product looked as such: 
[Stranger Things CLI Ruby Gem (youtube)](https://youtu.be/jxtIJNSKsnw)


