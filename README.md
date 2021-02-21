# Heron-RL-ICRA

## ROS RL-packages
These are the packages required to run our implementation of DREAMER with Gazebo and in Real-life
https://github.com/AntoineRichard/ROS_Dreamer_RL_Suite


## DREAMER trainer with ROS bindings
This is the code required to train DREAMER
https://github.com/AntoineRichard/dreamer

## Simulation
The simulation runs on Gazebo 9.0 and requires the following packages:
  - https://github.com/AntoineRichard/uuv_simulator modified version of the uuv-simulator (provides bouyancy and a couple worlds)
  - https://github.com/AntoineRichard/heron modified Heron packages
  - https://github.com/kf/kingfisher this packages are leagacy packages that we use for compatibility
  - https://github.com/AntoineRichard/heron_simulator/
  - https://github.com/heron/heron_controller
  
To install some of the required package use: `rosdep install --from-paths src --ignore-src -r -y` it should be sufficient to compile all the packages.
However, to run the simulation you will need the following packages:
  - ros-melodic-imu-filter-madgwick
  - ros-melodic-hector-gazebo-worlds
  - ros-melodic-hector-sensors-description
  - ros-melodic-hector-sensors-gazebo
  - ros-melodic-hector-gazebo

Python packages:
  - bottle
  - tensorflow-gpu==2.1 or higher
  - tensorflow-probability==0.9.0 or higher
  - opencv-python
  - gym
  
## Models
We are uploading them

## How to run:
If you have installed all the requirement ontop, you can start training and testing the models.

### Training:
To start the training please execute the following commands (we use byobu to run the training on distant servers):
  - In a terminal start a ros core: `roscore`
  - In another terminal start the simulation and the bridge: `roslaunch rl-server launch_train.launch`
  - In another terminal edit the agent: `rosed tensorflow2kingfisher X2Y_dreamer.py` and change the path where the episodes are saved (TODO make an arg)
  - Start the agent: `rosrun tensorflow2kingfisher X2Y_dreamer.py`
  - In another terminal start the training: `python3 X2Y_dreamer.py --logdir /path/matching/the/one/in/tf2kf` (this can be found in the dreamer git repository not the tensorflow2kingfisher package)

> Change `X` and `Y` to cmap or lzr.
