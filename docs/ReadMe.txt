# 启动mqtt-client代理
nick@nick-dell:~/zhengping_ws/mqtt_client_ws$ ros2 launch mqtt_client standalone-zhengping.launch.ros2.primitive.xml 
# 发送测试数据
nick@nick-dell:~/zhengping_ws/mqtt_client_ws/src/mqtt_client$ ros2 topic pub /device/exception std_msgs/msg/String '{"data":"ABCDEFGH"}'
# 订阅MQTT话题，验证测试数据
nick@nick-dell:~/zhengping_ws/mqtt_client_ws/src/mqtt_client/mqtt_client/config$ mosquitto_sub -v --insecure -V mqttv311 -h fms.bzlrobot.com -p 2884 -t "/device/ZHENGPING-001/exception" --cafile ./rootCA.ros2.pem


mosquitto_sub -v --insecure -V mqttv311 -h fms.bzlrobot.com -p 2884 -t "/device/ZHENGPING-001/#" --cafile ./rootCA.ros2.pem


mosquitto_sub -v --insecure -V mqttv311 -h fms.bzlrobot.com -p 2884 -t "/device/ZHENGPING-001/deviceinfo" --cafile ./rootCA.ros2.pem
ros2 topic pub /device/deviceinfo std_msgs/msg/String '{"data":"ABCDEFGH"}'
ros2 topic pub /device/all_exception std_msgs/msg/String '{"data":"[DEVICE ALL EXCEPTION]"}'
