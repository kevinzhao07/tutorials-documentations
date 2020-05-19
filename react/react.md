# React
React is a popular JavaScript library for building beautiful user interfaces resulting in smooth user experiences. It is able to update and render elements based on data changes on any application. React focuses on seeing elements as components keeping track of their own data and states, then seamlessly incorporating the changes into the front-end for users. 

This is a shortened/quick version of a tutorial found [here](https://reactjs.org/tutorial/tutorial.html).

## Starting React
To use React to create new apps and programs, refer to the following instructions:
1. Make sure you have the latest version of `Node.js` installed onto your computer. for reference, check [here](https://nodejs.org/en/).
2. Run the code `npx create-react-app [NAME OF APP]` in the terminal of the directory of your choosing. 
    - It might take a long time if it's your first time creating an app. To make sure everything worked, run `cd [NAME OF APP]`, and then `npm start`. If you see a blue screen saying to start your project in your `app.js`, then you've done it successfully!
3.  When starting the project with your own code, make sure this is present on the top of your `.js` files:
```javascript
import React from 'react';
import ReactDOM from 'react-dom';
import './[NAME OF CSS FILE].css'; // if needed
```

## How To Use React

### Explanation of Data Structures in React
To use React to build amazing UIs, we have to start with `React.Component` subclasses. These components can be seen as classes, with each having unique data and functionality. Here's an example:
```javascript
class ShoppingList extends React.Component {
  render() {
    return (
      <div className="shopping-list">
        <h1>Shopping List for {this.props.name}</h1>
        <ul>
          <li>Instagram</li>
          <li>WhatsApp</li>
        </ul>
      </div>
    );
  }
}
```
In this case, `ShoppingList` is a **React Componenet Class/Type**. We are able to acccess these objects using simple XML tags like so: `<ShoppingList name="your_name_here"/>`, and this will print out a full shopping list like an object. The JSX syntax inside the `return()` is what we want to see on our screen dyamically update when our data changes. During build, each of these tags are replaced with the `createElement` function like so: `React.createElement('[ELEMENT]', {className: '[CLASS NAME]', ...}`. However, this is not necessary in this tutorial.
> JSX fully supports any JavaScript written inside brackets!  

### Starter Code for React Development
When we analyze the starter code, we see that we have three React componenets: `Square`, `Board`, and `Game`.
- the `Square` class simple renders a button with no function as of now.
- the `Board` class is another component that renders 9 squares (in a 3x3 formation) onto the template. We are calling each `Square` class using XML tags as: `<Square />`.
- the `Game` class is the one that renders the `<div>` tags that encapsulate everything. 
> notice the `<Board />` inside the `Game` class. The `Game` is made of `Board`s, which is made of `Square`s. Notice how working this way relates each section to an object that can be called anywhere. 

### Passing Data using Props (Properties)
Using properties, or props, we are able to pass data between parent (`Board` component) and child (`Square` component) elements. Each `Square` component holds a `value` data of a number inside the XML tag. To get access to the `value` member in our `Square` component, we can call it through `{this.props.value}`, where:
- `this` refers to "this button here"; essentially grabbing THIS specific button object.
- `props` referes to properties of `this` button, which can also be seen as the arguments or data points that were passed in.
- `value` calls the specific data element. 

### Javascript
Using React, we are still able to add JavaScript into our XML tags. Regularly, we can add it this way:
```javascript
<button className="square" onClick={function() { alert('click'); }}>
```
However, React has shorthand syntax that allows for:
```javascript
<button className="square" onClick={() => alert('click')}>
```
What this means is we're passing the entire function as a `prop` to `onClick`. Make sure that `() =>` isn't forgotten!

