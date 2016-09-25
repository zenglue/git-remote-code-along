3.times do
LuLz

#OO overview Video Review notes

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

@instance variables belong to instance object (internal state)

#$ never use global variables, should only be used by interpreter

@@all vs @all is used to store all instances rather than a particular instance (class variable)
@@all is mostly same as ALL except ALL is not changeable i.e. reset_all! method with @@all = [], with ALL its ALL.clear

implicit vs explicit receiver
self.method = explicit_receiver
self = class Name
method = implicit_receiver(self is implicit_receiver), whenever receiver is not explicit, implicit receiver is always self

local variables always take precedence to method calls

:: is a scope accessor (name_space)

initialize routine is not required for class body

possible to operate on an individual object by name and only that object (name.method) #singleton method

self.find_by_name(name) is a class finder

#Object Properties Video Review notes

ruby #method look up chain
instance itself > class > module > object > kernel > BasicObject (no_method_error when not found)

@instance variable represents internal state using writers and readers((either through manual methods(name= & @name reader) or attr_accessor(Class Macro))

class body only gets read once, self in the body (not in method) is the class itself

define_method("arg") do, defines a method
attr_accessor manual ex:
class Dog

  def self.define_properties(props)
    define_method.each do
    #defining the reader
      #puts "You called #{prop}"
    #exposes instance variable
    instance_variable_get(:"@#{prop}")  
    end
    define_method("#prop}=") do |arg|
    instance_variable_set(:"@#{prop}"), arg)
  end
end

self.define_properties([:name, :breed])
end

object relationship "has"

class Owner
  attr_accessor :name
end

fido = Dog.new
fido.name = "Fido"

avi = Owner.new
avi.name = "Avi" #=> setting @name to a primitive
fido.owner = avi #=> setting @owner to a mature object
or
class Dog
attr_accessor :owner
end

fido.owner = avi

-- at this moment Avi needs to be informed he has a new pet
def owner=(owner)
  @owner = owner
  owner.pets << self # reciprocates relationship
end

#Object Models Review

understand self

instance scope/class scope (@all, @@all) class instance variable

def self.find_by_something(something)
reslut = object_name = object_name if object_name == something

--last line of code is what is returned
--iterate through @@all.detect {|somethin| somethin.name == name}
--@@all.each_with_index |object, i|
  counter = i if object.something == something

Finders
--detect/select/find/find_all

def self.create --custom constructor (adds more functionality to initalize, offers flexibility unlike intialize instance)
x = self.new
x.save
x
end

def self.new_from_hash(hash)
x = self.new_from_hash
x.name = hash[:name]
x
end

#Object Orientation and Scraping Review

abstraction is about specificty not vagueness

bad idea to name anything class, klass

--Class Custom Constructor allows data sources or logic or environments that leave initialize alone, so it can be bare bones, extends functionality and returns Object.new
self.new_from_url(url)
 object = Object.new

 properties = ObjectScraper.new(url)
 properties.each do {|k,v| animal.send("#{k}=", v)}  --#send calls a method, mass assignment pattern
 end
 object
end

refactored

self.new_from_url(url)
  Object.newtap do |object|
    ObjectScraper.url(url) each {|k,v| object.send("#{k}=", v)}
    end
  end
end

self.new_from_database(row)
  Object.new.tap do |object| --taps into block, and automatically returns Object.new
end
