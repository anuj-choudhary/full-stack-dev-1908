## Promise API

ES6 introduced the promise API which simplified callbacks and error handling within callbacks. 

It is used in many libraries where asynchronous coding is required.

**But what is a promise?**

A Promise is just an object which represents the eventual completion oe failure of an asynchronous operation. 

For example, when you make a request to a server, it could be successful and return the value or unsuccessful and return an error. When can then use the result of the promise to preform different operations. 

**Creating a promise**

Lets say you have a function called bonus that checks your monthly performance and your bosses mood. 

If your performance was `>50` and your boss was `"Happy"` you get a `bonus = performance * 10`. Otherwise you get no bonus and a reason. 

However in either case you are still promised a result. 

```javascript
const bonus = (performance, mood) => new Promise((resolve, reject) => {
    if(performance > 50 && mood === "Happy"){
        let totalBonus = performance * 10;
        resolve(totalBonus);
    }
    else{
        let reason;
        if(performance <= 50){
            reason = "Terrible performance";
        }
        else{
            reason = "Boss was in a bad mood!";
        }
        reject(reason);
    }
});
```
**Consuming promises:**
Here we actually use the promise function we made and if the promise is successful or resolved `then` we do something useful with the result like printing it to the console or we `catch` the error and print the reason we didn't get the bonus.

```javascript
const bonus = (performance, mood) => new Promise((resolve, reject) => {
    if(performance > 50 && mood === "Happy"){
        let totalBonus = performance * 10;
        resolve(totalBonus);
    }
    else{
        let reason;
        if(performance <= 50){
            reason = "Terrible performance";
        }
        else{
            reason = "Boss was in a bad mood!";
        }
        reject(reason);
    }
});

let performance = 100;
let bossMood = "Happy"

bonus(performance, bossMood)
.then((response) =>{
  console.log(`My bonus for this month was ${response}!`);
})
.catch((error) =>{
  console.log(error)
});

```
**Chaining Promises:**

Lets say you wanted to do something else if you got a bonus. For example you would want to add some of it to your bank account.

You can make another 

```javascript
const bonus = (performance, mood) => new Promise((resolve, reject) => {
    if(performance > 50 && mood === "Happy"){
        let totalBonus = performance * 10;
        resolve(totalBonus);
    }
    else{
        let reason;
        if(performance <= 50){
            reason = "Terrible performance";
        }
        else{
            reason = "Boss was in a bad mood!";
        }
        reject(reason);
    }
});

const addToBank = amount =>{
    return Promise.resolve(`You added ${amount} to your bank account`);
};

let performance = 100;
let bossMood = "Happy";

bonus(performance, bossMood)
.then((response) =>{
  console.log(`My bonus for this month was ${response}!`);
  return response;
})
.then(addToBank)
.then((response) =>{
  console.log(response)
})
.catch((error) =>{
  console.log(error);
});
```

You could chain multiple promises just like this!

There is a lot more to learn about the promise API which you can read about here [https://www.promisejs.org/](https://www.promisejs.org/). This website is just about the promise API! 

Also scan through the MDN docs [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise) 

## Axios and making HTTP requests in ReactJS

Front end applications that don't communicate with server seems a bit redundant. So lets connect our React Apps to a server. 

While we could use the good old `XMLHttpRequest`, its lack of inbuilt support for promises makes this a less than ideal option. 

Another viable option is the [Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch) introduced in ES6 and expanded in ES7. 

However I have chosen to go with the [Axios](https://github.com/axios/axios) package because of its various advantages. If you want to know why I prefer Axios over Fetch, [this medium post](https://medium.com/@jeffrey.allen.lewis/http-requests-compared-why-axios-is-better-than-node-fetch-more-secure-can-handle-errors-better-39fde869a4a6) explains it perfectly.

**Installing Axios:** 

`npm install axios`

**Writing your first request with Axios:**

Lets try to create an axios request in an App by using a randomuser generator api:

[Codesandbox](https://codesandbox.io/s/axios-7b6qc)

```javascript 
import axios from 'axios'

ComponentDidMount(){
    // This is placed inside 
    axios.get("https://randomuser.me/api/?results=10")
    .then(res => {
      const data = res.data.results;
      console.log(data);
      this.setState({
        data: data
      });
    })
    .catch(error=>console.log(error))
}
```




Lets try and get the local weather using the [FCC weather API](https://fcc-weather-api.glitch.me/).

```javascript
const axios = require('axios'); // This is an alternative to import statements, don't worry about it!
or
import axios from 'axios'


axios.get('https://fcc-weather-api.glitch.me/api/current?lat=35&lon=139')
    .then(response => console.log(response))
    .catch(err => console.log(err));
```

The most powerful part of Axios it the ability to pass request configuration through a JavaScript object literal.

```javascript
const axios = require('axios'); 
const requestParam = {
        method: 'get',
        url: 'https://fcc-weather-api.glitch.me/api/current',
        params : {
            lat : 12.9716,
            lon : 77.5946
        }
}
axios(requestParam)
     .then(response => console.log(response))
     .catch(err => console.log(err));
```

### Using Axios with React

The ideal place to place a http request is usually in `componentDidMount()`.

This because all your components are already mounted into the DOM and are waiting to receive some data. 

You could also do it in `componentDidUpdate()` after some user input. 

But **beware** using `setState` within `componentDidUpdate()` could cause an infinite loop since it once again invokes `componentDidUpdate()`.

To prevent this, make sure you are passing different props like this:

```jsx
componentDidUpdate(prevProps) {
  // Typical usage (don't forget to compare props):
  if (this.props.userID !== prevProps.userID) {
    this.fetchData(this.props.userID);
  }
}
```

Example weather app is located here 
[Codesandbox](https://codesandbox.io/s/axios-weather-api-f2ct4)


Axios 
```javascript

// Make a request for a user with a given ID
axios.get('/user?ID=12345')
  .then(function (response) {
    // handle success
    console.log(response);
  })
  .catch(function (error) {
    // handle error
    console.log(error);
  })
  .finally(function () {
    // always executed
  });

// Optionally the request above could also be done as
axios.get('/user', {
    params: {
      ID: 12345
    }
  })
  .then(function (response) {
    console.log(response);
  })
  .catch(function (error) {
    console.log(error);
  })
  .finally(function () {
    // always executed
  });  
```

Axios POST:

```javascript
axios.post('/user', {
    firstName: 'Fred',
    lastName: 'Flintstone'
  })
  .then(function (response) {
    console.log(response);
  })
  .catch(function (error) {
    console.log(error);
  });
```

[CheatSheet](https://kapeli.com/cheat_sheets/Axios.docset/Contents/Resources/Documents/index)