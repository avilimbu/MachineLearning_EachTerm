# Reinforcement Learning

**Reinforcement Learning (RL)** is a branch of machine learning where an autonomous **agent** learns to make decisions by interacting with an **environment** and receiving feedback in the form of **rewards or penalties**.

The main goal of reinforcement learning is to learn a strategy that **maximizes the cumulative reward over time**.

Unlike:

* **Supervised Learning**, which learns from labeled examples.
* **Unsupervised Learning**, which discovers patterns in unlabeled data.

Reinforcement Learning learns primarily through **trial and error** and does not require explicit step-by-step instructions for every decision.

---

# Core Idea of Reinforcement Learning

In reinforcement learning, an **agent** continuously interacts with an **environment**.

The basic interaction can be represented as:

```text id="rlflow1"
              Environment
                  │
                  │ State
                  ↓
                Agent
                  │
                  │ Action
                  ↓
              Environment
                  │
                  │ Reward
                  ↓
                Agent
```

The agent repeatedly performs the following steps:

1. Observes the current **state** of the environment.
2. Chooses an **action** according to its current strategy.
3. Receives a **reward or penalty**.
4. Moves to a new state.
5. Updates its strategy based on the received feedback.
6. Repeats the process.

Over many interactions, the agent learns which actions and sequences of actions produce better long-term outcomes.

---

# Example: Teaching a Robot

Imagine a robot learning how to reach a target location.

At the beginning, the robot does not know which path is best.

```text id="robot1"
Robot
  ↓
Try Action
  ↓
Move Forward
  ↓
Receive Reward
  ↓
Update Strategy
  ↓
Try Again
```

For example:

```text id="robot2"
Reaches Target        → +10 Reward
Moves Toward Target   → +2 Reward
Moves Away            → -2 Penalty
Hits Obstacle         → -10 Penalty
```

After many attempts, the robot learns which actions are more likely to lead to the target.

---

# Exploration vs Exploitation

One of the most important concepts in reinforcement learning is the balance between **exploration** and **exploitation**.

## Exploration

**Exploration** means trying new or unfamiliar actions to discover whether they can produce better results.

Example:

```text
Action A → Known reward: 5
Action B → Unknown

Agent tries Action B
```

The agent may discover that Action B actually produces a reward of `10`.

---

## Exploitation

**Exploitation** means choosing an action that the agent already knows tends to produce a good reward.

For example:

```text
Action A → Reward: 5
Action B → Reward: 10
Action C → Reward: 2

Agent chooses Action B
```

The agent uses its existing knowledge to maximize reward.

---

## Balancing Exploration and Exploitation

A successful RL agent needs to balance both:

```text
             Reinforcement Learning
                     │
            ┌────────┴────────┐
            │                 │
       Exploration       Exploitation
            │                 │
       Try new actions   Use known
                         good actions
```

Too much exploration may waste time trying poor actions.

Too much exploitation may prevent the agent from discovering better strategies.

---

# Key Components of Reinforcement Learning

A typical reinforcement learning system consists of several important components.

## 1. Agent

The **agent** is the learner or decision-maker.

It observes the environment, selects actions, receives rewards, and improves its strategy.

Examples:

* Robot
* Game-playing AI
* Autonomous vehicle
* Trading system
* Recommendation system

---

## 2. Environment

The **environment** is everything the agent interacts with.

Examples:

```text
Game-playing AI → Game world
Robot           → Physical surroundings
Self-driving AI → Road and traffic
```

The environment responds to the agent's actions by providing new states and rewards.

---

## 3. State

A **state** represents the current situation of the environment.

For example, in a chess game, the state may contain:

* Position of all pieces
* Whose turn it is
* Current board configuration

In a robot navigation system, the state may include:

* Robot position
* Target position
* Nearby obstacles
* Direction of movement

---

## 4. Action

An **action** is something the agent can do in a particular state.

For example, in a game:

```text
Move Up
Move Down
Move Left
Move Right
```

For a robot:

```text
Move Forward
Move Backward
Turn Left
Turn Right
```

The set of all possible actions is called the **action space**.

---

## 5. Reward

