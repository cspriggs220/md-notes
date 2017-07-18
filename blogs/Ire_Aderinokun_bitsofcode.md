# Ire Aderinokun - bitsofcode

## CSS - The :target Trick (CSS)
The `:target` pseudo-class refers to an element within the DOM that the URL's fragment points to. 

If you went to `https://bitsofcode.de/the-target-trick#target-test`, then that element will be the target and styles applied to the :target pseudo-class for that element will take effect.

### Hiding/Showing Content

Hide comments section until the user clicks to show them. To achieve this we can simply hide the element unless it is a :target

```html
<a href="#comments"> Show Comments</a>

<section id="comments">
    <h3>Comments</h3>
    <!-- Comments here -->
    <a href="#">Hide Comments</a>
</section>
```

```css
#comments:not(:target) {
    display: none;
}
#comments:target {
    display: block;
}
```

Slide-Out Navigation Drawer

```html
<header>
    <div class="wrapper">
        <h1>Site Title</h1>
        <a href="#nav" aria-label="Open Navigation"><i class="fa fa-bars"></i></a>
    </div>
</header>
<div class="wrapper body-wrapper">
...
</div>
<nav id="nav">
    <a href="#" aria-label="Close Navigation"><i class="fa fa-times"></i></a>
    
    <ul>
        <li><a href="#">Link One</a></li>
        <li><a href="#">Link Two</a></li>
        <li><a href="#">Link Three</a></li>
        <li><a href="#">Link Four</a></li>
    </ul>
</nav>
```

```css
#nav {
    position: fixed;
    top: 0;
    height: 100%;
    width: 80%;
    max-width: 400px;
}

#nav:not(:target) {
    right: -100%;
    transition: right 1.5s;
}

#nav:target {
    right: 0;
    transition: right 1s;
}
```

Pop-Up Modal

```html
<header>
    ...
        <a href="#modal-container" aria-label="Open Navigation">Open Modal</a>
</header>
<div id="modal-container">
    <div class="modal">
        
        <h2>Modal Title</h2>

        <p>Sriracha XOXO master cleanse lomo blue bottle, banh mi fashion axe man braid flexitarian. Meggings pug ennui, chambray 8-bit celiac gentrify. Bitters direct trade chia semiotics. Synth fixie mixtape, health goth four dollar toast vinyl 3 wolf moon VHS schlitz. Drinking vinegar letterpress VHS poutine, venmo cronut distillery artisan. Everyday carry craft beer butcher DIY. Normcore affogato chillwave, thundercats banh mi fingerstache keytar pop-up four loko four dollar toast.</p>

        <a href="#" aria-label="Close Modal"><i class="fa fa-times"></i></a>
    </div>
</div>
```

```css
#modal-container {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0,0,0,0.8);
    display: flex;
    justify-content: center;
    align-items: center;
}

.modal {
    width: 70%;
    background: #fff;
    padding: 20px;
    text-align: center;
}

#modal-container:not(:target) {
    opacity: 0;
    visibility: hidden;
    transition: opacity 1s, visibility 1s;
}

#modal-container:target {
    opacity: 1;
    visibility: visible;
    transition: opacity 1s, visibility 1s;
}
```

## Using Heading Elements to Create a Document Outline (Accessibility)

The outline for an HTML document shows the structure of the content on the page. This is useful for user agents, who can use the outline to create, for example, a table of contents for the document. 

In order to create an accurate and useful outline, we need to use the heading elements in a particular way.

### The heading element should only be used to specify the start and title of a new section of content.

Heading elements are sometimes commonly (and wrongly) used to markup subheading or subtitles. They should in fact only be used to define the title of the following section of content. (Page Title <h1> and <section> titles)

### Use the Heading Ranks to Specify Subsections

Headings of the same level imply equal rank on the page.

### Use the <section> Element to Explicitly Define Section Barriers

But also keep the appropriate heading rank (1 h1, subsections are h2, etc)

```html
<section>
    <h1>Heading Level One</h1>

    <section>
        <h2>Heading Level Two</h2>
    </section>

    <section>
        <h2>Heading Level Two</h2>

        <section>
            <h3>Heading Level Three</h3>
        </section>
    </section>

</section>
```

## Document Outlines in HTML 5.1 (Accessibility)

As of HTML 5.1 we can now nest <header> or <footer> elements as long as they are within a new sectioning context, which is created by nesting them with a sectioning element. Any of the following:

- <article>
- <section>
- <aside>
- <nav>

This way the <header> or <footer> element is always releated to a unique sectioning element. For example, an <article> element can have a <header>, which has various <section>s, detailing different information about the article.

```html
<article>
    <header>
        <h1>Creating a Document Outline in HTML 5.1</h1>'
        <section>
            <header>
                <h2>The Author</h2>
            </header>
            <p>Ire Aderinokun</p>
            <address>Lorem ipsum dolor sit amet</address>
        </section>
        <section>
            <header>
                <h2>The Publication</h2>
            </header>
            <p>bitsofcode</p>
            <address>Lorem ipsum dolor sit amet</address>
        </section>
    </header>
    <h2>Introduction</h2>
    <p>Lorem ipsum dolor sit amet</p>
</article>
```

