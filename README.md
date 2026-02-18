
# 编译
catkin_make -j


# 启动算法
source devel/setup.bash
roslaunch radar_graph_slam radar_graph_slam.launch odom_output:=/home/sax/4DRadarSLAM-NTU/odom.txt

# 保存地图
source devel/setup.bash
rosservice call /radar_graph_slam/save_map "{utm: false, resolution: 0.2, destination: '/home/sax/4DRadarSLAM-NTU/map.pcd'}"

# 输出odometry
source devel/setup.bash
rostopic pub -1 /command std_msgs/String "data: 'output_aftmapped'"




# 轨迹评估命令
## APE
evo_ape tum gt_odom-cp.txt cp.txt -vap --plot_mode xyz --save_results ape_trans.zip
evo_ape tum gt_odom-cp.txt cp.txt -vap --plot_mode xyz -r angle_deg --save_results ape_rot.zip

evo_ape tum gt_odom-garden.txt garden.txt -vap --plot_mode xyz --save_results ape_trans.zip
evo_ape tum gt_odom-garden.txt garden.txt -vap --plot_mode xyz -r angle_deg --save_results ape_rot.zip

evo_ape tum gt_odom-loop1.txt loop1.txt -vap --plot_mode xyz --save_results ape_trans.zip
evo_ape tum gt_odom-loop1.txt loop1.txt -vap --plot_mode xyz -r angle_deg --save_results ape_rot.zip

evo_ape tum gt_odom-loop2.txt loop2.txt -vap --plot_mode xyz --save_results ape_trans.zip
evo_ape tum gt_odom-loop2.txt loop2.txt -vap --plot_mode xyz -r angle_deg --save_results ape_rot.zip

evo_ape tum gt_odom-loop3.txt loop3.txt -vap --plot_mode xyz --save_results ape_trans.zip
evo_ape tum gt_odom-loop3.txt loop3.txt -vap --plot_mode xyz -r angle_deg --save_results ape_rot.zip

evo_ape tum gt_odom-nyl.txt nyl.txt -vap --plot_mode xyz --save_results ape_trans.zip
evo_ape tum gt_odom-nyl.txt nyl.txt -vap --plot_mode xyz -r angle_deg --save_results ape_rot.zip
## RPE
evo_rpe tum gt_odom-cp.txt cp.txt -vap -r point_distance_error_ratio -u m --plot_mode xyz --save_results rpe_trans.zip
evo_rpe tum gt_odom-cp.txt cp.txt -vap -r angle_deg -u m --plot_mode xyz --save_results rpe_rot.zip

evo_rpe tum gt_odom-garden.txt garden.txt -vap -r point_distance_error_ratio -u m --plot_mode xyz --save_results rpe_trans.zip
evo_rpe tum gt_odom-garden.txt garden.txt -vap -r angle_deg -u m --plot_mode xyz --save_results rpe_rot.zip

evo_rpe tum gt_odom-loop1.txt loop1.txt -vap -r point_distance_error_ratio -u m --plot_mode xyz --save_results rpe_trans.zip
evo_rpe tum gt_odom-loop1.txt loop1.txt -vap -r angle_deg -u m --plot_mode xyz --save_results rpe_rot.zip

evo_rpe tum gt_odom-loop2.txt loop2.txt -vap -r point_distance_error_ratio -u m --plot_mode xyz --save_results rpe_trans.zip
evo_rpe tum gt_odom-loop2.txt loop2.txt -vap -r angle_deg -u m --plot_mode xyz --save_results rpe_rot.zip

evo_rpe tum gt_odom-loop3.txt loop3.txt -vap -r point_distance_error_ratio -u m --plot_mode xyz --save_results rpe_trans.zip
evo_rpe tum gt_odom-loop3.txt loop3.txt -vap -r angle_deg -u m --plot_mode xyz --save_results rpe_rot.zip

evo_rpe tum gt_odom-nyl.txt nyl.txt -vap -r point_distance_error_ratio -u m --plot_mode xyz --save_results rpe_trans.zip
evo_rpe tum gt_odom-nyl.txt nyl.txt -vap -r angle_deg -u m --plot_mode xyz --save_results rpe_rot.zip

