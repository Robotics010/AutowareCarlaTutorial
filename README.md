# AutowareCarlaTutorial

Getting started steps for launching Autoware Universe autonomous driving stack with CARLA simulator.

Warning! This is Work in Progress tutorial. Reports and improvement suggestions are very welcome.

### Requirements

* Ubuntu 20.04

### Step 1. CARLA installation 

Install CARLA server 0.9.12 https://carla.readthedocs.io/en/0.9.12/start_quickstart/#carla-installation

Install carla client 0.9.12 https://carla.readthedocs.io/en/0.9.12/start_quickstart/#carla-0912

### Step 2. Autoware installation

Install Autoware Universe galactic https://autowarefoundation.github.io/autoware-documentation/galactic/installation/autoware/source-installation/

### Step 3. carla-ros-bridge installation

Clone carla-ros-bridge https://github.com/carla-simulator/ros-bridge/tree/0.9.12

Download and prepare map from https://bitbucket.org/carla-simulator/autoware-contents/src/master/

### Step 4. carla-autoware-bridge installation

Clone carla-autoware-bridge https://github.com/Robotics010/carla_autoware_bridge

### Step 5. Launch ad hoc simulation

Launch CARLA server:
```
~/CARLA_0.9.14$ ./CarlaUE4.sh -prefernvidia -carla-rpc-port=3000 -quality-level=Low
```

Launch carla_ros_bridge and carla-autoware-bridge
```
source /opt/ros/galactic/setup.bash
source ~/autoware/install/setup.bash
ros2 launch carla_autoware_bridge carla_ros_bridge.launch.py port:=3000
```

Spawn ego vehicle:
```
source /opt/ros/galactic/setup.bash
source ~/autoware/install/setup.bash
ros2 launch carla_autoware_bridge carla_autoware_ego_vehicle.launch.py
```

Launch manual control window:
```
source /opt/ros/galactic/setup.bash
source ~/autoware/install/setup.bash
ros2 launch carla_manual_control carla_manual_control.launch.py
```

Launch Autoware Universe:
```
source /opt/ros/galactic/setup.bash
ros2 launch autoware_launsource ~/autoware/install/setup.bash
h e2e_simulator.launch.xml map_path:=$HOME/autoware_map/carla-town-1 vehicle_model:=sample_vehicle sensor_model:=sample_sensor_kit
```
