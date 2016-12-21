## Responsive design with flexbox

![Understanding Flexbox - responsive design](http://i.imgur.com/kCh7pgs.jpg)

Books have been written on responsive design, and good books at that. Since this article focuses on the flexbox model, I wouldn't be taking a deep plunge into responsive designs generally.


Like I stated somewhere earlier, we do get some responsiveness out of the box with the flexbox model. flexbox as in "flexible box". However, it's equaly possible to target various screen sizes via media queries and then change the flex behaviour. Here's an example?

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
You're a pro at this flex stuff now so you understand what's going on up there. Here's how our navigation bar looks.

**simple-responsive-1**

While this is cool for desktops and tablets, at certain screen sizes it particularly doesn't look good. On mobile, you'd want to stack this item vertically. Then comes in media queries

```css

@media screen and (max-width: 769px) {
	/* code here only applies to screen devices that have a width lesser than 769px*/
	ul {
		flex-direction: column;
	}
}

```
**simple-responsive-2**
You do not need to forget all you've learnt about responsive designs, just transpose the flexbox model unto your existing knowledge and you're good to go.

https://github.com/ohansemmanuel/Understanding-Flexbox/blob/master/10.%20Conclusion/readme.md
