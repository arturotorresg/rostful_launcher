# rostful_launcher

A simple package to easily configure and launch rostful.

## Install rostful

```
sudo apt-get install ros-kinetic-rostful
```

## Configure rostful

The file config/rostful.cfg is condifured to publish/subscribe topic '/chatter' and to be a client of the service '/add_two_ints'. Thus, you can test basic connections with rostful with the examples in rospy_tutorials package.

By default, the server in configured as 'localhost:5000'.

You can modify this file or make a copy in your own package, modify it, and then launch rostful changing the argument "config_file".


## Run rostful

```
roslaunch rostful_launcher rostful.launch
```
OR
```
roslaunch rostful_launcher rostful.launch config_file="<your_path_to_config_file>"
```
OR
```
rosrun rostful_launcher run_rostful.py -c "<your_path_to_config_file>"
```