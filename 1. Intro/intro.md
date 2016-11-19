# Introduction

If you get to read only one article on the Flexbox model, this may be it.

The title, "Understanding Flexbox: Everything you need to know", may seem messed up. No one can fit everything there is to a subject within one article, and even if such person existed, it's not me.

Still, I'd take on the challenge to discuss everything you need to get good with the CSS Flexbox model. I hope you're ready for it.
 
Let's get started, and I'm excited to show you the vast richness Flexbox brings. Trust me, Flexbox can be a pain in the butt when getting started, but I'll do my best to make things as clear as possible. I'll highlight important points with the use of schematics and pictures where possible.

## Why Use Flexbox?
A lot of changes have been made to the CSS language in the past few years. The introduction of filters, transitions, and transforms to the css language were cool. We all loved them, but something else was missing. Something we all craved for. 

Crafting Intelligent page layouts with CSS was a problem that seemed to have persisted for too long. This got many of us writing _hackish css_. We always had to deal with floats, table display hacks and faced the consequences they brought. If you've written CSS for sometime, you can relate with this, and if not, welcome to a better world!

It seems like our agonies as designers and front-end developers have finally been heard. This time, in grand style. All that hackish CSS may all be gone now. No more incessant use of floats, table-cell displays and hacks you never understood. It's time to embrace a cleaner modern syntax for crafting intelligent layouts. Welcome the CSS Flexbox model.

## What Is Flexbox?
According to the specification, the flexbox model provides for an efficient way to layout, align, and distribute space among elements within your document, even when the viewport and the size of your elements is unknown and/or dynamic.  
If that sound too formal, I understand the feeling. In just a bit, I'll explain what that means in "English".

Whether you write css in your dreams or you're just getting started, you'll feel right at home. Since I've got a lot to show to you, go grab a cup of your favorite drink as I take you through a pretty long journey. 


## How do I start using the flexbox model?
This is the first question everyone asks, and the answer is much simpler than you may have expected. To start using the Flexbox model, all you need to do is first define a **flex-container**.

Okay, did I make you more confused there? Let me explain. In regular html, laying out a simple list of items takes this form.

```html
<ul> <!--parent element-->
  <li></li> <!--first child element-->
  <li></li> <!--second child element-->
  <li></li> <!--third child element-->
</ul>
```
If you glanced at that, you must have seen that the unordered list houses the list elements. You'd call the ```ul``` the parent element, and the ```li``` the child element.

To use the flexbox model, you must make a parent element a **flex container** _(aka flexible container)_. You do this by setting `display: flex` or `display: inline-flex` for the inline variation. It's that simple, and from there you're all set to use the Flexbox model. Told you it wasn't as difficult as you expected.


![flexbox tip](http://i1064.photobucket.com/albums/u363/Ohans_Emmanuel/flexbox-article/flexbox-tip-1_zps6y7o7rc2.jpg)


Using an unordered list and a bunch of list elements, this is what that would bring us to.

```css
/*Make parent element a flex container*/
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


![Flexbox kicks in](http://i1064.photobucket.com/albums/u363/Ohans_Emmanuel/flexbox-article/Screenshot_3_zpsytzach4m.png)


You may not have noticed, but something's happened already! 

By default, "divs" in CSS stack vertically, from top to bottom.


![default link style](http://i1064.photobucket.com/albums/u363/Ohans_Emmanuel/flexbox-article/Screenshot_2_zpsjvonxs0e.png)


The image above is exactly what you'd have displayed on the screen if you had not included the ```display: flex``` on the unordered list. However, with the inclusion of that simple one-liner, you already see a change in display. The list elements are now stacked horizontally, from left to right. 

![Flexbox kicks in](http://i1064.photobucket.com/albums/u363/Ohans_Emmanuel/flexbox-article/Screenshot_3_zpsytzach4m.png)

I really need you to follow along. The Flexbox model kicks in as soon as you introduce the display property on any parent element. It's all started now.

You may not understand why that change in display came to be right now, I promise I'll go into the inner workings of that very soon. For now, blind trust would suffice. Simply understand that the inclusion of the display property kicks off the Flexbox model.

There's one more thing I need to call your attention to. As soon as you introduce that display property, the unordered list automatically becomes the **flex container** and the child elements (in this case, the list elements ```li```) become **flex items**. These terms would come up over and over again as I walk you through some more intresting  things the Flexbox model has in place.


I have used two key words, I'd like to lay more emphasis on. They are vital to understanding what lies ahead.

1. Flex container : The parent element you've set ```display: flex``` on.
2. Flex items : The children elements within a Flex container.


![flexbox tip 2](http://i1064.photobucket.com/albums/u363/Ohans_Emmanuel/flexbox-article/flexbox-tip-2_zpsgvnqmdhw.jpg)


This is the foundation for using the flexbox model, and as soon as that's understood, more interesting things lie ahead.

So, here is where I wrap up the Introduction to the Flexbox model, and the next article in line is, **[THE FLEX-CONTAINER PROPERTIES](https://github.com/ohansemmanuel/Understanding-Flexbox/blob/master/2. flex container/flex-container.md)**

_If you think you like how this article is coming along, please don't forget to help [spread the word on Twitter](http://www.twitter.com/intent/tweet?text=I am currently reading this super cool article on the Flexbox model via @ohansemmanuel. Check it out https://github.com/ohansemmanuel/Understanding-Flexbox). Much appreciated! 
If for any reasons you'd prefer to read the entire tutorial as a single pdf document, one you can have access to at anytime and on any device, [just tell me where to send it](https://ohansemmanuel.typeform.com/to/zD5yI7)._

