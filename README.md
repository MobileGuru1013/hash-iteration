# Iterating Over Hashes With `#each`
## Overview

We'll use iteration to access and manipulate data from hashes.

## Objectives

1. Distinguish iterating over arrays from iterating over hashes.
1. Use `#each` to iterate over a hash.

## Iterating Over Hashes

Previously, we've compared hashes to dictionaries or storage containers. Just like with these storage methods in real life, not only do we need to access our stored information, but we need to utilize it in some way. This is where iteration comes in.

Without iteration, we would have to jump through some serious hoops in order to access every key/value pair of our hash. We would have to know the key of each pair and write something along the following lines:

```ruby
my_hash = {key1: value1, key2: value2, key3: value3}

my_hash[:key1]
my_hash[:key2]
my_hash[:key3]
```

This is painful, tedious, and impractical. What happens when we add more keys to our hash? What happens, as will certainly be the case in some of the programs you will build, when a hash contains hundreds or even thousands of key/value pairs?

Instead, we will use iteration to programmatically access and operate on all of the key/value pairs contained in a hash.

## The `#each` Method and Hashes

The `#each` iterator that we encountered in previous units can also be used to iterate over hashes. When we iterate over arrays, we iterate over one element at a time––each index in an array contains just one object. In a hash however, data is stored in key/value pairs so we will be iterating over those *pairs*. Let's take a look:

```ruby
hash = {key1: "value1", key2: "value2"}

hash.each do |key, value|
  puts "#{key}: #{value}"
end
```

When we iterate over a hash, the `#each` method (as well as any other iteration method you use) yields the key/value pair *together* into the block. Inside that block, you have access to the key *and* the value, and can manipulate either one or both.

Drop into IRB and enter in the above code. You should see this output:

```ruby
key1: value1
key2: value2
 => {:key1=>"value1", :key2=>"value2"}
```

Inside the iteration we have access to both the key and the value. We can `puts` out the key and value of a single pair. The return value, however, is always the original hash. **Remember that `#each` returns the original collection on which you are calling the method.**

Let's try it out together:

## Code Along I: Cruise Ship

**Open up this repo in your text editor to get started. Follow along with the instructions below to get your tests passing**.

The good news is you're on a cruise ship! The bad news is that you're *not* on vacation. You are a cruise ship director and you're selecting the day's lucky ticket winner to the 8:00pm magic show in the super swanky *Blue Room*. The criteria for picking the winner is that this person must be staying in Suite A and their name must start with the letter "A".

### Our Hash

We'll be operating on a hash of passengers that looks like this:

```ruby
passengers = {
suite_a: "Amanda Presley",
suite_b: "Seymour Hoffman",
suite_c: "Alfred Tennyson",
suite_d: "Charlie Chaplin",
suite_e: "Crumpet the Elf"
}
```

Open up `cruise_ship.rb` and you'll see the `passengers` hash, commented out. (It's just there to remind you what the hash we are using looks like.) We have a method `#select_winner` that will take in the passengers hash as an argument. Our job is to code the content of that method such that it returns the lucky winner.

### Our Method

We need to iterate over the passengers and collect the name of the passenger who is staying in Suite A *and* whose name begins with the letter "A". Let's give it a shot:

Place the following snippet of code inside the `#select_winner` method:

```ruby
winner = ""
passengers.each do |suite, name|
  if suite == :suite_a && name.start_with?("A")
    winner = name
  end
end

winner  
```

If you run your tests now, you should be passing.

### A Closer Look

Let's break this down:

* We iterate through the hash using `#each`. We chose `#each` instead of collect because we don't want to collect the key/value pair that contains the winner, just the *name* of the winner. With `#each`, we have the control we need to simply grab the winner's name and set it equal to a variable that we can return later on.
* Inside our iteration, we use an `if` statement combined with the `&&` ("and") boolean operator to check if we have the right suite and if the person in that suite has a name that begins with the letter "A".
* If that condition returns true, we've found our winner! We set their name equal to the `winner` variable and end our iteration.
* Then, we call on our `winner` variable to return the name of the lucky winner.

## Code Along II: Happy Birthday

In this example, we are the managers at Chuck E. Cheese's. Chuck E. Cheese's is a great place to have a birthday party, and there are several birthdays going on here today. Our job is to write a method that operates on a hash of birthday kids and wishes them a happy birthday.

### Our Hash

We will be operating on the following hash that tracks birthday kids and their associated ages:

```ruby
birthday_kids = {
	"Timmy" => 9,
	"Sarah" => 6,
	"Amanda" => 27
}
```

### Our Method

The `#happy_birthday` method is set up to take in the `birthday_kids` hash as an argument. We need to code the method such that it `puts` out to the terminal the following message for each kid:

```ruby
"Happy Birthday #{kids_name}! You are now #{age} years old!"
```

Let's give it a shot:

```ruby
def happy_birthday(birthday_kids)
  birthday_kids.each do |kids_name, age|
    puts "Happy Birthday #{kids_name}! You are now #{age} years old!"
  end
end
```

Here we are using `#each` to iterate over each pair of kids name/age. We are yielding the key/value pair to the block of code between the `do`/`end` keywords by assigning the variables `kids_name` and `age` in between the pipes, `| |`, to be the placeholders for each key/value pair.

Then, we can use those variable names in our string interpolation to `puts` out the actual values they point to at each step of the iteration.

Running the test suite with the above code should show all tests passing. You're ready to move on!

<p data-visibility='hidden'>View <a href='https://learn.co/lessons/hash-iteration' title='Iterating Over Hashes With #each'>Iterating Over Hashes With #each</a> on Learn.co and start learning to code for free.</p>
