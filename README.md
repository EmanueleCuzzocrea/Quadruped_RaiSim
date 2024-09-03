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
Basically, they use a **finite-state automaton** to represent a specific gait, and they encourages transitions inside it
by adding an **extra reward** to the stardard reward used for the locomotion. This way, multiple gaits can be learned
without any specific tuning of the hyperparameters.

### Trot gait

https://github.com/user-attachments/assets/80c5acc8-e00c-4b07-832d-d4af7a84b41f

### Bound gait

https://github.com/user-attachments/assets/effef32c-5ab7-4c20-9251-fb2b9ffa2f0f

### Pace gait

https://github.com/user-attachments/assets/c5e607b9-fc1b-476d-883e-43e83253da0e


## Robust Transition between Gaits
The individual gaits were trained separately, and no transitions between the gaits were explicitly trained.
What was done was to make each gait as robust as possible so that the policy switch could be performed instantaneously without the robot falling.
To make the transitions between different gaits more robust, a methodology was adopted that involves training the
individual gaits on **irregular terrains** generated using **Perlin noise**, which changes randomly every 5 iterations (for reducing
computational cost), and also applying **external disturbances** to the robot in the form of forces along the x,y,z axes at
the origin of the base frame. This choice was motivated by the need to improve the robot’s ability to regain control in
difficult conditions and thus better manage the runtime gait transitions.

### Terrrain randomization with Perlin noise

https://github.com/user-attachments/assets/ba15a646-0ebf-4e26-a024-8a1662a633ab

### External forces

https://github.com/user-attachments/assets/54d5ded4-c32b-4505-8900-dec41e7f3f8e

### Manual gait transitions

https://github.com/user-attachments/assets/77168623-93bf-45ee-ade3-391b6ae1aafe


## Condition for autonomous gait transition
The condition that was developed concerns the height difference of the feet at the moment of contact with the ground. Specifically, a higher-level controller manages four variables, encapsulated in the vector $h = [h_{FL}, h_{FR}, h_{BL}, h_{BR}]$. These variables represent the height of each foot relative to the body frame the last time each foot touched the ground. At each step of the simulation, a check is performed to determine which feet are in contact with the ground. For all feet in contact, the corresponding variable $h_i$ is updated. It is important to note that these variables are not part of the robot's state but are simply necessary for a higher-level controller to perform the policy change.

Now, at each step, the difference between all the values of $h$ is calculated. Since there are only 4 variables, this results in simply $6$ differences, and this computation is done in a straightforward manner with two nested $for$ loops. If this difference is greater than a certain threshold, which we denote by $\alpha$, then a counting variable that we denote by $k$ is incremented by one (or in general by some small number $\varepsilon$). As soon as this counting variable exceeds a certain threshold $\beta$, a gait change is performed. This algorithm is better explained in the following pseudocode
<p align="center">
  <img src="https://github.com/user-attachments/assets/da999643-ab8d-4c4c-aabc-aa3579aca0c1" alt="Pseudocode" width="400"/>
</p>


### Autonomous gait transition

https://github.com/user-attachments/assets/7d42453e-b7d4-481c-a656-58a2293191f1

### Autonomous gait transition (aerial_view)

https://github.com/user-attachments/assets/d6f6b937-39b0-4d0e-b3ec-dc15ddbdd2ad



Thank you!
