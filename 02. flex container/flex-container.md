## The Flex Container Properties
`Flex-direction || Flex-wrap || Flex-flow || Justify-content || Align-items || Align-content`

![Understanding flexbox - flex-container](http://i.imgur.com/xK4JUVX.jpg)

In the last article, I established some core principles. What flex-containers and flex-items are, and how to initiate the Flexbox model. Now is a good time to put all of that to good use. So, brace up.

Having set a parent element as a flex container, a couple of **alignment properties** are made available to be used on the flex container.  
Just like you'd define the width property on a block element as `width: 200px`, there are 6 different properties the flex container can take on, and defining these properties do NOT take a different approach.

### 1. Flex-direction
The ```Flex-direction``` property may take any of four values:, and it controls the direction in which the flex items are laid along the main axis.


```css
/*where ul represents a flex container*/
ul {
  flex-direction: row || column || row-reverse || column-reverse;
  }
```

The ```flex-direction``` property let's us decide how the **flex items** are laid out. Either horizontally, vertically or reversed in both directions.  
Technically, horizontal and vertical isn't what it's called in the _"flex world"_. These are described as **main-axis** and **cross axis**, and the defaults are shown below:

![main axis](http://i1064.photobucket.com/albums/u363/Ohans_Emmanuel/flexbox-article/flexbox-engl_zpsgmowsbbi.jpg)

By default, the `flex-direction` property is set to `row` and it aligns the flex-item(s) along the main axis. This explains what happened with our unordered list at the start of this article. Even though `flex-direction` property wasn't explicitly set, it took on the default value of `row` and so the flex items were laid across the main-axis, stacking horizontally from left to right.


### 2. Flex-wrap
The flex wrap property can take on any of three values:

```css
//where ul represents a flex container
ul {
  flex-wrap: wrap || no-wrap || wrap-reverse;
  }
```

Let's try sticking in a lot more list items within our unordered list. What do you think? Will our flex container resize or break up the list items?


```html
/*adding 3 more li elements*/
<ul> <!--parent element-->
  <li></li> <!--first child element-->
  <li></li> <!--second child element-->
  <li></li> <!--third child element-->
  <li></li>
  <li></li>
  <li></li>
</ul>
```

Fortunately, the flex-container adapts to accommodate our new flex-items

![Image of more children elements added to a flex container](http://i1064.photobucket.com/albums/u363/Ohans_Emmanuel/flexbox-article/Screenshot_4_zpsd860b8lu.png)

So let's go a bit further...Add a ridiculous amount of flex-items to our parent element. I choose 10 more items. What happens??

![Image of much more children elements added to a flex container](http://i1064.photobucket.com/albums/u363/Ohans_Emmanuel/flexbox-article/Screenshot_5_zpste0kkkru.png)


Again, the flex container adapts to fit all children in, even if I need to scroll my browser horizontally.  
This is the default behavior of every flex container. It keeps on accommodating more flex items on a single line because the ```flex-wrap``` property defaults to ```no-wrap```.

```css
ul {
	flex-wrap: no-wrap; /*Keep on taking more flex items without breaking (wrapping)*/
}
```

Well, with that number of flex-items, you certainly want the flex-container to 'wrap' around these elements. i.e. When the available space can no longer support the flex-items, break unto multiple lines when needed, and with that comes the ```wrap``` value

```css
ul {
	flex-wrap: wrap;
}
```
With this, the flex items now break up into multiple lines when needed. In this case, when a single line can no longer contain all the list items in their default width, they break up into multiple lines. Even on resizing the browser!!

![Image of much more children elements now in multiple lines](http://i1064.photobucket.com/albums/u363/Ohans_Emmanuel/flexbox-article/Screenshot_6_zpscnqcf7my.png)


There's one more value, ```wrap-reverse```. Yes, you guessed right. It lets the flex items break unto multiple lines but in the reverse direction.


![Image of much more children elements now in multiple lines with wrap-reverse](http://i1064.photobucket.com/albums/u363/Ohans_Emmanuel/flexbox-article/Screenshot_7_zpsi3w2os3q.png)



### 3. Flex-flow
The ```flex-flow``` is a shorthand property which takes ```flex-direction``` and ```Flex-wrap``` values. Ever used the ```border``` shorthand property? ```border: 1px solid red```. It's the same concept here. Multiple values declared in one line.

Re-writing the code above would yield this:

```css
ul {
	flex-flow: row wrap; /*direction 'row' and yes, please wrap the items.*/
}
```

![image explaining the flex-flow property](http://i1064.photobucket.com/albums/u363/Ohans_Emmanuel/flexbox-article/flexbox-flex-flow_zpshybxvgcy.jpg)


Try out the other combinations this could take. ```flex-flow: row no-wrap```, ```flex-flow: column wrap```, ```flex-flow: column no-wrap```
I'm sure you understand what those would produce. Give it a try.

### 4. Justify-content
Life's really good with the flexbox model! If you still doubt that, the justify-content property would convince you. It may take on any of these 5 values:

```css
ul {
	justify-content: flex-start || flex-end || center || space-between || space-around
}
```
And what exactly does the justify content property bring to the table? Well, It may remind you of the text-align property.


The justify content property defines how flex items are laid out on the main axis.

Consider the simple unordered list below:

```html
<ul>
  <li>1</li>
  <li>2</li>
  <li>3</li>
</ul>
```

Adding up some basic styling...

```css
  ul {
    border: 1px solid red;
    padding: 0;
    list-style: none;
    background-color: #e8e8e9;
  }

  li {
      background-color: #8cacea;
      width: 100px;
      height: 100px;
      margin: 8px;
      padding: 4px;
  }
```

We have this:

![initial](http://image.prntscr.com/image/a1aa457e10044a30b8fa3bd1d5fd4e31.png)

With the ```justify-content property```, the three flex-items may be aligned across the main-axis in whatever way you desire. Here's the breakdown of what's possible.

Fist off, the default value, ```flex-start```, groups all flex-items to the start of the main axis.
```css
  ul {
    justify-content: flex-start;
  }
```

![flex-start](http://i.imgur.com/Ct9Q1P5.png)

```flex-end``` groups the flex-items to the end of the main axis.
```css
  ul {
    justify-content: flex-end;
  }
```
![flex-end](http://i.imgur.com/Rn3C5oL.png)

```Center``` does just you'd expect - centering the flex items along the main axis.
```css
  ul {
    justify-content: center;
  }
```
![flex-center](http://i.imgur.com/kpm0rG0.png)

```Space-between``` keeps the same space between each flex item.
```css
  ul {
    justify-content: space-between;
  }
```
![space-between](http://i.imgur.com/cUYgqJs.png)

Uhmm, did you notice anything different here? Take a look again:

![Understanding-Flexbox, Space between](http://i.imgur.com/lH5HtXV.jpg)


Finally, ```space-around``` keeps the same spacing around flex items.
```css
  ul {
    justify-content: space-around;
  }
```
![space-around](http://i.imgur.com/anlXv8t.png)

A second look doesn't hurt:

![Understanding-Flexbox, Space around](http://i.imgur.com/krodS0R.jpg)

Don't worry if these seem like too much to get a hold of. With a bit of practice you will get very comfortable with the syntax.

### 5. Align-items
The ```align-items``` property is somewhat similar to the ```justify-content``` property. Having understood the ```justify-content``` property, this should be easier to take in.

```Align-items``` can be set to any of these values: flex-start || flex-end || center || stretch || baseline

```css
/*ul represents any flex container*/
ul {
	align-items: flex-start || flex-end || center || stretch || baseline
}
```
It defines how flex-items are laid out on the **cross axis**. This is the difference between the ```align-items``` property and ```justify-content```.

**The default value is ```stretch```, and this will 'stretch' the flex-items so they fill the entire height of the flex container.**

![stretch](http://i.imgur.com/z6hibEr.png)  

**The ```flex-start``` and ```flex-end``` properties do what you expect - group the items to the start or end of the cross-axis.**

![flex-start](http://i.imgur.com/7IWXXP3.png)

![flex-end](http://i.imgur.com/F0zDNT1.png)

**The ```center``` value is equally predictable. It aligns items to the center of the flex-container.**

![center](http://i.imgur.com/qSPeH9E.png)

**And the baseline value? It aligns flex-items along their baselines.**

![baseline](http://i1064.photobucket.com/albums/u363/Ohans_Emmanuel/flexbox-article/Screenshot_17_zpsovbaj6w0.png)

"Baseline" really sounds fancy. It appears to look just like ````flex-start``` but it is subtly different. What the heck is "baseline"? This should help:

![Understanding-Flexbox: Baseline](http://i.imgur.com/7vwt8Pb.jpg)  

Isn't it awesome the amount of layout control you have here?


### 6. Align-content
Remember when you added more list elements to our unordered list? You got a multi-line flex container by using the ```flex-wrap``` property. The ```align-content``` property is used on multi-line flex-containers.

It takes the same values as ```align-items``` apart from ````baseline```. By definition, it controls how the flex-items are aligned in a multi-line flex container. Just like ```align-items```, the default value is also ```stretch```

These are values you're familiar with. So, here's how they affect a multi-line flex-container.

**Stretch**

![stretch](http://i1064.photobucket.com/albums/u363/Ohans_Emmanuel/flexbox-article/Screenshot_18_zpsy8iaetza.png)

**Flex-start**

![flex-start](http://i1064.photobucket.com/albums/u363/Ohans_Emmanuel/flexbox-article/Screenshot_19_zpsdumnrbis.png)

**Flex-end**

![flex-end](http://i1064.photobucket.com/albums/u363/Ohans_Emmanuel/flexbox-article/Screenshot_20_zpsvtll0vn0.png)

**Center**

![center](http://i1064.photobucket.com/albums/u363/Ohans_Emmanuel/flexbox-article/Screenshot_21_zpsy0u5amdd.png)

...and that concludes this. You now understand how to use the various flex-container properties. Pretty soon, you'll need these to work through the practical sections coming up. I guess you're feeling much more confident now, right?  

More fun stuffs lie ahead!

_Don't forget to [spread the word on Twitter](http://www.twitter.com/intent/tweet?text=I am currently reading this super cool article on the Flexbox model via @ohansemmanuel. Check it out https://github.com/ohansemmanuel/Understanding-Flexbox). Much appreciated!_  

_Free PDF version available [here](bit.ly/und_f)._

**Next Read: [THE FLEX-ITEM PROPERTIES](https://github.com/ohansemmanuel/Understanding-Flexbox/blob/master/03.%20flex%20item%20properties/flex%20items.md)**
