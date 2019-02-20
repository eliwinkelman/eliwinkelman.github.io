---
layout: post
title: Trouble with Buoyancy in an Elevator 1
published: true
---

The following problem was a conceptual question in one of my physics classes. It has a simple correct solution, but it also has a clearly incorrect solution that follows from logically working through the free body diagram. Finding the mistake is revealing.

A jar of water sits in an elevator with an apple floating (statically) on its surface. When the elevator accelerates upwards, does the apple sink, rise, or stay at the same height relative to the water?

We can imagine a sketch of the initial (static) situation like this:

(Sketch initial system)

There are only two forces on the apple, gravity and buoyancy. We know the apple is in equilibrium so $F_{ga} = F_{ba}$.

Once the elevator starts moving, we don't get any new forces (on the ball), but the glass is accelerating upwards.

I propose two solution methods: calling on the equivalence principle or working out the free body diagrams of the ball and the jar.

The first method is much quicker so we'll explore that direction first. The equivalence principle states that a system with no internal forces accelerating upwards with acceleration $a$ is indistinguishable from a stationary system with a gravitational force $F_ga=m_{apple}a$ downwards.

This means that our accelerating elevator can be examined as a stationary elevator where our new gravitational acceleration $g_{new} = g + a$.

How does this effect our two forces on the apple?

It shouldn't, because if we look at our equation from before ($F_{ga} = F_{ba}$), substitute the equations for the forces, and simplify,

$$F_{ga} = F_{ba}$$

$$m_{a}g = \rho gV_{submerged}$$

$$m_{a} = \rho V_{submerged}$$

we see that the volume of the apple submerged isn't dependent on gravitational acceleration. So increasing the gravitational acceleration won't change the position of the ball and **it stays in the same place**.

What about the other method?

Our free body diagram looks like this:

(Sketch free body diagram)

The only forces acting on the apple are still $F_{ba}$ and $F_{ga}$.

The forces acting on the jar are the force of gravity $F_{gj}$ and the normal force of the elevator floor pushing up against the jar $F_{nj}$ with $F_{gj}=F_{nj}$ and a force to account for the next acceration of the jar with the elevator $F_{aj} = m_ja$. (Note that this last force could be included in the normal force, but then we wouldn't be able to conveniently preserve the stationary result $F_{gj} = F_{nj}$. So the total force on the jar is 

$$F_{totalj} = F_{gj} - F_{nj} + F_{aj} = F_{aj} = m_ja$$. 

Which gives us the expected result that the jar is accelerating upwards at the same speed as the elevator.

But what about the apple? For the apple to accelerate upwards at the same rate as the elevator and jar, the total force on it must be $F_{aa} = m_{apple}a$.

If we calculate for our total force we get 

$$F_{totala} = F_{ba} - F_{ga} = F_{aa}$$. 

If the apple reaches equilibrium, 

$$F_{ba} = F_{aa} + F_{ga} = \rho gV_{nowsubmerged}$$. 

Since $\rho$ and $g$ are constants the volume of the apple that is submerged must increase, and so **the apple sinks**.

Which one is incorrect? And where is the mistake?
