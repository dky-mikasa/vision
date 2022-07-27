## Setup

We assume that you have access to a GPU with CUDA >=9.2 support. All dependencies can then be installed with the following commands:

```
pip install -e .
```

## Training & Evaluation

The `starter` directory contains training and evaluation scripts for all the included algorithms. The `config` directory contains training configuration files for all the experiments. You can use the python scripts, e.g. for training call

```
python starter/ppo_locotransformer.py \
  --config config/rl/static/locotransformer/thin-goal.json \
  --seed 0 \
  --log_dir {YOUR_LOG_DIR} \
  --id {YOUR_ID}
```
出现问题，u need to install mpc_osqp
to run PPO+LocoTransformer on the environment, `thin-goal`. And you can use

```
python starter/locotransformer_viewer.py \
  --seed 0 \
  --log_dir {YOUR_LOG_DIR} \
  --id {YOUR_ID} \
  --env_name A1MoveGround
```
出现问题，u need to install mpc_osqp
to test the trained model on the same environment.

## Real Robot Deployment

### Set up robot interface

Since our robot interface based on  [Motion Imitation](https://github.com/erwincoumans/motion_imitation). We provide the simplified interface setup instruction here. For detailed version please check [Motion Imitation](https://github.com/erwincoumans/motion_imitation)

build the python interface by running the following:
```bash
cd third_party/unitree_legged_sdk
mkdir build
cd build
cmake ..
make
```
Then copy the built `robot_interface.XXX.so` file to the main directory (where you can see this README.md file).

To deploy visual-policy, we should also set up Intel RealSense interface. Please check detailed instruction on [Librealsense](https://github.com/IntelRealSense/librealsense)
