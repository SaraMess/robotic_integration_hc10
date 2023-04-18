# robotic_integration_hc10

## Environement : Machine virtuelle
Ubuntu 20.04
Ros Noetic + packages moveIt, Ros control, ...
Visual Studio Code
Python 3

catkin build 
source devel/setup.bash 

1. demo_fake

Se placer sur le répertoire catkin_ws :
cd robotic_integreation_hc10/catkin_ws

Dans la permier terminal lancer :
roslaunch hc10_moveit_config demo_fake.launch 

Dans la deuxième terminal lancer :
rosrun hc10_moveit_config  hc10_move_arm.py 

2. demo_gazebo

Se placer sur le répertoire catkin_ws :
cd robotic_integreation_hc10/catkin_ws

Dans la permier terminal lancer :
roslaunch hc10_moveit_config demo_gazebo.launch 

Dans la deuxième terminal lancer :
rosrun hc10_moveit_config  hc10_move_arm_kinect.py 


## Etape 1 : Prise en main de l'environnement


## Etape 2 : Génération de trajectoires


## Etape 3 : Environnement de simulation


## Etape 4 : Couplage capteurs
