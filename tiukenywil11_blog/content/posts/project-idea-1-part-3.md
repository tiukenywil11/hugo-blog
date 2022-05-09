---
title: "Project Idea 1 (Decentralized Portfolio): Part 3"
date: 2022-05-01T14:41:21+08:00
tags: ["project idea 1", "decentralized portfolio", "full stack", "reactjs", "javascript"]
description: "Part 3: Project idea to create a portfolio with decentrailized web3 technologies"
author: "Kenywil Tiu"
---
# Introduction

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; On the previous blog, I have added a prettier configuration to help with the code format, and added the global styles (css & scss) for the portfolio. I had a few issues with importing the fonts due to the font names but this was fixed by removing spaces for me. I will be resuming with the [Youtube tutorial](https://youtu.be/bmpI252DmiI).  
  
# Steps  
For this day I decided to add a 'Layout' component, and create a route to 'Layout' component using *'react-router-dom'* for this.

## Creating a 'Layout' component
1. Create the following directory *'tiukenywil11_portfolio/src/components/Layout'*.
2. Create the following files inside *'tiukenywil11_portfolio/src/components/Layout'*.
	- index.js
	- index.scss
3. Append *'tiukenywil11_portfolio/src/components/Layout/index.js'*.
- Import *'tiukenywil11_portfolio/src/components/Layout/index.scss'*
```javascript
import './index.scss';
```  
- Create functional component 'Layout'.
```javascript
const Layout = () => {
	return <> Layout component </>
}
```
- Export component so it could be used by other components.
```javascript
export default Layout;
```  
  
## Adding routes
4. Append *'tiukenywil11_portfolio/src/index.js'*.  
- Import components from 'react-router-dom'
```javascript
import { BrowserRouter } from 'react-router-dom';
```
- Remove the following snippets inside 'root.render'.
```html
<React.StrictMode>
	<App />
</React.StrictMode>
```
- Replace it with the following snippet to add routing function to components inside the 'BrowserRouter' tags.
```html
<React.StrictMode>
	<BrowserRouter>
		<App />
	</BrowserRouter>
</React.StrictMode>
```
5. Append *'tiukenywil11_portfolio/src/App.js'*.
- Import components from 'react-router-dom'
```javascript
import { Routes, Route } from 'react-router-dom';
```
- Import 'Layout' component.
```javascript
import Layout from './components/Layout/index';
```
- Remove the following snippet inside the return statement on App function.
```html
<div>
  Hello World!
</div>
```
- Replace it with the following snippet to enable Routes.
```html
<>
	<Routes>
		<Route path="/" element= {<Layout/>} />
	</Routes>
</>
``` 
6. Test if ReactJS app is working, and if the page is routed to the 'Layout' component
```bash
npm start
```
- The screen should look similar to this.
![screen-end](/img/project-idea-1-part-3/1_screen-end.png)
  
# Outro  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; The progress I made today adds more functionality to the portfolio, the changes can be found in my GitHub repository [here](https://github.com/tiukenywil11/decentralized-portfolio/commit/4d16ddb05b1edc2ec01472f7c27896333d4506e0).  
  
**Read More:**  
Previous:  
[Decentralized Portfolio: Introduction]({{< ref "project-idea-1-introduction.md" >}})  
[Decentralized Portfolio: Part 1]({{< ref "project-idea-1-part-1.md" >}})  
[Decentralized Portfolio: Part 2]({{< ref "project-idea-1-part-2.md" >}})  

Next:  
[Decentralized Portfolio: Part 4]({{< ref "project-idea-1-part-4.md" >}})  
[Decentralized Portfolio: Part 5]({{< ref "project-idea-1-part-5.md" >}})  
