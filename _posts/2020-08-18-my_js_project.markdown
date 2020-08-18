---
layout: post
title:      "My JS Project"
date:       2020-08-18 21:16:37 +0000
permalink:  my_js_project
---


It has been very exciting to work on my JS project. I had a chance to apply my knowledge that I earned throughout the JS section to the project. There were many a-ha moments just because I had a chance to use HTML CSS JS all at the same time. Many things made sense when I utilized them all together and it did not when I study them individually. 

In this blog, my focus would be on how I approached to sort and group lists of objects. It was easily accomplished with help of JS built in functions such as filter and find. All the information I was going to sort and group was placed within the current user object. When a user signed in, current user data would be passed into the frontend from the backend. In my case the database was rails activerecord storage. This data includes customer details and customer income and expenses. The following will help to understand the structure of user objects.

```
current_user:
{id: 1, email: "jc_barton@gleichner.com", password: "password", firstName: "Tu", lastName: "Williamson", …}

current_user.expenses:
[0: {id: 1, name: "ut", amount: 52.88, category: "entertainment", date: "2020-01-06", …}
1: {id: 2, name: "odio", amount: 10.87, category: "entertainment", date: "2020-01-23", …}
2: {id: 3, name: "aliquam", amount: 93.68, category: "home", date: "2020-01-18", …}
3: {id: 4, name: "reiciendis", amount: 23.41, category: "healthCare", date: "2020-01-24", …}
...

```

My goal is to have the result shown below.

![](https://drive.google.com/uc?id=1ymUE1oQR3oAwue3zopaqutZyNtasyXqg)

The first step I took was to sort the list of category names in alphabetical order with the sort built in method. Without localeCompare() method, it could have been hard. What does localeCompare() methods is that it compares two strings and returns a number.

```
let orderedCategory = current_user.expenses.sort((a,b) => a.category.localeCompare(b.category))
```

After that, I needed to have a function that returns a list of category names not duplicated. 
Because the expense object can have many categories that are the same and it had many same categories, there were 2 for loops as well as one temporary empty array utilized. 

```
const findUniqCategory = (orderedCategory) => {
            let temp = []
						categoryNames = []
            for (const e of orderedCategory) {
                temp.push(e.category)
            }
            for (const e of temp) {
                if (uniqCategory.length === 0) {
                    uniqCategory.push(e)
                }
                if (typeof uniqCategory.find(n => n === e) === 'undefined') {
                    categoryNames.push(e)
                }
            }
						return categoryNames
        }
```

Now we have a list of non duplicate category names, it would be very easy to group category names by using a filter method that loops through category names while filtering orderedCategory.

```
        const filterCategory = (orderedCategory, callback) => {
            callback
						result = []
            for (const e of findUniqCategory (orderedCategory)) {
                result.push(orderedCategory.filter(n => n.category === e))
            }
						return result
        }
```
I see JS built in methods such as filter and sort very helpful. These methods make code much shorter, clear and easy to understand what is really happening.  

