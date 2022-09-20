标定目标：得到四颗激光雷达到imu的变换矩阵，最终写入apollo/calibration/data/gaosApollo/rslidar_params/下对应的文件中  
  
标定方法：利用rviz的可视化，使得四颗激光雷达的点云基本重合，将三颗16线雷达标定到主雷达的坐标系。测量得到主雷达到imu的变换矩阵后，根据外参传递关系得到标定目标  
  
用到的ros驱动：同目录下的rslidar_sdk,usb_cam,chccgi610，分别为激光雷达，相机和华测GPS驱动，放到~/catkin_ws/src下，cd到catkin_ws后catkin_make。华测GPS的驱动有问题，只能读取IMU的信息无法读取GPS的信息，有待改善。  
  
标定步骤：  
1.用命令rosbag record -a（-a记录所有话题，也可以指定几个需要的话题进行录制）录制四颗激光雷达的点云信息和imu的信息（imu信息只是为了可视化坐标，GPS的ROS驱动待改善）  
2.rviz -d lidar_calibration.rviz显示可视化界面  
3.rosrun tf2_ros static_transform_publisher发布变换矩阵，根据rviz中的点云进行变换矩阵的调整。  
  
标定结果和详情见static_transform.txt。利用当前目录下的bag包可以可视化标定结果  
  
可以优化的地方：  
1.主雷达到imu的变换矩阵目前是通过测量获得，可以改用激光雷达到imu的标定算法获得  
2.可视化方法可以结合激光雷达到激光雷达的标定算法获得更小误差的变换矩阵  
