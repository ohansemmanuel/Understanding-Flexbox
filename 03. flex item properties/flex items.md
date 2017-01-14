## The Flex Item Properties
``` Order || Flex-grow || Flex-shrink || Flex-basis```

![Understanding flexbox - flex-item](http://i.imgur.com/7klPbEY.jpg)

In the previous article, we looked at flex containers and their alignment properties. Beautiful indeed. Sure you're getting a feel of what lies ahead now.
I'd take my focus off flex-containers now, and walk you through flex-items and their alignment properties.

Like flex-containers, a couple alignment properties are also made available on all flex-items. These are properties you can use on any children of a flex-container.
Let me walk you through them.

### 1. Order
The order property allows for reordering the flex items within a container. With the order property you can move a flex-item from one position to another. Just like you would do with sortable lists. This is done without affecting the source code. Which means the position of the flex items in the html source code isn't changed.

The default value for the order property is 0. It may take on either negative or positive values.


It's worth noting that flex items are reordered based on the number values of the order propery. From lowest to highest.  For example :
Consider the unordered list below, containing 4 list items.

```html
<ul>
	<li>1</li>
	<li>2</li>
	<li>3</li>
	<li>4</li>		  	 	 			
</ul>
```

By default, the flex items all have an ```order``` value of ```0```. Just as you expected, you get this after some basic styling:

![default](http://i1064.photobucket.com/albums/u363/Ohans_Emmanuel/flexbox-article/Screenshot_22_zpspzuplcpn.png)

The Flex items displayed just as specified in the html source order.

What if for some reason, you wanted the first flex item to appear last? Without changing the source order in the html document?

Without changing the source order means you do not get to do this:

```html
<ul>
	<li>2</li>
	<li>3</li>
	<li>4</li>
	<li>1</li>	  	 	 			
</ul>
```

Now that's where the ```order``` property comes in.
All you need to do is make the ```order``` value of flex item number 1 higher than that of other list items. (If you ever used the ```z-index``` property on block elements, you'd be familiar with this sort of thing)

```css

/*select first li element within the ul */
	li:nth-child(1) {
		order: 1; /*give it a value higher than 0. Remember it's ```order:0``` for other flex-items by default*/
	}

```

The flex items are then re-ordered from lowest to highest. Do not forget that list items 2, 3, and 4 all have the order value of 0. ```order: 0```. Flex-item 1 has an order value of 1. ```order: 1```.  

![one](http://i1064.photobucket.com/albums/u363/Ohans_Emmanuel/flexbox-article/Screenshot_23_zpsh8wuweny.png)

Flex-items 2, 3, and 4 all have an order value of 0. So, the html source order is kept - no modifications made to the default display.

Sure you got that!


What if you gave flex-item 2 an order value of 2? Yes, you guessed right. It goes up the stack too, since it now represents the flex-item with the highest ```order`` value.

![one and two](http://i1064.photobucket.com/albums/u363/Ohans_Emmanuel/flexbox-article/Screenshot_24_zpss9yeoaap.png)

And what happens when two flex items have the same order value?  
In the example below, flex-item 1 and 3 are given the same ```order values```.

```css
	li:nth-child(1) {
		order: 1;
	}

	li:nth-child(3) {
		order: 1;
	}
```		

![one and three](http://i1064.photobucket.com/albums/u363/Ohans_Emmanuel/flexbox-article/Screenshot_25_zpsu0aodhvy.png)


The items are still arranged from lowest to highest, but this time, flex-item 3 appears last because it comes after flex-item 1 in the source file (html document).

NB: The re-ordering is based on  the positions in the source file, when two or more flex items have the same order value.

That was a lot of explanation. Let's move on to some other properties.

### 2. Flex grow and flex shrink
The beauty of flex items is being "flexible". The ```flex-grow``` and ```flex-shrink``` properties allow us play around this 'flexibility' even more.

The ```flex-grow``` and ```flex-shrink``` properties control how much a flex-item should "grow" (extend) if there are extra spaces, or "shrink" if there are no "extra" spaces. They may take up any values ranging from 0 to any positive number. ```0 || positive numbers```

Let me demystify that. Consider the simple unordered list comprising just one list item:

```html
<ul>
	<li>I am a simple list</li>
</ul>
```
```css
ul {
	display: flex;
}
```
With a bit more styling, it appears like this.

![Flex grow](http://i.imgur.com/Ru6GV3r.png)

By default, the ```flex-grow``` property is set to ```0```. By implication, the flex-item does NOT grow to fit the entire space available. The value ```0``` is like a "turn-off" switch. The ```flex-grow``` switch is turned off. However, if you changed the ```flex-grow``` value to ```1```, here's what happens.

![Flex grow- 2](http://i.imgur.com/msa3JIS.png)

The flex-item now 'grows' to occupy all the available space. The switch's turned on! If you tried resizing your browser, the flex-item would also 'shrink' to accomodate the new screen size. Why? By default, the ```shrink``` property is set to 1. Which means the ```flex-shrink``` switch is also turned on!

I hope that doesn't feel like a short intro you cant wrap your head around. I'll take a closer look at the ```flex-grow``` and ```flex-shrink``` properties in a bit if you still don't get it.

Let's move  on.

### 3. Flex basis
Remember how I said the beauty of the flex-items is being "flexible"? Well, it appears you also have a control over that. How cool.

The ```flex-basis``` property specifies the **initial** size of a flex-item. Before the ```flex-grow``` or ```flex-shrink``` properties adjust it's size to fit the container or not.  


The previous statement is really important- so I'm taking a moment to reinforce that.

The default value is ```flex-basis: auto```.  ```Flex-basis``` can take on any values you'd use on the normal width property. That is, ```percentages || ems || rems || pixels``` etc

>Nb:  when trying to set the basis property to a zero based value, Use the unit also. e.g. Use ```flex-basis: 0px```` not just ```flex-basis: 0```

I'd bring back the 'one list' example here again.

```html
<ul>
	<li>I am a simple list</li>
</ul>
```

```css
ul {
	display: flex
}

li {
	padding: 4px; /*some breathing space*/
}
```

By default, the initial width of the flex item is influenced by the default value, ```flex-basis: auto```. The width of the flex-item is computed "automatically" based on the content size (and obviously, plus whatever padding you set too).

![Flex-basis](http://i.imgur.com/QzR7xhP.png)

This means if you increased the content in the flex-item, it automatically resizes to fit.

```html
<ul>
	<li>I am a simple list AND I am a simple list</li>
</ul>
```

![flex-basis-2](http://i.imgur.com/NVu6Q5e.png)

If you however want to set the flex-item to a fixed width, you also can!

```css
li {
	flex-basis: 150px;
}
```
Now the flex-item has been constrained to a width of 150px

![flex-item-3](http://i.imgur.com/72kMsE1.png)

It's getting even more interesting.

### 4. The flex shorthand
The ```flex``` shorthand allows us set the ```flex-grow```, ```flex-shrink``` and ```flex-basis``` properties all at once. When appropriate, I advice you set all three properties at once using the flex shorthand than doing so individually.


```css
li {
  flex: 0 1 auto;
}
```

This code above is equal to setting the three properties: ```flex-grow: 0; flex-shrink: 1; flex-basis: auto``` Please note the order. ```Flex-grow``` first, then ```flex-shrink```, and then ```flex-basis```. The acronym GSB may help.


What happens if you fail to set one of the values in the flex-shorthand?
If you set only the ```flex-grow``` and ```flex-shrink``` values, ```flex basis``` would default to  zero. This is called an _absolute flex_. And when you set only the ```flex-basis```, you get a _relative flex_.

```css
//this is an absolute flex item
li {
  flex: 1 1; //flex-basis defaults to 0;
}

//this is a relative flex item
li {
  flex-basis: 200px; //only flex-basis is set
}
```
I know what you're thinking. What's  the purpose of the relative and absolute flex?  I answer that question later in this article.

For now, let's take a look at some useful flex shorthand values.

### 1. ```flex: 0 1 auto```
```css
//again, the 'li' represents any flex-item
li {
  flex: 0 1 auto;
}
```

This is same as writing ```flex: default``` and It's the default behavior of all flex items.
Let me break this down, just a bit...

![flex-shorthand](http://i.imgur.com/5DV0ZeR.jpg)

It's easier to understand this by taking a look first at the ```flex-basis``` property first. It is set to ```auto```, which means the initial width of the flex-item will be _automatically_ determined based off the size of the contents. Got that?  

Moving on to  the next property, the ```flex-grow``` value being zero also means that the ```flex-grow``` property wouldn't tamper with the initial width of the flex item. The switch's off.
Since flex-grow controls the "growth" of the flex-items and it's set to zero, the flex-items here wouldn't "grow" to fit the screen.  
Finally, the flex shrink value being 1, says this - _"shrink the flex-item when it is necessary"_

Here is what this looks like when applied to our list items:

![flex-shorthand-1](http://i.imgur.com/OVqhSvc.png)

### 2. ```Flex: 0 0 auto```

```css
/*again, the 'li' represents any list-item*/

li {
  flex: 0 0 auto;
}

```
This is same as ```flex: none```. Using the same framework i established earlier, the width is computed automatically BUT the flex item does NOT grow or shrink (they are both set to zero). It's essentially a fixed width element whose initial width is based off of the content size in the item.

![flex-shorthand-2](http://i.imgur.com/MYYrQia.png)

It doesn't look like anything's changed, right?  
Try resizing your browser, and you'll notice that the flex items do NOT shrink even if they pop out of the parent element (we will deal with this later). You'd have to scroll your browser horizontally to view all the content.

![flex-shorthand](http://i.imgur.com/JYZl3GJ.png)

### 3. ```Flex: 1 1 auto```
This is same as ```flex: auto```.  Using the same approach you've used so far, this says, "compute initial width automatically, but grow to fit the entire available space and shrink if necessary"

![flex shorthand 3](http://i.imgur.com/XPKnjC7.png)

This time around the items fill up the available space and they shrink upon resizing the browser.

### 4. ``` Flex: "positive number"```
Where "positive number" represents any positive number (without the quotes)
This is the same as flex: "positive number" 1 0. For example, ```flex:2``` is the same as ```flex: 2 1 0``` where 2  represents any positive number.


```css
/*again, the 'li' represents any list-item*/
li {
  flex: 2 1 0; /*same as flex: 2*/
}
```

Following the same framework I established earlier, this translates to: set the initial width of the flex item to zero (ehm, no width?), grow the item to fill the available space, and finally shrink the item whenever possible (you'd easily notice this when you resize your browser).

It's more practical to use this when you have more than one flex items whose initial widths, ```flex-basis``` are set to 0% (or any other zero based values e.g. 0px). What really happens is, the widths of the flex items are computed based on the ratios of the ```flex-grow``` value. I'd break that down just a bit.

Consider two list items (being our flex-items here) marked up and styled below.

```html
<ul>
	<li>I am One</li>
	<li>I am Two</li>
</ul>
```
```css
ul {
	display: flex;
}
li:nth-child(1) {
	flex: 2 1 0; /*same as just writing flex: 2*/
}

li:nth-child(2){
	flex: 1 1 0;
	background-color: #8cacea;
}
```
Remember that setting ```flex-grow : 1``` lets the flex-item fill up the available space. Here you have two flex-items. One has a  ```flex-grow``` property of ```1``` and the other ```2```,  what then happens?
They both expand to fill up the available space, but in some proportion. Here's how it works.

The latter takes up 2/3 of the available space while the former takes 1/3. You know how I arrived at that? Basic mathematics ratio. ```individual ratio / total ratio```

![flex-shorthand 4](http://i.imgur.com/5bslNpH.png)

You see what's happening? Even though both flex-items have contents of the same size (approximately), they however take up different space with one being two times the other.

### 5. Align-self

The ```align-self``` property takes a step further in giving us so much control.  You already saw how the ```align-items```	property helped in collectively aligning all flex-items within a flex-container. So, what if you wanted to change the position of a single flex-item along the cross-axis, without affecting the neighbouring flex-items?
The ```align-self``` property comes to the rescue. It may take on any of these values: ```auto || flex-start || flex-end || center || baseline || stretch```

```css
li:first-of-type {
	align-self: auto || flex-start || flex-end || center || baseline || stretch
}
```
These are values you're already similar with, but as a refresher here's how they affect a particular targeted item. In this case, the first item within the container.

### ```flex-end```
![flex-end](http://i.imgur.com/1sdtEvg.png)

### ```center```
![center](http://i.imgur.com/20l9Vno.png)

### ```stretch```
![stretch](http://i.imgur.com/fZZsL2y.png)

### ```baseline```
![baseline](http://i.imgur.com/he9J3iB.png)

### ```auto```
![auto](http://i.imgur.com/2ZVbkIe.png)

And this is the base styling on the elements, just so you understand what's going on even better.

```css
ul {
	display: flex;
	border: 1px solid red;
	padding: 0;
	list-style: none;
	justify-content: space-between;
	align-items: flex-start; /*affects all flex-items*/
	min-height: 50%;
	background-color: #e8e8e9;
}

li {
  width: 100px;
  background-color: #8cacea;
  margin: 8px;
  font-size: 2rem;
}
```

You're pretty much getting ready for the fun part now :-)

_Don't forget to [spread the word on Twitter](http://www.twitter.com/intent/tweet?text=I am currently reading this super cool article on the Flexbox model via @ohansemmanuel. Check it out https://github.com/ohansemmanuel/Understanding-Flexbox). Much appreciated!_  

_Free PDF version available [here](bit.ly/und_f)._

**Next Read: [ABSOLUTE AND RELATIVE FLEX-ITEMS](https://github.com/ohansemmanuel/Understanding-Flexbox/tree/master/04.%20Absolute%20and%20Relative%20flex%20items)**
