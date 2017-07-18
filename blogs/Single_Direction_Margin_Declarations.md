[Single Direction Margin Declarations](https://csswizardry.com/2012/06/single-direction-margin-declarations/)

The basic premise is that you should try and define all your margins in one direction. This means always use `margin-botom` to push items **down** the page, and `margin-left` to push them **across** the page. 

## Benefits

- Easier to define vertical rhythm in one fell swoop
- More confidence in (re)moving components if you know their margins all push in the same direction.
- Components and elements don't have to necessarily live in a certain order if their margins aren't dependent on adjoining sides
- Not being concerned with collapsing margins means one less thing to worry about.

## Defining vertical rhythm

Whenever I start a new project I typically want to know two things; my base `font-size` and my base `line-height`. Let's say that I choose a base `font-size` of 16px and a base `line-height` of 24px. This gives me (in proper units) this:

```css
html{
    font: 1em/1.5 "Comic Sans MS", cursive;
}
```

That 1.5 is my Magic Number. This is massively important; knowing this number allows me to set up my entire project's vertical rhythm in _one_ go:

```css
h1,h2,h3,h4,h5,h6,hgroup,
ul,ol,dd,p,figure,
pre,table,fieldset,hr{
    margin-bottom: 1.5rem;
}
```

Now any block level element I add anywhere in that page will have a `line-height` of 24px (if my base `font-size` is 16px) and will be spaced apart by 24px (again, if my base font-size is 16px).

## Confidence in portability

If I had some odd situation where I have `margin-top` on element A, a `margin-top` and `margin-bottom` on element B and a `margin-bottom` on element C how can I be sure that removing B won't break anything? I can't, because I mixed up my margins!

## Exceptions

[Margin-plus-padding issues](http://jsfiddle.net/csswizardry/5p8ts/)
[Remove the margin-bottom from the last element](http://jsfiddle.net/csswizardry/5p8ts/1/)

