---
title: Convert any photo to seamless texture
layout: post
type: image
homedisplay: featimg
author: lolloo
featimg: seamless_script/leave_tile_expl.jpg
comments: true
tags:
- texture
- script
- maya
category:
- script
- featuring
---

# **Overview:**
I wrote a script that run in mayapy. It can convert photos into seamless tile. The quality of the result will obviously depended on the original image. Some images are just not made for seamless texture. The program itself is using a algorithm, minimal error boundary. The algorithm is a variation of another more famous algorithm called, seam curving. Seam curving is covered in most university level computer vision programming classes. It is almost a rite of passage for any programmer in the field of graphic or image editing. And because the algorithm uses dynamic programming. some advance programming courses will also use it as assignment or project.
<br/><br/>
![eamless_script UI]({{ site.baseurl | replace: '//', '/' }}/img/seamless_script/ui.jpg ){: .center-image }
<br/><br/>
# **What is Seamless texture?**
Seamless image, basically means the left side of the image matches the right side of the image. Same with the top and bottom side. This is useful because in a modeler may want to cover a large geometry with the same repeating textures.
<br/><br/>
![leave_tile]({{ site.baseurl | replace: '//', '/' }}/img/seamless_script/leave_tile_expl.jpg ){: .center-image }
<br/><br/>
# **My method:**
As the picture shown, the trick is overlapping the left and right part of the image. And to find the best seam to combine the image I am using the algorithm I mentioned above. To understand the algorithm I include this link for more detail.
<br/>
To make the image both vertical and horizontal seamless, I rotate the image and ran the same process again.
<br/>
Also, I included a check box in my UI to center the image. What it means is that do I preserve the original center of the original image. As you can see, the way I merge my image will split the center of the original image. In some case, user may still want to persevere center, so I offered the option to center it.
<br/><br/>
![method explain]({{ site.baseurl | replace: '//', '/' }}/img/seamless_script/method.jpg ){: .center-image }
<br/><br/>
Operation Demo:
[link to video](http://)