---
title: "Project Idea 1 (Decentralized Portfolio): Part 6"
date: 2022-05-22T11:36:43+08:00
tags: ["project idea 1", "decentralized portfolio", "full stack", "reactjs", "javascript"]
description: "Part 5: Project idea to create a portfolio with decentrailized web3 technologies"
author: "Kenywil Tiu"
---
# Introduction

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; On the previous blog, We have completed the "Sidebar" component. I encountered somr problems on nesting scss, but found a system to follow, so that it'll be more manageable. I will be resuming with the [Youtube tutorial](https://youtu.be/bmpI252DmiI). 

# Steps
For this day I decided to start with programming the styles (scss) for the 'Layout' component. This should help me visualize where my components will be placed.

## Fix 'Layout' component CSS
1. Open *'tiukenywil11_portfolio/src/components/Layout/index.scss'*
- Add style for '.page' class.
```css
.page {
    width: 100%;
    height: 100%;
    position: absolute;
}
```
- Add style for '.top-tags' class.
```css
.top-tags {
    bottom: auto;
    top: 35px;
}
```
- Add style for '.tags' class.
```css
.tags {
    color: #000000;
    opacity: 0.6;
    position: absolute;
    bottom: 0;
    left: 120px;
    font-size: 18px;
    font-family: OpenSans;
}
```
- Add style for '.bottom-tag-html' class.
```css
.bottom-tag-html {
    margin-left: -20px;
}
```

2. Open *'tiukenywil11_portfolio/src/components/Layout/index.js'*
-Inside 'Layout' class' return statement, Wrap 'Sidebar' component with div with class name 'App'.
```html
<div className='App'>
    <Sidebar />
<div>
```
- Below 'Sidebar' component, add div with class name 'page'
```html
<div className='page'>
</div>
```
- Inside class name 'page', add span tag with class name 'tags' and 'top-tags'. 
    - This will add the `<body>` tag on the top of the web page.
```html
<span className='tags top-tags'>&lt;body&gt;</span>
```
- Below class name 'tags' and 'top-tags', add an *Outlet'* component. 
    - **Note:** This will cause an error, so temporarily comment out
```html
{/*<Outlet />*/}
```
- Below 'Outlet' component, add span tag with class name 'tags' and 'bottom-tags'. 
    - This will add the `</body>` tag on the bottom of the web page.
```html
<span className='tags bottom-tags'>&lt;/body&gt;</span>
```
- Inside class name 'tags' and 'top-tags', add  ay `</br>,`, then a span tag with class name 'bottom-tag-html'. 
    - This will add the `</html>` tag on the bottom of the web page.
```html
<br />
<span className='bottom-tag-html'>&lt;/html&gt;</span>
```
3. Test if ReactJS app is workin.
```bash
npm start
```
- The screen should look similar to this.
![screen-end](/img/project-idea-1-part-6/1_screen-end.png)

# Outro  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; The progress I made today adds some helpful features for our 'Layout' component. The changes can be found in my GitHub repository [here](https://github.com/tiukenywil11/decentralized-portfolio/commit/8c4417a6f33860790020b1fc8c06a27ae78baaa4)

**Read More:**  
Previous:  
[Decentralized Portfolio: Introduction]({{< ref "project-idea-1-introduction.md" >}})  
[Decentralized Portfolio: Part 1]({{< ref "project-idea-1-part-1.md" >}})  
[Decentralized Portfolio: Part 2]({{< ref "project-idea-1-part-2.md" >}})  
[Decentralized Portfolio: Part 3]({{< ref "project-idea-1-part-3.md" >}})  
[Decentralized Portfolio: Part 4]({{< ref "project-idea-1-part-4.md" >}})  
[Decentralized Portfolio: Part 5]({{< ref "project-idea-1-part-5.md" >}})  