A **reward** is numerical feedback provided by the environment after an action.

It tells the agent how good or bad the result was.

For example:

```text
Successful Action → +10
Normal Action     → +1
Bad Action        → -5
Failure           → -10
```

The agent's objective is to maximize the total reward it receives over time.

---

## 6. Policy

A **policy** defines how the agent chooses an action based on the current state.

It can be thought of as the agent's **strategy**.

Conceptually:

```text
State
  ↓
Policy
  ↓
Action
```

For example:

```text
State: Enemy nearby
        ↓
     Policy
        ↓
Action: Move Away
```

A good policy selects actions that are expected to produce high long-term rewards.

---

# Markov Decision Process (MDP)

Many reinforcement learning problems can be modeled using a **Markov Decision Process (MDP)**.

An MDP provides a mathematical framework for representing decision-making problems where outcomes depend on the current state and chosen action.

A typical MDP contains:

```text
State
  ↓
Action
  ↓
Reward
  ↓
Next State
  ↓
Action
  ↓
Reward
  ↓
...
```

The main components are:

* **States**
* **Actions**
* **Rewards**
* **Transition dynamics**
* **Policy**

The agent attempts to find a policy that maximizes the **expected cumulative reward**.

---

# Cumulative Reward

The agent does not necessarily optimize only the immediate reward.

Instead, it generally considers the **long-term reward** obtained over a sequence of actions.

For example:

```text
Action 1 → +1
Action 2 → +1
Action 3 → +10
```

Even if Action 3 provides the largest reward, the earlier actions may be necessary to reach it.

The agent therefore learns to consider the consequences of its actions over time.

---

# Discount Factor

In many reinforcement learning algorithms, future rewards are discounted using a **discount factor**, commonly represented by `γ` (gamma).

The discount factor satisfies:

```text
0 ≤ γ ≤ 1
```

A higher value of `γ` means the agent places more importance on future rewards.

A lower value means the agent focuses more heavily on immediate rewards.

The discounted return can be represented as:

```text
Gₜ = Rₜ₊₁ + γRₜ₊₂ + γ²Rₜ₊₃ + ...
```

Where:

* `Gₜ` = return at time `t`
* `R` = reward
* `γ` = discount factor

---

# How Reinforcement Learning Works

The general learning process can be summarized as:

```text
              Start
                ↓
        Observe Current State
                ↓
          Choose Action
                ↓
       Interact with Environment
                ↓
        Receive Reward
                ↓
          New State
                ↓
       Update Policy / Knowledge
                ↓
        Repeat the Process
                ↓
       Better Decision Making
```

Through repeated interaction, the agent gradually improves its decision-making strategy.

---

# Common Reinforcement Learning Algorithms

There are several important reinforcement learning algorithms.

## Q-Learning

**Q-Learning** is a value-based reinforcement learning algorithm.

It learns a **Q-value**, which represents the expected future reward for taking a particular action in a particular state.

Conceptually:

```text
Q(State, Action)
       ↓
Expected Future Reward
```

The agent can use Q-values to choose actions that are expected to produce higher rewards.

---

## Deep Q-Network (DQN)

**Deep Q-Network (DQN)** combines Q-learning with a neural network.

Instead of storing Q-values in a traditional table, a neural network is used to estimate them.

```text
State
  ↓
Neural Network
  ↓
Q-Values
  ↓
Choose Action
```

DQN became well known for its ability to learn strategies for complex game environments.

---

## Policy Gradient

Policy gradient methods directly optimize the **policy** rather than learning only action values.

The model learns which actions should become more or less likely in different states.

```text
State
  ↓
Policy Network
  ↓
Action Probabilities
  ↓
Select Action
```

---

## Actor-Critic

**Actor-Critic** methods combine two ideas:

* **Actor** — Learns which actions to take.
* **Critic** — Evaluates how good the current state or action is.

```text
              State
                ↓
        ┌───────┴───────┐
        ↓               ↓
      Actor           Critic
        ↓               ↓
     Action         Evaluation
        └───────┬───────┘
                ↓
             Update
```

---

# Applications of Reinforcement Learning

Reinforcement learning is particularly useful for problems involving **sequential decisions**, where the outcome depends on a series of actions.

