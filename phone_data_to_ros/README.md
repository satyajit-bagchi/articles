# Using your smartphone as a sensor suite for playing around in ROS

After seeing all these cool developments and results coming out in the  Autonomous driving space - Computer vision/Sensor fusion/Object tracking space, I wanted to play around with some of these algorithms, and hopefully recreate some of the results. But I don't have an autonomous car lying around my apartment (yet), and doing object tracking with a webcam is to be honest, kind of lame. So...I started to look around for alternatives.

I wanted to share something really cool I recently found to be possible: Making your smartphone publish its sensor data via ROS.

After failing twice, I finally got this thing to work and to be frank, I didn't do much. I just went through a bunch of outdated information, discouraging comments, forum posts, and a couple of unsuccessful attempts. Easy.

I am sharing this information with the hope that this might be of help to any fellow hackers, students, hobbyists, or lab inhabitants out there.

## Prerequisites

1. Working [ROS](https://www.ros.org/) distribution, preferably on Linux
2. An Android smartphone 

## Tutorial

### Download the sensor driver app:

1. The [ROS sensors driver](https://play.google.com/store/apps/details?id=org.ros.android.sensors_driver) allows you to use most of your sensors. \[3\]

2. The [ROS All Sensors Driver](https://play.google.com/store/apps/details?id=org.ros.android.android_all_sensors_driver) gives you the ability to use your camera in addition to other sensors. \[4\]


### Create a local hotspot from your phone

**Now, here's the caveat**: You want to create a local network or hotspot with your phone, rather than share your network via a router.

This is usually under the tethering/hotspot option on Android phones.


### Find your local ip address

Connect to your phone's hotspot, then open a terminal on your computer and find your local ip address.

This is usually found via the `ifconfig` command on Linux (and Unix), and `ipconfig` command on Windows. It should usually start with 192.*

![echo](assets/ifconfig.png)

### Run the android app

Run the android app, and enter your `ip_address:ros_master_uri`.
The ros master uri (Uniform resurce identifier) can be found by the command `echo $ROS_MASTER_URI` on your computer terminal.
It's usually set to 11311 by default.

![app](assets/app.png)

## Screenshots:

### Imu data echo

`rostopic echo /phone1/android/imu`
Data echo:
![echo](assets/imu_echo.png)

### Sensor orientation


Phone orientation visualized via Rviz

![orientation](assets/imu_orientation.png)

### Camera stream

To view the camera message stream, use the command:

`rosrun image_view image_view image:=phone1/camera/image _image_transport:=compressed`

![camera_stream](assets/camera_image_1.png)

### Sensors you can use:

- Accelerometer(Part of the Imu message)
- Gyroscope(Part of the Imu message)
- Camera stream (Most useful in my opinion)
- Illumination sensor
- GPS(Topic published but no messages)

## Use cases:

- You're playing around with computer vision algorithms without a working webcam or you want to have your camera moving rather than moving the objects in front of the camera, whatever floats your boat. 
    - Basically, If you need a camera, I'm guessing you have a pretty great one in your pocket, or lying in a drawer somewhere.

- You have an object detection inference network running as a node, and you want to (because now you can) overlay your object detections on top of that.

- You're playing around with Visual SLAM, or Sensor fusion or ROS and you just need some sensor data to play with.

So, yeah, that's about it. Happy hacking.

## References:

\[1\]: Running a roscore on an Android smartphone https://wiki.epfl.ch/roscontrol/roscore-android-smartphone

\[2\]: Android sensors driver https://play.google.com/store/apps/details?id=org.ros.android.sensors_driver

\[3\]: Android all sensors driver https://play.google.com/store/apps/details?id=org.ros.android.android_all_sensors_driver
