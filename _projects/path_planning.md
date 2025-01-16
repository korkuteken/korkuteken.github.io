---
layout: page
title: Path Planning using Dynamic Programming
description: Robot Planning and Learning
img: assets/img/planning_cover.gif
importance: 2
category: robotics
related_publications: false
---

In this project, I have utilized Markov Decision Process and Dynamic Programming to find an optimal path for my agent to reach a goal state. In the sample 5x5 environment figure below, red triangle represents the agent and the green square is the goal state. I came up with a motion model as well as step costs and terminal costs. The project consisted of two parts: Part A with a known map and Part B with an unknown random map with some constraints. The full report on the implementation can be found <a href="https://drive.google.com/file/d/1pOnXoYQ2c4oza3pGRqMp36wi9t4Gqc9C/view">here</a>.

For Part A of the project, I defined the state of the agent to have the position of the agent, direction that it is facing, whether the key is picked up or not, and finally whether the door is locked or not. In order to solve for the optimal path, we first need to find all possible states as defined earlier. Algorithm loops through all the non-wall cells, generating every possible configuration of direction, key status, and door status. Then, terminal costs are assigned for each state and step cost of each state is initialized and saved to a matrix. The step cost of agent being stationary is set to be 0. Finally the optimal policy is obtained using dynamic programming. Some examples from this part is shown below.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/agent1.gif" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/agent2.gif" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/agent3.gif" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

For Part B of the project, environment was chosen randomly instead of being known to the agent beforehand. A random map in this project has the following structure, it has two doors at locations (4,2) and (4,5) where either can be locked or unlocked; the key can be in any one of the locations (1,1), (2,3), (1,6); and the goal can be in any one of the locations (5,1), (6,3), (5,6). All the maps in this part is 8x8 environments. In order to compute a policy for all these possibilities beforehand, I added goal position, key position, and the status of the doors to the states to encode the parameters of the environment. Similar to the algorithm for a known map, we start by generating every possible state using the state space definition. Then, step costs and terminal costs of each state are calculated. To cut down the computation time, step cost is only calculated for states that share the same environment parameters, i.e. has the same goal position and key position. Then, the same algorithm is used to find a policy. This policy has all the different states for any configuration of random environments. After a random environment is created, the initial state is found including the door status, key position, and goal position. Then, the optimal action sequence for this initial state is found using the policy computed earlier. Some examples can be found below.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/agent4.gif" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/agent5.gif" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/agent6.gif" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
