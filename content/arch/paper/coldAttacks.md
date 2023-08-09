---
title: "ColdAttacks"
date: 2023-08-07T14:20:40+08:00
draft: true
---

[The paper link](https://www.usenix.org/legacy/event/sec08/tech/full_papers/halderman/halderman_html/index.html)

##  paper summary

We always assume that the data in the merory will be lost immediately after the power shutdown. But it may be keeped in the memory for some time, so it is possible to recover the data like password or other informations.

## The effect to dram 

- If we recharge the machine, the data in the dram will be lost.
- The windows with the bigger densities will be more difficult to recover.
- The bios may destruct the memory during the POST(power on self test). 
