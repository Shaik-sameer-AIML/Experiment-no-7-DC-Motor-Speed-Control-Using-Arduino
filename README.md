# Experiment-no-7-DC-Motor-Speed-Control-Using-Arduino
### AIM : To control the speed and the direction of a DC motor using L293D driver ic( H- bridge)

### Components Required:
•	Arduino UNO board
•	L293D driver
•	12V DC motor
•	10K ohm potentiometer
•	Pushbutton
•	12V source
•	Breadboard
•	Jumper wires
### THEORY 
The L293D quadruple half-H drivers chip allows us to drive 2 motors in both directions, with two PWM outputs from the Arduino we can easily control the speed as well as the direction of rotation of one DC motor. (PWM: Pulse Width Modulation).
Arduino DC motor control circuit:
Project circuit schematic diagram is the one below.

![image](https://user-images.githubusercontent.com/36288975/167763051-b230c183-afc5-46f2-ba95-0f95e10dd6c9.png)
FIGURE-01 H BRIDGE CIRUCIT INTERFACE 
 
The speed of the DC motor (both directions) is controlled with the 10k potentiometer which is connected to analog channel 0 (A0) and the direction of rotation is controlled with the push button which is connected to pin 8 of the Arduino UNO board. If the button is pressed the motor will change its direction directly.
The L293D driver has 2 VCCs: VCC1 is +5V and VCC2 is +12V (same as motor nominal voltage). Pins IN1 and IN2 are the control pins where:
![image](https://user-images.githubusercontent.com/36288975/167763120-1421c2c5-8381-49eb-b376-03f6e1113b7a.png)
TABLE-01 EXITATION TABLE FOR H BRIDGE 

As shown in the circuit diagram we need only 3 Arduino terminal pins, pin 8 is for the push button which toggles the motor direction of rotation. Pins 9 and 10 are PWM signal outputs, at any time there is only 1 active PWM, this allows us to control the direction as well as the speed by varying the duty cycle of the PWM signal. The active PWM pin decides the motor direction of rotation (one at a time, the other output is logic 0).

### PRGORAM 
### Normal RPM:

```
const int motorpin1 = 5;
const int motorpin2 = 6;

void setup()
{
  pinMode(motorpin1, OUTPUT);
  pinMode(motorpin2, OUTPUT);
}

void loop()
{
  digitalWrite(motorpin1, HIGH);
  delay(2000);
  digitalWrite(motorpin2, LOW);
  delay(2000);
}
```
### TO control RPM:
```
#define motorIn1 5
#define motorIn2 6

void setup()
{
  pinMode(motorIn1,OUTPUT);
  pinMode(motorIn2,OUTPUT);
}
void loop()
{
  clockwise(0);
  delay(3000);
  counterclockwise(50);
  delay(3000);
}
void counterclockwise(int speed)
{
  analogWrite(motorIn1,speed);
  analogWrite(motorIn2,0);
}

void clockwise(int speed)
{
  
  analogWrite(motorIn1,0);
  analogWrite(motorIn2,speed);
}
```



### OUTPUT
### CIRCUIT DIAGRAM:

![198203922-f381cf5e-00b9-431e-bcac-838a0f3ef79c](https://user-images.githubusercontent.com/93427186/203054988-40df4bf0-7004-449b-857c-81c5a5cf7c0b.png)
### READINGS:
### CLOCKWISE:
![198203998-7d487364-1e9f-494c-99e5-89cb03d4bf9f](https://user-images.githubusercontent.com/93427186/203055078-a5cd1a88-1a48-4ee3-9c06-0eaa63e77d08.png)
### GRAPH:
![198204094-7181df43-9f38-4ebe-9579-68011d3fbabf](https://user-images.githubusercontent.com/93427186/203055166-d0326989-fb6f-4af6-a0b5-c339de9f321f.png)
### COUNTER CLOCKWISE:
![198204205-e0bac79f-2342-4bab-890a-5b36247a7660](https://user-images.githubusercontent.com/93427186/203055192-8a25f4e8-6ee0-4bac-bf9d-c361cd88e659.png)
### GRAPH:
![198204255-74236a89-cea5-4b56-9b30-d8c31981d259](https://user-images.githubusercontent.com/93427186/203055266-81edb58a-d997-4f03-be99-e6be14f05aeb.png)





### RESULTS AND DISCUSSION 
Thus, the speed and the direction of a DC motor using L293D driver ic( H- bridge) is controlled.

