---
title: "In-vivo Electrophysiology"
date: 2020-09-15
featured: true
weight: 1
---

Single-cell recording from head-fixed and freely-moving rodents.

![traces of recoded cells](/images/skills/ephy/traces.jpg)

# In my PhD
## Preparation

In the first half of my PhD, I spent a lot of time developing and testing custom tools to use [Thomas Recording tetrodes](https://www.thomasrecording.com/tetrodes-for-other-manipulators) for chronic recordings in rats.
These tetrodes are 95um in diameter with 4 conductive platinum/tungsten wires insulated from one another and laid inside a glass body.
We were buying the raw fibers of 50cm length which were then cut to size, pulled and ground to increase their final impedance.

![tip of a single electrode](/images/skills/ephy/tetrodeTip.png)

Although we had the pulling machine and the grinder from _Thomas Recording_ in the lab, but still, handling <100um fibers is no easy task.
Even if the fiber was pulled well, inserted into the grinder's canula properly, ground to shape, still I had to chemically strip the glass off the other end, glue it to a custom PCB, separate the metal cores, and solder each one to an actual strand of wire which could then be connected to the amplifier.
The image below displays a tetrode coming from the bottom, glued and prepared.
Mind that the green PCB is almost 3x5mm.

![tetrode installed on a PCB](/images/skills/ephy/pcbBoard.png)

After preparing several tetrodes, I loaded them into a micro-drive.
I used 2 types of micro-drive in this project.
A commercial one (more on this in another post) and one custom drive which housed 8 tetrodes in an 2x4 array with a single screw.
This drive, shown in the image below, was designed in the lab based on 3D printed parts (like its body) and some CNC machined parts (like the plate holding the tetrodes).
I machined the CNC parts and manually de-burred the body and assembled everything.

![the drive installed with tetrodes](/images/skills/ephy/drive.png)

The process of building the drive was extremely delicate and stressful.
There were 8 tetrodes, each one at least took 2hr to make, and a drive which took a couple of days to build, and it only needed a small bump to fall and break everything!

Another issue was ensuring that after everything was done, the tips of the tetrodes were at the same level.
This took a lot of time to master, but finally resulted in drives such as the one below, with parallel and relatively-level tetrodes.

![the tips of the tetrodes installed in a drive](/images/skills/ephy/electrodeArrayTips.png)

## Test
The final step, before chronic implantation, was to test the drive in a anaesthetized preparation (under urethane) to check if all the tetrodes and connections were working.
I would just hold the drive and the amplifier in a custom stereotaxic arm and check the quality of the signal in cortex and the striatum (our targeted area).

Finally, I implanted the micro-drive in the dorsal striatum of several animals.
I also affixed the amplifier in the headstage to minimise noise levels and make connecting the cable easier later on.
After recovery, these animals were trained in a treadmill-based task.
Unfortunately, these data are not yet analysed.
However, as an  example, I have prepared the video below, showing a single tetrode implanted in the dorsal striatum synchronised with the behaviour.
There is a neuron that preferentially fires when the animal turns backward on the treadmill.
The video concatenates windows around each spiking event, regardless of behaviour.
(Video source is a high-speed IR camera, that's why it doesn't look that good!)

<iframe title="Tetrode on a treadmill!" width="560" height="315" src="https://www.youtube.com/embed/lpujjEL8krs" frameborder="0" allow="accelerometer; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>