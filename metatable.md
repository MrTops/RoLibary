# Metatables
In Roblox there are times when you need to create custom objects, this could be a very abstract container for something, or a useful controller with tons of *methods*, in this tutorial we will talk about how to use *metatables* and how to use *methods*, so first of all let's define some words. A metatable is just a type of table which connects two tables together. A method is a function which is part of a metatable. Ok now that we know what those mean how do we create a metatable? Well metatables live in modulescripts. If you do not know what a module script is then please go view that tutorial as I will not go over it here. So here is the basic metatable.

```lua
module = {}
module.__index = module

function module.new()
  return setmetatable({},module)
end

return module
```

ok so let's break this down, so we have the default module, then we have module.__index. That just means when we create a metatable with it, if we don't find something in the first table we go look there, without this methods won't apply. then we have a function called module.new(), this returns a metatable. this is how we create a member of our class, a member is just something that is created from this class. So we use the global function "setmetatable" which just creates a new metatable from two table inputs.
So how do we add a method to this well let me give an example

```lua
module = {}
module.__index = module

function module.new(name)
  return setmetatable({
    Name = name
  },module)
end

function module:returnName()
  return self.Name
end

return module
```

ok so not much changed however we added "module:returnName()", this is a method, a method is defined by the ":" syntax, it's like "." however we get access to the "self" value. Which I'll explain after we create a member of that class

```lua
local class = require(thatModule)

local member = class.new("Hello, world!")
print(member:returnName())
```

``
Expected Output:
Hello, world!
``

as you can see we created a member then called the function "returnName" using the ":" syntax. this returned the .Name value from the object of which it was called. You can also edit data in "self". I could go over loads of use cases but I think it's best for you to experiment with that I've given you. DevTops