## 1. Game Playing

RL can be used to train agents to play:

* Chess
* Go
* Video games
* Strategy games

The agent learns strategies by interacting with the game environment.

---

## 2. Robotics

RL can help robots learn tasks such as:

* Walking
* Grasping objects
* Navigation
* Manipulation
* Movement control

---

## 3. Autonomous Vehicles

RL can be used for decision-making tasks such as:

* Navigation
* Path planning
* Lane selection
* Traffic decision-making

---

## 4. Resource Management

RL can optimize the use of resources in systems such as:

* Data centers
* Energy systems
* Inventory management
* Network management

For example, an RL agent could learn how to optimize data-center cooling while maintaining safe operating conditions.

---

## 5. Recommendation Systems

RL can be used to improve recommendations by learning from user interactions.

For example:

```text
User Interaction
      ↓
Recommendation
      ↓
User Response
      ↓
Reward / Feedback
      ↓
Update Recommendation Strategy
```

---

## 6. Ad Bidding

RL can be used to make sequential decisions about:

* Advertising bids
* Budget allocation
* Campaign optimization

The agent learns strategies based on the rewards generated by its decisions.

---

# Reinforcement Learning vs Other Machine Learning Types

| Aspect              | Supervised Learning    | Unsupervised Learning     | Reinforcement Learning     |
| ------------------- | ---------------------- | ------------------------- | -------------------------- |
| **Data / Feedback** | Labeled data           | Unlabeled data            | Rewards and penalties      |
| **Main Goal**       | Predict target values  | Discover patterns         | Maximize cumulative reward |
| **Learning Method** | Learn from examples    | Discover hidden structure | Trial and error            |
| **Decision Making** | Usually not sequential | Usually not sequential    | Sequential                 |
| **Human Labels**    | Required               | Not required              | Not necessarily required   |
| **Example**         | Predict house price    | Group customers           | Train a robot to navigate  |

---

# Simple Example

Consider a game where an agent must reach a goal.

```text
Start
  ↓
Move Right → +1
  ↓
Move Right → +1
  ↓
Move Up → -1
  ↓
Move Right → +1
  ↓
Reach Goal → +10
```

The agent remembers the outcomes of its actions and gradually learns which sequence of actions is more effective.

After sufficient training:

```text
Start
  ↓
Best Action
  ↓
Best Action
  ↓
Best Action
  ↓
Goal
  ↓
High Cumulative Reward
```

---

# Key Difference

The easiest way to remember the three major learning approaches is:

> **Supervised Learning:** Learn from labeled examples.

> **Unsupervised Learning:** Discover patterns from unlabeled data.

> **Reinforcement Learning:** Learn through interaction, trial and error, and rewards.

```text
                    Machine Learning
                           │
          ┌────────────────┼────────────────┐
          │                │                │
     Supervised       Unsupervised    Reinforcement
          │                │                │
     Labeled Data     Unlabeled Data    Environment
          │                │                │
          ↓                ↓                ↓
     Prediction        Pattern         Trial & Error
                      Discovery            │
                                           ↓
                                       Reward
                                           │
                                           ↓
                                    Better Decisions
```

---

# Summary

**Reinforcement Learning (RL)** is a machine learning approach in which an **agent learns to make decisions by interacting with an environment**.

The agent:

1. Observes a **state**.
2. Selects an **action**.
3. Receives a **reward or penalty**.
4. Moves to a new state.
5. Updates its knowledge or policy.
6. Repeats the process.

The ultimate goal is to learn a policy that **maximizes cumulative reward over time**.

### Key Concepts

* **Agent** → The learner or decision-maker.
* **Environment** → The world in which the agent operates.
* **State** → Current situation.
* **Action** → Decision made by the agent.
* **Reward** → Feedback from the environment.
* **Policy** → Strategy used to select actions.
* **Exploration** → Trying new actions.
* **Exploitation** → Using known successful actions.
* **MDP** → Mathematical framework for sequential decision-making.

In short:

> **Reinforcement Learning is learning what to do by trying actions, observing their consequences, and using rewards to improve future decisions.**
