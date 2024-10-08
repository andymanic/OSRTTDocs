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




