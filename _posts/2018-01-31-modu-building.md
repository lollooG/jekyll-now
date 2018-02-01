---
author: lolloo
type: image
featimg: modu_building/fin_b.jpg
title: My Custom Module Architect Building Tool
tags: [modeling, scripting, maya]
category: [script]
---

I recently came across a Maya plugin: Ninja Dojo, ninja city (aka, Render ready Demo)
http://www.bk3d.com/Ninja_Dojo/
https://www.highend3d.com/maya/script/render-ready-demo-for-maya

It is a very well written script, but unfortunately the author has stop updating it for newer Maya. Also there are limitations in the software that I dislike (mostly because I am using a different renderer), I prefer tools with more freedom. So I decide to write my own.

![result overview]({{site.url}}/img/modu_building/ui.jpg ){: .center-image }

So on the left side I have the finished script UI. In principle, this script is basically just a duplicator. User can put a mesh or a mesh group name into the "object name" field in the top left side, which will link to the "Module Name" on the left side. And in the main table below, I can use these modules to one by one build the building.

The reason I wrote it this way is because:
One, I can link multiple objects to the same Module Name. So that, when the script duplicates the module, it will randomly choose one from the multiple objects. This is useful when, for example, user has several different window shadings and wants them to be placed at random positions. Two, user may wants different meshes for the ground floor and top floor, but retaining the same basic patterns that established one story below. By linking the object and module this way, user don't have to go into the "Modula Name" field and update each rows in the main table, which is usually much longer than the list above. Also by doing it this way I am not importing object files every time I build a new module. Duplicating is not only faster, but also it wouldn't trigger the student version import warning.

This script's UI is based on pyqt5, which is new for Maya 2017. The reason behind it is because it handles list/table objects better than other UIs I tried. The saving and loading is done by using JSON file format. This way is preferred because the result JSON file is human friendly. User can imminently open it as a text file and see the data just created. But I have to admit, there is a down fall with this method. The saved data has a strong relation with mesh dimension. The saved JSON data can only correctly duplicate modules, if they use the same travel and offsets.

Comparing with Ninja City, my script has less constraints. User have the choice to use any meshes or shaders they want to, no string attached. Functionally, I can place my module at any degree I want, let say 30 degree or 45 degree. Which is very hard to do in Ninja City. Also, I can change my design pattern midway on the building, for example, the base can be a 4x5 pattern. And everything above can be 3x3 pattern. Which in Ninja City I have to stack 2 buildings to achieve the same affect.

And since this script was written within 1 day, I am happy to share it:
