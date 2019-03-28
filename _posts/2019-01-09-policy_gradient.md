---
layout: post
title: linZHank's Reinforcement Learning
subtitle: (part 1) Vanilla Policy Gradient
data: 2019-01-09 21:29:00
---
> My procrastination went because of a spring break, I guess? So, I gladly found my hands on keyboard again almost three months later after I initiate this post. Anyway, Let me write something for Reinforcement Learning (RL) and Vanilla Policy Gradient (VPG) today.

# Intro Thinking
As an animal living on Earth, I have various goals: fill my starving belly, win a soccer game, become a paleontologist, etc.. I struggle to fulfill these goals and most (if not all) of my actions and behaviors are based on these goals. Of course, some of my actions bring me toward my goals while others take me away. Theoretically, I can improve my performance by practicing again and again. Some people are calling this process as training. So, after training, I should be able to take actions (make decisions) that maximize the probability of achieving these goals.

# Probability Talking
If we model this world as a series of random events, then my life must be the same, so does the process of fulfilling my goals. I am under certain states (hungry, 0-1, in GEOL-1001 class, etc.), I can take actions (eat, run, study, etc.). All of my goals, my states and my actions can be random events, then how do I achieve my goals against randomness? Although they are random, there are probabilities. The probability of I feel hungry at 12 PM is greater than the probability that I am at the state of hungry at 12 AM. The probability of my team scored 3 goals at first minute of the game is extremely small compare to the probability of we are at the state of 3:0 at 90 minutes of the game. The probability of I become a Paleontologist is higher when I am at the state of working in a museum than I am at the state of attending a GEOL 101 class.

# Settings
