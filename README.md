# Autonomous Gait Transitions
This technical report presents a simple framework for managing dynamic **gait transitions** for a quadruped robot.
Controlling a legged robot with different gaits is a fundamental problem, which reinforcement learning techniques are
successfully addressing. Another very important aspect concerns **how and when** to perform transitions between gaits
completely autonomously by the robot, thus without requiring manual switching by an operator. Here, the robot was trained
to perform different gaits using **reward machines** technique. Meanwhile, a condition based on the height difference of the
four feet, handled by an higher level control system, is used for automatic gait switching. The **ANYmal B quadruped** from
ANYbotics was trained using the **Raisim simulator**.


## Reward Machines for Quadruped Locomotion
Reward Machines can be used to specify the sequence of foot contacts required to perform a specific gait.
So that, in our case we can introduce the variable $P = \{{PFL,PFR,PBL,PBR\}}$, where $p \in P$ is a Boolean variable,
indicating whether the front-left (FL), front-right (FR), back left (BL), and back-right (BR) feet are in contact with the ground.

### Trot gait

https://github.com/user-attachments/assets/80c5acc8-e00c-4b07-832d-d4af7a84b41f

### Bound gait

https://github.com/user-attachments/assets/effef32c-5ab7-4c20-9251-fb2b9ffa2f0f

### Pace gait

https://github.com/user-attachments/assets/c5e607b9-fc1b-476d-883e-43e83253da0e


## Robust Transition between Gaits


### Terrrain randomization with Perlin noise

https://github.com/user-attachments/assets/ba15a646-0ebf-4e26-a024-8a1662a633ab

### External forces

https://github.com/user-attachments/assets/54d5ded4-c32b-4505-8900-dec41e7f3f8e

### Manual gait transitions

https://github.com/user-attachments/assets/77168623-93bf-45ee-ade3-391b6ae1aafe


## Condition for autonomous gait transition


### Autonomous gait transition

https://github.com/user-attachments/assets/7d42453e-b7d4-481c-a656-58a2293191f1

### Autonomous gait transition (aerial_view)

https://github.com/user-attachments/assets/d6f6b937-39b0-4d0e-b3ec-dc15ddbdd2ad



Thank you!
