---
layout: post
title:      "My React-Readux Project"
date:       2020-09-11 06:02:15 +0000
permalink:  my_react-readux_project
---

 This blog is for my last project. I have made an application that manages user forms such as user login and logout and registration by using react and redux technologies. For the backend, it is powered by rails API. It takes me a while to figure out how to implement user authentication that communicates with react and redux. However, it was done by using a session controller and it worked great. Other than that, the backend setup was not that complicated. During the setup, the user model and all the necessary controllers are created. There is one special model needed to be done in order to send current user data to the frontend. I think it might be enough about the backend and I want to focus on the frontend specially packages called thunk and axios.  

To create a new application, I ran a command called `npx create-react-app` followed by a new application name. After the setup was complete, all the packages needed in my application were installed such as `redux`, `react-redux`, `redux-thunk`, and `react-router-dom`, `axios`. Two of the packages are special among all the packages I installed. The first one is Axios. 
```
Import axios from ‘axios’
```

I am using Axios for requesting an API endpoint because it requires less code and is easy to read. Its syntax is the following.
```
       axios.post('http://localhost:3001/registrations', {user: {
                                                           email: state.email,
                                                           password: state.password,
                                                           password_confirmation: state.password_confirmation,
                                                           name: state.name}}, {withCredentials: true})                                             
       .then(response => {
           if (response.data.status === 'created') {
               dispatch({ type: 'USER_REGISTRATION', user: response.data.user})
           }
       })
       .catch(error => {
           console.log('registration error', error)
       })
 
```
In addition to its simplicity, axios automatically `stringifies` the data when sending a request. 

The other special package I have mentioned earlier is Thunk. It is a middleware and used to handling async action creators in applications. This method allows us to wrap dispatch in a function and to call it later. This way we can fit any API endpoint request to synchronous change in our application. 

```
Import thunk from ‘redux-thunk’
Const state = createStore(userReducer, applyMiddleware(thunk))
```
This is the setup in index.js. 
The following is the action creator that is making a post request to the API endpoint. 

```
export const fetchUserRegistration = (state) => {
    return (dispatch) => {
        dispatch({ type: 'LOADING_USER'})
        axios.post('http://localhost:3001/registrations', {user: {
                                                            email: state.email, 
                                                            password: state.password, 
                                                            password_confirmation: state.password_confirmation,
                                                            name: state.name}}, {withCredentials: true})                                              
        .then(response => {
            if (response.data.status === 'created') {
                dispatch({ type: 'USER_REGISTRATION', user: response.data.user})
            }
        })
        .catch(error => {
            console.log('registration error', error)
        })
    }
}

```
Now, we have our dispatch method wrapped in a function, we can implement to fit in any synchronous changes in containers `export default connect(null, { fetchCurrentUser })(App)`. I did not create a container directory but my App.js file is acting as a container because of ease in distribution of state and function props to other components.

