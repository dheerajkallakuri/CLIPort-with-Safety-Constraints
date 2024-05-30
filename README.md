# CLIPort with Safety Constraints

## Video Demonstration

For a visual demonstration of this project, please refer to the video linked below:

[Project Video Demonstration](https://youtube.com/shorts/_EB557-6mew?feature=share)

[![Project Video Demonstration](https://img.youtube.com/vi/_EB557-6mew/0.jpg)](https://www.youtube.com/watch?v=_EB557-6mew)

## Overview
This project aims to build an end-to-end system capable of taking a linguistic goal and executing it in a real-world scenario. The system leverages the CLEVR dataset and Transporter Networks to process images and translate them into end-effector poses. The primary objective is to handle various daily objects with different shapes, sizes, and colors without predefined object classes. Additionally, we incorporate safety constraints to ensure the robot avoids forbidden regions while performing tasks.

## Introduction
This project focuses on enhancing the CLIPort model to manipulate objects based on visual and linguistic inputs, ensuring the robot avoids forbidden regions. The task involves picking up a green block and placing it in a pink square while avoiding a blue forbidden region.

## Requirements
- Python 3.8 or higher
- TensorFlow 2.x
- PyTorch
- NumPy
- OpenCV
- CLEVR Dataset
- Transporter Networks

Download CLEVR Dataset:
   - Follow instructions from [CLEVR dataset](https://cs.stanford.edu/people/jcjohns/clevr/) to download and set up the dataset.

Configure Environment:
   - Ensure your Python environment is correctly configured with the necessary libraries.

## Model Architecture
The system uses the CLIPort model, which integrates visual and linguistic inputs to guide robot manipulation tasks. The Transporter Network identifies the best pick-up (Tpick) and place (Tplace) points based on the environment's state.

### Key Components:
- **CLIP Model**: Links linguistic goals with visual inputs.
- **Transporter Network**: Processes images to generate end-effector poses.

## Task Description
The primary task is to manipulate objects while avoiding forbidden regions:
- **Pick**: Identify and pick up a green block.
- **Place**: Place the block in a pink square region.
- **Avoid**: Ensure the trajectory does not pass through a blue forbidden region.

## Safety Constraints Implementation
The Transporter Network initially failed to account for forbidden regions. To overcome this, we implemented the Liang-Barsky clipping algorithm to calculate intersection points and generate safe trajectories that avoid forbidden areas.

### Mathematical Formulation:
- **Tpick**: Best pick-up point.
- **Tplace**: Best place point.
- **Safety Constraint**: Adjust trajectory to avoid forbidden regions using calculated intersection points and offsets.

## Evaluation
An evaluation matrix was created to track the number of trajectory points passing through the forbidden region. This metric quantifies the robot's ability to avoid the forbidden area while completing tasks.

### Evaluation Metrics:
- **Trajectory Points**: Number of points passing through the forbidden region.
- **Episodes**: Number of successful task completions.
<img width="367" alt="evaluation" src="https://github.com/dheerajkallakuri/CLIPort-with-Safety-Constraints/assets/23552796/c1ca014c-b23c-45c7-b1c8-0e21d2a398e2">


## Results
The results are visualized through a graph showing the number of episodes against the trajectory points through the obstacle region for 100 episodes. Our goal is to minimize these points, indicating successful avoidance of forbidden regions.

<img width="478" alt="compare" src="https://github.com/dheerajkallakuri/CLIPort-with-Safety-Constraints/assets/23552796/ff36f600-dea2-4443-a0b2-918ca5b54e86">


## Links
- **CLIPort GitHub Repository**: [CLIPort GitHub](https://github.com/cliport/cliport)
- **Project Report**: [Project Report](Report.pdf)
- **Presentation**: [Presentation](Presentation.pdf)
