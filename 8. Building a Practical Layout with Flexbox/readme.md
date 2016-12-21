## Building a Practical Layout with Flexbox

![Understanding Flexbox - building a music app](http://i.imgur.com/WTTAWO5.jpg)

Let’s walk through a practical example and apply our newly acquired flex skills! 

It took me days to come up with a good project for which you may really learn to apply the flexbox model practically, but out of the lack of a creative option, I could only come up with a music player app layout for cats. I called it catty music. Maybe by 2036, we'd have cats singing in rock bands somewhere in mars.  

Here's what the finished layout looks like, and it is completely laid out with Flexbox.

![catty-board](http://i.imgur.com/EYSoc5A.png)

See my JS fiddle here **add jsfiddle link**  

I've got a confession to make though. I've done something considered wrong by many, and that is, I've completely built the overall layout with flexbox. For many reasons this may not be ideal, but it's intentional in this scenario. I intentionally want to point out a lot of "what can i do with flexbox" within one project.

If you're curious as to when it's considered right or wrong to use the flexbox model, you may check out my article, [Flexbox is awesome but it's NOT welcome here](https://medium.com/@ohansemmanuel/flexbox-is-awesome-but-its-not-welcome-here-a90601c292b6#.zbf4msgoh) 


I got that off my chest! Now I'm sure no one's going to yell at me after reading this.

Everything in Catty Music is laid out using the flexbox model - this is intentional to show off what's possible. So let's get this thing built!

As with any reasonable project, a bit of planning goes a long way sifting through inefficiencies. I'll take you through a planned approach to building the __catty music__ layout. So where do we start?

Whenever building a layout with flexbox, you'd want to look out for what sections of your layout may stand out as flex-containers, so you may leverage the powerful alignment properties flexbox makes available.

Take a look at the finished layout again, and you'd see that you may have the overall containing body as a flex container (represented by the red border in the image below) and have the other sections of the layout split into flex-item (item 1 and 2). 

![initial-breakdown](http://i.imgur.com/u4ov0oJ.jpg)

You got that right? You'd agree that this makes total sense as item 1 contains every other part of the layout other than the 'footer' - the section that contains the music control buttons.

Did you know that a flex-item could also be made a flex-container that contains other flex-items?? Yes, yes, yes! that's possible.

We may nest as deep as we want (it's only sane to keep this to a reasonable level though). So, with that new revelation comes this: Item 1 (our first flex-item) may also be made a flex container with the sidebar(item 1b) and main section(item 1a) of the layout being flex-items!

![second-breakdown](http://i.imgur.com/i5rD6w8.jpg)

You're still with me right? Breaking things down this way gives you a really good image to work with while building even more complex layouts with the flexbox model. You do not need a fancy image like the ones above, a simple rough paper sketch should be just fine to get you going.

You remember I said you could nest as deep as you wanted? It appears you need to do one more nesting here. Take a look
at the main section (item 1a). It could also be made a flex container to house the sections highlighted below.

![third-breakdown](http://i.imgur.com/5gfoJWn.jpg)

You may decide not to make the main section (item 1a) a flex container and just put within it two "divs" to house the highlighted sections. Yes that's possible since by default "divs" stack vertically. It's how the box model works. However, by making the main section a flex-container, you get some responsiveness off the bat - no extra styling! The "Flex" in Flexbox means flexible, remember?  Flex-containers are by default flexible, kind off responsive, which is why I'm choosing to do it this way.
I'll touch up on some other things as you build catty music. For now let's get to writing some code!

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

So let's style this ...

```css
  html,
  body {
    height: 100%; /*setting this explicitly is important*/
  }

  body {
    display: flex; /*flex superpowers activated! */
    flex-direction: column; /*Stack the flex-items vertically not the default horizontal view*/
  }

```

Usually, the first step to using the flexbox model is establishing a flex container and that's just what you did by setting the body element's display propery to ```flex```
Here we have a flex container, the body element, and our flex items are defined as in the breakdown earlier done (item 1 and item 2)
NB: You may take a look at the images shown in initial breakdown I discussed earlier if things look fuzzy now.


Keeping the image of the end in view, let's get our flex-items working. The footer which houses the music controls is to stick to the bottom of the page while the main section fills up the remaining space. How do you do that?

```css
  main {
    flex: 1 0 auto; /*fill the available space*/
  }

  footer {
    flex: 0 0 90px; /*don't grow or shrink - just stay at a height of 90px.*/
  }
```

Thanks to the ```flex-grow``` property, you can easily have the main section fill the entire space by setting it's value to 1. You should also set the ```flex-shrink``` property to zero. The reason may not be evident here but there's a bug on some browsers that allows flex-items shrink below the size of their flex-container and a workaround to this bug is to keep the shrink value at zero while setting the ```flex-basis``` property to ```auto```. Don't forget  the framework for which I broke down the flex shorthand property. There's going to be a lot of shorthand stuffs coming on!

Now that you have things coming together, let's put in a bit of styling to define spacing, colors, etc.

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
and here's what we've got now:

**flex-initial-1**

Seeing how things are beginning to take shape, you'll make it even better. Fix the sidebar. If you're coding along then update your html document

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

The listing above is quite explanatory. As explained earlier, the "main" section above will also be made a flex container! So the sidebar (represented by the aside tag), and the section will both be flex itms. Just as you made the footer stick to the bottom of the page, you also want the sidebar to stick - this time to the left. It's better explained in codes I guess

```css
  main {
  flex: 1 0 auto; /*was a flex item*/
  display: flex; /*I just included this! - now a flex container with flex items: sidebar & main content section*/
  }
```

Alright, this is geting interesting, huh? Now you have the main section as a flex container. Let's deal with one of its flex ites, the sidebar. There's something cool happening here. The sidebar has icons stacked vertiacally. So we can make this a flex-contianer with a flex-direction that let's all icons stack vertically and in position! Let's see how you may do this:


```css
  aside {
  	flex: 0 0 40px; /*as a flex item: do not grow or shrink. Just stay fixed at 40px*/
  	display: flex; /*Now you're a flex-container, you can decide how your flex-items are laid*/
  	flex-direction: column; /*Stack my flex-item s vertically...change the default direction*/
  	justify-content: space-around; /*Interesting...since direction is changed, this works on the vertical direcion*/
  	align-items: center; /*direction is changed! This affects the horizontal direction*/
  	background-color: #f2f2f2; /*make me pretty*/
  }

  /*font size for the icons*/
  aside i.fa {
  	font-size: 0.9em;
  }
```

I have obsessively commented through the code above and now see how pretty everything is laid out ...super neat with few lines of codes. Reasonable codes, no messy hacks.

**flex-initial 2**

The main content section is empty but don't forget it's the second list item where the sidebar is first. Let's put in some stuff there. What do you think?  You may take a look at the finished project again, so you don't lose sight of where we're headed. More importantly, it'd help you understand the next code listing

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

Uhmm, I added a bit more than the last time but its pretty simple: I populated the empty content section with a ```div``` that holds the album art and some details of the catty album. What about the unordered list? The ```ul``` holds a list of songs from the amazing album! The song title, artiste, time and "catty cloud sync" are contained in individual paragraphs within the list.

So what are you going to do with styling? See what I did. Can you figure it out?

First off, I make the main content section a flex container...

```css
.content {
    display: flex;
    flex-direction: column;
}
```

So let's deal with it's flex-items:

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

```.music-head``` holds the album art and other related album details. Same memo, do not grow or shrink but keep a height of 280px. Height NOT width? YEs! The parent element already had the  ```flex-direction``` switched. Oh, and because I can see into the future, you're going to need this to be a flex-container later on too, so I put in ```display: flex```
```.music-list``` holds the list of songs and it feels up the remaining available space shared with ```.music-head``` above.


This doesn't feel very pretty yet but c'mon you're doing great if still following. Thumbs up.

**flexbox-initial-3**

I've got a few problems here:

1. The list of songs looks terrible. You can fix that, can't you? 
2. The section containing the music art has really ugly looking texts. You should deal with that too.

Again, I'd walk you through solving these problems. Here is the solution I propose for problem 1 above: 

Each list of songs contain 4 paragraphs: song title, artiste, duration, and "catty cloud sync". There's got to be a way to put all of this in one line with each paragraph taking up equal space along this line. Flexbox to the rescue!! The concept here is the same employed in many grid systems. Let's translate that to codes:


```css
li {
  display: flex; <!--Target each list containing the paragraphs-->
  padding: 0 20px;
  min-height: 50px;
}

li p {
  flex: 0 0 25%; <!--This is the sweet sauce-->
}

```

You see what's happening there with the paragraphs? "Don't grow or shrink but each paragraph should take up 25% of the available space"
Let's style a bi more by giving the lists alternate colors and deal with the "caty cloud sync" label

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
So, you're killing it, and really getting to understand the flex lingo better!

**flexbox-initial - 4**

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

**flexbox-initiial-5**

Try fixing the footer. Just employ the same techniques. You can do this you know? If you get stuck, you can always check out the full source code for catty music here.

Here's  a quick tip for dealing with the footer. You may break the entire footer into flex-items too, and get going from there.

![footer breakdown](http://i.imgur.com/GaFdZJN.jpg)
