---
layout: post
title:      "React & Redux, the Perfect Marrige"
date:       2020-11-25 22:12:52 +0000
permalink:  react_and_redux_the_perfect_marrige
---

### And the End of My Journey at Flatiron School



For my fifth and final project here at the Flatiron School, I made a web application that allows a user to send photo release forms to new clients. At the time of me writing this, the email portion is still a work in progress. I am using a library called EmailJS to achieve this but have been running into some hiccups around that bit. 

All that to say, I started the app by creating the backend repository. As this has been my second Rails backend and fourth app working with Ruby, this was done quickly. There are currently two Models, Users and Release Forms. Although I have not extended the application to have user accounts, I went ahead and added it in anyways to allow for this feature to be added in the near future. With that, Users have many Release Forms and a Release Form belongs to a User. I found this cool computer app called Postman that allows me to send requests to my backend quite easily. I used this app to verify the relationships worked as well as my strong params. 

Now that the backend was set up and my API was functioning, time to move into my frontend. This was using the beautiful command, npx create-react-app . Once that finished, I started with setting up a way to get my data from my backend once the app loads. This process completed using the React lifecycle component, componentDidMount. This function is provided by my class based, App component. Once the App component is mounted to the DOM, this sends a fetch request to my backend to get and store my data. 

Before I could store the data, I needed to create a store to...store it. This is where Redux comes in. By creating Reducers, I am able to store and manipulate the apps global state. Using the amazing createStore function (given to us through react-redux), I passed in my rootReducer and thus, my store is active.  Through creating an action to dispatch and using the middleware thunk, I was able to send asynchronous requests to the backend, get my data, and store it in the global state by using the previous App function, componentDidMount. 

After saving the data, I created a route (using React Router) that rendered a container displaying some general information about each form as well as a search bar to filter the results. The search bar initially had its own component state, but since I needed that state to be accessed by the sibling component, I moved the state to the parent container, then passed that state into the child as a prop. 

I proceeded to set up a controlled form which allowed users to enter in client data, preview a PDF document that has that data passed on, then submit that form to the database using a dispatch. The action that gets dispatched sends a post request to the backend, saves the new form, then returns that object. Using Router props, we can pass in the history and then call history.push which allows us to route to a new URL and display the component of the single form that was submitted. 

Overall the app runs very smoothly thanks to react and the limiting of requests to the server. By loading the information once, this allows the app to switch, search, and display components with ease. 

What a journey this has been and so excited for what's to come! Many thanks to everyone at Flatiron for their help, everyone at AQ that was there to help debug my code, just to find that I was missing a period or capital letter. 