This markup will produce the following outline - 

1. Creating a Document Outline in HTML 5.1
    1. The Author
    2. The Publication
    3. Introduction

## nth-child vs nth-of-type

are **structrual pseudo-classes**, which are classes that allow us to select elements based on information within the document tree that cannot typically be represented by other simple selectors

### How nth-child() works

position amongst it's siblings

the number represents the number of siblings that exist _before_ the element in the document tree (minus 1)

Expressed as a function, `an+b`, where `n` is the index, and `a` and `b` are any integers we pass.
```css
:nth-child(1n+0) {}
:nth-child(n+0) {}
:nth-child(1n) {}
```

We can pass a single integer or use on of the set keywords
```css
:nth-child(1) {}
:nth-child(odd) {}
:nth-child(even) {}
```

GIvin this markup:
```html
<div class="example">  
    <p>This is a <em>paragraph</em>.</p>
    <p>This is a <em>paragraph</em>.</p>
    <p>This is a <em>paragraph</em>.</p>
    <div>This is a <em>divider</em>.</div>
    <div>This is a <em>divider</em>.</div> <!-- Element to select -->
    <p>This is a <em>paragraph</em>.</p>
    <p>This is a <em>paragraph</em>.</p>
    <div>This is a <em>divider</em>.</div>
    <p>This is a <em>paragraph</em>.</p>
    <div>This is a <em>divider</em>.</div>
</div>
```

If we wanted to select the fifth element, the div, we could simply write:
```css
.example :nth-child(5) { background: #ffdb3a; }
```

However, unexpected results may occur when there are multiple types of elements, and we need to combine the `:nth-child()` pseudo-class with type or class selectors. For example, to select that same div element again, we may be tempted to write the following:
```css
.example div:nth-child(2) { ... }
```
The reason this will not work is because the element that selector is targeting does not acutally exist. Using the above selector, the user agent will go through the following steps -

1. Select all the child elements of `.example`
2. Find the second element in that list, irrespective of type
3. Check if that element is a type of <div>

If we wanted to select the second div element, we would have to use the `nth-of-type()` pseudo-class.

### How nth-of-type() works
used to match an element based on a number

this number, however, represents the element's position within _only those of its siblings that are of the same element type_

we can select all the odd paragraphs - 
```css
.example p:nth-of-type(odd) { ... }
```

The user agent goes through the following steps -

1. Select all the child elements of `.example` that are of the type <p>
2. Create a new list of only these elements
3. Select the odd numbers from that list

We can now select the second <div>, the fifth child of `.example` - 
```css
.example div:nth-of-type(2) {...}
```

### Other "nth" Pseudo-Classes

2 categories:

1. type-independent (like nth-child)
    + nth-last-child()
    + first-child()
    + last-child()
    + only-child()
2. type-dependent (like nth-of-type())
    + nth-last-of-type()
    + first-of-type()
    + last-of-type()
    + only-of-type()


The `last-of` child and type begin counting from the last element in the group of siblings instead of the first.

## JavaScript Promises 101

Promises are meant to handle callbacks when you can't determine when you necessarily expect to get them back. Mostly for when we need to complete multiple asynchronous steps in sequence, when callbacks become unmanageable and result in the infamous callback hell.

```js
doSomething(function(responseOne) {  
    doSomethingElse(responseOne, function(responseTwo, err) {
        if (err) { handleError(err); }
        doMoreStuff(responseTwo, function(responseThree, err) {
            if (err) { handleAnotherError(err); }
            doFinalThing(responseThree, function(err) {
                if (err) { handleAnotherError(err); }
                // Complete
            }); // end doFinalThing
        }); // end doMoreStuff
    }); // end doSomethingElse
}); // end doSomething
```

Promises provide a standardized and cleaner method of dealing with tasks that need to happen in sequence
```js
doSomething()  
.then(doSomethingElse)
.catch(handleError)
.then(doMoreStuff)
.then(doFinalThing)
.catch(handleAnotherError)
```

### Creating Promises
```js
var promise = new Promise( function(resolve, reject) { /* Promise content */ });
```

Within the function, we can execute whatever async task we want. To mark a promise as **fulfilled**, we call `resolve()`, optionally passing a value we want to return. To mark as **rejected**, we call `reject()`, optionally passing an error message.

Here is a common promise-ified version of an XMLHttpRequest
```js
/* CREDIT - Jake Archibald, http://www.html5rocks.com/en/tutorials/es6/promises/ */

function get(url) {  
  return new Promise(function(resolve, reject) {

    var req = new XMLHttpRequest();
    req.open('GET', url);

    req.onload = function() {
      if (req.status == 200) { 
          resolve(req.response); /* PROMISE RESOLVED */
      } else { 
          reject(Error(req.statusText)); /* PROMISE REJECTED */
      }
    };

    req.onerror = function() { reject(Error("Network Error")); };
    req.send();
  });
}
```

