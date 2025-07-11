## 1. Unity Package Installation: **ROS–TCP–Connector**  
  
Official GitHub:  
  
https://github.com/Unity-Technologies/ROS-TCP-Connector  
  
Reference Materials:  
  
https://github.com/Unity-Technologies/Unity-Robotics-Hub/tree/main/tutorials/ros_unity_integration  
  
https://velog.io/@sunbei00/Unity-Robotics-01-Setting  
  
Unity Package 설치:  
  
1. Open Unity Project  
2. `Window > Package Manager > Add package from git URL...`  
3. Enter address:  
  
```csharp  
https://github.com/Unity-Technologies/ROS-TCP-Connector.git?path=/com.unity.robotics.ros-tcp-connector  
```  
  
  
> This package acts as a ROS node within Unity (such as Publisher/Subscriber)  
>  
  
---  
  
## 2. Run the **ROS TCP Endpoint node in the ROS container in Docker**  
  
(Important) Inside the container:  
  
```bash  
# Running a container  
docker start -ai ros1  
  
# Add ROS TCP Endpoint Node  
cd ~/catkin_ws/src  
git clone https://github.com/Unity-Technologies/ROS-TCP-Endpoint.git  
cd ~/catkin_ws  
rosdep install --from-paths src --ignore-src -r -y  
catkin_make  
source devel/setup.bash  
```  
  
### Run:  
  
```bash  
roslaunch ros_tcp_endpoint endpoint.launch  
```  
  
> Role of this node to receive incoming TCP connections from Unity  
>  
  
---  
  
## 3. Unity and Docker ROS communication connection (host ↔ container)  
  
### Problem: Unity runs on **host**, ROS in **Docker container**  
  
→ This requires **port forwarding** or **container IP access**  
  
### Workaround:  
  
When running the container, you can add the option '--network=host':  
  
```bash  
docker run \  
--name ros1 \  
-it \  
--privileged \  
--network=host \  
--env="DISPLAY=$DISPLAY" \  
-v=/tmp/.X11-unix:/tmp/.X11-unix:ro \  
-v=/r1/catkin_ws:/root/catkin_ws \  
-w=/root/catkin_ws \  
osrf/ros:melodic-desktop-full  
```  
  
- **Containers and Unity are connected to the same network** thanks to '-network=host'  
- IP settings on the Unity side can be set to 'localhost' or '127.0.0.1'  
  
❗ (Important) [Some of the container's internal settings need to be re-established] (https://www.notion.so/ROS-Melodic-with-Docker-on-WSL2-Ubuntu-24-04-226e6b6465d080c4b5fdd44c3b0df23d?pvs=21)  
  
---  
  
## 4. Setting Up the Unity Side  
  
- Adding 'ROSConnection' Components  
- `ROS IP` → `127.0.0.1`  
- 'ROS Port' → '10000' (port opened by endpoint node)  
- Topic name, Message type setting  
  
---  
  
## 5. Testing  
  
1. Send message such as '/cmd_vel' from Unity to 'ROSConnection'  
2. Check 'rostopic echo /cmd_vel' in Docker ROS container  
  
---  
  
## Summary Flow  
  
```bash  
Unity (ROS–TCP–Connector)  
↓ TCP  
Docker (ros_tcp_endpoint in Melodic container)  
↓  
ROS 노드 (omo_r1 or etc.)  
```  
  
---  
  
## Precautions  
  
- Build 'ros_tcp_endpoint' and do 'catkin_make' again  
- Port/network between Docker container and Unity must be opened for communication  
- Windows + WSL2 environment requires additional settings (you are a Ubuntu host so it's okay)