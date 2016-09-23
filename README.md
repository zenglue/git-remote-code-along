3.times do
LuLz

OO overview lecture notes

"objects are all the data and logic needed to accomplish a goal"

"object orientation is ability to bring metaphors to code" abstract real world objects into code

"objects are data structures to pass around"

"Class is blueprint and factory" schematic and manufacturer

every instance of an object has a uniq address or object_id

String.new = "something_in_double_quotes"

only thing you can do on objects in Ruby is call methods

name=(baby_name) #writer method is name=()
@myname = baby_name #casting or hoisting the local variable(name=) to the instance variable
end

local variables scoped to method

attr_accessor is useful for consolidating reader and writer methods(meta-programming, writes code for us)

#@instance variables belong to instance object (internal state)

#$ never use global variables, should only be used by interpreter

@@all vs @all is used to store all instances rather than a particular instance (class variable)
@@all is mostly same as ALL except ALL is not changable i.e. reset_all! method with @@all = [], with ALL its ALL.clear

implicit vs explicit receiver
self.method = explicit_receiver
self = class Name
method = implicit_receiver(self is implicit_receiver)

local variables always take precedence to method calls

:: is a scope accessor (name_space)

initialize routine is not required for class body

possible to operate on an individual object by name (name.method)
