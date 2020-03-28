---
layout: post
title:      "My First CLI Using an API"
date:       2020-03-28 21:10:10 +0000
permalink:  my_first_cli_using_an_api
---


One down and a few more to go. I finally finished building my first program from the ground up.

After searching the web for a few hours I finally landed on a fun, free API to use for my project. I decited to go with the [PokeAPI](https://pokeapi.co/). This seemed like a fun, easy one to go with but did turn out to a little different than I expected. 

I first expereicned some hangups when I tried to call the API using HTTParty. For this assignment, we were required to call the API, create objetcs out of the material, then return up to three differetnt aspects of the data. The issue I ran into was that this specifc API was so massive, that everything was seperate. The first URL I pulled from was:

https://pokeapi.co/api/v2/pokemon?limit=151

The issue with that was this listed the full 151 pokemon, but there was no other data to pull. What I did find is that all individual Pokemon had thier own API that had their name and stats:

https://pokeapi.co/api/v2/pokemon/1

I knew that if I wanted to use this, it would require some work, but I first needed to figure out how to pull the data and create the objects. I decited to do was find a way to pull from each individual Pokemons API. The info that I pulled was an array of hashes and some with hashes within those hashes. This meant that I needed to do a lot of iteration. Once I was able to pull the proper data, I needed a way to do it 150 more times. As each Pokemon had their own API, I needed to crate a simple loop to add to the end of my URL and add the next number. Here is what I came up with:

```
  def self.create_objects
    index = 1
    while index <= 151 do
      self.info(index)
      index += 1
    end
  end
```

This added each number to my main method which pulled and created the objects:

```
  def self.info(index)
    url = "https://pokeapi.co/api/v2/pokemon/#{index}/"
    info = HTTParty.get(url)
    name = info["species"].fetch("name").capitalize # -- this gets the pokemon name
    full_stats = info["stats"]
    stats = full_stats.collect {|n| n.fetch("base_stat")} # -- this gets the stats
    index = info["id"] # -- this gets the pokemon index
    find_type = info["types"]
    type = find_type.collect {|n| n["type"].fetch("name")}

    @@all_stats += [name, stats, index, type]
    index = Pokemon.new
    self.all.clear
  end
```

As each number was added, it was passed in as an arguement, then the argemnet was interpolatied into my string which held the URL. One it was added, it was passed to the HTTParty which I used to pull the info. All of the info (name, id, stats, etc.) was passed into an array which I used to create each object. This definitly wasn't what I had in mind when startng this project, but I was surprised at how fun it was to figure out. I also learned that it does take some time for 151 different objects to be created at once. 

Once the objects were created it was as simple of iterating over all my objects and pulling out the needed stats and putsing them for users to see. Coming into this project, I was super nervious as I had not built anything from the ground up before but this taught me so much more than I had throught it would and I am looking forward to continung to built this out. 



