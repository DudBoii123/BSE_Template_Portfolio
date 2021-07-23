# Gesture Controlled Car
In this project, I make an RC Gesture Controlled Car. The car is controlled using a glove on my hand and can be controlled to go forward, backward, and turn left and right. It also has an ultrasonic sensor on it, allowing it to take measurements and display them to an lcd screen.

| **Engineer** | **School** | **Area of Interest** | **Grade** |
|:--:|:--:|:--:|:--:|
| Daniel Saptari | Lexington High School | Engineering | Incoming Freshman

# Final Milestone
Coming Soon!
![Coming Soon](https://images.squarespace-cdn.com/content/v1/591fd77d29687fd09cca478b/1555546030336-YXVPG30KTCM92JW89UTL/ke17ZwdGBToddI8pDm48kDrQ9tfdcvPUv7NgXGP4R2R7gQa3H78H3Y0txjaiv_0fDoOvxcdMmMKkDsyUqMSsMWxHk725yiiHCCLfrh8O1z4YTzHvnKhyp6DaNYroOW3ZGjoBKy3azqku80C789l0gmXcXvEVFTLbYX9CdVcGe4zwrosjp5YtnrvbmlM1LFKb7wNXE8lRZ0Z8l5PIsW3Vw/AdobeStock_139559217.jpeg)

# Second Milestone
 My second milestone was getting readings from the accelerometer/gyroscope, connecting the two ESP32s, and having one ESP32 display what the car should be doing on the serial monitor from the accelerometer input on a remote ESP32. The accelerometer is able to measure X, Y, and Z acceleration forces, while the gyroscope measures rotational velocity. For my project I need to know the 3D orientation of the accelerometer/gyroscope. To get this information I just needed to combine the data from the accelerometer and the gyroscope. The code for this was uploaded to the ESP that would be going on to the glove in the end.
[![Milestone #2](https://res.cloudinary.com/marcomontalbano/image/upload/v1627068354/video_to_markdown/images/youtube--ygeNRCWvoiI-c05b58ac6eb4c4700831b2b3070cd403.jpg)](https://www.youtube.com/watch?v=ygeNRCWvoiI "Milestone #2")
# First Milestone
My first milestone was getting the car to be able to move. This involved learning how the ESP32 works, getting it to work with the L298N motor driver, building the car chassis, and mounting and wiring up the 4 DC motors. I also wrote the code for the ESP32, motor driver, and motors to work. The ESP32 controls what the motor driver does through 6 wires/pins. There are three for each pair of motors (left and right). Each set of three pins has one enable terminal, and two input pins. The enable pin determines whether or not the motor is ready to be controlled, depending on whether the signal is HIGH or LOW. It can also be used with a pwm signal to control the speed of the motors. The input pins determine the direction the motor spins. One input pin should be HIGH, while the other should be LOW. The motor direction is determined depending on which input pin is HIGH and which is LOW. The way the motor driver is able to control the motor direction like this is because it is an H-Bridge. An H-Bridge is a circuit that has four switches that control the flow of current to a load. In this case the load is the motor. I am able to control which pins are HIGH, LOW, or using a pwm signal through code being uploaded to the ESP32. One issue I had was figuring out how to code for the use of the pwm signal, and also how to control the direction while using that signal. In the end, the parts I used for this milestone were an ESP32, one L298N motor driver, 4 DC motors, 4 AA batteries, the battery pack, the car chassis kit, and a screwdriver.
[![Milestone #1](https://res.cloudinary.com/marcomontalbano/image/upload/v1626378643/video_to_markdown/images/youtube--YWbhqKimJSA-c05b58ac6eb4c4700831b2b3070cd403.jpg)](https://www.youtube.com/watch?v=YWbhqKimJSA "Milestone #1")
Schematics:
![ESP32-L298N-Motor(4)-Schematics](https://user-images.githubusercontent.com/87206873/125861398-ce9c9933-9027-46c3-ac5f-727f8acb9a88.jpg)
![Car Milestone #1 Picture](https://user-images.githubusercontent.com/87206873/125862108-9747a757-2350-45e2-a597-5f9d5013f07b.jpg)
My Code:

<details>
  <summary>Click to expand!</summary>
  
 ```C++
//Define the GPIO pins the motor input and enable pins are connected to
int motor1Pin1 = 27;
int motor1Pin2 = 26;
int enable1Pin = 14;
int motor2Pin1 = 25;
int motor2Pin2 = 33;
int enable2Pin = 32;
//Set pwm properties to control speed
const byte pwmChannel1 = 0;
const byte pwmChannel2 = 1;
const byte freq = 30000;
const byte resolution = 8;
int dutyCycle = 200;

void setup() {
//Set pins as outputs
pinMode(motor1Pin1,OUTPUT);
pinMode(motor1Pin2,OUTPUT);
pinMode(enable1Pin,OUTPUT);
pinMode(motor2Pin1,OUTPUT);
pinMode(motor2Pin2,OUTPUT);
pinMode(enable2Pin,OUTPUT);
//Configure pwm functionalities
ledcSetup(pwmChannel1,freq,resolution);
ledcSetup(pwmChannel2,freq,resolution);
//attachh the pwm channel to the GPIO to be controlled
ledcAttachPin(enable1Pin,pwmChannel1);
ledcAttachPin(enable2Pin,pwmChannel2);
//Set up serial monitor
Serial.begin(9600);
Serial.print("Motor Test Beginning...");
}

void loop() {
Serial.print("Motor Test Beginning...");
delay(200);
//Motors spin backwards at full speed
Serial.print("Attempting Motor 1 Full Speed Backward Rotation...");
delay(100);
digitalWrite(motor1Pin1,HIGH);
digitalWrite(motor1Pin2,LOW);
digitalWrite(motor2Pin1,HIGH);
digitalWrite(motor2Pin2,LOW);
delay(2000);

//Stop motor
Serial.print("Motor Stopped");
digitalWrite(motor1Pin1,LOW);
digitalWrite(motor1Pin2,LOW);
digitalWrite(motor2Pin1,LOW);
digitalWrite(motor2Pin2,LOW);
delay(2000);

//Motors spin forward at full speed
Serial.print("Attempting Motor 1 Full Speed Forward Rotation...");
delay(100);
digitalWrite(motor1Pin1,LOW);
digitalWrite(motor1Pin2,HIGH);
digitalWrite(motor2Pin1,LOW);
digitalWrite(motor2Pin2,HIGH);
delay(2000);

Serial.print("Motor Stopped");
digitalWrite(motor1Pin1,LOW);
digitalWrite(motor1Pin2,LOW);
digitalWrite(motor2Pin1,LOW);
digitalWrite(motor2Pin2,LOW);
delay(2000);

//Use pwm signal to make motors speed up to full speed
Serial.print("Attempting Motor 1 Forward Speed Up...");
digitalWrite(motor1Pin1,LOW);
digitalWrite(motor1Pin2,HIGH);
digitalWrite(motor2Pin1,LOW);
digitalWrite(motor2Pin2,HIGH);
 for (int i = 0; i < 256; i++) {
   Serial.println(i);
   ledcWrite(0,i);
   ledcWrite(1,i);
   delay(25);
   }

//Stop motors
Serial.print("Motor Stopped");
digitalWrite(motor1Pin1,LOW);
digitalWrite(motor1Pin2,LOW);
digitalWrite(motor2Pin1,LOW);
digitalWrite(motor2Pin2,LOW);
delay(2000);
}
```
                         
</details>
