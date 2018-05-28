+++
title = "uBlox NINA-W102 minimal breakout"
description = ""
date = "2018-05-27"
categories = []
tags = []
thumbnail = "/project/nina-w102-minimal-breakout/NINA-W102_minimal_breakout_pcb-front_rev.0.5.png"
aliases = [
    "/ninab/"
]
draft = false
+++

While working on the [badge design for MakeZurich 2018](/project/makezurich-18-badge), I had the need to first make a breakout for the NINA-W102 we got from [ublox](https://www.u-blox.com) to see what is possible, do some tryouts with different components like the display and start developing drivers and firmware we need for it. This is the outcome of it and as we did go on with the badge design, we switched from having a single-board badge to a modular badge where the modules can be reused standalone in a project. Hence on the final badge design you can reuse the display and the NINA-W102 module in your hacks and with a little bit of desoldering you can reuse the sensor module (which we got from [Sensirion](https://www.sensirion.com)) as well.
<!--more-->


## Pinout
{{< figure src="pinout-diagram.png" link="https://github.com/rac2030/breakout-boards/raw/master/ublox_NINA-W102/pinout/pinout-diagram.pdf" target="_blank" attr="Made by gnz.io" attrlink="http://gnz.io">}}

## Sources
KiCAD schematic and PCB design sources are available on my github at https://github.com/rac2030/breakout-boards/tree/master/ublox_NINA-W102

## Team contributions
During the design phase, this board has been reviewed and challanged from various people that are not github commiters. Therefore here I would like to thank all the people who helped going into production:

- Benjamin Marty
- [Dirk Zugenmaier](http://fastfocus.ch)
- [Gonzalo Casas](http://gnz.io)
- Matthias Schibli
- Michael Ammann
- Oliver Walkhoff
- Tillo Bosshart
- Urs Marti

> Note: List is not in a specific order other than taken directly from TTN slack channel mz-badge and I may have forgotten to list someone here, ping me if it's you.
