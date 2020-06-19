---
layout: post
title:      "Sinatra medical history"
date:       2020-06-19 15:59:40 +0000
permalink:  sinatra_medical_history
---

In the second project, i made the web application in Sinatra, Sinatra is a DSL language implemented in Ruby, means using it has his own rules from the domain. It used to write codes for specific purposes. My CLI project was about scripting data from websites and displaying the best hotels in the world in the command line. This project was more fun because of its  GUI (Graphic User Interface), which uses graphic images, including icons, menus, bars, windows. So I decide to change the domain for something different. In this project, I decided to do something familiar with, and I chose to do something with medical stuff, so my project name is Sinatra-medical-history. This app tracks the medical history of the family members including appointments with doctors, procedures, and  what kind of diseases catch them in their life, 

The benefit of this lightweight app i to record your family of  medical history  when you are going to doctor, they ask you your medical history, so it's easy to save all histories in a web application ito use them n the future .



The project includes:

1-User signup and  login 

2-Dashboard account and logout

3-Family members and medical histories for each member

4-View, create, update and delete history 

5-Show all diseases of members they catch in their life.

6-Medical procedures for each member 

7-View, create, update and delete the  procedure


I used UML to design this idea, object associations shown below :



![](https://www.hostpic.org/images/2006192031580323.png)


I started  coding by installing the corneal gem; it will establish you  necessary frames of a project
 
$gem install corneal        #installing corneal gem

$corneal new Sinatra-medical-history      #makes new corneal that includes all neccessory files and folders for a project

$code .     #opens   VScode

-made  new repository called sinatra-medical-history

$git init        #initialize   github

$git status   #will tell you there is stuff but not commited yet 

$git add . #grap file change file and submitting to repository

$git status     #status shows all filess chnge to green but not commited yet

-add any thing to your code like writing something in readme.md codes  then committed  below:

$git commit -m "start project"     #commited 

$git remote add origin git@github.com:engahmed10/sinatra-medical-history.git #add remote

$git push -u origin master  #pushes local branch to remote branch 

-craete tables

$git status   #

$git add . #

$git commit -m "tables created"

$git push

$corneal model users



I created tables and  created some objects and pushed data to the database, created necessary models and their associations which each other.then made controllers and view codes.

I used some heplers method to simplify my codes :

```

    def authorize(member)
        redirect "/members"  if member.user != Helpers.current_user(session)     
    end

    def authorize_history(member,history)
      #binding.pry
      redirect "/members/#{member.id}/histories"  if history.member_id != member.id 
    end
    
    def  authorize_procedure(member,procedure)
         
         redirect "/members/#{member.id}/procedures"   if procedure.member_id != member.id
    end
```


Also to find all diseases for current user  i made nested array  because user has many members and members has many histories and each history belongs to disease .

```
def self.all_desease(session)
      @all_diseases1 =[]
      members= self.all_members(session)
      members.each do |member| 
          member.histories.each do |his| 
             @all_diseases1 << his.disease
          end
      end
      @all_diseases1.compact.uniq
   end  
```

i had some tricks  to access history id  to each user and each member coming each member 
so to solve this issue we passed both members and histories in our history route:

```
`get "/members/:id/histories/:id1"  do
``
also we should change second id to something diffrent like :id1 because you will get error to mix between two id's :

```
get "/members/:memid/histories/:historyid"  do
```


Finally, I added some CSS and HTML to make the design better, but I still don't do enough, and I promise we'll do better in upcoming projects :

![](https://www.hostpic.org/images/2006192047050321.png)


later we can add more stuff like doctors, hospitals, laboratories, and chronic diseases, etc... tables and models and make connections between all.
