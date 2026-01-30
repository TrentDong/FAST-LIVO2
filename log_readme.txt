1 image/image_poses.txt
  时间辍 坐标 四元数
  timestamp x y z q_x q_y q_z q_w
	
2 pcd/lidar_poses.txt
  时间辍 坐标 四元数
  timestamp x y z q_x q_y q_z q_w

3 imu.txt
  源码
  fout_imu << setw(10) << head->header.stamp.toSec() - first_lidar_time << " " 
         << angvel_avr.transpose() << " " << acc_avr.transpose() << endl;
  意义
  记录IMU传感器的原始测量数据，包括：
	时间戳：相对第一个激光雷达帧的时间（秒）
	角速度：IMU测量的三轴角速度（rad/s）
	加速度：IMU测量的三轴加速度（未校准单位）
	
4 mat_pre.txt
  记录状态估计处理前的系统状态，包括：
	时间戳：相对第一个激光雷达帧的时间（秒）
	姿态：欧拉角（滚转、俯仰、偏航，单位：度）
	位置：世界坐标系下的三维位置（x, y, z，单位：米）
	速度：世界坐标系下的三维速度（vx, vy, vz，单位：米/秒）
	传感器偏置：陀螺仪偏置和加速度计偏置
	相机参数：逆曝光时间（用于视觉曝光补偿）

5 mat_out.txt
  记录状态估计处理后的系统状态，与mat_pre.txt相比，增加了：
	特征点数量：当前处理帧中有效特征点的数量
