## The Flex Container Properties
`Flex-direction || Flex-wrap || Flex-flow || Justify-content || Align-items || Align-content`

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
  flex-direction: wrap || no-wrap || wrap-reverse;
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



### 3. Flex flow
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

### 4. Justify content
Life's really good with the flexbox model! If you still doubt that, the justify-content property would convince you. It may take on any of these 5 values:

```css
ul {
	justify-content: flex-start || flex-end || center || space-between || space-around
}
```
And what exactly does the justify content property bring to the table? Well, It may remind you of the text-align property.  
The justify content property defines how flex items are laid out on the main axis
The default value is ```flex-start```, which groups the flex-items to the start of the main axis, ```flex-end``` groups the flex-items to end of the main axis, ```center``` does just you'd expect - centering the flex items along the main axis, ```space-between``` keeps the same space between each flex item and space around keeps the same spacing around flex items.

**include descriptive images just after its text. Especially for ```space-between``` and ```space-around```, be Super descriptive**

![flex-start](http://i1064.photobucket.com/albums/u363/Ohans_Emmanuel/flexbox-article/Screenshot_8_zpsazx7bio1.png)

![flex-end](http://i1064.photobucket.com/albums/u363/Ohans_Emmanuel/flexbox-article/Screenshot_9_zps63fw9qu3.png)

![flex-center](http://i1064.photobucket.com/albums/u363/Ohans_Emmanuel/flexbox-article/Screenshot_10_zpscx3ppxxl.png)

![space-around](http://i1064.photobucket.com/albums/u363/Ohans_Emmanuel/flexbox-article/Screenshot_11_zpszve3gmih.png)

![space-between](http://i1064.photobucket.com/albums/u363/Ohans_Emmanuel/flexbox-article/Screenshot_12_zpslp8gv2ai.png)


Don't worry if these seem like too much to get a hold of, with a bit of practice you should get very comfortable with the syntax.

### 5. Align-items
The align items property can be set to any of these values:

```css
/*ul represents any flex container*/
ul {
	align-items: flex-start || flex-end || center || stretch || baseline
}
```
It may also remind you of the  vertical align property as it defines how flex items are laid out on the **cross axis**.
The default value is ```stretch```, and this will 'stretch' the flex-items so they fill the entire height of the flex container.  
The ```flex-start``` and ```flex-end``` properties does what you expect - group the items to the start or end, along the cross-axis. And the baseline value? It aligns items along their baselines. Don't worry if you don't get that. The images below would really help you understand better.  

![stretch](http://i1064.photobucket.com/albums/u363/Ohans_Emmanuel/flexbox-article/Screenshot_13_zps1nwnarjp.png)

![flex-start](http://i1064.photobucket.com/albums/u363/Ohans_Emmanuel/flexbox-article/Screenshot_14_zpsjq3fqh9g.png)

![flex-end](http://i1064.photobucket.com/albums/u363/Ohans_Emmanuel/flexbox-article/Screenshot_15_zpstwulkeyt.png)

![center](http://i1064.photobucket.com/albums/u363/Ohans_Emmanuel/flexbox-article/Screenshot_16_zpsa0ougr7u.png)

![baseline](http://i1064.photobucket.com/albums/u363/Ohans_Emmanuel/flexbox-article/Screenshot_17_zpsovbaj6w0.png)


Isn't it awesome the amount of control you have here?


### 6. Align content
Remember when you added more list elements to our unordered list? Yes, you got a multi-line flex container by using the ```flex-wrap``` property.

The ```align-content``` property takes the same values as ```align-items``` apart from ````baseline``` and it controls how the flex-items are aligned in a multi-line flex container. The default is also ```stretch```

![stretch](http://i1064.photobucket.com/albums/u363/Ohans_Emmanuel/flexbox-article/Screenshot_18_zpsy8iaetza.png)

![flex-start](http://i1064.photobucket.com/albums/u363/Ohans_Emmanuel/flexbox-article/Screenshot_19_zpsdumnrbis.png)

![flex-end](http://i1064.photobucket.com/albums/u363/Ohans_Emmanuel/flexbox-article/Screenshot_20_zpsvtll0vn0.png)

![center](http://i1064.photobucket.com/albums/u363/Ohans_Emmanuel/flexbox-article/Screenshot_21_zpsy0u5amdd.png)
