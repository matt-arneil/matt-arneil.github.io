---
layout: post
title:  "A Visual Scene Management System"
categories: Games
---

[![Example Scene Graph Screenshot]({{site.url}}//assets/img/sceneManagementScreenshot.jpeg)]({{site.url}}/games/2000/01/02/scene-management-system.html)

### Visual Scene Management
The goal with this system was to speed up iteration times and be able to see the flow of a game at a glance. It requires more effort up front compared to a basic scene management script, but once made it's incredibly easy to use.

A node contains a list of scenes that should be active when this node becomes active. A node also has a list of connected nodes "Option 1", "Option 2" etc. that make moving to another scene a simple action. It can be triggered from anywhere using a messaging system to publish a numbered "Option" event to the scene management system, or even more simply by calling a pre-made helper method.

Scenes are grouped in memory zones, which basically means that any scenes not listed in the currently active node, but in the active node's memory group are loaded but set inactive. This allows for pre-loading groups of scenes that are known to link together with little loading in between. Setting a memory group for a node is just an enum dropdown.

Graphs can also contain sub graphs so different parts of a project can be split up to help with readability.

### Project Navigation
A nice bonus for navigating the Unity project itself is that if you double click a node, it will load all of its listed scenes. Much quicker and easier than remembering which scenes need to be opened together, or navigating the folder structure for each scene. 

### Graph UIs for Unity
For a graph, I've used Nody which is included with DoozyUI. It was easy to add custom nodes for my custom functionality and it seemed relatively stable, and best of all I happened to already own it. This graph wasn't intended for a standalone scene management solution but it's feature set was enough to get it working. Ideally I would have used a solution integrated into Unity itself but after many many years a publicly available one still doesn't exist. It does seem like a standard solution is finally on the horizon in the form of the "Graph Tools Authoring Framework", but again that still isn't actually available in a stable way.
