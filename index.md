---
title: DD1354 ModSim Project blog - Spring 2023
---

Authors: Erik Fahlman (efahlman@kth.se) and Fredrik Östlund (jfmos@kth.se).

This is the landing page for the project blog, here we will document the project journey post by post. Enjoy the ride!


![Screenshot](pictures/eleventh.png)

Latex: 

$X \sim Bin(n, p)$

# 2023-02-16 First post!

This blog will follow the development of a physics simulation project in the course DD1354 Models and Simulations at KTH. 

The project aims to simulate a Galton Board. This is a toy where metal balls are dropped onto pegs that are arranged in a triangle-pattern. On each peg, the ball bounces of the peg and if it is calibrated(well built enough), there is roughly a 50/50 chance that the ball moves either to the right or to the left on each bounce. Each ball follows a binomial distribution **X~Bin(n, p)** where **n** is the number of rows in the board, and **p** is the chance of a bounce in either direction, i.e 0.5.

Together, all balls approximate a Probability Mass Function (PMF) of the binomial distribution (and given enough balls, a normal distribution).

See below for a picture on how it can look like.

![Screenshot](/pictures/galtonBoardProjectSpecification.png)

