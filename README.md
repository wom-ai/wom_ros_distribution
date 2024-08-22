
# WOM ROS Distribution

This repository hosts the Debian packages for the `wom_ros_interfaces` and `wom_ros` ROS 2 packages. These packages are built and distributed for limited use, making it easier to install and use them in your ROS 2 projects.

## Packages Overview

- **wom_ros_interfaces**: Provides the foundational interfaces for WOM projects.
- **wom_ros**: Builds on `wom_ros_interfaces` and provides additional functionalities. **Requires `wom_ros_interfaces` to be installed first.**

## Installing the Packages

These packages are distributed through GitHub Releases as `.deb` files. Follow the steps below to download and install the packages.

### Step 1: Download the `.deb` Files

Go to the [Releases](https://github.com/wom-ai/wom_ros_distribution/releases) section of this repository and download the `.deb` files for both `wom_ros_interfaces` and `wom_ros`.

Make sure to download the appropriate versions that are compatible with your ROS 2 distribution (e.g., Humble).

### Step 2: Install `wom_ros_interfaces`

Install `wom_ros_interfaces` first, as `wom_ros` depends on it.

```bash
sudo dpkg -i /path/to/downloaded/ros-humble-wom-ros-interfaces_<version>_arm64.deb
```

Replace `/path/to/downloaded/` with the actual path to where you downloaded the `.deb` file and `<version>` with the version number of the package.

### Step 3: Install `wom_ros`

After `wom_ros_interfaces` is installed, install `wom_ros`:

```bash
sudo dpkg -i /path/to/downloaded/ros-humble-wom-ros_<version>_arm64.deb
```

## Usage

Once both packages are installed, you can use them in your ROS 2 projects. For example:

```bash
source /opt/ros/humble/setup.bash
ros2 run wom_ros <node_name>
```

Replace `<node_name>` with the appropriate node provided by the `wom_ros` package.

## Adding `wom_ros` Source List to rosdep [Optional]

To ensure `rosdep` can resolve dependencies for these `wom_ros` packages, you'll need to add a custom source list file to `rosdep`.

### Step 1: Add the Source List to rosdep

Add your custom source list file to `rosdep`:

```bash
sudo sh -c 'echo "yaml https://raw.githubusercontent.com/wom-ai/wom_ros_distribution/main/wom_ros.yaml" > /etc/ros/rosdep/sources.list.d/50-wom-ros-packages.list'
```

### Step 2: Update rosdep

Update `rosdep` to include the new source:

```bash
rosdep update
```

Now `rosdep` will be able to resolve dependencies for `wom_ros_interfaces` and `wom_ros` using your custom source.
