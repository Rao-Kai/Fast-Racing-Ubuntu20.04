# Fast-Racing

An Open-source Strong Baseline for SE(3) Planning in Autonomous Drone Racing

Official version can be checked by the links [Fast-Racing](https://github.com/ZJU-FAST-Lab/Fast-Racing)

## 0. Overview
**Fast-Racing** is a strong baseline that focuses on high-quality and extremely aggressive SE(3) trajectory generation. 

The back-end optimization is a parallel extension of [__GCOPTER__](https://github.com/ZJU-FAST-Lab/GCOPTER) for drone racing, also powered by [__MINCO__](https://arxiv.org/pdf/2103.00190.pdf).

**Related Paper**: 

Please cite __BOTH__ papers below if this repo helps you.

- [Fast-Racing: An Open-source Strong Baseline for SE(3) Planning in Autonomous Drone Racing](https://arxiv.org/abs/2105.10276), Zhichao Han, Zhepei Wang, Neng Pan, Yi Lin, Chao Xu, and Fei Gao
- [Geometrically Constrained Trajectory Optimization for Multicopters](https://arxiv.org/abs/2103.00190), Zhepei Wang, Xin Zhou, Chao Xu, and Fei Gao

**Video Links**: [youtube](https://www.youtube.com/watch?v=kjSU2vXCXXg) or [bilibili](https://www.bilibili.com/video/BV1sq4y1779e/).

## 1. Setup
All the tests are conducted in the Linux environment on a computer equipped with an Intel Core i7-10700 CPU and a GeForce RTX 2060 GPU.

Moreover, Our software is developed and tested in Ubuntu 20.04 with ROS installed.

ROS can be installed here: [ROS Installation](http://wiki.ros.org/ROS/Installation).

Also,  we need to install `gcc>=8.0.0` and `Eigen>=3.3.0`.

(**Notion:** if you are using Ubuntu 20.04, just ignore this step because higher version of  ` gcc` and `Eigen` have been installed while you are installing ROS; but if you are using Ubuntu18.04, you need to update these versions.)

### Install `gcc>=8.0.0:`

 1. Type the following command to install it.

    ```
    sudo apt-get install gcc-8 g++-8
    ```

 2. Verify installation by:

    ```
    gcc-8 --version
    ```

### Install `Eigen>=3.3.0`

You can download the source code package from [Eigen Installation](https://eigen.tuxfamily.org/index.php?title=Main_Page).

Please make sure to install the **correct version**.

Your can run the following command to check `Eigen` version.

```
sudo gedit /usr/include/eigen3/Eigen/src/Core/util/Macros.h
```

## 2. Download Track Binaries

1. Download the [**settings.json**](https://github.com/ZJU-FAST-Lab/Fast-Racing/releases/tag/v1.0) 

2. Download any one of the tracks such as [**Zhangjiajie.zip**](https://github.com/ZJU-FAST-Lab/Fast-Racing/releases/tag/v1.0), and unzip it.

3. Test it. Take `Zhangjiajie` as an example. Open a terminal window, `cd` to `Zhangjiajie/`directory. and type the following command:

   ```
   ./run.sh -windowed
   ```

## 3. Build on ROS

1. Install the dependence.

   ```
   sudo apt-get install libarmadillo-dev
   sudo apt-get install ros-noetic-octomap*
   sudo apt-get install ros-noetic-tf2-sensor-msgs ros-noetic-tf2-geometry-msgs ros-noetic-mavros*
   ```

2. Create an empty new workspace and clone this repository to your workspace: 

   ```
   git clone https://github.com/Rao-Kai/Fast-Racing-Ubuntu20.04
   cd Fast-Racing-Ubuntu20.04
   ```

3. Compile it.

   ```
   catkin_make
   ```

## 4. Run the Simulation

 1. Run the track binary.

    Before the simulation racing, you need to run the rack binary.

    Open a terminal window, `cd` to `Zhangjiajie/` directory. and type the following command:

    ```
    ./run.sh -windowed
    ```
    
    Copy `settings.json` downloaded in Step 2.1 to`~/Documents/AirSim/settings.json`. Then rerun

    ```
    ./run.sh -windowed
    ```

3. Run the planner.

    Open a new terminal window, `cd ` to `~/your_catkin_ws/` and type:

    ```
    source devel/setup.bash
    ```

    Then, run the script corresponding to the track. Take `Zhangjiajie` as the example:

    ```
    ./zhangjiajie.sh 
    ```

    After the global map is set up, you can use the **3D Nav Goal** in **RVIZ** to trigger the planning.

