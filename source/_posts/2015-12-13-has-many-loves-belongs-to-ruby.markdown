---
layout: post
title: "My Heart: Has Many Loves; Belongs to Ruby"
date: 2015-12-12 14:21:31 -0500
comments: true
categories: 
---

For my blog I decided to write a little about the has many / belongs to relationships between classes. I decided to explore this concept in the context of a side project that I've been tinkering with. I'm trying to build an app that should ultimately predict the outcome of NHL games, based on a variety of factors. This should include such factors as who the starting goalies will be, how the teams have performed against each other historically, whether the opposing team has a player who repeatedly scores against the specific opposing goalie, and so on. The app is called the Hockey Oracle and it is definitely going to take the fantasy sports market by storm.

At its most basic level, an individual player belongs to a team. We give the player a `team` `attr_accessor`, and then subsequently set that team attribute to an instance of the `Team` class. On the other end, a team has many players. We enact this relationship by giving teams a goalies or players property upon initialization that is set to an array of goalie or player instances. We add goalies and players to their respective arrays by defining an instance method within the team class called `#add_goalie` or `#add_player`.

Anyhoo, I decided to start by setting up three basic classes: `Goalie`, `Skater`, and `Team`. Goalies and Skaters (aka simply Players) belong to a team, while each instance of the `Team` class 'has many' goalies and skaters. I also created a parent class, `Player`, which I will use for common methods that goalies and skaters can both inherit.

So let's first take a look at our Goalie class:

```ruby
class Goalie < Player
	attr_accessor :name, :team, :reflexes, :athleticism, :puck_control

	# these parameters might be good representing a hash with more specific attributes as keys and a number rating as values
	def initialize(name, team=nil, **args)
		@name = name
		@team = team

		args.each do |property, value|
			self.public_send("#{property}=", value)
		end

		if team
			team.add_goalie(self)
		end
	end

	def team_name
		self.team.name
	end
end

```
I'm doing some fun Steven-inspired meta-programming in my initialize method, which lets me take in a hash of the goalie's attributes and corresponding ratings as args. Each attribute gets set to an integer corresponding to their actual perceived skill in that area based on scouting reports. I stole the attribute designations from NHL 16. But I digress. 

The first two arguments are more important for our discussion right now: name, which is required, and team, which is optional and will be nil if you don't feel like setting it right away, or the goalie is a free agent or something like that. But let's focus on team. Assuming the goalie has a team, which would be an already-created instance of the Team class, and also assuming you pass it in as an argument instead of letting it remain as nil. 

So how do we get a goalie associated with a team? Well, first we had to make sure our Team class was set up. This meant giving team objects their own proper initialize method:

```ruby
class Team
	attr_accessor :name

	@@roster_count = 0

	def initialize(name)
		@name = name
		@skaters = []
		@goalies = []
	end

	def add_goalie(goalie)
		@goalies << goalie
		goalie.team = self
		@@roster_count += 1
	end
	
	def add_skater(skater)
		@skaters << skater
		skater.team = self
		@@roster_count += 1
	end

	def goalies
		@goalies.map do |goalie|
			goalie.name
		end
	end

	def skaters
		@skaters.map do |skater|
			skater.name
		end
	end
end
```

I set up a class variable, `@@roster_count`, so we can keep track of the total number of players on a given team, which will come in handy later. Then in my initialize method for `Team`, I added empty arrays for skaters and goalies. The next thing is, how do we get a goalie to be on a certain team, and enact that relationship? Let's write an `#add_goalie` method that takes in an argument of an already-created instance of goalie. 

```ruby
	def add_goalie(goalie)
		@goalies << goalie
		goalie.team = self
		@@roster_count += 1
	end
```

Once we get that down, we can create team objects. Say we want to make the New York Rangers.

```ruby
rangers = Team.new("New York Rangers")
```

Now, let's create our new goalie. Superstar Henrik Lundqvist, of course. I'm not going to worry about his specific attributes like reflexes and puck control right now, since I just want to focus on bringing him into existence as an instance of the Goalie class, and adding him to the Rangers.

```ruby
lundqvist = Goalie.new("Henrik Lundqvist", rangers)
```

Nice, we passed in our team object, `rangers`, as the argument for Lundqvist's team. Now 'lundqvist' belongs to one team, and that team can have many goalies. 

The reason this works is because we are actually calling the `#add_goalie` method on the team argument at the moment that we initialize a new goalie. That method gets called on team, the goalie is shoveled into the team's goalies array, goalie.team is set to self (since self is the team in the context of that instance method), and we also make sure to increment the `@@roster_count` by one. The methods for adding a skater looks exactly the same, except for different naming of variables, and we run the `#add_skater` method in the initialize for that class as well. 

In this way, I've set up the preliminary relationship of my hockey prediction app, where teams have many skaters and goalies, and are able to keep track of them and add new ones with a simple adding method, and goalies and skaters belong to a specific team, which can be set based on the code in the two initialize methods for those two classes when each object gets created, assuming you pass in a instance of team as one of the arguments (but you don't have to, since it's easy to set it later). 

There are a ton of other aspects to this complex interplay between related classes, but I think this gives an overview of how the relationship gets established at the most basic level, and in the context of my own app that I'm working on. I am looking forward to expanding on this as I work to build out my software, and explore the multitude of ways that related classes can reference each other and work together.

Thank you for listening! 

{% img center https://nesncom.files.wordpress.com/2014/01/835735616-1.gif?w=1136&h=638 %}



