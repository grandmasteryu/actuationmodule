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
The forces received at the end of the cylinder's piston is as follows:  

