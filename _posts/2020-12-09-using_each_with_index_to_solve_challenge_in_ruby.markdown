---
layout: post
title:      "Using  each.with_index to solve challenge in Ruby"
date:       2020-12-10 04:33:33 +0000
permalink:  using_each_with_index_to_solve_challenge_in_ruby
---

# 


The purpose of this challenge is to learn how to use each.with_index or  map.with_index  enumerator  method , 
In this challenge you will receive two arguments: array and starter index, the task of this challenge is to return 
list of fruit with the given started to index and  skip fruits that have index less than given index in the argument,for example, if you have an array with starter index
```
        skip_fruits(['lemon', 'orange','apple', 'bannana'], 2)
``` 

The  result should be like this:

2:apple
3:banana 

so the easy way to solve this challenge is iterate through given array by using the enumerator method each.with_index,
and using his internal index and item  to get the result we want, we will make an empty array to iterate to put the collected result on it and return it, also we have to use the ternary operator (?:) and check if the given index equal to the internal index 
if yes we will put the first item with index in the new array, also in the same statement we used  (  || )  OR operator  to check  the size of the new array if its not empty we will start to put every element after the starter index until loop around  original array finished, then we will return the new  array


def skip_fruits(arr,resfruit)
         array=[]
         arr.each.with_index  { |item,index| 
         index == resfruit ||  array.length != 0 ? array.push("#{index}:#{item}"): array
  }
	
   array

end

 puts skip_fruits(['lemon', 'orange','apple', 'bannana'], 2)