Once we have created the Promise, we need to actually use it. We now have access to the `.then()` method, which we can append to the function and which will be exectued when the Promise is no longer pending.

Th `.then()` method accepts two optional params. First, a function called if the promise if fullfilled. Second, a function called if the promise is rejected.
```js
get(url)
.then(function(response) {
    /*successFunction */
}, function(err) {
    /*errorFunction*/
})
```

### Handling Errors

Since both the success and error functions are optional, we can split them into two `.then()`s for better readability
```js
get(url)
.then(function(response) {
    /*successFunction */
}, undefined)
.then(undefined, function(err) {
    /*errorFunction*/
})
```

To make things even more readable, we make use of the `.catch()` method, which is a shorthand for a `.then(undefined, errorFunction)`
```js
get(url)
.then(function(response) {
    /*successFunction*/
})
.catch(function(err) {
    /*errorFunction*/
})
```

### Chaining
The real value in promises is when we have multiple async functions we need to execute in order. We can chain `.then()` and `.catch()` together to create a sequence of async functions. Return another promise within a success or error function.

```js
get(url)  
.then(function(response) {
    response = JSON.parse(response);
    var secondURL = response.data.url
    return get( secondURL ); /* Return another Promise */
})
.then(function(response) {
    response = JSON.parse(response);
    var thirdURL = response.data.url
    return get( thirdURL ); /* Return another Promise */
})
.catch(function(err) {
    handleError(err);
});
```

If a promise within the chain resolved, it will move on to the next success function (`.then()`) in sequence. If, on the other hand, a promise is refected, it will jump to the next error function (`.catch()`) in the sequence.

### Executing Promises in Parallel

There may be cases where we want to execute a bunch of promise-ified functions in parallel, and then perform an action only when all the promises have been fulfilled. For example, if we want to fetch a bunch of images and display them on the page.

To do this, we need to make use of two methods. First, the `Array.map()` method allows us to perform an action on each item in an array, and creates a new array of the results of these actions.

Second, the `Promise.all()` method returns a promis that is only resolved when every promise within an array is resolved. If any single promise within the array is rejected, the `Promise.all()` promise is also rejected.

```js
var arrayOfURLs = ['one.json', 'two.json', 'three.json', 'four.json'];  
var arrayOfPromises = arrayOfURLs.map(get);

Promise.all(arrayOfPromises)  
.then(function(arrayOfResults) {
    /* Do something when all Promises are resolved */
})
.catch(function(err) {
    /* Handle error is any of Promises fails */
})
```

If we look at the Network panel in our Development tools, we can see that all the fetch requests are happening in parallel. (screenshot)

For IE, you must use the Promise Polyfill

## Whats the Deal with Collapsible Margins

`margin area` is the space outside an element's border

`box model` is **content**, **padding**, **border**, **margin**

The margin area is different to the other three areas of the box model because it is not technically part of the element itself. Even if we specify a set  margin for an element in our CSS, the actual margin painted on the document can be affected by other elements within the document.

"A collapsed margin is what occurs when two block-level elements with meeting _vertical margins_ combine. When this happens, the larger of the two margins (or any if they are equal) is assumed as the single collapsed margin."

### When do Margins Collapse?

"As a general rule, adjoining vertical margins between in-flow, block-level boxes will always collapse".

- Case 1: The top margins of a parent and it's first child
    + If a top margin is applied to a parent element as well as it's first in-flow child, those margins may be collapsed together

- Case 2: The bottom margins of a parent and it's last child
    + Similarly to the first example, margins may be collapsed if both a parent and last in-flow child have a bottom margin. However, unlike the top margins, bottom margins will only collapse if the parent has a computed height of **auto** 

- Case 3: The bottom and top margins of siblings
    + If we have two elements, where one has a bottom margin and the second in-flow sibling has a top margin, those margins may be collapsed.

- Case 4: Empty elements
    + Finally, both the top and bottom margins on a single element may collapse if the element has a computed height of 0, i.e. if it is an empty element

### Exceptions

Margins will **not** collapse for:

- Flexbox, Grid, and other non-block-level elements
- Lines boxes, clearance, paddings, and borders
    + In the example cases mentioned above, collapsing will not happen if there are line boxes, clearance, paddings, or borders, that stand between the two elements. This happens because the **margin of the parent is no longer in direct contact with the margin of the child**.

### Dealing with Collapsed Margins

Collapsed margins that occur because of empty elements or parent/child relationships can't really be avoided. The only way to counteract collapsible margins that occur this way is by inserting something between the elements, for example a border. Otherwise, changing the element's display status to something that is not block-level would be an option.

Collapsed margins that occur because of adjoining sibling elements, on the other hand, can be avoided with a change in CSS writing style. Personally, I prefer to follow Harry Robert's rule of [Single-direction margin declarations](https://csswizardry.com/2012/06/single-direction-margin-declarations/), which has other benefits besides helping to avoid collapsible margins.
