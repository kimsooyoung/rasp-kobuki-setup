# rasp-kobuki-setup

original install

```
sudo apt install python-catkin-tools
sudo apt-get install ros-melodic-kobuki-\* -y
sudo apt-get install ros-melodic-ecl-streams -y
sudo apt install ros-melodic-joy
```

## gedit ~/.bashrc 후 다음의 커맨드들을 추가해 주세요!!

```
alias eb='gedit ~/.bashrc'
alias sb='source ~/.bashrc'
alias gs='git status'
alias gp='git pull'
alias cw='cd ~/catkin_ws/src'   
alias cs='cd ~/catkin_ws/src'
alias cm='cd ~/catkin_ws && catkin_make'
```
