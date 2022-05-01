---
title: "Project Idea 1 (Decentralized Portfolio): Part 2"
date: 2022-04-30T14:21:00+08:00
tags: ["project idea 1", "decentralized portfolio", "full stack", "reactjs", "javascript"]
description: "Part 2: Project idea to create a portfolio with decentrailized web3 technologies"
author: "Kenywil Tiu"
---
# Introduction

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; On the previous blog, I have already created a ReactJS template, and installed different dependencies we will be using for the project. There isn't much complications that occured for me, so I will be resuming with the [Youtube tutorial](https://youtu.be/bmpI252DmiI).  
  
# Steps
For this day I decided to add some prettier configurations, and add global styles using css, and sass.

## Configurations
1. Add a new file called **'.prettierrc'**.
- This would be a configuration file which helps when formatting codes. 
- This would be placed inside the *'tiukenywil11_portfolio'* directory.
- It will contain the following code snippets.
```json
{
    "trailingComma": "es5",
    "tabWidth": 2,
    "semi": false,
    "singleQuote": true
}
```

## Global styles
2. Add a new file called **'App.scss'**.
- This is a sass file, which would be used to replace App.css. 
- This would be placed inside the *'tiukenywil11_portfolio/src'* directory.
- This is where we will put our global styles.

3. Add the following snippets to **App.scss**
- Add the primary color that is going to be used by the portfolio, primary color I picked was pastel orange, with hex #ffb347.
```css
$primary-color: #ffb347;
```
- Import **animate.css**
```css
@import 'animate.css';
```
- Add a font face.
	- Download a font face from the internet, for me I'm going to use 'Open-Sans, which can be downloaded [here](https://fonts.google.com/specimen/Open+Sans).
	- Create the following directory *'tiukenywil11_portfolio/src/assets/fonts'*
	- Extract and place the downloaded *.ttf* files in the *'fonts'* directory.
```css
@font-face {
	font-family: 'OpenSans';
	src: url('./assets/fonts/OpenSans-Regular.ttf') format('ttf');
}

@font-face {
	font-family: 'OpenSans-SemiBold';
	src: url('./assets/fonts/OpenSans-SemiBold.ttf') format('ttf');
}

@font-face {
	font-family: 'OpenSans-Bold';
	src: url('./assets/fonts/OpenSans-Bold.ttf') format('ttf');
}
```	
- Add default font face for 'input' and 'textarea' classes.
```css
input,
textarea {
    font-family: 'Open Sans';
}
```

4. On *'tiukenywil11_portfolio/src/index.css'*.
- Remove the following pre defined snippets.
```css
code {
  font-family: source-code-pro, Menlo, Monaco, Consolas, 'Courier New',
    monospace;
}

body {
  margin: 0;
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Roboto', 'Oxygen',
    'Ubuntu', 'Cantarell', 'Fira Sans', 'Droid Sans', 'Helvetica Neue',
    sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
```
- Add the following css snippet, to fix font size in html tag.
```css
html {
  font-size: 62.5%;
}
```
- Add the following css snippet, to fix the font on 'body' tag.
- font-family:'[default font-family]','[backup font-family]' 
- color: black
- background: white
```css
body {
	margin: 0;
	font-family: 300 11px/1.4 'Open Sans', 'sans-serif';
	color: #000000;
	background: #ffffff;
	overflow: hidden;
	display: block;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
}
```
  
5. On *'tiukenywil11_portfolio/src/App.js'*.
- Remove the following snippet.
```javascript
import logo from './logo.svg';
import './App.css';
```
- Replace it with this snippet.   
```javascript
import './App.scss';
```
- Remove the following snippets after the word 'return'.
```html
<div className="App">
  <header className="App-header">
	<img src={logo} className="App-logo" alt="logo" />
	<p>
	  Edit <code>src/App.js</code> and save to reload.
	</p>
	<a
	  className="App-link"
	  href="https://reactjs.org"
	  target="_blank"
	  rel="noopener noreferrer"
	>
	  Learn React
	</a>
  </header>
</div>
```
- Replace it with this snippet: This is to check if the styles have taken effect.
```html
<div>
	Hello World!
</div>
```

6. Test if ReactJS app is working, and if the styles have taken effect.
```bash
npm start
```
- The screen should look similar to this.
![screen-end](/img/project-idea-1-part-2/1_screen-end.png)

# Outro  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; The progress I made today adds to the base boilerplate, the changes can be found in my GitHub repository [here](  https://github.com/tiukenywil11/decentralized-portfolio/commit/d255e1ca3497fe4232d2959a1cc28e1c0dc1c18f). 
  
**Read More:**   
Previous:  
[Decentralized Portfolio: Introduction]({{< ref "project-idea-1-introduction.md" >}})  
[Decentralized Portfolio: Part 1]({{< ref "project-idea-1-part-1.md" >}})
  
Next:  
[Decentralized Portfolio: Part 3]({{< ref "project-idea-1-part-3.md" >}})  
  