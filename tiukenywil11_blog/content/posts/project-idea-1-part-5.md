---
title: "Project Idea 1 (Decentralized Portfolio): Part 5"
date: 2022-05-09T11:44:06+08:00
tags: ["project idea 1", "decentralized portfolio", "full stack", "reactjs", "javascript"]
description: "Part 5: Project idea to create a portfolio with decentrailized web3 technologies"
author: "Kenywil Tiu"
---
# Introduction

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; On the previous blog, We have created a simple logo, then made a base "Sidebar" component. I encountered no problem with those. I will be resuming with the [Youtube tutorial](https://youtu.be/bmpI252DmiI). 

# Steps  
For this day I decided to start with programming the styles (scss) for the 'Sidebar' component. This would include some simple animations.

## Resuming with 'Sidebar' component
1. Append the following file: *'tiukenywil11_portfolio/src/components/Sidebar/index.scss'*.
- Add style to 'nav-bar' class.
```css
.nav-bar {
	background: #000000;
	width: 60px;
	height: 100%;
	position: absolute;
	top: 0;
	z-index: 3;
	min-height: 500px;
}
```
- Inside 'nav-bar' class, nest 'logo' class.
```css
.logo {
	display: block;
	padding: 8px 0;
}
```
- Inside 'logo' class, , nset 'img' tag. 
```css
img {
	display: block;
	margin: 8px auto;
	width: 24px;
	height: auto;
}
```
- Below 'logo' class create 'nav' tag style. 
```css
nav {
    display: block;
    text-align: center;
    position: absolute;
    height: 210px;
    top: 50%;
    margin-top: -120px;
    width: 100%;
}
```
- Inside 'nav' class, nest 'a' tag.
```css
a {
	font-size: 22px;
	color: #ffffff;
	display: block;
	line-height: 51px;
	height: 51px;
	position: relative;
	text-decoration: none;
}
```
- Inside 'a' tag, nest 'i' tag.
```css
i {
	transition: all 0.3s ease-out;
}
```
- Inside 'a' tag add 'hover' animation. (Added gray color upon hover)
```css
&:hover {
	color: #808080;

	svg {
		opacity: 0;
	}

	&:after {
		opacity: 1;
	}
}
```
- Inside 'a' tag, add animations on 'after'.
```css
&:after {
	content: '';
	font-size: 9px;
	letter-spacing: 2px;
	position: absolute;
	bottom: 0;
	display: block;
	width: 100%;
	text-align: center;
	opacity: 0;
	-webkit-transition: all 0.3s ease-out;
	transition: all 0.3s ease-out;
}
```
- Below 'a' tag style, add color when button is active. (Added light gray color when active)
```css
a.active {
	svg {
		color: #d3d3d3;
	}
}
```
- Below 'nav' class, add 'ul' tag style.
```css
ul {
	position: absolute;
	bottom: 20px;
	width: 100%;
	display: block;
	padding: 0;
	list-style: none;
	text-align: center;
	margin: 0;
}
```   
- Inside 'ul' tag, add  empty 'li' tag style.
```css
li {

}
```   
- Inside 'li' tag, add 'a' tag style.
```css
  a {
	padding: 7px 0;
	display: block;
	font-size: 15px;
	line-height: 16px;
	color: #4d4d4e;
}
``` 
- Inside 'a' tag, add a 'hover' design. (Added gray color upon hover.
```css
&:hover {
  color: #808080;
}
```
2. Append *'tiukenywil11_portfolio/src/components/Sidebar/index.js'*.
- Append import from 'react-router-dom'. Add 'NavLink'
```javascript
import { Link, NavLink } from 'react-router-dom';
```
- Import from '@fortawesome/react-fontawesome'.
```javascript
import { FontAwesomeIcon } from '@fortawesome/react-fontawesome';
```
- Import icons from '@fortawesome/free-brands-svg-icons'.
```javascript
import {
	faLinkedin,
	faGithub,
} from '@fortawesome/free-brands-svg-icons';
```
- Import icons from '@fortawesome/free-solid-svg-icons'.
```javascript
import { faHome, faUser, faEnvelope } from '@fortawesome/free-solid-svg-icons'
```
- Add 'nav' tag below closing 'Link' tag.
```html
<nav>

</nav>
```
- Add 'Navlink' tag inside 'nav'
```html
<NavLink exact="true" activeclassname="active" to="/">
</NavLink>
```
- Add 'FontAwesomeIcon' tag inside 'NavLink' tags.
```html
<FontAwesomeIcon icon={faHome} color="#ffffff" />
```
- Duplicate 2 more times for 'about' and 'contact' links.
```html
<NavLink exact="true" activeclassname="active" className="about-link" to="/about">
	<FontAwesomeIcon icon={faUser} color="#ffffff" />
</NavLink>

<NavLink exact="true" activeclassname="active" className="contact-link" to="/contact">
	<FontAwesomeIcon icon={faEnvelope} color="#ffffff" />
</NavLink>
```
- Add 'ul' tag with 'li' tag inside, below 'nav' tag.
```html
<ul>
	<li>
	
	</li>
</ul>
```
- Add 'a' tag inside'li' tag. These will contains links to social media accounts.
```html
<a target="_blank" rel="noreferrer" href="https://www.linkedin.com/in/kenywil-tiu-0b6a4612b">
	<FontAwesomeIcon icon={faLinkedin} color="#ffffff"/>
</a>
```
- Duplicate 1 more times for 'github' account.
```html
<li>
	<a target="_blank" rel="noreferrer" href="https://github.com/tiukenywil11">
		<FontAwesomeIcon icon={faGithub} color="#ffffff"/>
	</a>
</li>
```
3.  Append *'tiukenywil11_portfolio/src/components/Layout/index.js'*.
- Import 'Sidebar' component.
```javascript
import Sidebar from '../Sidebar';
```
- Add 'Sidebar' tag on 'Layout' component.
```javascript
const Layout = () => {
	return (
	<div>	
		<Sidebar/>
	</div>
	)
}
```
4. Test if ReactJS app is workin.
```bash
npm start
```
- The screen should look similar to this.
![screen-end](/img/project-idea-1-part-5/1_screen-end.png)

# Outro  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; The progress I made today adds the 'Sidebar' component and its style. I had encountered a few problems when nesting the scss for 'Sidebar' component. I learned to simply model the nesting similar the HTML element.  
  
Example:  
- HTML element
```html
<ul>
	<li>
		<div className="sample"></div>
	</li>
</ul>
```
- SCSS element
```css
ul {
	/* css for 'ul' tag */
	li {
		/* css for 'li' tag */
		.sample {
			/* css for 'sample' class */
		}
	}
}
```
  
The changes can be found in my GitHub repository [here](https://github.com/tiukenywil11/decentralized-portfolio/commit/26fb540de1ccd2f6756d496974160052db33e029).  
    
**Read More:**  
Previous:  
[Decentralized Portfolio: Introduction]({{< ref "project-idea-1-introduction.md" >}})  
[Decentralized Portfolio: Part 1]({{< ref "project-idea-1-part-1.md" >}})  
[Decentralized Portfolio: Part 2]({{< ref "project-idea-1-part-2.md" >}})  
[Decentralized Portfolio: Part 3]({{< ref "project-idea-1-part-3.md" >}})  
[Decentralized Portfolio: Part 4]({{< ref "project-idea-1-part-4.md" >}})  
Next:  
[Decentralized Portfolio: Part 6]({{< ref "project-idea-1-part-6.md" >}})  
