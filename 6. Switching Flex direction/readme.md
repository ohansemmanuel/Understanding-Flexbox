## What happens when you switch flex-direction?
**Warning**: Some weird stuff on the way.

When starting off with learning the flexbox model, this part was a bit confusing and I bet a lot of newcomers to the flex world find it that way too.

You remember when I talked about the default main and cross axis being in the "left-to-right" and "top-to-bottom" directions?

![main axis](http://i1064.photobucket.com/albums/u363/Ohans_Emmanuel/flexbox-article/flexbox-engl_zpsgmowsbbi.jpg)

Well, you can change that too, and that's what happens when you use ```flex-direction: column``` as described in an earlier section (remember the default value is ```flex-direction: row```). When you do this, the main and cross axis are changed as seen below:

![flex-direction-changed](http://i.imgur.com/01q5kWa.jpg)

If you've ever written any text in the English language, then you already know we write from left-to-right and top-to-bottom! That's equally the direction taken for the default main and cross axis of the flexbox too. However, on switching the flex direction to ```column```, it no longer follows the "English Language" pattern but japanese! Oh yes, japanese.
If you've written any text in the Japanese language, then this will be familiar! (for the records, I've never written any japanese text). Japanese text is written from top-to-bottom and left-to-right! Not so weird, huh?

That explains why this can be a bit confusing for English writers.

Take a look at this example... our standard unordered list with 3 list items, except this time I'll change the flex-direction


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

__wtf??__

I earlier said the flex-basis property defines the initial-width of every flex-item. I guess i was wrong - or better put, I was thinking in "English". Let's switch to japanese for a bit.

Upon switching flex-direction, every property that affected the main-axis now affects the __new__ main axis and a property like ```flex-basis``` that affected the width of the flex-items along the main-axis now affects the height NOT width. The direction has been switched!

So even if you used the ```flex-grow``` property, it'd affect the height too!
Essentially, every flex property that operated on the horizontal axis (the then main-axis) now operates on the new main-axis, vertically - It's just a switch in directions.

Let's see one more example. I promise you'd undersand better now.

Reduce the width of the flex-items we looked at just before now, and they no longer fill the entire space:

```css
li {
	width: 200px;
}
```

![width-changed](http://i.imgur.com/rrrIB19.png)

what if you wanted to move the list items to the center of the screen?
In English language, that'd mean "__move the text to the right of the main-axis__". So, you'd have used ```justify-content: flex-end``` However, doing that here does NOT work.

So let's think in Japanese. The main-axis is from top-to-down, you don't need that. You need to "__move the text from the center of the cross axis".

Any flex-container property rings a bell here? Yeah, the ```align-items``` property deals with alignment on the cross-axis. So to move those to the center, you'd do this:

```css
li {
	align-items: center;
}
```
and voila! We've got our centered flex-items.

![flex-direction 4](http://i.imgur.com/dc7IVs8.png)

It can get a bit confusing, I know. While studying the flexbox model, i noticed a lot of css books skipped this part. A bit of thinking in japanese would go a long way to help and it's worth understanding that these properties work based on the "direction" in place.