---
layout: post
title: Robocomp Basics
---

In this post we will disccuss about the [Robocomp](https://github.com/robocomp/robocomp) Robotic framework. Robocomp is a component based robotic framework. That means robocomp enables you to define individual entities called components and allows them to instrat with each other. For example, consider the case of a robot which can be conrolled by a keyboard. In this case we will have 3 components, a keyboard component, a processig component, a motor component. The keyboard component will get the input from the users keyboard, pass it to the processing component, which will process the input and will decide the direction/speed of motor. and will send that info to motor component which will control motor. They depends as shown below.

![base comp arch]({{ site.baseurl }}/images/base_comp_arch..jpg)

In robocomp, the components are written using a language called CDSL. The CDSL will be compiled to genrate the code in whatever language you specified. You can read more about CDSL [here](). You wont write the application logic in the CDSL, you can write the application logic once the code is genrated. So in our case we need to write 3 cdsl files, one for each components.

## Communication
Now, once we have all the components generated, how can they comunicate with each other? In robocomp there are two methods in which two components can communicate. Using interface methods or using publish/subscribe mechanism. Lets talk about interfaces first.

### Interfaces
Interfaces decalares a set of functions. A component can relate to an interface in two ways - Impliment it; depend on it.

If a component impliment an interface, then it has to impliment all the functions declared in the interface. If a component _A_ depends on interface _I_ means it would call the functions declared in the interface, so it needs a component _B_ which impliments _I_ to be running. 

In our case the keyboard will impliment a keyboard interface, motor a motor interface. But the processing component wont impliment any interfaces, but will depend on keyboard and motor interface. So for the processing component to work, two other components which impliments them should be running.

### Publish/Subscribe
In publish–subscribe messaging pattern consists of entities called topics which are intermediater between those who want to send data (publishers) and those who want to get data (subscribers). Many subscribers can subscribe to a topic, also may publishers can publish to a node. Whenever a node publishes to a topic all the subscribers will be notified and the data will be sent to them.
In our case the keyboard -processing component's comunication can be replaced with a pub-sub pattern. So there can be a topic called inputState to which the keyboard component is publishing info and processing compoenent is subscribed.


