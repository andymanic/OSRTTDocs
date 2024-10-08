---
layout: default
title: Unusual Behaviours
parent: Troubleshooting
nav_order: 3
---

# Monitors are Weird
{: .no_toc }

## Documenting weird behaviours
Monitors do weird stuff, a lot. In my years of looking at response time data, I've been stumped more than once, and while many I can now explain, and the tool can handle on it's own, I thought that documenting interesting behaviour may be helpful in allowing others to learn more about what they are testing. So, here goes!

## PWM Backlight Control 
![PWM backlight ripple shown on light level over time chart]({{site.baseurl}}/assets/images/weird-behaviours/pwm1.png)
See that ripple in the otherwise steady-state light level? That is a pulse-width-modulated backlight that pulses slightly throughout a frame cycle. If you see this in the raw data, you are in luck! Not only do you now know it has a PWM controlled backlight, but you can also confirm adaptive sync is working properly! How? Easy. Run a test with adaptive sync enabled, and set the framerate limit to below the refresh rate - so for a 180Hz monitor, set the FPS limit to 100 FPS or something, as long as the FPS limit is LOWER than the refresh rate, you're golden.
![Close up of PWM backlight ripple shown on light level over time chart]({{site.baseurl}}/assets/images/weird-behaviours/pwm2.png)
Now looking at the raw data graphs again, drag the edges of the green box to line up with one cycle of the pulsing. The measurement on the right hand side will then read out how long it is inside the green box, and that's your frame time. You can do 1000 divided by that figure to get the frequency - ie 1000 / 8.3 = 120 Hz - so if that figure matches the FPS limit, wonderful! Adaptive Sync is working. If it still matches the refresh rate though... Well congrats, you've got a good story to run! 


## OLED Adaptive Brightness Limiters
![OLED light level over time graph]({{site.baseurl}}/assets/images/weird-behaviours/oled1.png)
OLEDs do a lot of weird stuff, but the creme of the crop is the adaptive brightness limiter, or ABL for short. ABLs are an unfortunate consequence of mostly W-OLED panel technology not being able to sustain high brightness levels without damaging themselves. They also can be an issue when it comes to measuring response times. To get around this, when the test window opens, hit ALT + ENTER to make it windowed, then resize the window to be as small as the OSRTT unit is on your screen. The smaller the window, the less the ABL will be triggered by high light levels. You can also try testing at lower brightness settings, which may help limit the ABL's harsh cutback - although it can be useful to still capture this data to be able to profile the ABL for your review. You might find setting the capture time to a smaller time frame (say 100ms) might help hide the trail-off too, or setting it to 250ms and one run to capture as much of the ABL's behaviour as possible may be useful for profiling. 

It's also worth pointing out from that image that OLEDs flicker at the start/end of each frame. I still need to speak to an engineer about why they do that...

## OLED Overshoot
![OLED light level over time graph]({{site.baseurl}}/assets/images/weird-behaviours/oled2.png)
OLEDs also have a weird habit of overshooting for one frame. Some do this on rising only, some falling only, and some both ways. This overshoot lasts for one whole frame, and although normally it isn't noticable to the eye, and therefore likely shouldn't be included in your measurements where possible. You might want to use the Initial Response Time for these sorts of panels and issues. 

