---
layout: page
sidebar:
  nav: cm
aside:
  toc: true
title:  "Particles"
categories: applied_math classical_mechanics
mathjax: true
---

So I started writing some cool shit last week on setting up physical systems from the ground up, which assumes a non-physics background and I decided to work on this site again in order to have these things online as a possibly useful learning resource. The end goal is to have a physics pages that doesn't look ancient, with a little more body to it, like wikipedia has (and all the links that come with it), with the personality of a blog or some hitchhiker's guide to the galaxy encyclopedia. If I do want to encompass all of physics, it's pretty ambitious, especially considering I'd like to add in simulations, graphs and the associated code (I'll be working in python).

For now, the plan is to keep writing standalone 'articles', which will eventually be linked together with theory reference pages, once I have enough content written out. The following post will build on what I've been writing already (I will upload this in due course), but will be more of a reference for people already familiar with calculus.

Static particles from a modelling perspective (say you wanted to simulate some physical system), can be described simply by a three dimensional position vector in cartesian coordinates, and a mass. The mass of an object allows us to define momentum and in turn, force. We note that these are vector quantities, momentum is another property of the particle, it is zero if the particle is static. Force can apply to a region or a point and therefore influence one particle or many. Therefore, sticking to this modelling perspective, force ought to be considered separately from particles. Momentum is formally defined by the product of the mass and the velocity (a scalar multiplied by a vector). The velocity of a particle is the change of position with respect to time. One can differentiate the vector quantities of particles indefinitely in order to get new crazy descriptors of how these entities behave in space, however, we typically consider only the first two, velocity and acceleration.

Acceleration is a particularly useful quantity because it relates to the force. Hence we consider it but we don't consider anything further, since there usually isn't any physical purpose to do so.

$$\vec{F} = \frac{d\vec{p}}{dt}$$

The derivative of momentum with respect to time is equal to the force, or alternatively, the acceleration is equal to the force divided by the mass (feel free to verify this). An entity worth considering at this point is a frame. The frame contains the system where the particles reside. It contains the space in which we can define position, and it possesses a property of time that governs the motion of the particle. It can also move, and accelerate. A non-accelerating frame is also called a non-inertial frame. In such a frame, the sum of the momenta of everything inside must be constant. Additionally, the total energy of everything inside an isolated frame (one that does not gain or lose energy to its surroundings) must be constant. Under the conditions of this isolated frame, these laws of conservation together with the relationship between force and momentum allow us to predict the motion of particles.

This is a limited picture, but it is already possible to gain substantial physical insight concerning the ways we can use mathematical models to manipulate and explain the world we live in. I'll add a 'to be completed' table to contents (links) here.

1. [projectiles]
2. [lifting tools]
3. [springs]
4. [trampolines](https://ragnamus.github.io/applied_math/diff_eq/ode-2-trampolines.html)
5. [parachutes](https://ragnamus.github.io/applied_math/diff_eq/ode-1-parachutes.html)
6. [collisions]
7. [pressure]
8. [rockets]

Suppose we now extend our picture by considering the non-linear motion of particles. Similarly to how we can break movement into 3 directions a general particle can move linearly, we can express the general rotation of a particle using the same 3 cartesian axes. For an arbitrary rotation in a single axis, one can define the direction as one parallel to the line whose position remains unchanged during the rotation. By convention we pick something such that the math keeps everything consistent. The right hand rule is a helpful tool in determining which direction is correct. Imagine a closed hand with the thumb pointing out. The direction of the curled fingers is the direction of rotation as one would observe it (or intuitively imagine it), the direction of the thumb specifies the vector direction. By thinking of rotations in this vector form, I think it's easier to conceptualise torque and angular momentum.

Suppose the particle moves with respect to some reference point. We have previously established that such a reference point allows us to define position (other quantities like velocity, momentum and acceleration however do not require this). So far we have thought of velocity, momentum, force and acceleration from the perspective of the particle (in the defined space). However, we can also define these quantities in relation to the reference point.

$$\vec{\omega} = \vec{r} \times \vec{v}$$

$$\vec{L} = \vec{r} \times \vec{p}$$

$$\vec{\tau} = \vec{r} \times \vec{F}$$

define angular velocity, angular momentum and angular force (or torque) respectively. The idea is that this type of motion accounts for the kinds of motion that linear motion cannot deal with effectively, and resolves the issues that linear motion has once we depart from this zero size assumption for particles. Similarly to linear motion, angular motion has a set of conservation laws. The sum of angular momenta is constant in a frame that has zero angular accleration (or alternatively if the total torque is zero). Conservation of energy is as before but mathematically we will start to see extra terms when considering rotation (I will go into this later).

We can now add to the list of things we can model. (which I will update)

1. [levers]
2. [wheels]
3. [orbits]

To complete this simple picture of particles, we can define work done, the result of applying force to move particles around. Work done is defined formally as

$$W = \int_{C}\vec{F}\cdot d\vec{x}$$

When applied to particles, we assume constant mass and therefore the work done can be expressed as a path independent integral between two points a and b.

$$W = m\int^b_a\frac{d\vec{v}}{dt}\cdot\vec{v}dt = \frac{m}{2}\int^b_a\frac{d}{dt}(v^2)dt$$

Therefore the work done is the difference between two expressions of the form

$$T = \frac{1}{2}mv^2$$

which is the expression of kinetic energy for a particle. Dissipation forces like friction prevent us from assuming a path independent integral. These forces make the system non-conservative. Sticking to conservative forces for now, one can additionally define a potential function, defined such that

$$\vec{F} = -\nabla V(\vec{r})$$

which is allowed for conservative vector fields. The integral form of the above equation is

$$\int_{C} \vec{F}\cdot d\vec{x} = -\int dV$$

Which is incidentally equal to the definition of work done. This potential function is therefore an energy function like kinetic energy and the work done can be written as a difference in potential energy terms. The law of energy conservation directly follows from this observation (write out the relationship between work, kinetic energy and potential energy for yourself to clearly see this). Essentially for conservative forces, the total energy or the sum of the kinetic energy and the potential energy is conserved. This derivation is not that obvious. For example, we sort of just came up with this potential energy term from the force without any intuitive explanation as to why this might be a useful thing. I haven't even defined potential energy! Kinetic energy was seen to be the energy desribing the motion of the particle. The potential energy can be thought of as the energy the particle must have to exist in a particular region of space where there are conservative forces acting. For example, the force of gravity which pulls all particles towards the Earth (and each other, although this effect is so small we don't consider it) is conservative and therefore can define a related potential V exactly as we showed earlier. As for why potential is defined by that exact equation, it's a result of a theorem in vector calculus, and of course the motivation of having a quantity of that form in the first place is from the defined work done function.
