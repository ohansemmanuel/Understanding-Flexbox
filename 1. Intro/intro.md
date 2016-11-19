# Introduction

If you only get to read only one article on the Flexbox model, this may be it.

The title for this article, _"Understanding Flexbox: Everything you need to know",_ may seem rather messed up. No one can fit everything there is to a subject within one article. Even if such person existed - I may not be qualified for such. However, I'd take on the challenge head on, and try to discuss everything you need to get going with the powerful Flexbox model.
 
So, let's get started, and I'm really excited to show you the vast richness Flexbox brings. Trust me, Flexbox can be a pain in the butt when getting started, but I'll do my best to make things as clear and detailed as possible, using schematics and diagrams where possible.

## Why Use Flexbox?
A lot of changes have been made to the CSS language in the past few years. The introduction of filters, transitions and transforms to the css language were cool, but the age long  problem of crafting intelligent layouts with css persisted, and that got many of us writing _hackish css_. I wrote a lot of those, and never really understood them. We lways had to deal with floats, table display hacks and the consequences they bring. If you've written CSS for sometime, you crainly can relate with this, and if not, welcome to a beter world!

Like curdling a crying child, it really seems like our agonies as designers or front-end developers have finally been heard - and this time, in grand style. All that hackish CSS may all be gone now. No more incessant use of floats, table-cell displays and hacks you probably never understood.It's time to embrace a cleaner modern syntax for crafting intelligent layouts. Welcome the CS Flexbox model.

## What Is Flexbox?
According to the specification, the flexbox model provides for an efficient way to layout, align, and distribute space among elements within your document, even when the viewport and the size of your elements is unknown and/or dynamic.  
If that sound too formal, I understand the feeling. In just a bit, I'll explain what that means in "English".

Whether you write css in your dreams or you're just getting started, you'll feel right at home - hopefully.  
There's a lot to say, so grab a cup of your favorite drink (or just get comfortable) as I take you through a pretty long journey. 


## How do I start using the flexbox model?
This is certainly the first thing you want to know and thank goodness, the idea behind starting off with the flexbox model is quite simple. Here it is: You must first define a **flex container** (explicitly an element to be a flex container ) to start using the flexbox model.

Okay, did I make you more confused there? Let me explain. In regular html, when you lay out a simple unordered list ```ul```, you have the list items stack vertically with the unordered list tag, `ul` being the parent element of the list tags `li`.

```html
<ul> <!--parent element-->
  <li></li> <!--first child element-->
  <li></li> <!--second child element-->
  <li></li> <!--third child element-->
</ul>
```

Likewise, to use the flexbox model, you must first set a certain parent element (in this case the unordered list tag) to be a **flex container** _(aka flexible container)_ by using `display: flex` or `display: inline-flex` for the inline variation and from there you're all set to use the Flexbox model. Told you it wasn't as difficult as you expected.

![flexbox tip](http://i1064.photobucket.com/albums/u363/Ohans_Emmanuel/flexbox-article/flexbox-tip-1_zps6y7o7rc2.jpg)

Going by the example I gave, using an unordered list and a bunch of list elements, this is what that would bring us to.

```css
/*Style parent element*/
ul {
  display: flex; /*or inline-flex*/
}
```

I'm going to style the list items just a bit, so you may see what's going on here. 

```css
li {
  width: 100px;
  height: 100px;
  background-color: #8cacea;
  margin: 8px;
}

```
And here is what we have: 

![Flexbox kicks in](http://i1064.photobucket.com/albums/u363/Ohans_Emmanuel/flexbox-article/Screenshot_2_zpsjvonxs0e.png)

You may not have noticed, but something's happened already! 

By default, "divs" in css stack vertically from top to bottom like this:
![default link style](http://i1064.photobucket.com/albums/u363/Ohans_Emmanuel/flexbox-article/Screenshot_3_zpsytzach4m.png)

The image above is exactly what you'd have displayed on the screen if you had not included the ```display: flex``` on the unordered list, ```ul```. However, with the inclusion of that simple one-liner, you already see a change in display. The list elemnts are now stacked horizontally, from lef to right. I really need you to follow along now as the Flexbox model kicks in as soon as you introduce the display property on any parent element. It's all started now.

You may not understand why that change in display came to be right now, I promise I'll go into the inner workings of that very soon. For now, blind trust would suffice. Simply understand that the inclusion of the display property kicks off the Flexbox model.

There's one more thing I need to call your attention to. As soon as you introduce that display property, the unordered list automatically becomes the **flex container** and the child elements (in this case, the list elements ```li```) become **flex items**. These terms would come up over and over again as I walk you through some more intresting  things the Flexbox model has in place.


I have used two key words, I'd like to lay more emphasis on. Theyare vital to understanding what lies ahead.

1. Flex container : This is the parent element whose display property is set to ```flex``` and it houses or contains the Flex items.
2. Flex items : The children elements within a Flex container are referred to as Flex items.


![flexbox tip 2](http://i1064.photobucket.com/albums/u363/Ohans_Emmanuel/flexbox-article/flexbox-tip-2_zpsgvnqmdhw.jpg)


This is the foundation for using the flexbox model, and as soon as that's understood, more interesting things lie ahead.

Here is where I wrap up the Introduction o the Flexbox model, and this is the next article in line, **[the flex container properties](https://github.com/ohansemmanuel/Understanding-Flexbox/blob/master/2. flex container/flex-container.md)**

If you think you like how this article is coming along, don't forget to help [spread the word on Twitter](http://www.twitter.com/intent/tweet?text=I am currently reading this super cool article on the Flexbox model via @ohansemmanuel. Check it out https://github.com/ohansemmanuel/Understanding-Flexbox). Much appreciated! and If for any reasons you'd prefer to the entire tutorial as a single pdf document you can have access to anytime and on any device, [just tell me where to send it](https://ohansemmanuel.typeform.com/to/zD5yI7).

