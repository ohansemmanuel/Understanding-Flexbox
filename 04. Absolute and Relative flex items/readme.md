## A closer look at Absolute and Relative flex-items.

![Understanding Flexbox - absolute and relative flex](http://i.imgur.com/uL7XQwX.jpg)

This is perhaps the shortest article in this series. However, it is important. Remember the goal of this series is to "understand" the inner workings of the Flexbox model.

So, what really is the difference between these two?. The major difference between these two is got to do with spacing.

The spacing within a relative flex item is computed based on it's content size. In an absolute flex item, it is based solely on "flex" NOT content.

![albert_einstein quote](http://i.imgur.com/KM8EZcn.jpg)  
_image from alberteinsteinquotes.com_

Here's a good example.

Consider the unordered list marked up and styled below
```html
<ul>
	<li>
		This is just some random text  to buttress the point been explained.
  	Some more random text to buttress the point being explained.
	</li>

	<li>This is just a shorter random text.</li>
</ul>
```

```css
ul {
	display: flex; /*flexbox activated*/
}

li {
	flex: auto; /*remember this is same as flex: 1 1 auto;*/
	border: 2px solid red;
	margin: 2em;
}
```

**Here's the result:**

![relative_flex](http://image.prntscr.com/image/4599e12c9915403fa086a5f1cd4dc20b.png)

Incase you forgot, ```flex: 1 1 auto``` is same as setting: ````flex-grow: 1``` ```flex-shrink: 1``` and ```flex-basis: auto```

Using the framework I established much earlier : The initial width of the flex-items are automatically computed ```flex-basis: auto```, and then they "grow" to fit the available space ```flex-grow: 1```.


When flex-items have their widths computed automatically, ```flex-basis: auto```, it is based on the size of the content contained within the flex-item.

The flex-items in the example above do NOT have contents of the same size. Hence, the sizes of the flex-items would be unequal.

Since the individual widths weren't equal in the first place (it was based off content), when the items grow, the widths also stay unequal.

![relative_flex](http://image.prntscr.com/image/4599e12c9915403fa086a5f1cd4dc20b.png)

The flex-items in the example above are relative flex-items.

Let's make the flex-items absolute - meaning this time their widths should be based on "flex" NOT content size.  

A 'one-liner' does the magic.

```css
li {
	flex: 1 ; /*same as flex: 1 1 0. see flex: 'positive number'*/
}
```

**Here's the result:**

![absolute_flex](http://image.prntscr.com/image/8285e749472642fca16fcae7dc006ff9.png)

Do you see both flex-items have the same widths this time?
The initial widths of the flex-item is zero ```flex-basis: 0```, and then they 'grow' to fit the available space. This time around, the widths aren't computed automatically or based on content size. The widths are based on the flex value specified.

So you got that.

Here's a recap. Absolute flex-items have their widths based solely on flex, while relative flex items have their widths based on content size.


_Don't forget to [spread the word on Twitter](http://ctt.ec/wZ5U9). Much appreciated!_  

_Free PDF version available [here](bit.ly/und_f)._

**Next Read: [AUTO-MARGIN ALIGNMENT](https://github.com/ohansemmanuel/Understanding-Flexbox/blob/master/05.%20Auto%20margin%20alignment/auto_margin.md)**
