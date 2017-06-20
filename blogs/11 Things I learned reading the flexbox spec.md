# 11 Things I learned reading the flexbox spec

[Blogpost](https://hackernoon.com/11-things-i-learned-reading-the-flexbox-spec-5f0c799c776b)
[Spec](https://www.w3.org/TR/css-flexbox-1/)

## Margins have special powers

Header with an image and button "floated" visually to the right

```css
.header { display: flex };
.header .logo { /* nothing needed */ };
.header .sign-in { margin-left: auto };
```

No need to mess with `space-between` to the flex container, just set `margin-left:auto` on the button.

This is _the_ method used to push a flex item to the end of a flexbox. It even has its own chapter, [Aligning with auto margins](https://www.w3.org/TR/css-flexbox-1/#auto-margins)

(this has been assuming `flex-direction:row` but also applies to column)

## min-width matters

`min-width` is initially set to `auto`, which in cases of items next to each oteher could not break or wrap properly when the content of one of the items should become too long and the flexed item breaks.

Override this by setting `min-width:0`, instructing flexbox that it's OK for this item to be narrower than the content within it. And handle word-wrap and the rest like this:

```css
.book {
  display:flex;
}
.book .description {
    font-size: 30px;
    min-width: 0;
    word-wrap: break-word;
}
.book .buy {
    margin-left: auto;
    width: 80px;
    text-align: center;
    align-self: center;
}
```

## The flexbox authors have crystal balls

Defaults keywords for flexbox

`initial = flex 0 1 auto;`
- If I want to squish in a bit if there isn't enough room, but not to stretch any wider than it needs to

`auto = flex 1 1 auto;`
- If my flex item should stretch to fill the available space and squish in a bit if there's not enough room
- 
`none = flex 0 0 auto;`
- If my item should not flex at all

Back to the button example, set the button to `none` to make it take up available space

```css
.book {display:flex;}
.book .description {
    ...
}
.book .buy {
    margin-left: auto;
    flex: none;
    width: 80px;
    text-align: center;
    align-self: center;
}
```

Instead of writing `flex: 0 0 80px`, having those on two lines as `flex: none` and `width: 80px` clearly represents the intention of the code for future readability

## inline-flex is a thing

`display: inline-flex` creates a flex container that is inline, instead of a block

## vertical-align has no effect on a flex-item

Straight from the spec, "vertical-align has no effect on a flex item" (same as `float`, for the record)

## Don't use % margins or padding

As quoted in the spec, "Authors should avoid using percentages in paddings or margins on flex items entirely" as the CSSWG could not come to a consensus?

## The margins of adjacent flex items don't collapse

You may already know that margins collapse onto each other sometimes. You may also know that margins _don't_ collapse onto each other at some other times.

And now we all know that the margins of adjacent flex items do not ever collapse onto each other.

## z-index works even if position:static

## Flex-basis is subtle and important

once your requirements go beyond the keywords `initial`, `auto`, and `none`,
things get a bit more complex.

If you have three flex items with flex values of 3, 3, and 4. Then they _will_ take up 30%, 30% and 40% of the available space, regardless of their content, if their `flex-basis` is `0`. And _only_ if it's zero.

However, if you want flex to behave in a friendlier, but less predictable way, use `flex-basis:auto`. This will take your flex values into consideration, but also take other factors into account, have a bit of a think about it, then come up with some widths it thinks will work for you (see diagram from the blog post or the spec: it distributes extra space automatically)

## align-items: baseline

also an option if your items have different font sizes and you want their baselines to align

`align-self: baseline` also works
