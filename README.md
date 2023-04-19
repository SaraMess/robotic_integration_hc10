# robotic_integration_hc10

## Environment : Virtual Machine
Ubuntu 20.04  
Ros Noetic + packages moveIt, Ros control, ...  
Visual Studio Code  
Python 3  


## Prise en main de l'environnement
Prise en main de l'environnement ROS et de l'outil de génération de trajectoire MoveIt


```bash
catkin build 
source devel/setup.bash 
```

#### demo_fake

Se placer sur le répertoire catkin_ws :
```bash
cd robotic_integreation_hc10/catkin_ws
```

Dans la permier terminal lancer :
```bash
roslaunch hc10_moveit_config demo_fake.launch 
```

Dans la deuxième terminal lancer :
```bash
rosrun hc10_moveit_config  hc10_move_arm.py
```

#### demo_gazebo

Se placer sur le répertoire catkin_ws :
```
cd robotic_integreation_hc10/catkin_ws
```

Dans la permier terminal lancer :
```
roslaunch hc10_moveit_config demo_gazebo.launch 
```

Dans la deuxième terminal lancer :
```
rosrun hc10_moveit_config  hc10_move_arm_kinect.py 
```




## Génération de trajectoires
Utilisation de l'API MoveIt! pour générer des trajectoires dans l'espace cartésien



## Environnement de simulation
Intégration d'un environnement de simulation (Gazebo) et ajout d'un capteur de type 3D



## Couplage capteurs
Intégration des données du capteur 3D dans le programme de génération de trajectoires

