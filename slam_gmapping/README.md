SLAM gmapping
========================================
Visit following Website for more details about slam-gmapping: http://www.ros.org/wiki/slam_gmapping

How to build slam-gmapping package
========================================
  1. Clone this project to your catkin's workspace src folder
  2. Run catkin_make to build slam-gmapping node

How to run gmapping package
========================================
To make a map from a robot with a laser publishing scans on the scan topic:

```
rosrun gmapping slam_gmapping scan:=scan
```

To run the slam-gmapping node, you must launch the laser node(in our cass rplidar node), first.

What slam-gmapping node subscribes and publishes
========================================
1. Subscribed Topics
* tf (tf/tfMessage)
* scan (sensor_msgs/LaserScan)
2. Published Topics
* map_metadata (nav_msgs/MapMetaData)
* map (nav_msgs/OccupancyGrid)
3. Services
* dynamic_map(nav_msgs/GetMap)

Important parameters
========================================
* maxUrange: 사용가능한 레이저 범위의 최대 값 (그 이상 값은 cropped)
* linearUpdate: 레이저 값을 얻기 위하여 움직여야 하는 linear 거리 값
* angularUpdate: 레이저 값을 얻기 위하여 움직여야 하는 angular 값
* temporalUpdate: 레이저 값을 읽기까지 기다리는 시간
* particles: 파티클 필터의 수
* xmin, xmax, ymin, ymax: 초기 맵 크기
* delta: 지도의 resolution 값

Customizing in this project
=========================================
The following two changes were made to create an our office map with Kobuki.

1.Remap subscribed scan topic values:
```xml
     <remap from="scan" to ="/scan" />
```

2. Change the parameter values described above:
```xml
     <param name="maxUrange" value="7.0"/>
     <param name="linearUpdate" value="0.001"/>
     <param name="angularUpdate" value="0.002"/>
     <param name="temporalUpdate" value="0.5"/>
     <param name="resampleThreshold" value="0.5"/>
     <param name="particles" value="500"/>
     <param name="xmin" value="-5.0"/>
     <param name="ymin" value="-5.0"/>
     <param name="xmax" value="5.0"/>
     <param name="ymax" value="5.0"/>
     <param name="delta" value="0.08"/>
     <param name="llsamplerange" value="0.15"/>
     <param name="llsamplestep" value="0.15"/>
     <param name="lasamplerange" value="0.55"/>
     <param name="lasamplestep" value="0.55"/>     
```

You can find this changed settings launch file in `/gmapping/launch/slam_gmapping_rplidar.launch` and also launch it:

```
roslaunch slam_gmapping  slam_gmapping_rplidar.launch
```