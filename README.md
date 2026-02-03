
# 编译
catkin_make -j


# 启动算法
## CP
source devel/setup.bash
roslaunch radar_graph_slam radar_graph_slam.launch odom_output:=/home/sax/4DRadarSLAM-NTU/odom.txt

# 保存地图
source devel/setup.bash
rosservice call /radar_graph_slam/save_map "{utm: false, resolution: 0.2, destination: '/home/sax/4DRadarSLAM-NTU/map.pcd'}"

# 输出odometry
source devel/setup.bash
rostopic pub -1 /command std_msgs/String "data: 'output_aftmapped'"
