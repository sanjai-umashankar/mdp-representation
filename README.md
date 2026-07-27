# MDP REPRESENTATION

## AIM:
To model the wall painting task as a Markov Decision Process (MDP) and analyze the states, actions, and rewards involved in completing the task efficiently.

## PROBLEM STATEMENT:

### Problem Description
An agent (painter) is assigned to paint a wall. The goal is to complete the painting task efficiently while minimizing time and effort. The agent decides actions such as painting, moving, or resting based on the current state of the wall.

### State Space
The state space represents all possible conditions of the wall:

S0 Not Painted\
S1 Partially Painted\
S3 Fully Painted

### Sample State
"Wall is partially painted"

### Action Space
The possible actions available to the agent:

Start Painting\
Continue Painting\
Move to Next Section\
Stop Painting

### Sample Action
"Continue Painting"

### Reward Function
The reward function guides the agent:

+10 → Successfully paints a section\
-2 → Time delay or inefficiency\
+50 → Fully painted wall (goal state)

### Graphical Representation

<img width="913" height="623" alt="image" src="https://github.com/user-attachments/assets/ece775b4-1b15-4324-aa9f-1d29affee401" />


## PYTHON REPRESENTATION:
```
P = {
    0: {  # Not Painted
        0: [(1.0, 1, 10)],  # Start → Partially Painted
        1: [(1.0, 0, -2)],  # Continue → No effect
        2: [(1.0, 0, 0)]    # Stop
    },
    1: {  # Partially Painted
        0: [(1.0, 1, -2)],  # Start again (waste)
        1: [(1.0, 2, 50)],  # Continue → Fully Painted
        2: [(1.0, 0, -5)]   # Stop → Back to start
    },
    2: {  # Fully Painted (Terminal)
        0: [(1.0, 2, 0)],
        1: [(1.0, 2, 0)],
        2: [(1.0, 2, 0)]
    }
}
```
## OUTPUT:
<img width="1202" height="43" alt="image" src="https://github.com/user-attachments/assets/c79b2b24-fab3-4bc0-801a-8c9ddc2ee17b" />
<img width="568" height="34" alt="image" src="https://github.com/user-attachments/assets/3f6223bd-1edc-44a4-a16a-c4c95a4b117f" />

## RESULT:
The MDP model successfully represents the wall painting process. The agent learns that continuing to paint leads to the highest reward, while stopping early results in lower rewards. The optimal strategy is to start painting and continue until the wall is fully painted.

