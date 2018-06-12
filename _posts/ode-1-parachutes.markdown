---
layout: page
title:  "Parachutes"
date:   2016-10-09 19:04
categories: applied_math diff_eq
mathjax: true
---

Over the centuries, many scientists have performed experiments involving the nature of falling objects. As a result, we can make certain assumptions when thinking about people falling through the sky. Firstly, they fall directly towards the surface in more or less a straight line. Secondly, the time it takes to fall a certain distance is the same regardless of how heavy a person is. Physicists like to write mathematical relations to describe these observations. In the case of a falling entity we have

$$t\propto\sqrt{d}$$

where d is the height at which we start timing the fall, and t is the time that it takes to hit the ground. The relation was derived by noticing that every time the distance was increased by say a factor of four, the time taken to hit the ground would double, hence the square root relationship. One can rearrange and find the distance travelled as a function of time.

$$d(t)=ct^2$$

where c is some constant. Since velocity is the change of displacement with respect to time, and acceleration is the change of velocity, one can deduce that the speed of a falling object is proportional to the time from whence it was dropped, and the acceleration does not change at all (by the rules of differentiation).

This is significant because objects according to this model, don't slow down! So falling is definitely fatal, if you start high enough. Of course, we know that height is not the only thing that determines your survival, or parachutes would not work. So what is wrong with the model? Now in physics, it's important to remember that we don't know how to simulate anything exactly, we make models that closely resemble the truth (the goal being that one day, our model of the universe will be 100% accurate). Today, I'll stick to Newtonian physics which is a simplification of the model we currently have, and most of the time, works very well. Newton's laws include a force acceleration relationship which is incredibly important for most of the physical calculations we will ever encounter. Simply force is proportional to acceleration, double the force, double the acceleration. So all we need to do is know what forces are acting on an object, and we know how it moves around.

This is great because now we know that there is in fact a constant force that acts on a falling body, despite our inability to see it. Up until now I have kept the constants unknown but I will replace these with known attributes so that it's easier to see what's going on. $$F = ma = mg$$ where F is the force, m is the mass of an object and g is the constant acceleration when falling. Now let's work backwards. What if we know this relation $$F = mg$$ and we want to know where something is at a particular time? This isn't as easy. First we write a relation between displacement and something we do know,

$$\frac{d^2x}{dt^2} = a = g$$

where $$x$$ is displacement. This is known as a differential equation. Alternatively, one can try and find the velocity at some given time, so that the differential equation takes the form

$$\frac{dv}{dt} = g$$

I will start with this equation and come back to the other one later.

The above equation is a first-order differential equation (read to the end for more details about this). It is separable, which means you can integrate both sides of the equation and solve each side independently. We end up with two integrals

$$\int dv = \int gdt$$

which is trivial to solve,

$$v = gt + c$$

where the c is a constant. Note that each integral will generate a different constant but we can combine the two. We see the speed increases indefinitely with time. Now what if there was a force opposing a falling object? Would the speed carry on increasing to infinity, or will we reach a limit? Clearly if we just add a constant force, the equation becomes

$$\frac{dv}{dt} = g - b$$

and since g and b are constants, they can be combined and we have effectivly the same scenario (assuming b was less than g). Now what if this drag force b was proportional to the velocity and also separately dependent on time in some fashion (say the parachute takes time to open )? As the object got faster, the opposing force would increase. Once the force equalled the force pulling the object down, the net force would be zero and there would be no change in velocity! This seems to be what a parachute does, it limits the velocity of a falling object thus preventing death.

This new scenario is a non-separable equation. We have

$$\frac{dv}{dt} + b(t)v = g$$

How can we solve this? Clearly this is non-trivial, unless we have some mathematical insight into what is going on. Unfortunately, this is one of those cases where it is incredibly difficult to see what is happening unless you already know how to solve such an equation. However, I will try to be more thorough than most textbooks that simply assume the answer. In practice when solving such problems, it is not necessary to be so rigorous. The general idea is to use the product rule. For functions of t, x and y, it is known that

$$\frac{d}{dt}(xy) = x\frac{dy}{dt} + y\frac{dx}{dt}$$

Now suppose it is possible to convert the differential equation we intend to solve into this equation given by the product rule. The left hand side of our equation already has a $$v$$ and a $$\frac{dv}{dt}$$ term, so we just need to determine the other function. However as the equation is at the moment, nothing fits. So we multiply both sides of our differential equation by some third function of $$t$$, call $$\mu(t)$$. Now

$$\mu\frac{dv}{dt} + b\mu v = \mu g$$

