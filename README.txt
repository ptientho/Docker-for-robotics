# How to launch Docker container
Please follow each step carefully

1. Install Docker (in case Docker is not installed)

    sudo apt-get update
    sudo apt-get install -y docker.io docker-compose
    sudo service docker start

2. Use Docker w/o sudo (in case a new terminal is up)

    sudo usermod -aG docker $USER
    newgrp docker

3. Launch docker compose file

    cd ~/ros2_ws/src/tortoisebot_ros2_docker
    docker-compose up -d

4. Verify that the expected containers are up and running

    docker ps

5. Execute each running container by the following

    docker exec -it [container_name] bash

for example, to run "tortoisebot-ros2-gazebo"

    docker exec -it tortoisebot-ros2-gazebo bash

inside the container, run

    colcon build
    source /ros2_ws/install/setup.bash
    ros2 launch tortoisebot_bringup bringup.launch.py use_sim_time:=True

do the same steps for the other containers