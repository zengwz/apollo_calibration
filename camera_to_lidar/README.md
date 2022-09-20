标定目标：得到camera_6mm到lidar_top，camera_12mm到camera_6mm的变换矩阵

使用方法见：https://github.com/acfr/cam_lidar_calibration

标定直接得到R1和R2矩阵，camera_12mm到camera_6mm的变换矩阵由如下转换得到：
 P_short = R1 * P_top
 P_long = R2 * P_top
 P_short = R2 ^ -1 * R1  * P_long 

待改善的地方：
使用质量更好的标定板（标定板有弯曲）
使用支架更方便标定
