## Building a Music App Layout with Flexbox

![Understanding Flexbox - building a music app](http://i.imgur.com/WTTAWO5.jpg)

After walking through the boring rigorous stuffs, you deserve some fun project. It's time to walk through a practical example and apply your newly acquired Flex skills!

It took me days to come up with a good project. Out of the lack of a creative option, I came up with a music app layout for cats. I call it catty music. Maybe by 2036, we'd have cats singing in rock bands somewhere in mars :-)  

Here's what the finished layout looks like, and it is completely laid out with Flexbox.

![catty-board](http://i.imgur.com/EYSoc5A.png)

You may view it online [here](http://output.jsbin.com/wubudog/1)  

I've got a confession to make though. I've done something considered wrong by many. I've completely built the overall layout with Flexbox.  
For many reasons this may not be ideal, but it's intentional in this scenario. I want to point out a lot of "what can I do with flexbox" within one project.

If you're curious as to when it's considered right or wrong to use the Flexbox model, you may check out my article, [Flexbox is awesome but it's NOT welcome here](https://medium.com/@ohansemmanuel/flexbox-is-awesome-but-its-not-welcome-here-a90601c292b6#.zbf4msgoh)


I got that off my chest! Now I'm sure no one's going to yell at me after reading this.

Everything in Catty Music is laid out using the flexbox model - this is intentional to show off what's possible. So let's get this thing built!

As with any reasonable project, a bit of planning goes a long way sifting through inefficiencies. I'll take you through a planned approach to building the __catty music__ layout.  

So where do we start?

Whenever building a layout with flexbox, you should start by looking out for what sections of your layout may stand out as flex-containers. You may then leverage the powerful alignment properties flexbox makes available.

Take a look at the finished layout again. You may have the overall containing body as a flex container (represented by the red border in the image below) and have the other sections of the layout split into flex-items (item 1 and 2).

![initial-breakdown](http://i.imgur.com/u4ov0oJ.jpg)

You got that right? You'd agree that this makes total sense as item 1 contains every other part of the layout other than the 'footer' - the section that contains the music control buttons.

Did you know that a flex-item could also be made a flex-container that contains other flex-items?? Yes, yes, yes! that's possible.

We may nest as deep as we want (it's only sane to keep this to a reasonable level though). So, with that new revelation comes this: Item 1 (our first flex-item) may also be made a flex container. The sidebar(item 1b) and main section(item 1a) would then be flex-items!

![second-breakdown](http://i.imgur.com/i5rD6w8.jpg)

You're still with me, right?

Decomposing your layout gives you a really good visual image to work with. When you begin building even more complex layouts with the flexbox model, you'd see how vital this is. You do not need a fancy image like the ones above, a simple rough paper sketch should be just fine to get you going.

You remember I said you could nest as deep as you wanted? It appears you need to do one more nesting here. Take a look
at the main section (item 1a). It could also be made a flex container to house the sections highlighted below.

![third-breakdown](http://i.imgur.com/5gfoJWn.jpg)

You may decide not to make the main section (item 1a) a flex container and just put within it two "divs" to house the highlighted sections. Yes that's possible. By default, "divs" stack vertically. It's how the box model works.

If you choose to make the main section a flex-container, you get the powerful alignment properties at your disposal. The "Flex" in Flexbox means flexible. Remember?  Flex-containers are by default flexible, kind off responsive. This may be another reason to use a flex-container over regular "divs". This depends on the case scenario though.

I'll touch up on some other things as you build catty music. You should get to writing some code now!

We'll start off with the basic html set up below:
```html
<!DOCTYPE html>
  <html>
  <head>
  <title>Catty Music</title>
  </head>
  <body>


  <main></main> <!--to contain the main section of the app-->

  <footer></footer> <!--to contain the music control buttons and song details-->


  </body>
</html>
```

So style this ...

```css
  html,
  body {
    height: 100%; /*setting this explicitly is important*/
  }

  body {
    display: flex; /*flex superpowers activated! */
    flex-direction: column; /*Stack the flex-items (main and footer elements) vertically NOT horizontally*/
  }

```

The first step to using the flexbox model is establishing a flex container. This is exactly what the code above does. It sets the body element's display property to ```flex```

Now we have a flex container, the body element. The flex items are defined too (item 1 and item 2) - as in the breakdown earlier done.
NB: You may take a look at the images shown in initial breakdown I discussed earlier if things look fuzzy now.


Keeping the image of the end in view, you should get the flex-items working. The footer which houses the music controls is to stick to the bottom of the page while the main section fills up the remaining space.
How do you do that?

```css
  main {
    flex: 1 0 auto; /*fill the available space*/
  }

  footer {
    flex: 0 0 90px; /*don't grow or shrink - just stay at a height of 90px.*/
  }
```

Thanks to the ```flex-grow``` property. It's relatively easy to have the main section fill the entire space. Just set the ```flex-grow``` value to 1. You should also set the ```flex-shrink``` property to zero. Why?

The reason may not be evident here because the flex-direction is changed. In some browsers, there's a bug that allows flex-items shrink below their content size. It's quite a weird behavior. The workaround to this bug is to keep the ```flex-shrink``` value at ```0``` NOT the default, ```1``` and also set the ```flex-basis``` property to ```auto```.

It's like saying: _"Please take on an initial width based on your content size, but never shrink."_ This will cause the flex-item to be at least as big as its width or height (if declared) or its default content size.

Please don't forget the framework for which I broke down the ````flex-shorthand``` property. There's going to be a lot of shorthand stuffs coming on!

Now that you have things coming together, put in a bit of styling to define spacing, colors, etc.

```css
  body {
    display: flex;
    flex-direction: column;
    background-color: #fff;
    margin: 0;
    font-family: Lato, sans-serif;
    color: #222;
    font-size: 0.9em;
  }
  footer {
    flex: 0 0 90px;
    padding: 10px;
    color: #fff;
    background-color: rgba(61, 100, 158, .9);
  }

```
Nothing magical yet. Here's what we've got now:

![initial-look-1](http://image.prntscr.com/image/7f648e515a0f4558ace5717726da4822.png)


Seeing how things are beginning to take shape, you'll make it even better. Fix the sidebar. If you're coding along, update your html document

```html
<main>
  <aside> <!--This represents the sidebar and contained in it are icon sets from font-awesome-->
    <i class="fa fa-bars"></i>
    <i class="fa fa-home"></i>
    <i class="fa fa-search"></i>
    <i class="fa fa-volume-up"></i>
    <i class="fa fa-user"></i>
    <i class="fa fa-spotify"></i>
    <i class="fa fa-cog"></i>
    <i class="fa fa-soundcloud"></i>
  </aside>

  <section class="content"> <!--This section will house everything other than the sidebar-->
  </section>

</main>
```

The listing above is quite explanatory. As explained earlier, the "main" section above will also be made a flex container! So the sidebar (represented by the aside tag), and the section will both be flex-items. ]

Just as you made the footer stick to the bottom of the page, you also want the sidebar to stick - this time to the left. It's better explained in codes I guess.

```css
  main {
  flex: 1 0 auto; /*was a flex item*/
  display: flex; /*I just included this! - now a flex container with flex items: sidebar & main content section*/
  }
```

Alright, this is getting interesting, huh? Now you have the main section as a flex container. Deal with one of its flex items, the sidebar.

There's something cool happening here. The sidebar has icons stacked vertically. You can make this a flex-container and give it a flex-direction that lets all icons stack vertically and in position! See how you may do this:


```css
  aside {
  	flex: 0 0 40px; /*as a flex item: do not grow or shrink. Just stay fixed at 40px*/
  	display: flex; /*Now you're a flex-container, you can decide how your flex-items are laid*/
  	flex-direction: column; /*Stack my flex-item's vertically...change the default direction*/
  	justify-content: space-around; /*Interesting...since direction is changed, this works on the vertical direction*/
  	align-items: center; /*direction is changed! This affects the horizontal direction*/
  	background-color: #f2f2f2; /*make me pretty*/
  }

  /*font size for the icons*/
  aside i.fa {
  	font-size: 0.9em;
  }
```

I have obsessively commented through the code above and now see how pretty everything is laid out ...super neat with few lines of codes. Reasonable codes, no messy hacks.

![second-layout](http://image.prntscr.com/image/e0e6da44a5d348dfba045fd3c39d6ab2.png)


The main content section is empty but don't forget it's the second list-item. The sidebar is first.

Put in some stuff there. What do you think?  You may take a look at the finished project again, so you don't lose sight of where we're headed. More importantly, it'd help you understand the next code listing.

```html
<section class="content"> <!--This section was empty. Populating it with content-->

  <div class="music-head"> <!--First list item: contains music details-->

      <img src="images/cattyboard.jpg" /> <!--Album art-->

      <section class="catty-music"> <!--other details of the album-->
          <div>
            <p>CattyBoard Top 100 Single Charts (11.06.36)</p>
            <p>Unknown Artist</p>
            <p>2016 . Charts . 100 songs</p>
          </div>

          <div> <!--Music controls-->
            <i class="fa fa-play"> &nbsp;Play all</i>
            <i class="fa fa-plus"> &nbsp;Add to</i>
            <i class="fa fa-ellipsis-h">&nbsp;&nbsp;More</i>
          </div>
      </section>
  </div> <!--end .music-head-->


  <ul class="music-list">  <!--Second list item: Contains a list of all songs displayed-->
      <li>
          <p>1. One Dance</p>
          <p>Crake feat CatKid &amp; Cyla</p>
          <p>2:54</p>
          <p><span class="catty-cloud">CATTY CLOUD SYNC</span></p>
      </li>

      <li>
          <p>2. Panda</p>
          <p>Cattee</p>
          <p>4:06</p>
          <p><span class="catty-cloud">CATTY CLOUD SYNC</span></p>
      </li>

      <li>
          <p>3. Can't Stop the Feeling!</p>
          <p>Catin Cimberlake</p>
          <p>3:56</p>
          <p><span class="catty-cloud">CATTY CLOUD SYNC</span></p>
      </li>

      <li>
          <p>4. Work From Home</p>
          <p>Cat Harmony feat Colla</p>
          <p>3:34</p>
          <p><span class="catty-cloud">CATTY CLOUD SYNC</span></p>
      </li>
    </ul>
</section>    
```

Uhmm, I added a bit more than the last time but its pretty simple.

I populated the empty content section with a ```div``` that holds the album art and some details of the catty album. What about the unordered list?  
The ```ul``` holds a list of songs from the amazing album! The song title, artiste, time and "catty cloud sync" are contained in individual paragraphs within the list.

So what are you going to do with styling? See what I did. Can you figure it out?

First off, you should make the main content section a flex container...

```css
.content {
    display: flex;
    flex: 1 0 auto; /*this makes sure the section grows o fill the entire available space*/
    flex-direction: column;
}
```

You should also deal with it's flex-items:

```css
.music-head {
  flex: 0 0 280px; /*Same memo, don't grow or shrink - stay at 280px*/
  display: flex;  
  padding: 40px;
  background-color: #4e4e4e;
}

.music-list {
	flex: 1 0 auto;
	list-style-type: none;
	padding: 5px 10px 0px;
}

```

```.music-head``` holds the album art and other related album details. Same memo, do not grow or shrink but keep a height of 280px. Height NOT width? Yes!  
The parent element already had the  ```flex-direction``` switched. Oh, and because I can see into the future, you're going to need this to be a flex-container later on too, so I put in ```display: flex```
```.music-list``` holds the list of songs and it feels up the remaining available space shared with ```.music-head``` above.


This doesn't feel very pretty yet but c'mon you're doing great if still following. Thumbs up.

![third-look](http://image.prntscr.com/image/3ee82d09e644445a9439528eb8e29628.png)

I've got a few problems here:

1. The list of songs looks terrible.

![list of songs](http://image.prntscr.com/image/2ff7241bd60545caa5ee0b8c3389374c.png)

2. The section containing the music art has really ugly looking texts. You're going to deal with that too.

![ugly texts](http://image.prntscr.com/image/04ec8c1e799a480bbcc708b019bda1fe.png)

Again, I'd walk you through solving these problems. Here are the solution I propose.

1. Each list of songs contain 4 paragraphs: song title, artiste, duration, and "catty cloud sync". There's got to be a way to put all of this in one line with each paragraph taking up equal space along this line.

Flexbox to the rescue!! The concept here is the same employed in many grid systems. Translate that to codes:


```css
li {
  display: flex; /*Targets each list containing the paragraphs*/
  padding: 0 20px;
  min-height: 50px;
}

li p {
  flex: 0 0 25%; /*This is the sweet sauce*/
}

```

You see what's happening there with the paragraphs?  "Don't grow or shrink but each paragraph should take up 25% of the available space".

![lists initial look](http://image.prntscr.com/image/d1051d406a5d42fab2388a90303c4b6f.png)

Style a bit more by giving the lists alternating colors and deal with the "catty cloud sync" label too.

```css
li span.catty-cloud {
  border: 1px solid black;
  font-size: 0.6em;
  padding: 3px;
}

li:nth-child(2n) {
  background-color: #f2f2f2;
}
```
So, you're killing it, and really getting to understand the flex lingo better! This is what you should have now.

![catty music- almost done](http://image.prntscr.com/image/a6d6bd4800d641bb8679900d02a8f105.png)

The second problem will be dealt with now. Making the album details text look prettier. Really simple stuff going on here:

```css
.catty-music{
  flex: 1 0 auto;
  display: flex;
  flex-direction: column;
  font-weight: 300;
  color: #fff;
  padding-left: 50px;
}

.catty-music div:nth-child(1){
  margin-bottom: auto;
}

.catty-music div:nth-child(2){
  margin-top: 0;
}

.catty-music div:nth-child(2) i.fa{
  font-size: 0.9em;
  padding: 0 0.7em;
  font-weight: 300;
}
.catty-music div:nth-child(1) p:first-child{
  font-size: 1.8em;
  margin: 0 0 10px;
}

.catty-music div:nth-child(1) p:not(:first-child){
  font-size: 0.9em;
  margin: 2px 0;
}
```

and you did it!

![pretty music art text](http://image.prntscr.com/image/5a55fe62f9894ab79b30b0cf9d186685.png)

### Quick Exercise
Try fixing the footer yourself. Just employ the same techniques. You can do this you know? If you get stuck, you can always check out the full source code for catty music.

Here's  a quick tip for dealing with the footer. You may break the entire footer into flex-items too, and get going from there.

![footer breakdown](http://i.imgur.com/GaFdZJN.jpg)


Wow. I can't believe you got to this point. That's great! You're becoming a Flexbox ninja now. Next, we will see how Flexbox helps with responsive designs.

_Don't forget to [spread the word on Twitter](http://www.twitter.com/intent/tweet?text=I am currently reading this super cool article on the Flexbox model via @ohansemmanuel. Check it out https://github.com/ohansemmanuel/Understanding-Flexbox). Much appreciated!_  

_Free PDF version available [here](bit.ly/und_f)._

**Next Read: [RESPONSIVE DESIGN WITH FLEXBOX](https://github.com/ohansemmanuel/Understanding-Flexbox/blob/master/09. Responsive design with Flexbox/readme.md)**
