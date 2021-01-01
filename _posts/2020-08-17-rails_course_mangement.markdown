---
layout: post
title:      " Course Management By Using Rails "
date:       2020-08-17 17:09:27 -0400
permalink:  rails_course_mangement
---

 
The idea of my rails project is to manage courses added by an individual or added from  API's data,
so it will be more accessible to the users when they login to look for a specific course in the new york area. 

My Project includes 4 models  and tables in data base:

1. User for sessions
2. Education
3. Course 
4. Institute

![](https://www.hostpic.org/images/2008180101560296.png)

Explain steps:

* User can  signup, login and  log out
* Used devise gem for authentication, gem provides strong authentication has more features like entering email, password, password confirmation, remind me, forget the password, all validations, and validations messages 
* User Third-party auth with GitHub login

![](https://www.hostpic.org/images/2008180130190305.png)

* User has admin option for control the app 
* Admin will create education types everything would like to tech, psychology , English...
* User can view, create, update, delete a course and choose education and  institutes  they want
* many to many relationships used  between educations, courses, institutes
* Used    API to grab some data from third party websites 
* Home page  has a search option  so users can search for  any courses they want, by typing a word of course
   , for  example: if you type network in search bar, you will see all courses have network word in their name:
 
 ![](https://www.hostpic.org/images/2008180155530305.png)
 
 
*   Nested optional route used between educations and courses 
*   Bootstrap ,html,css  used to create layout and some styles 
 



This app can be developed by adding more features to it, for example, can add review and rating attributes to the course's models so that the course can have many reviews by different users. 
Also, we can add more courses to this app by getting JSON data from different API's in the same state or other states, and users can find more courses and institutes.


