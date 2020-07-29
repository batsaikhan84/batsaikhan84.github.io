---
layout: post
title:      "Ruby CLI Project"
date:       2020-07-29 17:51:51 +0000
permalink:  ruby_cli_project
---


It has been a month since I started my learning to code journey with Flatiron School. My experience and learning outcome has been great. Flatiron school provides a very easy to navigate web learning platform. It has an amazing support staff. I feel very lucky to be in the program.

However, my main goal of posting this blog is to share my experience with my first independent project.



In this short blog, I would like to talk about a couple of challenges that I encountered during my CLI gem project. 

A CLI gem project is the last individual project I am completing in a Ruby session. As we all know, gem is the bundle of codes put together and it offers some functionality to a ruby program. Also, it is a library built by people in the ruby community. 

In the process of building my gem project, there have been a number of challenges. Scraping from the web was one of them. 

At the beginning, my nokogiri was not working in an Atom developer tool. It turned out I had to install xcode command line tools. This can be accomplished by typing XCODE-SELECT --INSTALL in the command line. After that, you can install nokogiri by typing gem install nokogiri. This might be irrelevant to any coding part of the project. But, if anyone is having a hard time with nokogiri not working. This might help. 

The next part where I got stuck and needed to do some research was getting URL from href attribute in a HTML file. Yet, it can be easily done by typing attr(“href”).value. For example, major.css("a").attr("href").value. I think this is nokogiri format. Therefore, all I had to do was memorize the format in order to get the url from the HTML file. 

Also, It was an important lesson for me to understand when to use each and collect method when iterating over. There was a header in the HTML file which had a long white space before and after. I could not get rid of that white spacewhile iterating through using each method. The reason why I could not get rid of it was that I used the wrong iteration. I had to use the collect method so that it can return changes vs each method returns original items. 



I am keeping it short because this is my first blog ever written in my coding journey. In the near future, I hope I will have many more helpful blogs like so many blogs that helped me throughout completing my project.
