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

## Test rostful

To test rostful, follow the instructions on each case.

### Subscribe to a topic

 1. `roslaunch rostful_launcher rostful.launch`
 2. Run the rospy_tutorials examples: `rosrun rospy_tutorials talker.py`
 3. In a web browser, go to the URL: http://localhost:5000/frontend/chatter
 4. Click on the 'GET LATEST MSG' button. You will see the JSON formatted message.

### Publish in a topic

 1. `roslaunch rostful_launcher rostful.launch`
 2. Run the rospy_tutorials examples: `rosrun rospy_tutorials listener.py`
 3. In a web browser, go to the URL: http://localhost:5000/frontend/chatter
 4. Fill the data field in 'Send message' section. Click on 'POST NEW MSG' button and check the listener.

### Service client

The rostful web frontend does not support non string types. Thus, for this example, you need to install a REST client plugin (there are plenty in Firefox or Chrome).

 1. `roslaunch rostful_launcher rostful.launch`
 2. Run the rospy_tutorials examples: `rosrun rospy_tutorials server_connection_header.py`
 3. From the REST client plugin, set URL to: http://localhost:5000/ros/add_two_ints
 4. Select POST method, and put the JSON code in the body of the message:
```
{
  "a": 1,
  "b": 2
}
```
 5. Check the JSON formatted response.


## Use rostful

Rostful provides a frontend that allows you to do a first testing very easily. However, as it only support strings, it could very limited for different topics or services. Thus, the best way to test the rostful interface is through a REST client plugin in your web browser.

The frontend is accessed via: http://localhost:5000/frontend/<topic_name>

The URL for the REST client is: http://localhost:5000/ros/<topic_name>

All messages are formatted in JSON. The HTTP method is different on each case:

 * Use GET to obtain the latest message received in a subscribed topic.
 * Use POST to send a message to a topic.
 * Use POST to call a service.
