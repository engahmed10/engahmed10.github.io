---
layout: post
title:      "Command Line Interface Project "
date:       2020-04-19 19:33:41 -0400
permalink:  command_line_interface_project
---

We have collected what we have learned in curriculum and study groups.
In this project we used two souls of ruby language is an OOP (object-oriented programming language) and data structure.
I went through several project ideas, in the end, I chose my project, the goal of my project is to bring data from a popular specific website and make the process to this data and display the result in our CLI :
 
* 25 best hotels in the world for 2020 years, their location and their webpages 
* Show details of each hotel 
* Show customers have visited these hotels 
* Show the review of each customer 

The first thing we have to make our folders and files required for this project, Ruby has a form of a gem or a packaged library.
By typing this command in terminal:
 
```
$ bundle gem besthotels 
```
 
This command will build folders and some files required for the project.
 
First, we got a bin folder that already has a console file is load an IRB instance that has access to your project's code. Then we made other files inside the bin folder; we called it exeprogram responsible for running our program.
 
lib folder includes all our classes and modules rakefile .
 
In the lib folder, we have made necessary classes in this project; these classes include:

*   	Scripting class: responsible for scripting data from website 
*   	Hotel class: responsible for creating new instances of hotel classes also assign attributes hotel name, location
       ,and url of each hotel. 
*   	Customer class: responsible for customers name, and their review for each hotel 
*   	CLI class: display results.

Our project has other files and folders necessary for any CLI project like Gemfile and Rakefile 
Its already created when we bundle a gem no need any modification 
 
Also, any project should have projectname.gemspec file,here we called besthotels.gemspec .Gemspec file contains information about the version, author, summary, description, internal dependencies, execution and everything about the Gem,we made some modification to run this project  .
 

We have two ways to parse data from website:

*   Scripting data using Nokogiri gem: Is an open-source software library or gem to parse HTML, SAX, and XML in
     Ruby. Among Nokogiri's many features is the ability to search for documents via XPath or CSS3 selectors.
*  An application programming interface (API): Ruby API is a Ruby on Rails app that makes browsing and searching 
    Ruby's   documentation easy and fast for users.
 
In this project, I used nokogiri to scrap data from a website, Scripting data was a little tricky, but I used Repli.it, it's beneficial script data from websites
Finally, I got my data, and I used the hash to return an array of hashes, with keys and values.
 ```
    {
       rank: i.css("div.posn span").text,
       name: i.css("div.winnerName div.mainName.extra a").text,
       location: i.css("div.winnerName div.smaller a").text,
       url: "https://www.tripadvisor.com"+i.css("div.winnerName 
         div.mainName.extra a").attribute('href').value
      }  
```
After bringing data from a specific site and turned to an array of hashes, I built my hotel class
and what I needed in this project, including class methods, class variables, instances methods, instance variables, and attribute accessors.

To make objects, inside scripting class I called class variable responsible for creating a new instance of the class hotel for each hotel attribute that saved inside our scripting class because our purpose is to make objects not hashes  

```
Besthotels::Hotels.new_hotel(hotel_hashes) .
```

After finished scripting list all hotels info, I used another method to bring details of each hotel 
From websites.
After finish coding, I started to run my project, its run fine but runs slow, and I have to wait 30 sec until show me the result of the list of hotels in the command interface screen.
Lastly, I figured out why my project runs slowly in the first 30 seconds. I realized the reason was that when I script data to show the detail of each hotel, I was using iterate to go through each 25 hotel webpage and bring data then assign it to new attributes makes the program slow.



```
def self.eachwebsite

    Besthotels::Hotels.all.each do |i|
        doc = Nokogiri::HTML(open(i.url)) 
        spec = doc.css("#ABOUT_TAB div.cPQsENeY").text
        cont = doc.css("a > span.public-business-listing-ContactInfo__nonWebLinkText--nGymU.public-
				business-listing-ContactInfo__ui_link--1_7Zp.public-business-listing-ContactInfo__level_4--3JgmI").text
        ameni = doc.css("#BODY_BLOCK_JQUERY_REFLOW div.hotels-hr-about-amenities-Amenity
				__amenity--3fbBj").text.strip
        i.specific = spec  
        i.contact =  cont  
        i.amenities = ameni  
    end
  end
```



After watching one of my teacher's video about API and CLI walkthrough, I figured out how he uses each object as an argument to pass to get detail of each website not the whole of them one time

So I worked on my scripting detail of each website again, I changed the way for getting data by sending every instance of an object as an argument to scripting class method, get_info_of_each(hotelobject)
  def self.get_info_of_each(hotelobj)
      
```
def self.get_info_of_each(hotelobj)
      
        doc = Nokogiri::HTML(open(hotelobj.url))
        spec = doc.css("#ABOUT_TAB div.cPQsENeY").text
        cont = doc.css("a > span.public-business-listing-
        ContactInfo__nonWebLinkText--nGymU.public-
        business-listing-ContactInfo__ui_link
        --1_7Zp.public-business-listing- ContactInfo__level_4--3JgmI").text
        ameni = doc.css("#BODY_BLOCK_JQUERY_REFLOW 
                div.hotels-hr-about-amenities-Amenity__amenity--3fbBj").text.strip
        hotelobj.specific = spec
        hotelobj.contact =  cont
        hotelobj.amenities = ameni

        aa=doc.css("#component_13 > div > div:nth-child(3) 
        div.hotels-community-tab-common-Card__card--ihfZB.hotels-
        community-tab-common-Card__section--4r93H")
        aa.each do |i|
          customer_n= i.css("div.social-member-event-MemberEventOnObjectBlock__member_event_block--1Kusx > 
          div > div.social-member-event-MemberEventOnObjectBlock__event_type--3njyv > span > a").text
           review= i.css("div.cPQsENeY > q").text
           cusobj=Besthotels::Customer.new(customer_n,review)
           hotelobj.add_customer(cusobj)
        end
      

end
```



Finally, my project runs faster no needed to wait 30 sec until I show the results.

My CLI class goes two-level deeper after asking the user to enter the list to show a list of all best hotels for 2020, I did another level to show to user detail of each hotel and asking the user to enter the rank of the hotel to see details of each hotel (description, property, contact number, customer), I used class method self.find_by_rank(rank) to find a description hotel. The last level was about customer reviews; when you ask the user to enter the name of the customer, it appears me the review of that customer, I used class method self.find_by_name(name) to find the specific object of customer and display of his review in the screen.

