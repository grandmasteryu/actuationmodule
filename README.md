# actuationmodule
## Instructions
<What is actuation module>  
  
**Actuation Modules(ActMs)** are morphology configurable "fruit sized" blocks supplied by mini pneumatic actuators. ActM provides a novel joint strucutre to configurate its morphology and stiffness comparing with traditional rigid link mechanism in the field of Robotics.  

ActMs was designed and developed by [Ishiguro Laboratory](http://eng.irl.sys.es.osaka-u.ac.jp/), Osaka University. The ActM was developed by using wide-used mechanical parts, and parts manufactured by CNC which was provided by [OriginalMind](http://www.originalmind.co.jp/). The design and simulation were made in [Autodesk Inventor 2017](https://www.autodesk.com/products/inventor/overview).  

### (1)Citing
If using this structure for academic purposes please consider citing the following papers.  

>Yu, S., Nakata, Y., Nakamura, Y. et al.(2017). 
>*A design of robotic spine composed of parallelogram actuation modules.*
>Artif Life Robotics. 22(4), 477-482.

### (2)Concept
<The concept of ActM and what it can achieve>  
When we design humanoid robots, for the sake of functionality, the mechanism of the robots are always "carefully designed".  
  
Robot behaviors are always changed by software synergies.  

This is an Actuation Module. In the future, it will become more compact-sized.  
<img src="https://github.com/grandmasteryu/actuationmodule/blob/master/screenshot/IMG_0638.png" width="200px">  

### (3)Actuation Mechanism
The actuator which changes the morphology of the ActM is a Double Acting Cylinder.
There are 2 chambers and 1 piston in a Double Acting Cylinder.
To control the position of piston, we use a pair of 3/2 solenoid valves as a set to control the airflow of a chamber. For example, a typical allocation of valve sets  
<img src ="https://github.com/grandmasteryu/actuationmodule/blob/master/screenshot/valvesets.png" width="150px">  

we use `vn.outx` to describe the valve named **"x"** in the side of chamber named **"out"**, of the actuator with the serial number **n**.  
  
The states of the chamber airflow is as follows:  

chamberstate | keep | keep | exhaust | supply  
--- | --- | --- | --- | ---
`vn.outx` | 0 | 0 | 1 | 1
`vn.outy` | 0 | 1 | 0 | 1

### Force Receiving Analysis
In this analysis, the damp force of the air at standard atmospheric pressure is ignored, to simplify the problem.  
The forces received at the end of the cylinder's piston is as follows:  
  
![f1]  

![f2]: The force of current state of vn.out. **supply->positive; keep or exhaust->zero.**  
![f3]: The effect of module's gravity and loads. In current experiment settings, it is always positive.
![f4]: The force corresponding to hte state of vn.in. **always negative.**  
![f5]: The damp force of damper. **when motion direction is out, negative; when direction is in, positive**  
![f6]: friction of the module. **when motion direction is out, negative; when direction is in, positive**   
  
Some constraints:   
![f7]: 

[f1]: http://chart.apis.google.com/chart?cht=tx&chl=F=F_o%2BF_G-F_i-f_D-f
[f2]: http://chart.apis.google.com/chart?cht=tx&chl=F_o
[f3]: http://chart.apis.google.com/chart?cht=tx&chl=F_G
[f4]: http://chart.apis.google.com/chart?cht=tx&chl=F_i
[f5]: http://chart.apis.google.com/chart?cht=tx&chl=f_D
[f6]: http://chart.apis.google.com/chart?cht=tx&chl=f
[f7]: http://chart.apis.google.com/chart?cht=tx&chl=F_G<F_i%2Bf_D%2Bf
  
### Step response
In this experiment we physically connected the Actuation Modules, by using high-speed electronic-magnetic solenoid valves. For example, we connect n.in together to a public node, each .in chamber has a valve n.inx to determine state **connected** or **unconnected** to the public node.  
![](https://github.com/grandmasteryu/actuationmodule/blob/master/screenshot/ans2.png)  
The initialized positions of the five modules are all set to rectangles, every time the positions are set, the time(s) which the air pulses are input is(are) the same.   
The illustration of the experiment percedures are as follows:  
<img src="https://github.com/grandmasteryu/actuationmodule/blob/master/screenshot/IMG_0636efg.png" width="300px">
<img src="https://github.com/grandmasteryu/actuationmodule/blob/master/screenshot/IMG_0631efg.png" width="300px">  
In the experiment, a weight(500g) is hanged by a string. To carry out step response, we use a pair of pincers to grab another string to hold the weight in the position that make the tension of the hanging string **just zero**. The step response starts when the pinceers are opened, so that the string which holds the weight is released. The purpose is to control the condition each time the experements are conducted.  

By changing the on/off status of the solenoid valves, we suppose to get **variations of these step responses towards time**.  

In the experiment of **0.4MPa/0.2MPa**(based on standard atmospheric pressure), v1.out(7 times), v2.out(3 times), v3.out(5 times), v4.out(3 times), v5.out(3 times), is equally configured each time the data is recorded. For experiment procedure details, please see
https://docs.google.com/document/d/1ly_cKkNyd3H71KAWRwUz1D6GKgH2-kLmijMkbtDZU4M/edit  
  
  **However, there is still some points that have to be claimed here:**  
    
There is a manual valve between **0.2MPa** and the public node. The public node is connected with **0.2MPa** when configuring module positions, and when conducting experiment, the valve is closed to keep the pressure in the interconnected chambers constant.  
This experiment referenced the time scale datagraph of **0.3MPa/0.15MPa**, and some on/off combinations have been omited in the current experiment because of the results of these combinations makes no significant difference, and to shorten the experiment time.  
The picked data is as below, named with binary 5-digit number, which means the on/off state of the n.inx.  
e.g.: "01100" means v5.inx = 0, v4.inx = 1, v3.inx = 1, v2.inx = 0 v1.inx = 0  

