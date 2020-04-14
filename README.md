# myrobot
Project này dùng để tạo model robot (wheeled robot), add camera, laser, tạo map, 
điều khiển robot bằng bàn phím, và cho robot chạy tự động
(Link tham khảo: http://moorerobots.com/)
- Các câu lệnh để chạy
1. Robot models
+ Mô phỏng trên gazebo
roslaunch mybot_description mybot_gazebo.launch
+ Mô phỏng trên rviz
roslaunch mybot_description mybot_rviz.launch
+ Cho robot chạy tự động bằng command
rostopic pub /cmd_vel geometry_msgs/Twist "
linear:
x:0.2
y:0.0
z:0.0
angular:
x:0.0
y:0.0
z:0.1"
2. Mapping and Navigation
+ Mô phỏng trên gazebo
roslaunch mybot_gazebo mybot_gazebo.launch
+ Bắt đầu vẽ bản đồ
roslaunch mybot_navigation gmapping_demo.launch
roslaunch mybot_description mybot_rviz_gmapping.launch
+ Điều khiển bằng bàn phím
rosrun teleop_twist_keyboard teleop_twist_keyboard.py
+ Lưu map
rosrun map_server map_saver -f ~/mybot_ws/src/mybot_navigation/maps/test_map
+ Tải lại map và sử dụng navigation waypoints trên rviz cho robot chạy tự động
- roslaunch mybot_gazebo mybot_world.launch
- roslaunch mybot_navigation amcl_demo.launch
- roslaunch mybot_description mybot_rviz_amcl.launch
