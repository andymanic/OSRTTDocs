---
layout: default
title: Backlight Strobing/MPRT/ULMB/ELMB
parent: Troubleshooting
nav_order: 2
---

# Backlight Strobing Breaks Results
{: .no_toc }

## To be clear: DISABLE BACKLIGHT STROBING MODES FOR RESPONSE TIME TESTING!
Backlight strobing, which goes by many names:
- ULMB
- ELMB
- MBR
- MPRT
- Aim Stabilizer
Is the enemy of good response time testing. As mentioned in the getting started guide, to measure response times is to measure the change in light level over time. Backlight strobing modes work by disabling the backlight for all but a fraction of the frame time in order to help trick the eyes into perceiving a smoother image than without - which does work, but to state the obvious **IT DISABLES THE BACKLIGHT, MEANING NO LIGHT IS OUTPUT FOR THE MAJORITY OF THE FRAME.** This means we cannot measure the light level change over time, in the absence of light to measure. You ***MUST*** disable any backlight strobing modes before testing with OSRTT. You are welcome to run a test, or use the live view mode, to capture light data on the strobed mode itself to verify manufacturer claims (ie a maker claims 0.5ms MPRT, you can check the on-time to confirm that), but do not expect the tool to provide useful response time data, or potentially function at all, with such a mode enabled.


