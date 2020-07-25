---
layout: post
title:      "Fantasy Pick-Em an a Rails App"
date:       2020-07-25 22:49:26 +0000
permalink:  fantasy_pick-em_an_a_rails_app
---

​
Unlike my previous bouts with fantasy football, my first ever Rails app was a victory...I think.
​
​
Looking back at the start of my coding journey, I am shocked and proud to be where I am now. Not like a pat on the back, but really a reflection on the idea that what I have accomplished, anyone can do if they out their minds to it. And being able to build something out of nothing is SO COOL! But I am sure you all have not click on this blog to talk about how amazing this is. On to what I think made the app what it is:
​
​
## The Project:
​
Every year my close friends and I play fantasy football. With that, we also have a pick-em pool. For those who do not know, a pick-em consists of picking a team that you will think will win each week. If your pick wins, you move onto the next week. If not, you have to buy back in.
​
This app consists of just that. Users create an account, have access to a full NFL schedule, then they can pick a team that week. Users can only make one pick per week. And once they pick a team, they can no longer pick them for the remaining season.
get the
​
## The Core:
​
The app itself consists of seven controllers, six models, and six tables in the database. This started off with only three of watch but quickly changed as I added more to the application. In order to display the NFL schedule without manually seeing the DB with all 256 games, I used the API (MYSPORTSFEEDS) to get this data. I created a method to search the API data and create a game object and save it into the database. The game consisted of the two teams playing, date, victor, and time data. Moving on from that, I needed to find a way to make sure that users could only submit one pick per week. I was initially able to achieve this using a custom validator, but quickly ran into some issues as using normal Date ruby methods would not since a week needs to consist of a Tuesday - Thursday night rather than a Monday - Sunday. To achieve this, I created a Week table and had a custom Start of week and End of week. I then created my pick validator using a range. 
 
## Take-aways
 
There were three things that really helped me through this project. 
 
1. Map out everything - This helped a TON! I first spent time in a notes document drawing out the models, relationships, routes, etc.. figuring out early on exactly what you want to happen from login to logout and everywhere in between is so important. 

2. Work in the console - Working within a rails console helped so much as I began working with the code. I was able to manipulate code, test methods and more. If I received an error, working in the console made it easy to troubleshoot and move forward. 

3. Knowing the code - This may seem obvious, but as apps get bigger and more code is added, knowing what each bit of code does is key to understanding how everything works together.  It did mean having to go over each file many times to make sure I had a firm understanding of everything, but it helps overall. 


## Conclusion

Overall this was such a learning experience and I loved every bit of it. Although the project requirements are complete, this will be something that I will continue to work on and grow. 

Never Stop Coding 



