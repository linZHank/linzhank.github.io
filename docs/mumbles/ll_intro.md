---
layout: default
title: Landing on the Moon with Reinforcement Learning 
parent: Mumbles
nav_order: 1
---

# Prelude
Since the pandemic, I spent some spare time to study deep reinforcement learning(DRL) and I decided to replicate some DRL algorithms "from scratch". Now, I have realized a few through Python and a high-performance numerical computing library: [JAX](https://jax.readthedocs.io/en/latest/). So, I started writing this series to record my progress. 

# What is Reinforcement Learning
To me, it is just a fancier term of "trial-and-error". A toddler learns to walk, a basketball player learns to shoot 3-pointers, a puppy learns to sit, an artificially intelligent agent learns to play video games, etc.. As long as an agent(human, animal, AI) improves its performance through the interactions with the environment guided by some sort of reward, such improvment can be viewed as reinforcement learning.

# LunarLander Environment
And yes, I need a task to start my journey of DRL. As [Gymnasium](https://gymnasium.farama.org/) provides hundreds and thousands of environments, it becomes a convenient tool for people who want to study or implement control algorithms. Although, the [CartPole](https://github.com/Farama-Foundation/Gymnasium/blob/main/gymnasium/envs/classic_control/cartpole.py) environment is the most welcome one among the beginners, it only offers discretized action space. As I would like to experiment on the algorithms working under the continuous action space, the [LunarLander](https://github.com/Farama-Foundation/Gymnasium/blob/main/gymnasium/envs/box2d/lunar_lander.py) became my first choice. Besides: 
1. It is not too easy. Compare to the CartPole's observation space (4 dimensions), LunarLander has 8 dimensions. The algorithms discretizing the observation space such as Q-learning works well on the former but could be struggling on the later due to the curse of dimensionality.  
2. It is not too hard. Many more advanced environments (such as Atari) now are serving observations (e.g. image) with higher dimensions. LunarLander, however, serves semantic observations in 8 dimensions so that only a simple neural network structure(stack of fully connected layers) is needed.

## Observation Space
To figure out what do these 8 dimensions in the observation space mean, let me decode the environment canvas a little.

There is a global coordinate system at the center of the landing pads with X-axis pointing to the right and Y-axis pointing upward. A body frame is attached on the lander with y-axis pointing its top. The observation (state) of the lander at each time step can described as the position, velocity, orientation, angular velocity of the lander, plus two boolean contact indicatorsi (x,y,x',y',\theta,\theta',leftLegContact, rightLegContact).  
![LunarLander Observation Space]({{ site.baseurl }}/images/20210128/ll_obs.png)

## Action Space
As mentioned before, LunarLander environment offers 2 types of action spaces. For discrete action space, use 'LunarLander-v2'. For continuous action space version, use 'LunarLanderContinuous-v2'. 
1. If working under discrete action space, 4 actions available: do nothing, fire left orientation engine, fire main engine, fire right orientation engine.
2. If working under continuous action space, action is two real values vector from -1 to +1. First controls main engine, -1..0 off, 0..+1 throttle from 50% to 100% power. Engine can't work with less than 50% power. Second value -1.0..-0.5 fire left engine, +0.5..+1.0 fire right engine, -0.5..0.5 off.

## Reward 
> Quate
```markdown
After every step a reward is granted. The total reward of an episode is the
sum of the rewards for all the steps within that episode.

For each step, the reward:
- is increased/decreased the closer/further the lander is to the landing pad.
- is increased/decreased the slower/faster the lander is moving.
- is decreased the more the lander is tilted (angle not horizontal).
- is increased by 10 points for each leg that is in contact with the ground.
- is decreased by 0.03 points each frame a side engine is firing.
- is decreased by 0.3 points each frame the main engine is firing.

The episode receive an additional reward of -100 or +100 points for crashing or landing safely respectively.

An episode is considered a solution if it scores at least 200 points.

```

Specific reward function is defined in the [source code](https://github.com/Farama-Foundation/Gymnasium/blob/main/gymnasium/envs/box2d/lunar_lander.py), line 634-658.

