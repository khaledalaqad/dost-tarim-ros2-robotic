# dost-tarim-ros2-robotic
# 🌿 Dost Tarım Teknolojileri – ROS2 AGV Mission Control Dashboard

A modern ROS 2 web-based dashboard for visualizing, replaying, and monitoring Automated Guided Vehicle (AGV) missions using real ROS 2 bag files recorded inside a greenhouse environment.

---

## 📌 Overview

This project was developed to visualize and replay real AGV missions recorded in a greenhouse using ROS 2.

Instead of displaying simulated data, the dashboard loads actual ROS 2 Bag recordings, reconstructs the robot trajectory, and displays the robot moving on the original occupancy grid map.

The goal is to provide a modern Mission Control Dashboard similar to industrial fleet management systems used in autonomous robotics.

---

## ✨ Features

### 🚜 Mission Replay

- Replay real ROS 2 bag missions
- Play / Pause / Reset
- Adjustable replay speed
- Timeline playback

---

### 🗺 Interactive Map

- Display original occupancy grid map
- Robot localization
- Robot heading visualization
- Robot trail
- Start point
- Goal point
- Zoom
- Pan
- Center Robot
- Follow Robot
- Fit Map

---

### 📊 Robot Telemetry

Displays real robot information extracted from ROS Bag.

- X Position
- Y Position
- Heading (Yaw)
- Mission Time
- Distance Travelled
- Current Speed
- Average Speed
- Maximum Speed
- Mission Progress

---

### 📈 Mission Statistics

- Mission duration
- Total distance
- Average velocity
- Maximum velocity
- Number of stops
- Number of turns

---

### 📑 Event Log

Displays important mission events.

Example:

- Mission Started
- Mission Loaded
- Robot Moving
- Robot Stopped
- Mission Finished

---

### ⚙ ROS 2 Integration

The dashboard uses native ROS 2 libraries to read recorded data.

Supported technologies:

- rosbag2_py
- rclpy
- nav_msgs
- geometry_msgs
- sensor_msgs

---

## 🏗 System Architecture

```
                ROS2 Bag (.db3)

                       │

               rosbag2_py Reader

                       │

          Deserialize ROS Messages

                       │

        Mission Replay Controller (ROS2)

                       │

           Flask + Socket.IO Backend

                       │

             Web Dashboard (HTML)

                       │

          Canvas Map Visualization
```

---

## 📂 Project Structure

```
dost-tarim-ros2-dashboard

├── backend
├── frontend
├── ros2
├── maps
├── bags
├── docs
├── screenshots
├── assets
├── README.md
├── requirements.txt
└── docker-compose.yml
```

---

## 🛰 ROS Topics Used

The dashboard reads recorded topics from ROS 2 bag files.

Primary topic:

```
/odometry/filtered_uwb
```

Fallback:

```
/odom
```

Other supported topics:

```
/scan
/cmd_vel
/tf
/tf_static
/imu
/map
```

---

## 🗺 Map Files

The dashboard uses the original map generated during SLAM.

Files:

```
map.pgm
map.yaml
```

The map is displayed as the environment background while robot coordinates are converted into pixel coordinates using:

- map resolution
- map origin
- occupancy grid size

---

## 📦 Technologies

### Backend

- Python
- ROS 2 Humble
- Flask
- Flask-SocketIO
- rosbag2_py
- PyYAML
- Pillow

---

### Frontend

- HTML5
- CSS3
- JavaScript
- Canvas API
- Socket.IO

---

## 🚀 Installation

Clone the repository

```bash
git clone https://github.com/YOUR_USERNAME/dost-tarim-ros2-dashboard.git
```

Go into the project

```bash
cd dost-tarim-ros2-dashboard
```

Build the ROS package

```bash
cd ~/ros2_ws

colcon build

source install/setup.bash
```

Run

```bash
ros2 run agv_dashboard dashboard
```

Open

```
http://localhost:5050
```

---

## 📸 Screenshots

Dashboard

```
screenshots/dashboard.png
```

Mission Replay

```
screenshots/mission.png
```

Map Viewer

```
screenshots/map.png
```

---

## 🎯 Future Improvements

- Live ROS2 Topics
- Camera Streaming
- LiDAR Visualization
- Multi Robot Fleet
- Battery Monitoring
- Diagnostics
- Heat Maps
- Path Planning
- Waypoint Editor
- WebRTC Camera
- 3D Viewer
- RViz Integration

---

## 📜 License

This project is intended for educational and research purposes.

---

## 👨‍💻 Author

Developed using

- ROS 2 Humble
- Python
- Flask
- Socket.IO
- HTML5
- JavaScript

---

## 🌱 About

This project demonstrates how real ROS 2 bag recordings can be transformed into a modern web-based Mission Control Dashboard for agricultural autonomous robots operating inside greenhouse environments.
