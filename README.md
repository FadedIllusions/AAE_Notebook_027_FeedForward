# AAE_Notebook_027_FeedForward
![Controller Math](/images/controller_math.png)

When working with the proportional controller, our vehicle was made aware of the error in position from the target. When working with a derivative controller, our vehicle was made aware of its error in velocity when approaching the position of the target trajectory. What if we had a trajectory that moved relatively quickly and we, also, needed to make the vehicle aware of some target acceleration(z_dot_dot_target)?

Enter the world of the feed forward controller.
