---
title: "Project Idea 1 (Decentralized Portfolio): Part 4"
date: 2022-05-02T14:26:18+08:00
tags: ["project idea 1", "decentralized portfolio", "full stack", "reactjs", "javascript"]
description: "Part 4: Project idea to create a portfolio with decentrailized web3 technologies"
author: "Kenywil Tiu"
---
# Introduction

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; On the previous blog, I have added a 'Layout' component, and added routing pointing to the 'Layout' component utilizing 'react-router-dom'. The steps are very straightforward, and I encountered no problem. I will be resuming with the [Youtube tutorial](https://youtu.be/bmpI252DmiI). 

# Steps  
For this day I decided to add the logo assets, and a 'Sidebar' component. I will create a separate blog for programming the styles (scss) for the 'Sidebar' component.

## Making logos
1. Use [Online PhotoSoft](https://www.onlinephotosoft.com/).
- Click on 'New Project'.
![1_Photopea_1](/img/project-idea-1-part-4/1_Photopea_1.png)
- Change name to *'Logo'*
- Choose the 'Screen' tab.
- Pick the 'HD' template.
- Click the 'Create' button.
![2_Photopea_2](/img/project-idea-1-part-4/2_Photopea_2.png)
- Pick the 'Text' tool, which has the 'T' icon on the left sidebar.
![3_Photopea_3](/img/project-idea-1-part-4/3_Photopea_3.png)  
- Type any letter, for me it would be my initial.
- Change the font and size to whatever preference you have, for me I made it sized '500px' and use the font 'Open Sans ExtraBold'
- Center the text.
![4_Photopea_4](/img/project-idea-1-part-4/4_Photopea_4.png)  
- On the layers tab on the right side of the screen, right click and duplicate your initial text.
- Highlight and change the color of the text, for me I made it pastel orange (#ffb347).
![5_Photopea_5](/img/project-idea-1-part-4/5_Photopea_5.png)  
- Move the second letter by pressing the 'right directional button' on your keyboard.
![6_Photopea_6](/img/project-idea-1-part-4/6_Photopea_6.png)  
- On layers, remove the 'Background' layer so the image would have a transparent background.
- Press the 'file' button on the toolbar on the top left side of your screen.
- Click 'Export as', then choose 'PNG'.
- Press 'Save as PSD' to have save an editabble copy.
![7_Photopea_7](/img/project-idea-1-part-4/7_Photopea_7.png)  
- Click the 'Save' button on the screen that popped up.
- A file called 'Logo.png' would be downloaded.
![8_Photopea_8](/img/project-idea-1-part-4/8_Photopea_8.png)  

2. Create the following directory *'tiukenywil11_portfolio/src/assets/images'*.
3. Copy the following to *'tiukenywil11_portfolio/src/assets/images'*.
	- Logo.png
	- Optional: Logo.psd
- Note: Reference for images can be found [here](https://github.com/bobangajicsm/react-portfolio-website/tree/master/src/assets/images). These assets are used on the original Youtube tutorial by freeCodeCamp I'm following.

## Creating a 'Sidebar' component
3. Create the following directory *'tiukenywil11_portfolio/src/components/Sidebar'*.
4. Create the following files inside *'tiukenywil11_portfolio/src/components/Sidebar'*.
	- index.js
	- index.scss
5. Append *'tiukenywil11_portfolio/src/components/Sidebar/index.js'*.
- Import 'Link' from 'react-router-dom'.
```javascript
import { Link } from 'react-router-dom';
```  
- Import *'tiukenywil11_portfolio/src/components/Sidebar/index.scss'*.
```javascript
import './index.scss';
```  
- Import *'tiukenywil11_portfolio/src/assets/images/Logo.png'*.
```javascript
import Logo from '../../assets/image/Logo.png';
```  
- Create functional component 'Sidebar'.
```javascript
const Sidebar = () => {
	return <></>
}
```
- Add div tags with class name 'nav-bar' in the return statment for Sidebar function.
```javascript
const Sidebar = () => {
	return 
    <div className='nav-bar'>

    </div>
}
```
- Add a 'Link' component from 'react-router-dom'.
```javascript
const Sidebar = () => {
	return (
		<div className='nav-bar'>
			<Link className='logo' to ='/'>
				<img src={Logo} alt="logo" />
			</Link>
		</div>
	)
}
```
- Export component so it could be used by other components.
```javascript
export default Sidebar;
```  
6. Test if ReactJS app is working, the screen would look similar to [Part 3]({{< ref "project-idea-1-part-3.md" >}}), because we have not imported the 'Sidebar' component to the 'Layout' component yet.

```bash
npm start
```

# Outro  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; The progress I made today adds a new component that would be styled on the next blog, the changes can be found in my GitHub repository [here](https://github.com/tiukenywil11/decentralized-portfolio/commit/ae9de68ba583ae7dbfca0bfab9cb1ddce266bad9).  
  
**Read More:**  
Previous:  
[Decentralized Portfolio: Introduction]({{< ref "project-idea-1-introduction.md" >}})  
[Decentralized Portfolio: Part 1]({{< ref "project-idea-1-part-1.md" >}})  
[Decentralized Portfolio: Part 2]({{< ref "project-idea-1-part-2.md" >}})  
[Decentralized Portfolio: Part 3]({{< ref "project-idea-1-part-3.md" >}})  
