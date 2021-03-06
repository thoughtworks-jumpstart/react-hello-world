# React Hello World

👋 🌏 Hello, world in React

## Objectives

In this exercise you will learn

- to create React elements with `React.createElement()`
- to create React elements with JSX syntax
- to create React elements with function components and pass in props
- to create React elements with class components and pass in props
- to render React elements with `ReactDOM.render()`

## Instructions

Create an `h1` tag with the content "Hello, world!" and append it to `<div id="app"></div>`.

First, let's do this in vanilla JavaScript by manipulating the DOM directly.

Next, we will try to do the same thing in React by creating a React element with `React.createElement()` and using `ReactDOM.render()` to render it to the DOM.

Next, we will use JSX to create a React element.

Now let's create React elements with function components. Do the same thing for class components.

## React

React provides a `createElement` method that creates a React element of a given type, which can be an HTML tag name (e.g. `div`, `h1`, etc.), a React component, or a React fragment.

```js
React.createElement(type)
```

For instance, `React.createElement('div')` will create a `<div></div>` element. To add text in the element you can specify that in the third argument, like so:

```js
React.createElement('div', null, 'Some interesting content here')
```

which results in `<div>Some interesting content here</div>`.

## ReactDOM

ReactDOM provides a `render` method that renders a React element into the DOM in the specified container.

```js
ReactDOM.render(element, container);
```

You would use `React.createElement()` to create the React element.

You could use `document.querySelector()` to select the container where you want to place your React element in.

## JSX

Each JSX element is just syntactic sugar for calling `React.createElement()`. This means that instead of creating a React element with `React.createElement()`, we can instead use JSX.

We can see this in action [here](https://babeljs.io/repl/#?presets=react&code_lz=GYVwdgxgLglg9mABACwKYBt1wBQEpEDeAUIogE6pQhlIA8AJjAG4B8AEhlogO5xnr0AhLQD0jVgG4iAXyJA).

In order to use JSX, we need to get Babel to help transpile our JavaScript files for us.

First, we have to add the Babel library in our `index.html`

```
<script src="https://unpkg.com/babel-standalone@6/babel.min.js"></script>
```

Next, add `type="text/babel"` to our `<script>` tag where we want Babel to transpile

```js
<script defer type="text/babel" src="app.js"></script>
```

### Create React elements in JSX

To create a React element in JSX

```js
const element = <div>Some text here!</div>
```

### Embed expressions in JSX

To embed JavaScript expressions within JSX

```js
const name = 'Bob'
const element = <div>My name is {name}</div>
```

You can put any valid JavaScript expressions inside the curly braces in JSX. For example, `100 + 10`, `user.name`, `getName(user)` are all valid JavaScript expressions.

### Specifying attributes in JSX

You can specify attributes in JSX

```js
const image = <img src="path/to/user/avatar.png" />
```

or, with expressions

```js
const image = <img src={user.avatar} />
```

### Nesting children in JSX

You can nest elements in JSX

```js
const element = (
  <div>
    <h1>Hello!</h1>
    <h2>Good to see you here.</h2>
  </div>
);
```

## React components and props

Function components are regular functions that accepts `props` as a single argument and returns a React element.

```js
function Hello(props) {
  return <h1>Hello, {props.name}!</h1>
}
```

Note that function components must only have one argument. React will not treat functions with multiple arguments as a component.

When we define JSX attributes they are passed in to the component as a single object called `props`, which is short for properties.

So `<Article author="Bob" content="My first article" />` will be available in the component as `props.author` and `props.content`.

This is how you would call a function component and render it to the DOM

```js
const element = <Hello name="Sara" />;

ReactDOM.render(
  element,
  document.getElementById('root')
);
```

We can also use `class` introduced in ES6 to create class components

```js
class Hello extends React.Component {
  render() {
    return <h1>Hello, {this.props.name}!</h1>;
  }
}
```

Note that class components extend from `React.Component` and include a `render()` method that returns a React element.

Also notice that we capitalized our first letter when we defined our component. This is because React treats components starting with lowercase letters as DOM tags.

For example, `<div />` represents an HTML div tag, but `<Welcome />` represents a component.

## References

- [`React.createElement()`](https://reactjs.org/docs/react-api.html#createelement)
- [`ReactDOM.render()`](https://reactjs.org/docs/react-dom.html#render)
- [Introducing JSX](https://reactjs.org/docs/introducing-jsx.html)
- [Componenets and Props](https://reactjs.org/docs/components-and-props.html)
