## Auto-margin Alignment

![Understanding Flexbox - auto-margin](http://i.imgur.com/bipZFFi.jpg)

### Beware of ```margin: auto```  alignment on flex items.
When you use ```margin: auto``` on flex-items, things can look quite weird. You do need to understand what's going on. It may result in unexpected results, but I'm going to explain all that.

When you use ```margin:auto``` on a flex-item, the direction (left, right or both) that has the value 	```auto``` will take up any empty spaces available.

That's a difficult one to catch. Here's what I mean:

Consider the navigation bar marked up and styled below:

```html
<ul>
	<li>Branding</li>
	<li>Home</li>
	<li>Services</li>
	<li>About</li>
	<li>Contact</li>
</ul>
```

```css
ul {
	display: flex;
}
li {
	flex: 0 0 auto;
}
```

Here's what we've got:

![auto-margin](http://i.imgur.com/4KPx8EL.png)

There are a couple of things to note here. So listen up!

1. The ```flex-grow``` value is set to zero. This explains why the list items don't grow

2. The flex-items are aligned to the start of the main-axis (the default behavior)

3. Owing to the items being aligned to the start of the main-axis, some extra space is left on the right. You see that?

![extra-space](http://i.imgur.com/WrqMnjo.jpg)


Now use `margin: auto` on the first list item (branding) and see what happens.

```css
li:nth-child(1) {
	margin-right: auto; /*applied only to the right*/
}
```

![margin-auto](http://i.imgur.com/KyV88wg.png)

What just happened? The extra space that existed has now been distributed to the right of the first flex-item.

![Space-shift](http://i.imgur.com/0FaVqUi.jpg)

Remember what I said earlier? When you use ```margin:auto``` on a flex-item, the direction (left, right or both) that has the value 	```auto``` will take up any empty spaces available.
It doesn't end with just one side. What if you wanted a margin auto alignment on both sides of a flex-item?


```css
/*you may use the margin shorthand to set both sides of you wish*/
li:nth-child(1) {
	margin-left: auto;
	margin-right: auto
}
```

![margin-auto both sides](http://i.imgur.com/9RF3uSj.png)

Now the space is distributed across both sides of the flex-item.

So, is there a trade off with the cool auto-margin alignment? It appears there's one. It can be a source of frustration if you don't pay attention too.

When you use the auto-margin alignment on a flex-item, the `justify-content` property no longer works on the flex-items. It just doesn't work.

For instance, setting a different alignment option on the flex-items above via the `justify-content` property, has no impact on the layout.

```css
li {
	justify-content: flex-end;
}
```

![margin-auto both sides](http://i.imgur.com/9RF3uSj.png)

## Practical Use cases
Navigations are a very big part of every website or application. Almost every website on the planet is got some sort of navigation system in place.

Take a look at these popular sites and how they approach their navigation systems. Do you see how flexbox can help you build these layouts more efficiently? Take a closer look to see where the auto-margin feature can come in very handy too.



1. Bootstrapped Navigation
![bootstrap navigation](http://image.prntscr.com/image/6ae2053426f7429c805c4bb61d14b775.png)

2. AirBnB desktop Navigation
![airbnb navigation](http://image.prntscr.com/image/6d43b429050f4548969295cd1fd6568f.png)

3. Twitter desktop Navigation
![Twitter navigation](http://image.prntscr.com/image/1b04d1a0ab92450c926b1ed0eea54cb5.png)

If you're feeling good, I advice you actually write codes. Try implementing the navigation systems yourself. You've got all the knowledge you need now. A bit of courage to start writing is all you need.


See you in the next article. Hopefully after you've completed the navigation system exercises :-)

_Don't forget to [spread the word on Twitter](http://ctt.ec/wZ5U9). Much appreciated!_  

_Free PDF version available [here](bit.ly/und_f)._

**Next Read: [SWITCHING FLEX DIRECTION](https://github.com/ohansemmanuel/Understanding-Flexbox/blob/master/06.%20Switching%20Flex%20direction/readme.md)**
