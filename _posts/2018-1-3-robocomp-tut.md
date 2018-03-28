---
layout: post
title: Robocomp Basics
---

In this post we will disccuss about the [Robocomp](https://github.com/robocomp/robocomp) Robotic framework. Robocomp is a component based robotic framework. That means robocomp enables you to define a invidual entities called components and allows them to instrat with each other. For example, consider the case of a robot which can be conrolled by a a keyboard. In this case we will have 3 components, a keyboard component, a processig component, a motor component. They communicate/depends as shown.

![base comp arch]({{ site.baseurl }}/images/base_comp_arch.png)

In robocomp, the components are written using a language called CDSL. The CDSL will be compiled to genrate the code in whatever language you specified. You can read more about CDSL [here](). You wont write the application logic in the CDSL, you can write the application logic once the code is genrated. So in our case we need to write 3 cdsl files, one for each components.

## Communication
You might have already thought, how would these components commnunicate with earch other? In robocomp there are two major methods in which two components can communicate. Using interface methods, or suing publish/subscribe mechanism. Lets talk about interfaces first.

### Interfaces
Interfaces decalares a set of functions. A component can relate to an interface in two ways, 1) Impliment it 2)depend on it
If a component impliment an interface, then it has to impliment all the functions declared in the interface. If a component `A` depends on interface `I` means it would call the functions declared in the interface, so it needs a component `B` which impliments `I` to be running.

### Publish/Subscribe

