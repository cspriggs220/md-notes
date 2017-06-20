# Front-end Chapter Meeting

## Code Review Workshop

Vanilla JS for 
 - .setAttribute()
 - .appendChild()
 - CustomEvent("accordion:collapse", { "detail": section })
 - querySelector
 - new FormData(dom_node) // browser API

Where does it make sense to start writing in ES6 vs leveraging existing jQuery, or just use Vanilla JS

https://github.com/lampo/dr-elp/pull/467/files

A way to show JS-related things only when it's avaiable: Buttons and widgets that are used by the accordion should be created by the JS and can be removed from the view. These are only necessary when the JS is available so why not instantiate them via JS.

https://github.com/lampo/dr-contest/pull/117/files

```CSS
counter-reset: steps
```

### Skip Google Indexing

```.rb.erb
<% set_meta_tags noindex: true %>
```

## 5/10 Jim Ebert - Partnering with the Business

Business leader's goals 
+ Deliver Value and Create Profit
+ Bundle value as a product or service
+ Profit = Revenues - Expenses

### Increase Revenues

Reach (new FB ad - Marketing)
Convert (sales strategy - Sales)
Engage (via product - Product)
Retain (renew contract, upsell - Support)

### Reduce Expenses

Optimize or Automate
Technology and Operations

all of these aspects/teams create a Profit & Value Engine

How do we partner? 
+ Deliver with Excellence
    * Relationally
    * Just be good at what you're good at
    * Communication
    * Care
+ Be an Early Adopter (Alignment w/VP)
    * Buy-in to the vision
    * Learn your leader's currencies (how they best communicate with ideas/problems, etc)
    * Empathize with their responsibilities
+ Practice Tradeoff Evaluations (Stewardship)
    * decisions reflect attention to costs and priorities
    * balancing production vs perfection
    * build vs buy
    * Build trust - sell them the logic
+ Create Value (Innovation)
    * Ideas should connect with profitable opportunities
    * Always improve the profit engine
+ Give Me the Ball (Ownership)
    * Driven by commitment to success
    * product own something
    * Fight the business FOR the business

#### Ask my leaders about what is needed from their point of view. 
- What is lacking or what is of value for them at the moment.
- Ask them (Phillip/Ashley/Josh) questions on what they're working on

## DevTooling

- Lighthouse Chrome Extension and CLI Performance Tool -
- Progressive Web Metrics - pwmetrics

- Chrome Devtools
    + Performance Timeline
        * Flame Chart - hold shift to help zoom
        * Press Esc to see Rendering tab at bottom - use that to see error issues on the page with Re-painting elements, framerates
- Prettier (JS Auto-formatting)
- Ghostlab (Browser Sync Tool)
