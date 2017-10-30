# actuationmodule
## Instructions
Actuation Modules(AMs) are morphology configurable "fruit sized" blocks supplied by mini pneumatic actuators. AM allows joint strucutre to configurate its stiffness comparing with traditional rigid link mechanism in field of Robotics.
### Actuation Mechanism
At present, Double Acting Cylinder is implemented on Actuation Moudle. In controlling the two chambers in an Actuation Module, we use two 3/2 valve as a set, to control the airflow of a chamber. For example, a typical allocation of valve sets
![](https://github.com/grandmasteryu/actuationmodule/blob/master/screenshot/valvesets.png)  

we use `vn.outx` to describe the valve named "x" in the side of chamber named "out", of the actuator with the serial number n.  
  
The states of the airflow is as follows:  

valvestate | keep | keep | exhaust | supply  
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
