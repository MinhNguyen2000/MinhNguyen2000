## Hello World 👋

<!--
**PhantomLucario/PhantomLucario** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->

I am an aspiring student learning robotic programming 🤖⚙️ I am passionate about data-driven and learning-based methods in robotic applications.

# 🌱 Courses

- [ ] [Self-driving and ROS 2 - Udemy](https://www.udemy.com/course/self-driving-and-ros-2-learn-by-doing-odometry-control) => [bumperbot_ws Github Repo](https://github.com/MinhNguyen2000/bumperbot_ws)
- [x] [IBM Deep Learning and Reinforcement Learning - Coursera](https://www.coursera.org/learn/deep-learning-reinforcement-learning) => [Course_IBM_DLRL Github Repo](https://github.com/MinhNguyen2000/Course_IBM_DLRL)

# 🦾 Current Robotic and Control Projects
## Experiments with DRL algorithms ([experiment repo](https://github.com/MinhNguyen2000/experiment/tree/main/DRL))
This is an ongoing project that helps me build the foundational knowledge of RL and DRL, as well as testing my understanding of the algorithms in gymnasium environments by creating custom-made algorithms and compared them with stable_baselines3 implementations
  - [x] **FrozenLake-v1** (discrete state & action) for learning and testing classic RL methods such as Monte Carlo (MC), Temporal Difference (1-step TD with n-step TD coming), and REINFORCE.
  - [x] **CartPole-v1** (continuous state & discrete action) for learning and testing DQN, Double DQN, REINFORCE, A2C, and PPO.
  - [x] **MuJoCo environments** (continuous state & action spaces)
    - [x] **InvertedPendulum-v5** for testing PPO, and most recently TD3. After training and fine-tuning the hyperparameters of the TD3 algorithm, I created a custom wrapper to turn the problem into a SwingupInvertedPendulum. I used this environment for experimenting with reward engineering/shaping to perform the inverted pendulum control task.
    - [x] **InvertedDoublePendulum-v5** for testing the portability and performance of the TD3 algorithm created for the InvertedPendulum problem. The custom-made TD3 agent was able to learn without much modification, aside from some hyperparameter fine-tuning to achieve the maximum possible reward (staying healthy until episode truncation).
    - [x] **Reacher-v5** for training a TD3 algorithm. I had the most problems with this environment, where I had to manually tweak the early stopping logic to obtain a somewhat decent policy. The TD3 algorithm showed promise in learning the desired behaviour, reaching rewards of approximately -4.5 (benchmark performance by the Tianshou DRL library was reported as -2.7 for TD3). When I retrained using the stable_baselines3 implementation, I received similar results given the same hyperparameter set.
    - [x] **HalfCheetah-v5** for training a TD3 policy to control the forward motion of a 6-DOF robot. Given the benchmark performance of 10,000+ reward after 1,000,000 steps (Tianshou DRL library), my current implementation reached approximately 8,000 reward units in the same learning budget.
    - [x] **Walker** for training a TD3 policy.
    - [ ] Upcoming - experiment with A3C and SAC in the near future.

## ROSMaster X1 Robot and ROS2 

→ [DRL policy training repo](https://github.com/MinhNguyen2000/ROS2_DRL_Navigation)

→ [Physical robot deployment repo](https://github.com/MinhNguyen2000/X1_ROS2_ws)

**ROS2 Humble · PyTorch TD3 · ONNXRuntime + TensorRT · MuJoCo · Jetson Nano**
A full-stack robotics project deploying a **deep reinforcement learning (TD3) navigation policy** and a **real-time face detection pipeline** on a physical non-holonomic mobile robot, with ROS2 as the integration framework. The robot detects a human face through its RGB-D camera, estimates the face's 3D position in space, and autonomously navigates toward it — avoiding obstacles along the way using LiDAR — all running on a Jetson Nano 4GB at the edge.

#### Highlights
- Trained a TD3 policy in **MuJoCo** (Stable Baselines3) with curriculum learning and multi-core parallel rollouts (`SubprocVecEnv`), then deployed it on real hardware by exporting actor weights as plain `.pt` files — no SB3 runtime dependency
- Fused wheel odometry, LiDAR scan matching (RF2O), and IMU data through an **Extended Kalman Filter** (`robot_localization`) for stable pose estimation
- Ran **YOLOv5 face detection** at the edge with ONNXRuntime + TensorRT (fp16), achieving real-time inference on Jetson Nano; monocular depth estimated via pinhole camera model
- Bridged the sim-to-real gap with 18-sector min-pooled LiDAR observations, handling the scan direction mismatch between MuJoCo (clockwise) and ROS `LaserScan` (counter-clockwise)
- Implemented a ROS2 action server / client architecture (`NavigateToGoal`) with goal preemption, cancellation, timeout handling, and live feedback at 50 Hz

#### Stack
`ROS2 Humble` `PyTorch` `Stable Baselines3` `MuJoCo` `Gymnasium` `ONNXRuntime` `TensorRT` `robot_localization` `Docker` `Jetson Nano`


## Control of a physical inverted pendulum using LQR controller ([Inverted-Pendulum repo](https://github.com/MinhNguyen2000/Inverted-Pendulum))
A side project that I worked on before starting my MSc in UNB, where I improved upon the physical and electrical components of an inverted pendulum, and created a control program for the system. 

**Physical improvements**
  - Redesigned and 3D printed the pendulum carriage with a belt tensioner, the belt-drive pulley mounts, and the limit switch mounts. These parts were remade for added functionality and strength compared to the existing parts.
  - Recalibrated the linear rail of the pendulum carriage to reduce the wobble and improve smoothness during operation.
  - Created a CAD model for the pendulum system using Fusion 360.

**Electrical improvements**
  - Previously, the inverted pendulum was controlled by an insufficiently documented microcontroller; no one knew how to operate the inverted pendulum. I was tasked with upgrading this system, using a Raspberry Pi 5 as a microcomputer that interacts with a LabJack T7 microcontroller. I wrote a short control program in Python, following a simple finite state machine architecture, to control the motion of the system throughout different states, such as calibration, zeroing, and balancing.
  - The system also had no fail-safe mechanisms aside from an E-stop, so I added two limit switches as an electrical fail-safe and implemented a software fail-safe mechanism (based on the current carriage position) in the control program

# 📖 **Current Book List**
- Reinforcement Learning - An Introduction (Sutton and Barto, 2018) [Book Link](http://incompleteideas.net/book/RLbook2020.pdf)
- Multi-Agent Reinforcement Learning: Foundations and Modern Approaches (Albrecht, Christianos, and Schäfer) [Book Link](https://www.marl-book.com/download/marl-book.pdf)
- Introduction to Autonomous Mobile Robots (Siegwart, Nourbakhsh, and Scaramuzza)
- Understanding Deep Learning (Simon Prince) [Book Link](https://udlbook.github.io/udlbook/)
- Dive into Deep Learning (Zhang A., Lipton Z., Li M. and Smola A.) - [Link](https://d2l.ai/)