and therefore we now have two functions $$v$$ and $$\mu$$. By matching the terms of this equation with the product rule, the derivative of $$\mu$$ is simply $$b\mu$$ and the derivative of $$v\mu$$ is $$g\mu$$. First we solve for $$\mu$$ and then once we have it, solving for $$v$$ becomes a lot easier.

The equation for $$\mu$$ is a separable differential equation, this is the case for any equation of the type

$$y'+A(x)y = f(x)$$

our equation is just an example of this generalization. So we have

$$\frac{d\mu}{dt} - b\mu = 0$$

which on division by $$\mu$$ followed by integration by $$t$$, becomes

$$\int\frac{d\mu}{\mu} - \int b(t)dt$$

which can be solved to get

$$\ln\mu = \int b(t)dt + c$$

where $$c$$ is the constant of integration. Hence

$$\mu = A\exp(\int b(t)dt)$$

where $$A$$ is a constant equal to the $$\exp c$$. Now that we know $$\mu$$, we solve for $$v$$,

$$\frac{d(v\mu)}{dt} = g\mu$$

$$v\mu + c = \int g\mu dt$$

$$v\mu = Agb\exp(bt) - c$$

$$v = \frac{g}{b} + c\exp(-bt)$$

To solve for the constant, we need some boundary or initial condition. Here it makes most sense to assume that at $$t = 0$$, the speed is zero. Once we solve the constant, we get

$$v = \frac{g}{b}(1 - \exp(-bt))$$

I haven't figured out how to do graphs yet, but you'll get something that looks like an increase in velocity with increase in time, only there's a limit in the velocity! The velocity increase slows down and never actually reaches a certain point. This 'terminal velocity' can be calculated and it turns out it can be written $$g/b$$. So if $$b$$ is large enough, the limit in the falling speed can be made low enough so as not to permanently damage the object.

Let's take a step back and consider the problem from a non-mathematical perspective, how do parachutes do what they do? Well, one simplified way to think about it is to consider simply what air does. Back when scientist first formulated the rules governing falling bodies, they did so under the assumption that they were in a vacuum. That is, the reason acceleration can be slowed down is because we are not in a vacuum, it is the prescence of air that changes everything. But we can't see air, how do we know it exists? This is actually a big question to consider, in physics, we should not really assume the existence of anything. Fortunately with the aid of machines, we can verify the existence of air, but without them we must rely on observing it indirectly; how it affects the world around us. Air is everywhere and it pushes back on objects moving around. In the case of falling objects, air pushes back at them, it pushes up. The faster something is moving against air, the stronger this pushing force. You may hear the term pressure used to describe this kind of effect. In the case of the parachute, the air under the parachutes pushes upwards against the direction of motion, the result being an upward force which is proportional to the speed of the parachute, and the surface area.

The actual drag force equation is difficult to derive, and most cases require approximations. I'll just state the result and maybe come back to it one day. I got this from the [NASA][NASA] website,

$$F_d = \frac{k\rho v^2 A}{2}$$

where A is the surface area, and $$\rho$$ is the density of the air. I'll assume we have no control over these and we just want to look at the change in speed over time, so I'll write this as $$bv^2$$. The new differential equation which more accurately describes parachutes is

$$\frac{dv}{dt} + bv^2 = g$$

The result should be similar to beforehand, there should be a terminal velocity and the object never decelerates. I won't go into this because unless the drag b is constant, the equation is somewhat more tricky to handle (I think? I might come back to this). Hopefully you can see what the result of the differential equation should look like after thinking about how it's essentially the same as the case I described beforehand.

Now drag is never straightforward. So let's consider a particularly ugly looking scenario where the drag is approximated by a polynomial. I will ignore effects of gravity since this creates another ugly level of complexity. Take a look at the following differential equation

$$\frac{dv}{dt} + av + bv^3 = 0$$

This is unsolvable with any of the methods we have discussed so far. However it is possible to find a substitution. This equation is an example of a Bernoulli equation and is comprised of a y term, a y' term and some power of y, call this power n. The trick is to call $$u = y^{n-1}$$ and the equation becomes separable. In this case, call $$u = v^{-2}$$ and one gets

$$-\frac{du}{2dt} + au + b = 0$$

$$\int\frac{du}{au+b} = \int 2dt$$

$$u = \frac{1}{a}(\exp(2a+c)-b)$$

$$v = \sqrt{\frac{a}{\exp(2a+c)-b}}$$

If we include gravity? Look up [Chini][Chini] equations. These have not been solved in the general case.

[NASA]: https://www.grc.nasa.gov/www/k-12/airplane/drageq.html
[Chini]: http://www.maplesoft.com/support/help/Maple/view.aspx?path=odeadvisor/Chini
