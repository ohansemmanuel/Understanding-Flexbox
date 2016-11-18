# Everything you could possibly want to know about the CSS Flexbox Model

If you only get to read only one article on the Flexbox model, this is it. Period. 

The title for this article may seem pretty messed up. No one can fit all there is to anything within one article and even if such person existed - It certainly isn't me. However I'm going to give it a good trial and try to discuss everything you may need to get going with the powerful flexbox model.

Go ahead and skim through this article, from top to bottom (if you didn't already do so) and you'd notice it's quite a lot to take in at once. Medium suggests it'd take over 30mins to digest, so I decided to make it easier to take in -  If for any reasons you'd prefer to read this as a pdf document you can have access to anytime and on any device, just tell me where to send it. It's that simple.

So, let's get started.

## Why Flexbox?
Like curdling a crying child, it does seem like our plea as designers & front-end developers have finally been heard - and this time, in grand style.

The introduction of filters, transitions and transforms to the css language were cool, but the age long  problem of crafting intelligent layouts with css persisted, and that got many of us writing _hackish css_. I wrote a lot of those, and never really understood them. That may all be gone now. No more incessant use of floats, table-cell displays and hacks you probably never understood.

## What Is Flexbox?
According to the specification, the flexbox model provides for an efficient way to layout, align, and distribute space among elements within your document, even when the viewport and the size of your elements is unknown and/or dynamic.  
If that sound too formal, I understand the feeling. In just a bit, I'll explain what that means in "English".

Whether you write css in your dreams or you're just getting started, you'll feel right at home - hopefully.  
There's a lot to say, so grab a cup of your favorite drink (or just get comfortable) as I take you through a pretty long journey. As a reminder, you may get the entire article as a pdf document here. 

## How do I start using the flexbox model?

The idea behind using the flexbox model is quite simple. You must first define a **flex container** to start using the flexbox powerful layout properties.

What's a flex container? Let me explain. When you lay out a simple unordered list, you have the list items stack vertically with the unordered list tag, `ul` as the parent element of the list tags `li`.

```html
<ul> <!--parent element-->
  <li></li> <!--first child element-->
  <li></li> <!--second child element-->
  <li></li> <!--third child element-->
</ul>
```

Likewise, to use the flexbox model, you must first set a certain parent element (in this case the unordered list tag) to be a **flex container** _(aka flexible container)_ by using `display: flex` or `display: inline-flex` for the inline variation and from there you can move unto using the flexbox properties.

![flexbox tip](http://i1064.photobucket.com/albums/u363/Ohans_Emmanuel/flexbox-article/flexbox-tip-1_zps6y7o7rc2.jpg)

In the case of our lists, this is want I mean.

```css
/*Style parent element*/
ul {
  display: flex; /*or inline-flex*/
}
```
![default link style](http://i1064.photobucket.com/albums/u363/Ohans_Emmanuel/flexbox-article/Screenshot_3_zpsytzach4m.png)

As soon as you do that, the unordered list automatically becomes the **flex container** and the child elements become **flex items**, after which the flexbox model kicks in and a change in layout is also seen: The list items are now stacked horizontally instead of vertically.


Assuming the flex items _(the list items - you get that, huh?)_ are styled just a bit - you'd easily notice the change.

```css
li {
  width: 100px;
  height: 100px;
  background-color: #8cacea;
  margin: 8px;
}

```

![Flexbox kicks in](http://i1064.photobucket.com/albums/u363/Ohans_Emmanuel/flexbox-article/Screenshot_2_zpsjvonxs0e.png)

You may view the pen here

Don't bother a bit if you don't understand why the change came to be - that's exactly what I am going to be explaining in detail. Blind trust will suffice for now. So Let's move on.

I have used two key words, and understanding them goes a long way helping you understand every other section of this article:
1. Flex container : the parent element in which flex items are contained
2. Flex items : The children of the flex container


![flexbox tip 2](http://i1064.photobucket.com/albums/u363/Ohans_Emmanuel/flexbox-article/flexbox-tip-2_zpsgvnqmdhw.jpg)


This is the foundation for using the flexbox model, and as soon as that's understood, more interesting things lie ahead.
