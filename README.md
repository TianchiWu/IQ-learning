# Inverse Q-Learning (IQ-Learn)

## SOTA framework for non-adversarial Imitation Learning

IQ-Learn enables very fast, scalable and stable imitation learning.
Our IQ-Learn algorithm is present in `iq.py`. This file can be used standalone to add **IQ** to your IL & RL projects. 

IQ-Learn can be implemented on top of most existing RL methods (off-policy & on-policy) by changing the critic update loss to our proposed `iq_loss`. <br>
(IQ has been successfully tested to work with Q-Learning, SAC, PPO, DDPG and Decision Transformer agents).

## Requirement

- pytorch (>= 1.4)
- gym
- wandb 
- tensorboardX
- hydra-core=1.0 (>= 1.1 is incompatible currently)

Warning: torch version depends on training GPU

## Installation

- Make a conda environment and install dependencies: `pip install -r requirements.txt`
- Setup wandb project to log and visualize metrics, change the entity originally 'iq_learn' in train_iq.py to your account
- Download expert datasets for Mujoco and gym from [GDrive](https://drive.google.com/file/d/1UBSGAB38gnJ4NWrUaiMnW7uNApcl7TJr/view?usp=share_link), add them to folder experts.
- (Optional) Download expert datasets for Atari environments from [GDrive](https://drive.google.com/file/d/1wKdMi10_X0oV4URdkv8JSCY0rRB8iBFq/view?usp=sharing)

## Instructions
We show example code for training Q-Learning and SAC agents with **IQ-Learn** in `train_iq`.py. We make minimum modifications to original RL training code present in `train_rl`.py and simply change the critic loss function.
<!-- Our training code is present in `train_iq.py` which implements **IQ-Learn** on top of DQN/SAC RL agents by simply changing the Q-function update rule. RL training code is in `train_rl.py`. <br> IQ-Learn simplify modifies the loss function for the critic network, compared to vanilla RL. -->

- To reproduce our Offline IL experiments, see `scripts/run_offline.sh`
- To reproduce our Mujoco experiments, see `scripts/run_mujoco.sh`
- To reproduce Atari experiments, see `scripts/run_atari.sh`
- To visualize our recovered state-only rewards on a toy Point Maze environment: 
    `python -m vis.maze_vis env=pointmaze_right eval.policy=pointmaze agent.init_temp=1 agent=sac.q_net._target_=agent.sac_models.DoubleQCritic`. <br>
    Reward visualizations are saved in `vis/outputs` directory

## Reproduce Atari experiments

We followed the instruction and reproduced the Atari breakout experiment. In limited time, we achieved a
best reward, over 200.

<img src="./docs/breakout.png" width="500"> 


## Contributions

Contributions are very welcome. If you know how to make this code better, please open an issue. If you want to submit a pull request, please open an issue first. 

## License

The code is made available for academic, non-commercial usage. Please see the [LICENSE](LICENSE.md) for the licensing terms of IQ-Learn for commercial use and running it on your robots/creating new AI agents.

For any inquiry, contact: Div Garg ([divgarg@stanford.edu](mailto:divgarg@stanford.edu?subject=[GitHub]%IQ-Learn))