# Datatypes

This tutorial goes over something that's more general coding rather than Roblox specific tutorials.

*Datatypes*, the basis of coding. A Datatype just means a type of data. In Lua, the language that Roblox scripter's use, there are 5 basic datatypes. These are *ints*, *string*, *float*, *arrays*, and *tables*. Now time to explain them all. Int means a whole number, there is a limit but it's 179769313486231570814527423731704356798070567525844996598917476803157260780028538760589558632766878171540458953514382464234321326889464182768467546703537516986049910576551282076245490090389328944075868508455133942304583236903222948165808559332123348274797826204144723168738177180919299881250404026184124858368, so you *probably* won't hit it. A string means a word, so "hello world" is a string. A float is a number but can be 1.5 where a int cannot be that. A array is just a collection of items. A table is a key-pair, you can think about it like a dictionary where a word has a meaning associated with it.

Ok so how do we use each datatype?
```lua
local myInt = 10
local myString = "Hello, world!"
local myFloat = 1.5
local myArray = {
    "Apple", "Pear", "Grape"
}
local myTable = {
    ["Apple"] = 10,
    ["Pear"] = 5,
    ["Grape"] = 7
}
```
So let's break it down line by line. So first we declare a int, to do that just type in the number. In Roblox we usually use local before the name. For the string the use quotes. For float we use a decimal number. For the array and table we use enclosing "{}"'s. In the array we have data separated by a ",". The data there can be any type. In the table we have "["key"] = value", I'll explain key's and values later.

### Using Ints (and Floats)
Like you would have thought, you can do math! So I'll just go over the operators
```lua
local x = 10
local y = 5
x + y --15 Addition
x - y --5 Subtraction
x * y --50 Multiplication
x / y --2 Division
x ^ y --100000 Powers
```

### Using strings
Strings have some useful attributes that I won't go over here, but one that you'll use alot of is concatenation, or putting two or more string together
```lua
local message = "Hello,"
local message2 = " world!"
print(message..message2)
```

### Using Arrays
Arrays are pretty simple. They just contain data that are at *indexes* an index is just a position in an array, they start at 1.
```lua
local myArray = {
    "Apple", "Pear", "Grape"
}
print(myArray[1]) --Apple
print(myArray[2]) --Grape
```
I will go over arrays more in a separate tutorial as they are a simple but offer a ton of functionality.

### Using Tables
Tables are like arrays except their indexes are strings. You can also use '.'
```lua
local myTable = {
    ["Apple"] = 10,
    ["Pear"] = 5,
    ["Grape"] = 7
}
print(myTable["Apple"]) --10
print(myTable.Apple) --10
print(myTable.Grape) --7
```
