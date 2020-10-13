---
layout: post
title:      "JavaScript Rails travel  Project "
date:       2020-10-12 21:09:18 -0400
permalink:  javascript_rails_travel_project
---



The goal of the project was to learn all those stuff ( javascript, rails, database, DOM, CSS, HTML) together and makes a single web page,  I got the idea of the project from  because I am interested in tourism and travel, so any user can see, add delete, and update cities and his attributes, also anyone can see, create, delete, and update Thingstodo and his descriptions .so when someone wants to travel to any city , so will be easy for him to know all things todoss in that city, and after visiting that city he will add new thingstodo, that will help others to know more about that city.

The backend of the projectinludes , city model has many Thingstodo and Thingstodo belongs to city
The database  scheme like this:
```
 create_table "cities", force: :cascade do |t|
    t.string "name"
    t.string "country"
    t.string "population"
    t.string "url"
    t.datetime "created_at", precision: 6, null: false
    t.datetime "updated_at", precision: 6, null: false
  end

  create_table "thingstodos", force: :cascade do |t|
    t.string "name"
    t.string "description"
    t.integer "city_id", null: false
    t.datetime "created_at", precision: 6, null: false
    t.datetime "updated_at", precision: 6, null: false
    t.index ["city_id"], name: "index_thingstodos_on_city_id"
  end

  add_foreign_key "thingstodos", "cities"
	
```


Our  serialzer files :
```
class CitySerializer
  include FastJsonapi::ObjectSerializer
  attributes :id ,:name, :country, :population, :url
end

class ThingstodoSerializer
  include FastJsonapi::ObjectSerializer
  attributes :name, :description,:city_id
end

```
After finshed data serialzed 

http://localhost:3000/cities
```
[
  {
    "id": 1,
    "name": "Istnabul",
    "country": "Turkey",
    "population": "10.730 million",
    "url": "https://c8.alamy.com/comp/2A2BPPG/the-suleymaniye-mosque-beautiful-view-from-the-golden-horn-inlet-istanbul-turkey-2A2BPPG.jpg",
    "created_at": "2020-10-12T12:08:58.070Z",
    "updated_at": "2020-10-12T12:08:58.070Z",
    "thingstodos": [
      {
        "id": 1,
        "name": "Topkapi Palace",
        "description": "This enormous palace was the Imperial residence of Ottoman sultans for almost 400 years.Although much of the palace is not accessible, the daily tours of the Harem are of great interest to tourists",
        "city_id": 1,
```


Front end files contain: 

Cities.js :  to make CRUD of cities 
Thingsto.js:    to make CRUD Thingstodos
APIAjax.js connect to the Backend and fetches data from the backend 
index.js used to call necessary instance and static or class of  methods,listen to  some DOM's,

How the project works :
we make fetch all cities from the backend and make objects and then call render city for each object, make render HTML.
In the second step, I used event delegation, by listen add an event listener to the parent node (city collection), I was able  to listen to  multiple child listeners (del and update ), then click on update  city will show the update form for us and  hides others,then will put the required data to update to the form, after this  step we find the city id  to send it with a fetch to make an update in the backend ,after you make a change on the form and click submit ,we will send data-id and model arguments to the other class to fetch us updated data from the backend, we use HTTP verbs or method  PATCH, inside body our new data that require to update in the backend, the backend will send a promise in the first response to the front end by using method .then.

  fetchForUpdate(id,data){
    return fetch(`${this.URL}/${this.model}/${id}`,{
      method: 'PATCH',
                headers: {
                    'Content-Type': 'application/json',
                },
                body: JSON.stringify(data)
      }) 
      .then(res => res.json())
  }
Need second promise to get data and do the process on it in the front end, headers required to tell client content type is JSON.
.To see all things to do we added a button to each city card, the model page will open and the city collection page display will disappear to do CRUD processes to thingstodo model.
Also we used in this project some ES6 Features like  :
```
const{id,name,country,population,url,thingstodos} =this.city .

```

finally we got everything working ,and single page looks like this:

![](https://linkpicture.com/q/Screen-Shot-2020-10-12-at-5.22.58-PM.png)

