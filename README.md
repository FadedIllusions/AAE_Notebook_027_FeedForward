# AAE_Notebook_027_FeedForward
![Controller Math](/images/controller_math.png)

When working with the proportional controller, our vehicle was made aware of the error in position from the target. When working with a derivative controller, our vehicle was made aware of its error in velocity when approaching the position of the target trajectory. What if we had a trajectory that moved relatively quickly and we, also, needed to make the vehicle aware of some target acceleration(z_dot_dot_target)?

Enter the world of the feed forward controller.


### Feed-Forward PD Controller

Thusfar, when considering our Feed-Forward PD Controller, we have...

![FF PD Controller](/images/ff_control.png)

Which is just the derivatives of our error...

![Error Derivatives](/images/error_derivatives.png)

And can be rewritten as...

![Rewritten Equation](/images/rewritten_equation.png)

And, thus, when tuning our parameters, we can consider the following...

![Controller Tuning](/images/controller_tuning.png)

For a visual representation, consider...

![Visual](/images/visual_representation.png)

A big value (close to 1) of damping ratio (delta) yields to a faster decay. A smaller value (close to 0) constitutes, instead, a slower decay.

A big value of natural frequency (omega) causes high frequency oscillations. Smaller values of omega, instead, reduce the oscillations' amplitude.

The behavior of the PD controller's equation is a sinusoidal oscillation, whose amplitude is modified by a decaying exponential.

***   ***   ***   ***   ***   ***   ***   ***   ***

### PD Tuning Considerations

![PD Tuning Considerations](/images/pd_considerations.png)

There are very useful approximate relationships that one can derive for the above reparameterization. For a PD Controlled, double-integrated system, the response to a target altitude change looks something like the above diagram. 

As noted in the diagram, there are some properties of this response that we may want to tune... We tend to want to minimize overshoot, minimize rise time (within the constraints of our system), and minimize the overall settling time.

Being as second-order systems are so well understood, we can come up with equations that will tell us exactly what these quantities will be. Furthermore, each of these quantities have an associated design rule. (For example, if we want to increase the rise time, we have to decrease the natural frequency of the system.)

Tuning a system depends on the situation and the characteristics of the system. The video provides you with some guidelines on how to approach the tuning process.

A good practice is to start with the requirements that you need for your system, such as speed, accuracy, stability, etc. Precisely how you want the system to behave over time (therefore focusing on T-rise and overshoot) and the frequencies (bandwidth and damping ratio).

For example, if you want to reduce T-rise, you can increase the value of the P-gain (Kp). On the other hand, increasing the D-gain (Kd) decreases overshoot and improves the stability.

***   ***   ***   ***   ***   ***   ***   ***   ***

### Best Practices -- Tuning

![Best Practices](/images/best_practices.png)

  1. Choose a dampening ratio between 0.7 and 1.0 (When the damping is 1.0, you'll not see any overshoot; but, the rise-time will be a bit slower. At 0.7, the rise-time will be quicker; but, you'll see some overshoot.)
  2. Choose a large natural frequency, while making sure that your controls stay within the actuation limits of the vehicle. This will ensure a small rise-time and settling time.(When thinking in terms of time constants, T= 1/Wn, the rise-time is 1.57T.)

** Note: If the natural frequency is too large, it may amplify unmodelled dynamic effects.
