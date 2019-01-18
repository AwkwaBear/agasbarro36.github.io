---
layout: project
type: project
image: images/leg.png
title: Micromouse
permalink: projects/micromouse
# All dates must be YYYY-MM-DD format!
date: 2018
labels:
  - ARM
  - LEGv8
  - Verilog
summary: EE 361 Project: Write a functional LEGv8 Single Cycle Processor in Verilog Code.
---

<div class="ui small rounded images">
  <img class="ui image" src="../images/leg.png">
 
</div>


This is a functional single cycle (non-pipelined) processor is capable of performing basic arithmetic, logic and data operations. It is based on the ARM 64-bit architecture, with 32 registers each 64-bits wide with instruction lengths of 32-bits written in Verilog Code. 

Since the ARM CPU is little endian, the instruction memory in this project is designed to have 64 8-bits for each index. 

The Data Memory is made up of 31 64-bit values to show that the values could be accessed and stored via the CPU. 

Link to Project GitHub Page (https://github.com/agasbarro36/LEGv8-Single-Cycle).



