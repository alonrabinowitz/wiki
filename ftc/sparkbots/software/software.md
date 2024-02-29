# Software

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

## Other

* There is a version of teleOp that has field centric movement(directions are based on the driver/field instead of the robot) on the Centerstage robot, if you want to try/use it, the IMU must be configured as "imu"
