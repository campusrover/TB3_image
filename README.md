# Turtlebot3 ROS Noetic Ubuntu 20.04 Image


Download Image: [ROS Noetic Ubuntu 20.04](https://drive.google.com/file/d/1EGy9g5gE4kLXJk-oa_l-MDt5miUB33-r/view?usp=sharing)


## Instructions:

  1. Flash the image into a microsd card using an imager (dd for linux, or RPiImager).
  
  2. Connect the Turtlebot to a monitor and keyboard, insert the microsd card and turn on the bot.
  
  3. Log into the turtlebot with the username: *ubuntu* and the password: *ROSlab134*
  
  4. You will want to remove the tailscale information using the following commands:
  
    sudo apt-get remove tailscale
    sudo rm /var/lib/tailscale/tailscaled.state
    sudo nano /etc/hostname # edit this file to change the hostname from "roba" to your robot's name
    sudo reboot now

  5. Once the turtlebot is rebooted, change the hostname and reinstall tailscale:
  
    sudo apt-get install tailscale
    sudo tailscale up --authkey=<ask pito for the tailscale key to put here>
    
  6. Now update the OpenCR board with the following commands:
  
    export OPENCR_PORT=/dev/ttyACM0
    export OPENCR_MODEL=burger_noetic
    rm -rf ./opencr_update.tar.bz2
    wget https://github.com/ROBOTIS-GIT/OpenCR-Binaries/raw/master/turtlebot3/ROS1/latest/opencr_update.tar.bz2 
    tar -xvf opencr_update.tar.bz2 
    cd ./opencr_update
    ./update.sh $OPENCR_PORT $OPENCR_MODEL.opencr
    
  7. Once the OpenCR board is updated, shut down your bot and turn it back on and you are done with the setup.
