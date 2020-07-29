---
layout: post
title:      "Rails Portfolio Project"
date:       2020-07-29 17:42:50 +0000
permalink:  rails_portfolio_project
---


I would say that all the knowledge acquired throughout Module 13 had prepared me very well for this final project. The most crucial part of the project was planning, especially building a schema diagram. It involved lots of thinking and going back and forth. The following picture shows relationships between tables that I have used for the project. 

![](https://i.imgur.com/kNYJz6il.png)

Most of the relationships were one-to-many. Depending on whether it was parent or child table, has_many and belongs to statements were placed on files in the models directory.  Those relationships did not require any additional table connecting between them. However, many-to-many relationships were required to create one additional table including two foreign keys of parent tables.

After coming up with the schema diagram, I moved on to generating migrations, controllers, models, and views. Basically, that was the end of my planning for the project.

In the main content of my project, I started at creating ```helper_method``` and ```before_action``` for the user verification.

![](https://i.imgur.com/y52ETm3l.png)

The helper method - ```current_user``` is finding a current user logged in. If any user logged in, the session will have the user's id saved in and the user can be found easily by saying ```user.find_by```. About ```before_action```, it checks if the user logged in. Because ```before_action``` is located inside the application controller, it is applicable throughout the project scope. This means, unless you place ```skip_before_action``` in the controllers, it will check if the user is logged in before every action. BTW, you can use ```skip_before_action``` on a certain action or actions by having syntax as follows ```skip_before_action, only: [:create, :new]```. One additional thing to mention here, in the application controller, you can add ```add_flash_types``` to show flash messages, alerts or notices. In order to render the messages on the web, you can use the following code in the layout view. In this way, flash notice will show on any page you are currently on:

![](https://i.imgur.com/mUx3Dhnl.png)

Since we are on the login topic, I would like to share my experience with Google OAuth2 login capabilities. I had to look up many resources in order to complete this part of the project because steps to follow were somewhat complicated. At first, going to google developer website to create a client id and client secret was necessary before moving on to developing it on a code editor. One thing you cannot forget is that you need to enter your callback URI on google developer page, which is shown in the picture below.

![](https://drive.google.com/uc?id=1hZ00giySlg9_-9wBE3b7QPfvie81_B1V)

Once you are done with getting your credentials - client id and client secret from the google developer site, it is important to create a new file called .env on the highest level of directory. The .env file is where you can enter your client id and secret. Do not forget to add a gem called 'dotenv-rails' along with omniauth gems gem 'omniauth', gem 'omniauth-google-oauth2' gem 'omniauth-rails_csrf_protection.' The .env file is not accessible without the gem. Same is true with omniauth gem. It does not work without google omniauth gem. The next step would be to build a class level method in the user model. 

![](https://drive.google.com/uc?id=1YlQ4c8rp6xXiYxsLvlNQ6dY5Nx8tuI6D)

This method takes one argument which is the highest level of key of hash called request. The request hash possesses information that google can send to rails. You can get your user username, password and username from this hash. 

In addition, you need to have middleware to handle our requests to log in with Google.  

```
Rails.application.config.middleware.use OmniAuth::Builder do
    provider :google_oauth2, ENV['GOOGLE_CLIENT_ID'], ENV['GOOGLE_CLIENT_SECRET']
end
```
FInally, to process the response that we received from Google, we need to have an action created in the session controller where you can use the method in the user model to create or find users. You can assign session[:user_id] after the user found or created.

```
    def omniauth
        user = User.from_omniauth(auth)
        if user.valid?
            session[:user_id] = user.id
            redirect_to new_project_path
        else
            redirect_to signin_path, alert: 'Could not log in with your google account'
        end
    end
```




