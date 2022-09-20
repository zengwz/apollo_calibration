标定文件对应位置：gaosApollo放在/your_path_to_apollo/modules/calibration/data/下。可以看见此目录下有APOLLO默认的林肯车型和mkz车型的文件。文件夹名字可以改为对应的车名  
  
gaosApollo之外的文件夹分别记录了lidar,camera,radar的标定方法  
  
gaosApollo文件夹中除了*_params还有其他文件，注意修改  
  
此外yaml文件中的frame_id需要与其他地方的统一，注意修改  
  
gaosApollo直接拷贝自Lincoln2017MKZ_LGSVL，然后对相关的yaml文件中的参数进行修改，其中：  
camera_params：所有yaml文件修改完成，两个launch文件未变动  
gnss_params：yaml文件需要测量两个天线到IMU的距离，待补上。txt文件未变动  
radar_params：所有yaml文件修改完成，radar原名是不带rear的，不知是否为装在车后方的radar，此处暂且按照radar_rear标定  
init_params：不知有什么用，原文件为radar到camera_6mm的标定参数yaml文件加上init后缀，这里如法炮制  
rslidar_params：所有yaml文件修改完成，文件夹原名velodyne_params，应该需要修改相关路径  
vehicle_params：未变动，应该也不需要变动  
