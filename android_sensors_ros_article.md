# Using your smartphone as a sensor for playing around in ROS

I wanted to share something I recently found to be possible and just a really cool tool to know about. Thats to make your smartphone publish their sensor data as a ros nodes.

After failing twice, I finally got this thing to work, and I felt sharing this would be a lot of help to a lot of students/hobbyists/lab rats out there.

In all honesty, I didn't do much. But aggregating seemingly old information, and reminding people that this works, I felt was still a value addition.

## Tutorial

### Download the app off the app store:

1. The ROS sensors driver allows you to use most of your sensors

2. The ROS All Sensors Driver gives you the ability to use your camera too


### Create a local hotspot from your phone

Now, here's the caveat: You want to create a local network or hotspot with your phone, rather than share your network via a router.

This is usually under the tethering/hotspot option on Android phones.

### Find your local ip address

Connect to the local hotspot, then open a terminal and find your local ip address.

This is usually found via the `ifconfig` command on Linux, and `ipconfig` command on Windows. It should usually start with 192.*

### Run the android app

Run the android app, and enter your `ip_address:ros_master_uri`.
The ros master uri (Uniform resurce identifier) can be found by the command `echo $ROS_MASTER_URI` on your computer terminal.
It's usually set to 11311 by default.

Screenshot

## Use cases:
Maybe you're playing around with computer vision algorithms, without a working webcam or you want to have your camera moving rather than moving the objects in front of the webcam, whatever floats your boat haha. If you need a camera, you have (I'm guessing), a pretty great one in your pocket.

Maybe you have an inference network running as a node, and then you can overlay your object detections on top of that.

Maybe you're playing around with Visual SLAM, or Sensor fusion or ROS and you just need some sensor data to play with.

So, yeah, that's about it.

The world is your stinky awesome oyster.  Go build stuff.

## Screenshots:

### Hello world!

### Sensor orientation

References:

\[1\]: http://wiki.ros.org/android_all_sensors_driver

\[2\]: Running a roscore on an Android smartphone https://wiki.epfl.ch/roscontrol/roscore-android-smartphone
