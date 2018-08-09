# Google Summer of Code 2018 Project on Integration of PCL to ROS

Aim of the Project: The aim of the project is divided in following 4 parts/stages:
1. Visualization of Microsoft Kinect point cloud data in HTC Vive through ROS: Using vive_ros and RVIZ_vive_plugin to visualize point cloud data in HTC Vive headset.
Steps:
i) Setup vive_ros package (https://github.com/robosavvy/vive_ros) on the ubuntu workstation. Check HTC vive working.
ii) Setup Rviz_vive_plugin (https://github.com/AndreGilerson/rviz_vive_plugin)                      which allows RVIZ to render to the HTC Vive.
iii) Setup pcl_ros libraries
Rough Idea of carrying out visualization:
Currently, through pcl_ros libraries, we can visualize point cloud data to the desktop. 
We can leverage this technique to publish point cloud data through RVIZ on the vive node. 
This may need some code engineering for ROS on the vive_ros and Rviz_vive_plugin to work for our purpose.
Limitations: 
HTC Vive is still in beta phase for Ubuntu OS. So, all the functionalities are not available. HTC Vive has good support for running in Windows OS.
In theory it looks possible to publish depth point cloud data to HTC Vive through RVIZ but it seems nobody has achieved till now.
The visualization quality from rviz to HTC Vive headset is not as comparable to Unity engine. 
 
2. Integrating pcl_libraries for 3-D object detection with vive_ros: There are already methods implemented in pcl_ros for detecting 3-D objects. After visualizing the robot workspace in HTC Vive, it would be good to use these techniques to detect the object. This will help the operator to manipulate the objects easily in VR (Virtual Reality). This will also help in effective robotic teleoperation and other applications.

3. Improving filters in pcl_ros: There are algorithms already implemented on pcl_ros for filters. We can take few of them and try to optimize their performance. (need Prof. Okada help to define more concretely this part of the project)

4. Simple pick and place robotic teleoperation tasks: With the use of above three software implemented correctly, we can perform some basic robotic teleoperation in VR (Virtual Reality) example pick and place of cups using electric grippers. Few of the works done are listed as follows:
i) ROS Reality at Brown: https://www.youtube.com/watch?v=HlRJZYNNndI
ii) MIT CSAIL work on Teleoperating robots in Virtual Reality:  http://news.mit.edu/2017/mit-csail-new-system-teleoperating-robots-virtual-reality-1009
iii) Deep imitation learning for complex manipulation tasks from Virtual Reality Teleoperation at UC Berkley: https://arxiv.org/pdf/1710.04615.pdf

Motivation: The key motivation for this project is to create successful Kinect Visualization to HTC Vive in Ubuntu and ROS environment. This has been carried out by using Windows machine and Unity engine and transferring data via the internet to the Ubuntu machine. But this process can lose some packets over the internet and also has some delay in transfer. 

The second motivation is to detect 3D objects in robot space and track them for implementing concepts for dynamical changing goals. This can also help in achieving robust robotic teleoperation. Also, the integration of filters in pcl_ros can help to segment objects well. Finally, with all this, we can do faster and better robotic teleoperation for pick and place of objects.

Hardware Used: HTC Vive, Microsoft Kinect, Ubuntu Workstation, Baxter Robot

Work Done during GSoC'18:
1. Kinect Visualization to HTC Vive using rviz: In this work, we visualized the Baxter environment through the Kinect camera mounted on Baxter robot in HTC Vive via rviz plugin. As explained in the motivation that this is a big challenge to carry visualization in Ubuntu with ROS as HTC VIve has beta support for Ubuntu. We have not only successfully visualized the Kinect point cloud data to HTC Vive but also achieved better visualization than Vive-Unity visualization. The details of this work can be found here: https://github.com/sanketrahul/Kinect-Rviz-Vive

2. Position tracking of vive components: After having successful Kinect-Rviz-Vive visualization, we need position tracking of HTC Vive components for many reasons like position tracking of humans etc. The details of the code can be found here: https://github.com/sanketrahul/vive_ros

3. Add Hardware Safety in vive_ros code: Normally when we close the node in vive_ros it abruptly closes the hardware which can sometimes damage the Vive hardware. To overcome this problem we added SIGTERM in the forked vive_ros for hardware safety. The detailed code can be found here: https://github.com/sanketrahul/vive_ros

4. Integration of PCL 3D object detection integration with ROS: 3D object detection is an interesting problem in robotics. It can help robot reach autonomy. There is already an implementation of 3D object detection in PCL (http://www.pointclouds.org/documentation/tutorials/correspondence_grouping.php#correspondence-grouping). But to use in real time application we need to integrate it into ROS. The PCL version takes the input of scene and model from a .pcd file and outputs the matched object in the scene with the model given. In this implementation, we have given real-time point cloud data from Kinect as the scene to the PCL 3D detection algorithms and outputs the matched object with the model by highlighting it. The details of the implementation can be found here: https://github.com/sanketrahul/jsk_recognition/blob/master/jsk_pcl_ros/src/3D_object_detection.cpp 

5. Integration of Pointnet with ROS: Pointnet is a deep learning approach to 3D object detection. In this project, we trained the model offline and run the test code by passing real-time point cloud data to detect 3D objects in ROS. The details of the project can be found here: https://github.com/sanketrahul/pointnet

6. Tabletop tracking example: Object tracking is an interesting problem. It has been already implemented in ROS from PCL implementation (https://github.com/jsk-ros-pkg/jsk_recognition/blob/master/jsk_pcl_ros/launch/tracking.launch). But there is no good example to run this nodelet. After some interesting discussion at https://github.com/jsk-ros-pkg/jsk_recognition/issues/2308, we found a good running example. The example to run tabletop tracking can be found here: https://github.com/sanketrahul/jsk_recognition/blob/master/jsk_pcl_ros/example/example_tabletop_object_tracking.txt

Weekly Updates of the Project can be found here: https://docs.google.com/document/d/1MGZXTQCBM0Z9XXLTxmsHaTs0GGwwaTKxy5-jazcHSiw/edit?usp=sharing

Future Work:

Limitations:


