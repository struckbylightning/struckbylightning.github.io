---
layout: post
published: true
mathjax: false
featured: false
comments: false
title: Layman`s guide to Lightning Component Framework (Mindmap + Handson)
---
## Here\`s a simple laymans guide to learning Salesforce\`s Lightning Component Framework

Below mindmap and example code will explain,
- What is Lightning component framework
- Javascript basics
- Object Oriented Programming basics
- Lightning component basics
	+ComponentBundle
	+Example OpenTheDoor application which consists of
    	- `OpenTheDoor.app` (container for holding the guy & the door)
        
```html
<!-- OpenTheDoor.app (container for holding the guy & the door)-->
```
    	- `guy.cmp` (On clik of 'Knock Knock!' fires openDoor Event)
        
   ```html
    	<!--`guy.cmp` (On clik of 'Knock Knock!' fires openDoor Event)-->
```
   		- `openDoor.evt` (fired when guy knocks the door)    
        
```html
        <!--`openDoor.evt` (fired when guy knocks the door)-->       
```
       	- `door.cmp` (Listens(registers) to the openDoor event and accordingly opens the door acknowledging the receipt of the event)
        
        ```html
        <!--`door.cmp` (Listens(registers) to the openDoor event and accordingly opens the door acknowledging-->
```
  
  <embed src="{{site.baseurl}}/images/lightningComponentMindMap.pdf" width="800px" height="1100px" />
_Mind Map_


