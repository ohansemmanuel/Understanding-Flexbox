## What happens when you switch flex-direction?
**Warning**: Some weird stuff on the way.

![Understanding Flexbox - switching flex-direction](http://i.imgur.com/ILmpwiY.jpg)

When starting off with learning the flexbox model, this part was a bit confusing and I bet a lot of newcomers to the flex world find it that way too.

You remember when I talked about the default main and cross axis being in the "left-to-right" and "top-to-bottom" directions?

![main axis](http://i.imgur.com/8DgaIMV.jpg)

Well, you can change that too. Which is exactly what happens when you use ```flex-direction: column``` as described in an earlier section (remember the default value is ```flex-direction: row```). When you do this, the main and cross axis are changed as seen below:

![flex-direction-changed](http://i.imgur.com/DrkcwNn.jpg)

If you've ever written any text in the English language, then you already know he language is written from left-to-right and top-to-bottom. That's equally the direction taken for the default main and cross axis of the flexbox too.  
However, on switching the flex direction to ```column```, it no longer follows the "English Language" pattern but Japanese! Oh yes, Japanese.

If you've written any text in the Japanese language, then this will be familiar! (for the records, I've never written any texts in Japanese). Japanese text is written from top-to-bottom and left-to-right! Not so weird, huh?

That explains why this can be a bit confusing for English writers.

![flex-direction-changed](http://i.imgur.com/DrkcwNn.jpg)

Take a look at this example. The standard unordered list with 3 list items, except this time I'll change the flex-direction.

```html
	<ul>
		<li></li>
		<li></li>
		<li></li>
	</ul>
```

```css
ul {
	display: flex;
	flex-direction: column;
}

```

Here's the look before the change in direction:

![flex-direction 1](http://i.imgur.com/jz0P0QE.png)

and after:

![flex-direction 2](http://i.imgur.com/5JvhewK.png)

So what happened?
The 'text' is now written in japanese style - from top-to-down (main-axis).

There's something you may find funny, I'd love to point out.

You see the width of the items fill up the space, right? If you were to change that before now, you'd just deal with the ```flex-basis``` and(or) ```flex-grow``` properties. Let's see how those affect our new layout.

```css
li {
	flex-basis: 100px;
}
```
...and here's what we've got:

![flex-direction 3](http://i.imgur.com/VLcqEBU.png)

__wtf??__ The height is affected, NOT the width???

I earlier said the flex-basis property defines the initial-width of every flex-item. I was wrong - or better put, I was thinking in "English". Let's switch to Japanese for a bit.

Upon switching flex-direction, please note that every property that affected the main-axis now affects the __new__ main axis and a property like ```flex-basis``` that affected the width of the flex-items along the main-axis now affects the height NOT width. The direction has been switched!

So even if you used the ```flex-grow``` property, it'd affect the height too!
Essentially, every flex property that operated on the horizontal axis (the then main-axis) now operates on the new main-axis, vertically - It's just a switch in directions.

Let's see one more example. I promise you'd get a better understanding after this.

Reduce the width of the flex-items we looked at just before now, and they no longer fill the entire space:

```css
li {
	width: 200px;
}
```

![width-changed](http://i.imgur.com/rrrIB19.png)

What if you wanted to move the list items to the center of the screen?
In English language, which is how you've dealt with flex-containers until now. That'd mean "__move the flex-items to the center of the main-axis__". So, you'd have used ```justify-content: center``
However, doing that now does NOT work.

Since the direction's changed, the center  is along the cross-axis. Take a look again:

![flex-direction-changed](http://i.imgur.com/DrkcwNn.jpg)

So let's think in Japanese. The main-axis is from top-to-down, you don't need that. The cross-axis is from left-to-right. Sounds like what you need.
Hence, you need to "__move the flex-items from the start of the cross-axis to the center".

Any flex-container property rings a bell here? Yeah, the ```align-items``` property . The `align-items` property deals with alignment on the cross-axis. So to move those to the center, you'd do this:

```css
li {
	align-items: center;
}
```
and voila! We've got our centered flex-items.

![flex-direction 4](http://i.imgur.com/dc7IVs8.png)

It can get a bit confusing, I know. Just go over it one more time.

While studying the flexbox model, I noticed a lot of CSS books skipped this part. A bit of thinking in Japanese would go a long way to help and it's worth understanding that these properties work based on the ```flex-direction``` in place.


I'm sure you learnt something new again. I'm having fun explaining this. I hope you are having fun too :-)

_Don't forget to [spread the word on Twitter](http://ctt.ec/wZ5U9). Much appreciated!_  

_Free PDF version available [here](bit.ly/und_f)._

**Next Read: [FLEXBOX SOLVED THAT](https://github.com/ohansemmanuel/Understanding-Flexbox/blob/master/07.%20Flexbox%20solved%20that/readme.md)**
