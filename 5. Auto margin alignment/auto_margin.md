## Beware of ```margin: auto```  alignment on flex items.

![Understanding Flexbox - auto-margin](http://i.imgur.com/bipZFFi.jpg)

When you use ```margin: auto``` on flex-items, things can look quite weird if you do not understand what's going on. It may result in unexpected results if you had no idea what was going on, but I'm going to explain all that.

When you use ```margin:auto``` on a flex-item, the direction (left, right or both) that has the value 	```auto``` applied will take up any empty space left.

Here's what I mean.
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
**margin-auto-1.png*

There are a couple of things to note here, so listen up!

1. The ```flex-grow``` values are set to zero for all the flex items, this explains why the list items don't take up all the space

2. More importantly, note that the flex-items are alignd to the start of the main-axis (the default behaviour) and leave up some extra space on the right. You see that?

**add image of extra space**


Let's use `margin: auto` on the first list item (Branding)

```css
li:nth-child(1) {
	margin-right: auto;
}
```

**margin-auto-1.png*

What just happened? The extra space that existed on the right before appyling auto alignment has now been distributed to the direction where the auto alignment was set - to the right of the first flex-item.

**show image showing transfer of this spacing**

It doesn't end with just one side. What if you wanted a margin auto alignment on both sides of a flex-item?


Also note that the ```justify-content``` property on flex items will not work when margin:auto is applied.

```css
//you may use the margin shorthand to set both sides of you wish
li:nth-child(1) {
	margin-left: auto;
	margin-right: auto
}
```

**margin-auto-3.png**

So, is there a trade off with the cool margin auto alignment? It appears there's one. When you use the margin auto alignment on a flex-item, the `justify-content` property no longer works on the flex-items.

For instance, setting a different alignment option on the flex-items above via the `justify-content` property, has no impact on the layout.

```css
li {
	justify-content: flex-end;
}
```

or result stays the same

**margin-auto-4.png**

li

## Practical Use cases
1. Github mobile navigation (simple)
2. Twitter desktop Navigation (hardest)
3. Default Bootstrap Nav (Normal)
