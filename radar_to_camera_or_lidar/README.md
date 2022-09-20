标定目标：radar_front到lidar_top，radar_rear到camera_6mm的变换矩阵

ARS408的ROS驱动只找到SOCKET CAN的，没有适配ESD CAN的，无法接收radar数据和可视化标定，暂用测量值代替。
radar_front到lidar_front：高度差0.2，前后0.05，左右0
radar_rear到lidar_right：左右0.72，高0.4，前后0.5

radar_rear到camera_6mm的计算步骤（把后方的毫米波雷达标定到前面的camera_6mm上很奇怪，有待研究）：
P(right_lidar) = R1 * P(rear_radar) 
P(Top_lidar) = R2 * P(right_lidar)
P(camera_6mm) = R3 * P(Top_lidar)
R1从测量法得到，R2，R3由其他标定关系得到

radar_front到lidar_top的计算步骤：
P(top_lidar) = R1 * P(front_lidar) 
P(front_lidar) = R2 * P(front_radar)
R1从测量法得到，R2由其他标定关系得到

