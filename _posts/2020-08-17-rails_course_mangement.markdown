---
layout: post
title:      " Course Management By Using Rails "
date:       2020-08-17 17:09:27 -0400
permalink:  rails_course_mangement
---

 
The idea of my rails project is to manage courses added by an individual or added from  API's data,
so it will be more accessible to the user when he login to log for a specific course in the world. 

My Project includes 4 models :

1. User for sessions
2. Education
3. Course 
4. Institute

![](https://www.hostpic.org/images/2008180101560296.png)

Explain steps:

* User can log in log out and signup, Also user choice so can control for app
* Used devise gem for authentication  is pretty nice so login has email password, password
   confirmation, remind me, forget the password, all validations, and validations messages 
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
* Bootstrap ,html,css  used to create layout and some styles 
 



This app can be developed by adding more features to it, for example, can add review and rating Model to courses model so that course can have many reviews by different users. Also, you can add more courses for this app by getting JSON data from different API's .



