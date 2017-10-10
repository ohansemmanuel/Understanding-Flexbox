## Responsive Design with Flexbox

![Understanding Flexbox - responsive design](http://i.imgur.com/kCh7pgs.jpg)

Books have been written on responsive design, good books at that. 

Since this article focuses on the flexbox model, I wouldn't be taking a deep plunge into general state of responsive designs.


Like I stated somewhere earlier, we do get some responsiveness out of the box with the flexbox model. Flexbox as in "flexible box". However, it's possible to target various screen sizes via media queries and then change the flex behavior.

Here's an example?

The handy unordered list comes to the rescue again:

```html
  <ul>
    <li>Home</li>
    <li>About</li>
    <li>Contact</li>
    <li>Register</li>
    <li>Login</li>
  </ul>
```

and with a bit of styling:

```css
  ul {
		list-style-type: none;
		display: flex;
		border: 1px solid #4e4e4e;
	}

	li {
		flex: 0 0 auto;
		padding: 10px;
		margin: 10px;
		background-color: #8cacea;
		color: #fff;
		font-size: 1em;
	}
```
You're a pro at this flex stuff now so you understand what's going on up there. Here's how the  navigation bar looks.

![simple responsive nav -1](http://i.imgur.com/YkbsyGt.png)

While this is cool for desktops and tablets, at certain screen sizes it particularly doesn't look good. On mobile, you'd want to stack the nav items vertically. Then comes in media queries

```css

@media screen and (max-width: 769px) {
	/* code here only applies to screen devices that have a width lesser than 769px*/
	ul {
		flex-direction: column; /* On smaller devices, switch the direction*/
	}
}

```
![simple responsive nav -2](http://i.imgur.com/GJQZXDW.png)

If you knew a few things about responsive designs before now, that's great. Just transpose the flexbox model unto your existing knowledge and you're good to go.

By the way, I made the assumption that you understand what media queries are. If you don't, here's a quick brief.

Media queries are at the heart of responsive design. They let you target specific screen sizes and specify codes to be run on the devices alone.

The most popular form in which media queries are used is something called the @media rule. It looks like this:

```css
@media screen and (max-width: 300px) {
  /*write your css in this code block*/
}
```

Looking at it, you can almost guess what that does.

For an screen device with a maximum width of 300px ... do this and that (to be written in the code block - where the “write your css in this code block” comment exists).

Any styles within the code block will only apply to devices that match the expression, *screen and (max-width: 300px)*

I guess that helped clear up some confusion.

You're almost at the end! In the concluding article, I'll discuss browser support, helpful links and resources to get you moving. I'm sure you'd love it.

_Don't forget to [spread the word on Twitter](http://ctt.ec/wZ5U9). Much appreciated!_  

_Free PDF version available [here](bit.ly/und_f)._

**Next Read: [CONCLUSION](https://github.com/ohansemmanuel/Understanding-Flexbox/blob/master/10.%20Conclusion/readme.md)**
