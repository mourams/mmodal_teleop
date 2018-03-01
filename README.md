# Teleop_MIRO
Software Architecture: Teleoperation with MIRO using gesture and speech
Using Motion Capture for localization and gesture recognition

Usage Instructions:
- Clone the master branch of Teleop_MIRO repository inside the src folder of your catkin_ws
- Install OpenCV following these instructions: https://docs.opencv.org/master/d7/d9f/tutorial_linux_install.html
- Set OpenCV path corresponding to your system and add dependency in miro_teleop/CMakeLists.txt
- Run catkin_make from inside catkin_ws
- Download MIRO MDK and MIRO app from http://labs.consequentialrobotics.com/miro/mdk/
- Turn on MIRO. Run the app and connect with MIRO, to find MIRO's IP. Ensure your machine is on the same network as MIRO.
- Edit the ~/.profile file in root@<MIRO's IP>, set ROS_MASTER_IP with machine IP running the roscore. Source it.
- Run/Enable bridge on the app. You might need to do this at frequent intervals if MIRO stops responding.
- In the Motive software for Mocap Optitrack, enable Data Streaming and set broadcast IP to the machine running the roscore.
- Setup up markers in the Motion Capture area. Create Rigid Bodies in Motive (Robot, Obstacle, Gesture in order) after aligning required local axes with global axes.
- Launch the application using 'roslaunch miro_teleop miro_teleop.launch'
- Spatial Reasoner will run immediately displaying the first direction of mapping. Press any key to continue after each such image is displayed. Spatial Reasoner will display 4 images, whereas Pertinence Mapping will generate an image plot each time look command is entered in the interpreter.
- User points towards required target. Then, enter look command in Interpreter.
- Wait till path is generated by RRT* (see display on command logic terminal). Then issue go command on Interpreter.
- You can also issue stop command while MIRO is moving to pause. Entering go will make it resume its originak trajectory.
- MIRO halts once goal is reached.
- Pointing to a different direction and issuing look command can be used asynchronously in between actions to reset MIRO's trajectory with a new path.
- Keep an eye on the Motive screen. If rigid bodies are not being tracked properly, you might need to create rigid bodies again with proper alignment.

Objective:
 

Accomplishments:

MiRo and obstacle in the motion capture area with markers on them.

    Pointing gesture on the ground is used to calculate a goal-point where MiRo has to reach.
    Voice command - look (for now typed in the workstation) is used to orient MiRo towards the goal.
    Montecarlo simulation is used to generate an approximate point near the goal-point.
    RRT* planner is used to generate a path from MiRo to the montecarlo given goal-point.
    Voice command - go (for now typed in the workstation) is used to move MiRo towards the goal, as it avoids the obstacle.
    MiRo reaches the goal position.
    MiRo can also be stopped by a voice command - stop (for now typed in the workstation).

 

Modules (files) in the system:

    File 'bla-bla' - does bla-bla. Takes input bla-bla … gives output bla-bla

 

Limitations of the system:
