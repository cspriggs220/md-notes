# Front-End Notes

- 4/9
 
Don't manipulate the DOM on the fly, however clone the object, manipulate it in memory, and then replace the old with the finished product.
Use variables to store said manipulated "Builder" object

- 5/14

### CSS Component Variations

As much as possible it's better to keep variations limited to the root of the component for simplicity and sustainability. (instead of variations on the children of the components, e.g. -subheader--webinar, -list--webinar)

- 5/19

### Higher-Order Components

Conversation on PR with Josh: "You might have heard of higher-order functions, which are functions that take a function as an argument and return another function with additional capabilities. In the same was a higher-order component is a function that takes a component and returns a new component with additional functionality.

In this case we're passing in a Control component of some kind and and some arguments that define how we want the value in that control to be formatted. This formattedControl function then returns us a new component that handles that formatting. Here it provides an abstraction for containing the common logic around formatting the money and percentage controls.""

- 6/1

### setTimeout() Callback

[StackOverflow](https://stackoverflow.com/questions/5520155/settimeout-callback-argument)

Was wondering why a function of mine wasn't working correctly inside of a setTimeout call. Here's original:
```js
function getLink(source) {
  window.location = source.getAttribute('href');
};

if (specialButton) { 
  window.setTimeout(getLink(specialButton), 3000);
}
```

The `getLink()` func was getting invoked immediately and the setTimeout was ignored altogether. The problem is that when the setTimeout saw that I had invoked my getLink function, by passing the parens, I was in fact calling the function to run right then. Instead, I needed to pass a _reference_ to a callback function like so:
```js
if (specialButton) {
  window.setTimeout(function () {
    getLink(specialButton);
  }, 3000);
}
```
