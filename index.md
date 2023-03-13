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

We intend to implement this in Unity, without the help of built in physics engine. That is, we will try to do everything physics-related from scratch. The main physics components will be
 * Simulating gravity
 * Elastic collisions (meaning that no energy is lost within the system due to the collision) of two kinds:
     * ball-to-ball collisions, where the balls should react to eachother depending on their relative speeds and masses
     * ball-to-pin-collisions, where the pins are considered fixed, and the balls should bounce off them depending on angle and speed
 * Normal force, counteracting gravity when the balls become stationary on the ground

The intended end-result is that it should be possible to spawn a desired number of balls, seeing them bounce down through the board before settling in the bins. 
The ball-distribution should be that of a binomial distribution, where most balls should be located in the bins in the center, and then be approximately evenly thinning out to the sides. 

# 2023-02-23 Second post, project specification feedback!

Today we got feedback on our project specification by Chris himself:

"Excellent specification! The project idea is very good (great scenario) and is open to 'A' grade, depending of course on reporting. But since this project usually involves integrating a number of different physical forces together, for an 'A' grade, try to find one specific aspect of the physics simulation that you can go deep into, especially in the report (background equations, etc) and possibly in the implementation."

We are very excited that our idea is ambitious enough to qualify for a possible A grade. It was especially helpful to have emphasised that we need to focus on the physics simulation. The initial idea is to ensure that we pay close attention to the elastic collisions of the balls. However, there might be other aspects to consider. For now though, we are going through with this idea.

# 2023-02-28 Third post, brainstorming and implementation approach.

Today we started brainstorming and formulating a plan about how to attack this project.

The main challenge is that neither of us have much experience with Unity, so the task seems rather daunting since it's such a massive and versatile tool.

We agreed to focus on having a "minimum viable product" ready and focus on the core behaviour (i.e. not spending all our project time on making the textures look fancy).

We looked back on the previous labs that we had done in the course to try to take some inspiration, and also researched some basic tutorials and guides on the web. Of course we also looked into some of the past project blogs for inspiration, but more often than not they only contained some images and text, and not the nitty gritty details about the implementations.

This means that we will be going in to this fairly blind. One challenge we have found is that, since we intend to implement all physics from scratch, we will not be using the physics simulation engine provided by Unity. Since most actual application use Unity's simulation engine (it is one of the main attractors of Unity) it is quite hard to find good sources on how to best do this. Another challenge is that, since Unity is such a widely used tool, there is much discussion going on about it on the internet. This introduces further challenge to finding good information. The information space is simply bloated, and when coming from virtually nothing experience-wise, it is hard to filter out the good from the bad advice. 

In any case we are sure that we will manage to create something satisfying in the end. even if it means we will have to invent our own ways of working!



# 2023-03-02 Fourth post, a MVP using the Unity-provided physics engine and a first try of our own implementation.

After spending time the last few days learning how to operate Unity and watching guides and reading articles it was finally time to get started with some implementing!
In order to get a feel of what we what to accomplish, we started by building a concept using all the tools provided by Unity. This means we utilized the different colliders and settings provided by Unity. We built the board by manually placing out different pegs and created a funnel so balls fall down approximately in the middle of the board. This worked quite well, and given how easy it was to set up, the end result looked quite good and it could easily handle many balls. See below for a screenshot. Unity is a remarkable tool!

![Screenshot](/pictures/galtonboardConceptArt.png)

We started by writing a script that places pegs on the board in a systematic fashion. We also 
