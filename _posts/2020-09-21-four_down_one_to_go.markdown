---
layout: post
title:      "Four down, one to go."
date:       2020-09-21 16:49:58 +0000
permalink:  four_down_one_to_go
---


I cannot believe it. I have built four applications...using CODE?! When I say it out loud, it does feel a little weird, but...here we are. Leading up to each project, I generally had an idea of what I was doing. This app (Vanilla JS), was a little different. 

## The What:

What I went with for this project was a pretty simple, MLB manager app for picking the starting lineup for the day’s game. A user (the manager) would open the app, see all the players on the team and relevant stars, be able to filter players by their positions, then add them to the starting lineup. After the lineup is full, they send the data off and the lineup is saved and assigned to the day’s game. From there, the user can view the past lineups as well. 

## The How: 

Although the app is pretty straight forward, this definitely was another beast to work on. I started with the backend by creating the database tables and building the relationships. As I incorporated a has_and_belongs_to_many, there was quite a bit of work needed to be done when creating the joins table. The hard part came as the joins table had a Game_id and then 9 Player_id’s. This was resolved by creating custom forign keys for the players in the lineup table. 

Once the relationships were established and working properly, I went to work on creating and manipulating the DOM. I started with creating an event listener for when the DOM is loaded. Once loaded, the Games, Players, and Lineups were seeded in using a FETCH request and subsequently had JS Class objects made of them as well (that way, I wasn't constantly sending FETCH requests). I created a loop that iterates over each player object and collected their info and created a card. Once the data was generated and assigned to the property node, I appended the card to the DIV that was assigned to hold the player cards. Once those have been generated, the user can go through and create a lineup and select players. If they want to view the previous lineups, I added a button at the top of the page that toggles through the player cards and lineup cards. When the user clicks the lineups, that triggers a function that hides the player cards nodes using style.display = ‘none’ and then displays the past lineups and vice-versa. Once the user selects and submits the lineup, that sends a Post FETCH request to the DB, creates a JS Lineup object, then appends it to the DOM. 

## What I learned:

I guess what I learned the most has to do with javascript asynchronous calls and how each function and variable is called, created, and changed. Many times I had the right code, but was not able to get it working as the objects it was manipulating had not yet loaded or loaded with different data. Javascript is such a fun language to code in but knowing how and when something is loaded in the DOM or JS files are the first step in being able to make a good app, better. 


