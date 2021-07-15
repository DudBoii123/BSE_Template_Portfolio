# Gesture Controlled Car
In this project, I make an RC Gesture Controlled Car. The car is controlled using a glove on my hand and can be controlled to go forward, backward, and turn left and right. It also has an ultrasonic sensor on it, allowing it to take measurements and display them to an lcd screen.

| **Engineer** | **School** | **Area of Interest** | **Grade** |
|:--:|:--:|:--:|:--:|
| Daniel Saptari | Lexington High School | Engineering | Incoming Freshman

# Final Milestone
Coming Soon!
![Coming Soon](https://images.squarespace-cdn.com/content/v1/591fd77d29687fd09cca478b/1555546030336-YXVPG30KTCM92JW89UTL/ke17ZwdGBToddI8pDm48kDrQ9tfdcvPUv7NgXGP4R2R7gQa3H78H3Y0txjaiv_0fDoOvxcdMmMKkDsyUqMSsMWxHk725yiiHCCLfrh8O1z4YTzHvnKhyp6DaNYroOW3ZGjoBKy3azqku80C789l0gmXcXvEVFTLbYX9CdVcGe4zwrosjp5YtnrvbmlM1LFKb7wNXE8lRZ0Z8l5PIsW3Vw/AdobeStock_139559217.jpeg)

# Second Milestone
 Coming Soon!
![Coming Soon](https://images.squarespace-cdn.com/content/v1/591fd77d29687fd09cca478b/1555546030336-YXVPG30KTCM92JW89UTL/ke17ZwdGBToddI8pDm48kDrQ9tfdcvPUv7NgXGP4R2R7gQa3H78H3Y0txjaiv_0fDoOvxcdMmMKkDsyUqMSsMWxHk725yiiHCCLfrh8O1z4YTzHvnKhyp6Da-NYroOW3ZGjoBKy3azqku80C789l0gmXcXvEVFTLbYX9CdVcGe4zwrosjp5YtnrvbmlM1LFKb7wNXE8lRZ0Z8l5PIsW3Vw/AdobeStock_139559217.jpeg)
# First Milestone
My first milestone was getting the car to be able to move. This involved learning how the ESP32 works, getting it to work with the L298N motor driver, building the car chassis, and mounting and wiring up the 4 DC motors. I also wrote the code for the ESP32, motor driver, and motors to work. The ESP32 controls what the motor driver does through 6 wires/pins. There are three for each pair of motors (left and right). Each set of three pins has one enable terminal, and two input pins. The enable pin determines whether or not the motor is ready to be controlled, depending on whether the signal is HIGH or LOW. It can also be used with a pwm signal to control the speed of the motors. The input pins determine the direction the motor spins. One input pin should be HIGH, while the other should be LOW. The motor direction is determined depending on which input pin is HIGH and which is LOW. The way the motor driver is able to control the motor direction like this is because it is an H-Bridge. An H-Bridge is a circuit that has four switches that control the flow of current to a load. In this case the load is the motor. One issue I had was figuring out how to code for the use of the pwm signal, and also how to control the direction while using that signal. In the end, the parts I used for this milestone were an ESP32, one L298N motor driver, 4 DC motors, 4 AA batteries, the battery pack, the car chassis kit, and a screwdriver.
[![Milestone #1](https://res.cloudinary.com/marcomontalbano/image/upload/v1626378643/video_to_markdown/images/youtube--YWbhqKimJSA-c05b58ac6eb4c4700831b2b3070cd403.jpg)](https://www.youtube.com/watch?v=YWbhqKimJSA "Milestone #1")
