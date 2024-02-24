---
layout: default
title: Landing on the Moon with Reinforcement Learning 
parent: Mumbles
nav_order: 1
---

# Prelude
Since the pandemic, I spent some spare time to study deep reinforcement learning(RL) and I decided to replicate some DRL algorithms "from scratch". Now, I have realized a few through Python and Tensorflow 2. So, I started writing this series of posts to record my progress. Hopes it can inspire people who are interested in reinforcement learning. 

# What is Reinforcement Learning
To me, it is just a fancier term of "trial-and-error". A toddler learns to walk, a basketball player learns to shoot 3-pointers, a puppy learns to sit, an artificially intelligent agent learns to play video games, etc.. As long as an agent(human, animal, AI) improves its performance through the interactions with the environment guided by some sort of reward, such improvment can be viewed as reinforcement learning.

# LunarLander Environment
And yes, I need a task to start my journey of DRL. As [OpenAI Gym](https://github.com/openai/gym) provides hundreds and thousands of environments, it becomes a convenient tool for people who want to study or implement RL algorithms. Usually, people will get started with the `CartPole` environment because it is almost the simplest environment. However, it only offers discretized action space. As I would like to experiment on the algorithms working under the continuous action space, the **`LunarLander`** became my first choice. Besides: 
1. It is not too easy. Compare to the CartPole's observation space (4 dimensions), LunarLander has 8 dimensions. The algorithms discretizing the observation space such as Q-learning works well on the former but could be struggling on the later due to the curse of dimensionality.  
2. It is not too hard. Many more advanced environments (such as Atari) now are serving observations (e.g. image) with higher dimensions. LunarLander, however, serves semantic observations in 8 dimensions so that only the simplest neural network structure(stack of fully connected layers) is needed.

## Observation Space
There is a global coordinate system at the center of the landing pads with X-axis pointing to the right and Y-axis pointing upward. A body frame is attached on the lander with y-axis pointing its top. The observation (state) of the lander at each time step can described as the position, velocity, orientation, angular velocity of the lander, plus two boolean contact indicatorsi (x,y,x',y',\theta,\theta',leftLegContact, rightLegContact).  
![LunarLander Observation Space]({{ site.baseurl }}/images/20210128/ll_obs.png)

## Action Space
As mentioned before, LunarLander environment offers 2 types of action spaces. For discrete action space, use 'LunarLander-v2'. For continuous action space version, use 'LunarLanderContinuous-v2'. 
1. If working under discrete action space, 4 actions available: do nothing, fire left orientation engine, fire main engine, fire right orientation engine.
2. If working under continuous action space, action is two real values vector from -1 to +1. First controls main engine, -1..0 off, 0..+1 throttle from 50% to 100% power. Engine can't work with less than 50% power. Second value -1.0..-0.5 fire left engine, +0.5..+1.0 fire right engine, -0.5..0.5 off.

## Reward 
Reward for moving from the top of the screen to landing pad and zero speed is about 100..140 points. If lander moves away from landing pad it loses reward back. Episode finishes if the lander crashes or comes to rest, receiving additional -100 or +100 points. Each leg ground contact is +10. Firing main engine is -0.3 points each frame. Solved is 200 points. Specific reward function is defined in the [source code](https://github.com/openai/gym/blob/master/gym/envs/box2d/lunar_lander.py), line 318-329.

