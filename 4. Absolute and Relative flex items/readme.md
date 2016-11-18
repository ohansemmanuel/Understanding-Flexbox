## A closer look at absolute and relative flex items.
Earlier, I talked about relative and absolute flex items. The major difference between these two is, the spacing in (and around) a relative flex item is computed based off the content size, and in an absolute flex item it is based solely on "flex".  
Here's a good example.

Consider the unordered list marked up and styled below
```html
<ul>
	<li>This is just some random text  to buttress the point been explained.
  This is just some random text to buttress the point been explained.</li>
	<li>This is just a shorter random text.</li>
</ul>
```

```css
ul {
	display: flex;
}
li {
	flex: auto //remember this is same as flex: 1 1 auto;
	border: 2px solid red;
	margin: 2em;
}
```

Here's the result
**image

Using the framework I established earlier - The initial width of the flex items are automatically computed ```flex-basis: auto```, and then they "grow" to fit the available space ```flex-grow: 1```. However, since their individual width wasn't equal in the first place (it was based off content), when the items grow, the widths stay unequal.

Let's make the flex-items absolute - meaning this time their widths should not based on the size of content.  
A 'one-liner' does the magic.

```css
li {
	flex: 1 ; //same as flex: 1 1 0. see flex: 'positive number'
}
```

Here's the result.
**add image
This time, the widths of the flex items are initially zero (flex-basis: 0), and then they 'grow' to fit the available space with all items starting initially from width: 0px, which explains why they have the same width.

So here's a recap- absolute flex items have their widths based solely on flex, while relative flex items have their widths computed based off the size of the content they contain.