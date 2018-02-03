---
author: lolloo
type: image
featimg: renm_geo_light/fin_light.jpg
title: Throughts on using geometry as light in Renderman 21
tags: [modeling, maya, renderman, lighting]
category: [renderman]
---

In Renderman 21, when people need a self illumination geometry, for example a light bulb filament or a Neon light tube, there are usually 2 way to do that. One is adding value to 'Grow' attribute in a standard 'PxrSurface'. Two is using 'Pxrblack', treating the geometry as black body object emitting light.

The problem with that statement is that the 'Grow' lighting method is not really a lighting method. It lack basic lighting attribute, like intensity or exporsure. So I went on and did some experiments on my own. What I found is that, 'Grow' attribute is just a 'PxrConstant' shader. 

![result overview]({{site.url}}/img/renm_geo_light/pxrfur_g.jpg ){: .center-image }

<center>PxrSurface,  Grow_gain = 1.0</center>

![result overview]({{site.url}}/img/renm_geo_light/pxrcons.jpg ){: .center-image }

<center>PxrConstant, gain = 1.0</center>

As you can see, the PxrSurface grow gain and PxrConstant gain is practically the identical. The resulting image is virtually identical. What this proves is that, grow attribute actually don't grow. It just treat the mesh as a non-reflective surface with a constant color, no matter the direction the render ray arrive. Another thing worth noticing, if one look carefully, the brick wall behind the neon light did light up slightly. Although, the reflection is very dime, it did appear to light up. The reason behind it is because color a pixel is the summation of reflection and refraction. If there are no light, the refraction value will be zero( but to be 100% correct, Renderman have small default global illumination ). But because of reflection, a pixel can still light up. The smooth part of the wall reflect the render ray and the render ray may hit the neon light on the second path or maybe the forth path. Hence, the wall will appear to be light up.

And now, lets compare the result with PxrBlackBody geometry:

![result overview]({{site.url}}/img/renm_geo_light/fin_light.jpg ){: .center-image }

<center>PxrBlack as the only light source</center>

The light from the black body light up the surrounding geometry, including the wall and the floor. As you can see, there is a clear reflection on the wall behind the neon light. More importantly, everything in the room is light up, which means refraction is hard at work.

As a conclusion, there is only one way to using geometry as light, that is 'PxrBlack'. Both 'Grow' and 'constant color' are the same way to fake a self-Illuminati. But this don't mean 'PxrBlack' is the better shader, 'PxrBlack' will take significantly longer time to render. So if the geometry is not he only light source in the scene, the better choice may just be faking it. 
