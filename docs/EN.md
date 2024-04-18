#### Technical explanation

To implement our environments, we used the example in the [gym_examples repository](https://github.com/Farama-Foundation/gym-examples) as a boilerplate. This decision facilitated the reuse of the graphical elements of a rendered environment using Pygame, allowing us to focus primarily on implementing the logic of each environment.

The constructed environments are:

**PushBox**

- The simplest environment and the one upon which the others are based.
- Its characteristics include:
  - In its initial state, an *agent* and a box or *target* are randomly placed.
  - The agent has four possible actions: move up, down, left, and right.
  - If the agent is in a position adjacent to the target and moves in the direction of the target, then it will move the target (i.e., the agent can push the box).
  - The box remains fixed in the environment unless the agent moves it.
  - The agent's objective is to push the box to a defined region of the environment.
  - The agent's policy is binary and sparse. This means that the agent will receive 0 as a reward in each step that it does not achieve the goal, and it will receive 1 when it does.

**PushBoxRand**

- This environment has the same characteristics as `PushBoxBaseEnv` except for characteristic 4. In this case, the environment changes the box randomly every certain number of steps (defined by the size of the environment). Additionally, it adds a fifth action to characteristic 2: stay in the current position.

**PushBoxRandPol1**

- It shares the characteristics of `PushBoxRand` but modifies the rewards that the agent receives in each step. This particular environment rewards movements with 2 points and penalizes staying in the same position with -1 point. It gives 100 points for fulfilling the objective.

**PushBoxRandPol2**

- It shares the characteristics of `PushBoxRand` but modifies the rewards that the agent receives in each step. This particular environment penalizes movements with -1 point and rewards staying in the same position with 2 points. It gives 100 points for fulfilling the objective.

#### Getting started

For a complete overview of the project and how to use the environments, you can import the `.ipynb` file into Google Colaboratory. Local usage instructions can be found in the aforementioned file.

#### Additional notes

Due to the lack of a practical way to link commits from the README of a repository, the identifiers of each commit involved in the creation of each environment are provided below. This allows you to see what modifications were made from the original fork:

**PushBox (Base Environment)**

- Updates to imports, modules, and module requirements: 03437e0
- Graphic changes: 224e778, 58b5b5a, 2fee43f, 926fb90
- Modification of the reset method logic: a0220b6, 5366444
- Modification of the step method logic: 509e425, 5366444

**PushBoxRand**

- Declaration in the module and creation of the environment: 10bb95a
- Graphic changes: 7e50435
- Change in the logic of the step method and in the initializer of the environment: e998be4, 88f92d5, d647df3
