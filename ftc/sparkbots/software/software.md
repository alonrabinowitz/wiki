# Software

## [Game Manual 0](https://gm0.org/en/latest/) is a very useful resource

## Setup

* The robot for the 2023-2024 season Centerstage has the network 16532-B-RC, with the password accessible from the driver station - not here for security reasons.
* Robot configuration - changed on the driver station
  * All components should be named with descriptive names that are easy to understand in code, and documented somewhere
  * Motors go under the motors category, make sure to select the correct goBilda motor type
  * Servos go under the servo category, make sure to select the correct goBilda servo type if it exists, otherwise select the generic servo option
  * Sensors go in the I<sup>2</sup>C (I2C) buses, with only 1 device per bus if connected directly to the control/expansion hub
    * The built-in IMU(Inertial Measurement Unit - includes the gyro and accelerometer) on the control hub can only be used on I2C bus 0. Some of the control hubs have the BNO055 and some have the BHI260AP, so you will have to try both. The Control hub on the 2023-2024 Centerstage robot(16532-B-RC) has the BHI260AP IMU.
  * Cameras show up in the configuration outside of a control/expansion hub
* Robot Wi-Fi networks must be called [team number]-[Extra identifier(not required)]-RC
  * e.g. 16532-RC or 16532-A-RC
* Driver stations must be called [team number]-[Extra identifier(not required)]-DS
  * e.g. 16532-DS or 16532-B-DS
* You can connect to the robot's blocks and management interface by connecting to the control hub's wifi network and going to [http://192.168.43.1:8080](http://192.168.43.1:8080)

## Conventions

* Programs names are the year/season, followed by the version, and then by the type(auton/teleOp) and extra description:
  * Season + version + type + extra details(optional)
  * Version is in greek letters: alpha, beta, gamma, delta, etc.. Alpha is the main version and you create new programs with the other version for testing new things while still keeping the old code as a backup
  * e.g.:
    * 2022-23 alpha teleOp
      * The 2022-2023 season Powerplay
      * Main version
      * TeleOp
    * 2024-24 alpha auton III PURPLE ONLY
      * The 2023-2024 season Centerstage
      * Main version
      * Auton
      * Quadrant III(3), only the purple pixel
* Extract what you can into separate functions, and use parameters to pass information into the function
* Only programs that are used in comp or are actively being worked on and tested should be enabled

## How to Use Parts in Code

* ### Motors

  * Motors have a power range from -1(reverse full speed) to 1(forward full speed), with 0 as stopped
  * The direction can be set to reverse
  * When controlling multiple motors that are mechanically connected in some way, like in a drivebase(connected through the ground), make sure to carefully think through the order through which you power them on and off - for example, in auton, the robot can rotate a little unpredictably, making it hard to be precise

* ### Servos

  * Servos can also have their direction reversed.
  * Servos have two modes: continuous and servo
    * In continuous mode, the servo will act like a motor
    * In servo mode, the servo will have a range of 300˚ and should be controlled in software through the range 0-1, based on the angle you want. Servos in servo mode just go the the angle you tell them automatically and then stay there. You can also restrict the servo's range with a command.

* ### Controllers

  * Controller 1(start + a) is usually used for the drivebase and controller 2(start + b) is usually used for auxillary functions such as an arm and an intake
  * Most buttons return a boolean with their status
  * The joysticks' y-value is inverted, so make sure to account for that
  * The triggers do not act as a button, and instead return their position within the range 0-1, with 0 meaning unpressed and 1 meaning fully pressed, with infinite positions in between

* ### Sensors

  * Sensors work through their own interfaces
  * Distance sensors are not accurate against the clear walls in distances of more than ~80cm

## Other

* There is a version of teleOp that has field centric movement(directions are based on the driver/field instead of the robot) on the Centerstage robot, if you want to try/use it, the built-in IMU must be configured as "imu"
