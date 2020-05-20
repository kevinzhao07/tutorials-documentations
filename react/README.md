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

### Remembering States
An important feature about React is that we are able to remember the previous `state`s that each component has been in. This means we can treat each component as an object, and even construct a `constructor` for each. Here's how to do it:
```javascript
class Square extends React.Component {
  ...
  constructor(props) { // the constructor takes in props (arguments)
    super(props); // ALL React components need this in their constructor
    this.state = { // dictionary of data points
      value: null, // each data point
    };
  }
}
```
The `super(props)` is always needed for each constructor written in JavaScript, and `this.state` defines a dictionary of data thats needed to be tracked. To modify any values inside the `state` dictionary, we can do this inside the `onClick()` using `this.setState({VALUE: 'STRING', VALUE: 'OTHER', ...})`

**At this point, when the squares are pressed, they turn with a value of X. In order for the game to save each squares state separately, we have to add a constructor to the `Square`'s parent component, which is the `Board`.**

Instead of each `Square` remembering, we can have the entire `Board` remember every `state`. When writing a constructor for `Board`, we want to put `squares: Array(9).fill(null),` inside the `this.state` dictionary. Since we have a 3x3 board, we need an array of 9 `Square` components. They all start out having the value of `null`.

In order to have our `Square`s reflect their state, we have to modify our `renderSquare(i)` function. Instead of giving just `i`, we replace `value={i}` with `value={this.state.squares[i]}`. where essentially `i` is the index. Because we are unable to change `Board`'s state from `Square` (`Board` is private upwards), we can pass another prop `onClick()` that will tell `Square` how to update. We will name this function `handleClick(i)` for now:
- we will add on `onClick={() => this.handleClick(i)}` into the `renderSquare` function, inside the `Square` tags. Essentially, these are two props that are passed into the `Square` object.
- instead of setting the state in our `Square` class when clicked, we can just call new `onClick()` that was passed in as a prop. To do this, we can refer to OUR props, or `this.props.onClick()`. This still goes inside the `onClick`.
- we no longer need the `Square` constructor, which means `{this.state.value}` becomes `{this.props.value}`. (our `Square` object has no `state` if there is no constructor!)

**To clear up any confusion, the call path goes as follows:**
1. button comes with an `onClick` trigger. when that is clicked, we have to execute the function (`onClick()`) that was passed into `props`.
2. we see that `Board` passed in these `props` values, and sees that it did pass an `onClick` function. this function calls the `handleClick(i)` function. 
3. since it hasn't been defined yet, we will get an error for now. we have to define this function. 

### Adding More Functions
Going off the tutorial, we have to add the `handleClick(i)` function. This allows the game to played with 'X' and 'O', and eventually declare a winner.

```javascript
handleClick(i) {
  const squares = this.state.squares.slice(); // makes a COPY
  squares[i] = 'X'; // modifies new array
  this.setState({squares: squares}); // sets old squares to new squares
}
```
Each state is now stored in the `Board` component, not the `Square`s. This means that whenever the `Square` is updated, it reports back to the `Board`.

### Changing Data (Mutability vs. Immutability)
Looking at the code, we should ask, why did we need to make a copy? We did this because we knew we wanted a functionality of going back in time, so we would want to save previous `Board` values and data. There are many applications that have a redo/undo button, which requries keeping track of previous `state`s of objects. Immutability also helps with keeping track of which objects to re-render. It's easy to compare each new `state` to the previous `state` to see which needs to be re-rendered. 

### Cleaning up Code
Seeing that our `Square` class has no constructor/states, there is no reason to have an entire class-- we would rather have a function `Square` that returns the button. We can replace the entire class `Square` with the code below:
```javascript
function Square(props) {
  return (
    <button className="square" onClick={props.onClick}>
      {props.value}
    </button>
  );
}
```
This `Square` function takes in `props`, which are passed in from the `Board` object during the `renderSquare` function. Now, instead of calling `this.props.onClick()` (before, we were looking to call OUR [`this`] object's [`.props`], passed in function [`.onClick()`]), we can just call functions directly by accessing `props`.
> you can see this change at `{props.value}` too. 

### Constantly Updating States and Values
We need to be able to switch between 'X' and 'O' players. This requires being able to update each component after every move. We will have to keep a `bool` active and can change the states and data of our other components based on whose turn it is. 

We can also follow the tutorial and add the helper function to calculate winner. The code is just simple JavaScript syntax. 

