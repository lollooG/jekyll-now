---
author: lolloo
type: image
featimg: extu_idea/stairs.jpg
title: My throughts on extrude along curve
tags: [modeling, maya]
category: [maya]
---

Creating Stairs is one of the most tedious task in 3D modeling. There are a lot of repetition in the modeling and everything has been very precise.
In the end, I found out that the fastest way of building stairs is first build a curve, and than extrude along the curve to build handrails and other supporting structures. This is by far the fastest way of building stairs.

![result overview]({{site.url}}/img/extu_idea/rebuild_crv.jpg ){: .center-image }

There is also some experience I gained when using the extrude along curve Maya function. At first, I found the rebuild curve function is very useful when I was trying to preserve bend volume. See orange circles. The uniform rebuild curve has the best bend compare to the other two curves. But after closer examination, I believe the original curve gives the best result. Because it concentrate the division near the bend. And the only reason it failed at the orange bend is because I used only 3 points to define the bend. When I use 4 point to define the green bend. The resulting extrude gives much cleaner result. The concentration of divisions is defined by the density of my input control points. So what exactly did this experiment tell us?

There is a hidden( for me at least ) property on any NURB curve, I will called it parameter weight. Parameter is not just the percentage of length as one might believed. For example, when I use the extrude along curve function, It will check how many divisions the user wants and divide the parameter base on this division. But the parameter is not uniformly distributed along the length, the parameter weights more if I draw more CV/EP points, vise versa. 

![result overview]({{site.url}}/img/extu_idea/rebuild_crv.jpg ){: .center-image }

To better explain my point, I wrote a short script. The for loop will iterate from 0, 1, 2... to 10. Which corespondent to parameter percentage, 0%, 10%, 20%... to 100%. And the script will find the point on curve and placed a sphere at that position. As you can see even thought the parameter spans are the same, the span on the curve is not. It is concentrated at the corner, where I draw most of my CV points. But if I rebuild the curve (no matter which rebuild option I chose), the hidden property, parameter weight, will disappear. And now, the parameter is uniformly distributed along the curve length.
I am hoping user were given the option to chose the parameter weight in the future. And at last, like any programmer that get into animation, I used the knowledge above and wrote a procedural stair modeling script and here is the result:


![result overview]({{site.url}}/img/extu_idea/stairs.jpg ){: .center-image }