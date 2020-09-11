---
layout: post
title:      "What is Redux?"
date:       2020-09-11 02:54:27 +0000
permalink:  what_is_redux
---


You really do not need redux if you have only a few components in your react app and when there is not much going on with your states inside your components. However, if you are building an application that will be growing into a one big application, it can quickly get complicated and impossible to manage all different kinds of states inside your components. However, with Redux - a state management system, no matter how big and comlex your software is going to be, it still fits in the same architecture. That is where you need Redux. To me, learning about Redux was not easy as how Redux manages its store. I had to go through a number of resources and video tutorials to grasp the idea of what really is Redux and how it works. But, I will try my best to describe it in this blog. 

![](https://drive.google.com/uc?id=1MgZHalZyE_Ok6TabpX2fW4KMHczAEDY-)

The diagram above is showing the workflow of Redux. It starts with the store. This Redux store keeps all the data throughout components in a single javascript object. It does not mean that the Redux store takes a lot of memory because it has a lot of data inside a giant javascript object. Instead, the store manages all these data in an efficient way. Now we know about the store. How can we connect the store with indicitual react components? This is where providers and containers come into play. The provider acts as a bridge between the store and containers. In other words, it makes the store available to all containers. The following is how the syntax works an index.js file.
```
ReactDOM.render(
  <Provider store={store}>
    <App />
  </Provider>,
  document.getElementById('root')
```
We now have all the aspects of redux available to our react part of the app. This transition takes place in the containers. If you remember `mapStateToProps` and `mapDispatchToProps`, you can utilize them in the containers to make the store's states and functions available as Props to any of your react components. That means anytime the store gets updated, your components using the store data will be rerender automatically. 

So far we have talked about how store data gets to react components and when store data changes React components re renders automatically. What we have not talked about is how store data changes. This process goes through something called actions or action creators. Most of the time actions are going to be user events such as deleting items or clicking add buttons. In order to store data to be changed through actions, it needs a function called reducer. The reducer takes an action as parameter and decides what changes need the store data. 

Learning redux feels overwhelming first but once you get through figuring out how it works, it makes your life much easier. Of course it will not go to your next door grocery store to get bread for you, But it will centralize all of your data in one place and make it available to all of your components so that you no longer have to go through every single component to pass down one single data.

