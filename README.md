# Multi-Modal Teach & Repeat 

## Overview

 

## Installation

To set up **bearnav2** in your ROS workspace, follow these steps:

1. Clone the repository into your workspace:
    ```bash
    git clone -b humble --single-branch https://github.com/LCAS/bearnav2.git
    cd bearnav2
    ```

2. Install required Python dependencies:
    ```bash
    pip install -r requirements.txt
    ```

3. Navigate to your workspace and build the package:
    ```bash
    colcon build --packages-select bearnav2
    ```

## Usage

### Simple GUI Usage

The new version of **bearnav2** comes with a simple GUI for controlling mapping and repeating actions. To use the GUI:

1. Source the setup.bash and Launch the ROS2 nodes:
    ```bash
    ros2 launch bearnav2 bearnav2_launch.py
    ```

2. Navigate to the package directory and run the GUI script:
    ```bash
    python3 map_gui.py
    ```

    This will open the GUI interface.

    ![image](https://github.com/user-attachments/assets/b5106119-949f-49ec-9465-f7faaff218d6)

3. In the GUI, enter the name of the map and use the following controls:
    - **Start Mapping**: Click to begin the mapping process and move the robot.
    - **Stop Mapping**: Click to save the map once you’re done.
    - **Repeat Map**: Relaunch the node and GUI, enter the saved map name, and click **Repeat** to replay the map.

For visualization of GUI-related topics (this may impact performance), launch the following:
```bash
ros2 launch bearnav2 bearnav2-gui-launch.py
```

### Classic Usage

If you prefer not to use the GUI control, **bearnav2** can be controlled using a bash script:

1. Firstly, launch the basic node for mapping (without GUI):
    ```bash
    ros2 launch bearnav2 bearnav2_launch.py
    ```

    This will run the **bearnav2_launch** file.

2. If GUI-related topics are needed for visualization, run:
    ```bash
    ros2 launch bearnav2 bearnav2-gui-launch.py
    ```

### Mapping Control via Script

A script (`map_control.sh`) is provided for simpler control over the mapping and repeating actions. Use the following commands:

- **Start mapping**:
    ```bash
    ./map_control.sh start_map <name>
    ```

    Replace `<name>` with your desired map name. After running this command, drive the robot to your desired locations.

- **Stop mapping**:
    ```bash
    ./map_control.sh stop_map <name>
    ```

    This will save the map and stop the mapping process.

- **Repeat a saved map**:
    ```bash
    ./map_control.sh repeat_map <name>
    ```

    Replace `<name>` with the saved map name. This will replay the previously recorded map.

### Important Notes

- Ensure you have mapped your topics correctly in the launch files for your robot’s configuration (e.g., `/cmd_vel`, `/odom`, `/camera/image_raw`).

