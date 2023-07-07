---
title: "Deconstructing Commit"
date: 2023-07-07T09:31:32+08:00
---

# Deconstructing Commit

[link to the paper pdf](https://pharm.ece.wisc.edu/papers/ispass2004gbell.pdf)

## 1. Summary

This paper introduce the OoO commit in the cpu, which is less concerned than the OoO execution and branch prediction.

## 2. position of the commit

Commit is usually is last stage of the cpu. In the commit stage the resources allocated by rob, regfile... will be freed.

## 3. Why commit in order?

Commit inorder can avoid many problems like waw conflict or commit the misprediction instructions.


## 4. The condition for the OoO commit


### 4.1 Finished the execution

Before commit the instructions, it should complete it access to all of the function units.


### 4.2 WAR Hazard

A store instruction can not be commit until the load to the target register is already committed.

### 4.3 on the right branch

The instruction can not be commit when it knows it is on the right branch


### 4.4 there is no older instruction may raise exception

when there is no older instruction will raise exception, it can commit safely.

### 4.5  Replay Traps
For a memory operation to commit early it must be known
that an instruction is free from store-load and load-load replay
traps. 




