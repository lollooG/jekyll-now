---
title: My Facial Animation Solution
layout: post
type: image
homedisplay: featimg
author: lolloo
featimg: facial_anim/header.jpg
comments: true
tags:
- rigging
- animation
- maya
category:
- rigging
---

After testing a few different facial animation methods in Maya, I settle down with my own method. 
<br/>The ideal is to combining curved based animation and blendshape based animation, utilizing custom python script to get the best of both worlds.
<br/><br/>
<center>Gernel Oervew</center>
![overview]({{ site.baseurl | replace: '//', '/' }}/img/facial_anim/overview.PNG ){: .center-image }
<br/><br/>
Blendshape based facial animation is the most accurate and user-friendly way I found so far, but to perform a blendshape deform the machine have to check topology of all the blendshape copies, which preform-wise is very costly. 
<br/>Curved based deform is very light-weight, but user often don't get the optimal result because different curve usually interfere with each other.
<br/><br/>
As a result, I wrote my own method. First, I copied the face mesh using it as blendshape pipe. Second, I will create curves based on the model's facial structure. Third, the curves were build based on joints, I would use these joints to skin my blendshape mesh. And at last, I will copy and blendshpe the curves and create a blendshape control, so that, I have use my copied curves to blendshape deform the curves on the copied mesh. And pipe all my deform into my original mesh.
<br/><br/>
<center>Finished controls</center>
![control handles]({{ site.baseurl | replace: '//', '/' }}/img/facial_anim/contorls.PNG ){: .center-image }
<br/><br/>
 The whole idea is to use curves to replace blendshape mesh. And by doing blendshape blending on curves, we can accelerate the deformation calculation speed.