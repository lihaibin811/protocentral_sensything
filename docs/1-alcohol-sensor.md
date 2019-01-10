---
menu: Experiment 1 - Alcohol Sensor
parent: experiments.md
---
# Experiment 1 - Alcohol detector

### Objective
To determine the level of Alcohol in any liquid

### Application
Since this sensor has a good level of sensitivity it can be used as a portable alcohol detector.

### Procedure
MQ303A is a semiconductor sensor for Alcohol detection. It has very good sensitivity and fast response to alcohol, suitable for portable alcohol detector just plugging with sensything. Below you find the conversion of adc data to the content of alcohol to be detected with milligram per litre. When the content of alcohol is more than 0.8 it detects the presence of alcohol.

![Alcohol Sensor](images/alcohol-sensor.jpg)

Excerpts from the code:

```c
float adc_data = (float)((bit32*VFSR*1000)/FSR);     //In  mV
float v = (adc_data/10) * (5.0/1024.0);
float mgL = 0.67 * v;

if(mgL > 0.8)
{   
	Serial.print("mg/L : %f \n");
	Serial.print(" Alcohol Detected");
	Serial.println(mgL);
 }
else
{    
	Serial.print("mg/L : %f \n");
	Serial.print(" Alcohol Not Detected");
	Serial.println(mgL);
}  
```

[Download the full code here](https://github.com/Protocentral/protocentral_sensything/tree/master/software/Sensything_Arduino/experiments/Analog_Sensors/examples/sensyThing_mq303A)