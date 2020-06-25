---
layout: post
title:      "Sinatra Project"
date:       2020-06-24 23:47:48 -0400
permalink:  sinatra_project
---


This project was a great way of an introduction to a web application framework. It was fun and I learned so much about a web application framework. Because the lab was test driven, it was very easy to navigate and easy to follow it step by step. 

I started with a home page. It was a traightworfard task - I used the get '/' method and rendered index.erb in that method. However, there was a little feature I wanted to add, which was when any user logged in, the home page would not appear. Instead, it will redirect the user to the current user's page. In order to have this feature, I had to check if a user was logged in by having the following code: if Helpers.is_logged_in?(session), redirect "/users/#{Helpers.current_user(session).username}". 

Even though making the home page was an easy task, I had some challenges with a signup page. It took me a little while to figure out what happens if a user does not fill out one of the username, email, or password fields. Yet, it was accomplished with empty? method. For example, if a user leaves a username blank, signup page will redirect to signup page and it will ask a user to enter all the information again.

Another challenging part of this project helped me to understand the authentication. When a user creates a password (string), sinatra turns it into salted and hashed version of it and stores it in the database. Later, if the user wants to sign in into his or her account, authentication will turn the user's entry into salted and hashed version and will match it in the database. Since we are in a login topic, I would like to mention how an user logs out. It can be done by method called clear. Basically, it clears the session just like this session.clear in a logout method. Speaking of session, session is a special hash to store current user's information. It needs to be enabled in the configure method. 







