---
layout: default
title: The Basics
parent: Getting Started
nav_order: 2
---

# What even is a Response Time?
{: .no_toc }

In short, response times are the time it takes for a display to change colour. We usually measure all three sub-pixels together, meaning we measure shades of grey. Computers (generally anyway) control colour with an 8 bit byte per colour channel (so 256 times 256 times 256, AKA 16.77 million colours) - but if you tie all three together we have just 256 shades of grey to measure, which for response times is more than enough. The thing we measure is from one RGB value to another. That's called a **transition**.

## Measuring Transitions
The thing we are actually measuring during these transitions is the light level the monitor outputs. The light level over time. Depending on how large the transition is, and how strong the monitor's overdrive is, will generally effect how the transition looks. In OSRTT's case, we measure transitions in steps of RGB 51 - so 0, 51, 102, 153, 204 and 255, for a total of 30 transitions. At the most basic level, RGB 0 to 255 and RGB 255 to 0 are what you might call the basic response time figures - basically black to white, and white to black - but in testing the mid range you often find very interesting behaviours, such as the ones I've documented in the troubleshooting folder. 

## Response time types
For more information on this, please do read the OSRTT Guide linked in the sidebar, but as a brief note:
- Initial Response Time - this is the 'industry standard' measurement. This is the rising or falling edge only, and does not include overshoot time. This will be the fastest measurement.
- Perceived Response Time - this is generally my preferred measurement, as it includes both the rising or falling edge, AND any time spent overshooting the target.
- Complete Response Time - this is the full, end to end, no tolerance included measurement. This is often seen as excessively strict, as not including a tolerance can cause processing issues, and is not often true to the end user experience.

To view these options, with a heatmap open, hit "View" and change between the options. Default is Perceived response time. 

## USE THE GRAPH VIEW MODE!
If you want to know why a response time result looks fishy, or you just want to learn more about the monitor you are testing, hit the "Raw Data Graphs" button at the top of the heatmaps, or import raw data to be graphed, and make use of the interactive graphs to see the raw data in action. You can also toggle the "Denoise Graph" button in the top bar to see what the processing function sees, and to smooth out noisy data.