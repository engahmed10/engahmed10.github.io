---
layout: post
title:      "Simple Ruby cheatsheet "
date:       2020-12-10 20:10:23 +0000
permalink:  simple_ruby_cheatsheet
---



**variable **

n= 5   ,n=5.6 ,             Define variable and assign integer or float value on it,together define varibale and assign variable  called declaration
k="jack"  ,k="5"     Define  variable and assign  string value on it

**output and input **   


*    to  print on the screen, using  single or double quotes will work
*
```
puts ' stuff to print '     
```
 
*     to gets input from user
*
```
string  = gets.chomp     
```


**iterartion**

`each ,each.with_index `      * will use to iterate inside array elments ,will not retrun new data will get orignial array ,you must use varaible or new array to get what you need *
`map ,map.with_index `        *will store the data you can return it without using new array*
```

def fruit(arr)
        arr.each  { |item| 
             item * 2
        }
end

 fruit(['lemon', 'orange'])                    
    result :lemon
               orange
 
 
 
 def fruit(arr)
        arr.map  { |item| 
             item * 2
        }
end

 fruit(['lemon', 'orange'])
 
    result :lemonlemon
               orangeorange
```


using     n.times   #n times loop
#=>Hello,Hello,Hello,Hello,Hello

```
5.times do
  puts "Hello"      
end
```

 

  some array methods:
	
```
	arr = ['a', 'b', 'c',nil, 'd', 'e', 'f']
	arr.first                       #=> 'a'
	arr.last                        #=>  'f'
	k= arr.take(2)                     #=>  a b
```

```
  k.instance_of?Array     #=>  true
	arr.empty?               #=> false
	arr.include?('d')        #=> true
```
	
	Destructive array    : orignal array will changes
	
	pushes to end of array,resize of arary without of loosing data
```
arr.push('g')          #=>  ['a', 'b', 'c',nil, 'd', 'e', 'f','g']  
```
place to begining of array ,shift and resize of array without loosing data
 	                                                                                         
arr.unshift(5)        #=> [5,'a', 'b', 'c',nil, 'd', 'e', 'f','g'] 

* 	arr.insert(3, 'ahmed')   #=>  ['a', 'b', 'c','ahmed', 'd', 'e', 'f']    insert between element arrays depending on given index 
* 	arr.pop           #=> g   get last element of array ,with destructive original array
* 	arr.shift          #=>  a     get first  element of array ,with destructiveoriginal  array
* 	arr.delete_at(2)    #=> delete at index 2 
* 	arr.compact         #=> remove any nil from array  ['a', 'b', 'c','d', 'e', 'f','g'] 
* 	arr.uniq                #=>. remove duplicate from array

non-destructive array  :   original array will not change 
* arr = [1, 2, 3, 4, 5, 6]
* arr.select {|a| a%2 == 0  }      #=> [2,4,6]
* arr.reject {|a| a < 4}       #=> [ 4, 5, 6]
* arr.drop_while {|a| a < 2}   #=> [2,3,4, 5, 6]
* m=arr.drop(3)                  #=>  4,5,6 


split and join

```
  string='Hello ,nice to meet you'
```
  
  ```
string.instance_of?Array  #=> false
  string.split.instance_of?Array  #=> true
```

  #change to array and sperate by char including space is also charecter
  ```
string.split('') #=> ['H','e','l','l','o', ,'n','i','c'....]
  string.split('').size #=> 23
```
 
  #change to array and  sperate by space # 
```
  string.split(' ') #=> ['Hello','nice','to','meet','you'] 
  string.split(' ').length #=> 5
```
     
#change to array and  separate by given , comma in the string
```
 string.split(',')  #=> ['Hello','nice to meet you']
 string.split(',').size #=>2
```

#change to array and  sperate by space # 
```
string.split #=> ['Hello','nice','to','meet','you']`
```


#change array to string and depending on given argument in join(',') or without argument  join
```
string.split.join.instance_of?String   #=> true
```

```
array=['Hello','nice to meet you']
array.join(',')  #=> Hello nice to meet you
array.join(',').size #=> 22
```

```
array.join('              ') #Hello              nice to meet you
```

```
array.join('') #=> Hellonice to meet you
array.join('').size #=> 21
array.join #=> Hellonice to meet you
```
     
	
	
**methods**

```

    format to define method  without argument 
```
 def methodname                                                  
 
 end
```

format to define method  with argument 
```
 def methodname(5)                                                  

 end
```
 
 to call method we use
 
```
` methodname(),
```
or
```
methodname(parameter)`
```
 
 
    to change to string
*  to_s     
   to change to integer                  
*  to_i   
   to make  uppercase                       
*  .to_s.upcase          




scan      returns everting will match             
match    return first match

string="ahmedahmed"
puts string.**scan**('ah') ->  ['ah','ah']

puts string.**match**('ah') ->  ['ah']

```

**String interpolation**      
#{variable}
```
k=30

puts "They are about #{k} years old "  #=> They are about 30 years old 
```









