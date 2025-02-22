# Mastermind Solver: Reasoning and Decision-Making under Uncertainty

This project implements an automated Mastermind solver that leverages formal reasoning techniques—such as SAT encoding, pseudo-Boolean constraints, MAX-SAT, and decision-theoretic expected utility ranking—studied during the "Connaissances et Raisonnement" course. In addition to solving the puzzle, the notebook provides interactive visualizations (including argumentation graphs and heatmaps) that illustrate how the candidate space is narrowed down with each guess. A new performance evaluation module computes the average number of iterations over multiple simulations to assess the solver’s efficiency.

---

## Overview

Mastermind is a classic code-breaking game where the objective is to deduce a secret code based on feedback from previous guesses. In our implementation, the solver:
- **Encodes the Mastermind rules** into a set of logical constraints using SAT/CNF models and extends them with pseudo-Boolean (PB) constraints.
- **Uses SAT and MAX-SAT solvers** (via PySAT) to iteratively eliminate inconsistent codes.
- **Applies decision theory** (expected utility and rank-dependent utility models) to select the next guess.
- **Represents the reasoning process as an argumentation framework,** visualized with NetworkX graphs.
- **Provides interactive widgets** for manual simulation and rich visualizations (e.g., heatmaps of candidate evolution).
- **Evaluates performance** by computing the average number of iterations needed over multiple simulated games.

This project demonstrates the application of formal reasoning and decision-making techniques from the course in an original context, merging algorithmic problem solving with advanced visualization and performance assessment.

---

## Project Structure

- **`Mastermind_Solver.ipynb`**  
  The main Jupyter Notebook containing all the code, explanations, interactive visualizations, and performance evaluation.
  
- **README.md**  
  This file, which explains the project objectives, design, and instructions for running the solver.

---

## Detailed Work Plan

### 1. Project Setup and Literature Review
- **Review Course Techniques:**  
  Revisit key concepts from the course such as SAT encoding, pseudo-Boolean constraints, MAX-SAT, decision-making under uncertainty, and computational argumentation.
- **Research Related Approaches:**  
  Explore similar puzzle-solving techniques (e.g., for Sudoku or Rubik’s Cube) to inform our design.
- **Define Objectives:**  
  Establish clear goals for the notebook: input parameters, output displays, interactive simulations, and performance evaluation.

### 2. Formalization of the Mastermind Problem
- **Game Rules Recap:**  
  Outline the rules of Mastermind, including the set of possible colors, the structure of the secret code, and the feedback mechanism.
- **Logical and PB Encoding:**  
  Define variables and constraints to model the game:
  - Boolean variables for each peg’s color (SAT encoding).
  - Additional pseudo-Boolean constraints to capture feedback (exact number of black and white pegs).
- **Mapping to Course Concepts:**  
  Relate the formalization to examples studied in the course (e.g., the licorne and graph coloring exercises).

### 3. Solver Implementation
- **Choosing a Solver Library:**  
  Utilize Python-based SAT and MAX-SAT solvers (e.g., PySAT) to enforce constraints and prune candidates.
- **Encoding Constraints in Code:**  
  Develop functions to encode a guess, its corresponding feedback, and update the candidate space accordingly.
- **Iterative Guessing Loop:**  
  Implement an iterative loop where:
  - A candidate guess is generated using an expected-utility heuristic.
  - The solver refines the candidate space by discarding codes inconsistent with previous feedback.
- **Heuristics and MAX-SAT:**  
  Use a MAX-SAT approach to select guesses that satisfy the maximum number of soft constraints, thus optimizing the guessing process.

### 4. Visualization and Interactive Components
- **Interactive Widgets:**  
  Use `ipywidgets` to create interactive elements that let users simulate games by manually entering feedback.
- **Graphical Representations:**  
  Visualize the evolution of the candidate space with:
  - A line plot (or heatmap) showing the number of remaining candidates over iterations.
  - An argumentation graph using NetworkX that explains conflicts among successive guesses.
- **Enhanced Visualizations:**  
  Additional plots such as histograms of iteration counts over multiple simulations.

### 5. Performance Evaluation
- **Average Iteration Analysis:**  
  A new module in the notebook (Cell 13) runs multiple simulations (e.g., 100 games) to compute statistics such as the average number of iterations and standard deviation. This provides insight into the efficiency and robustness of the solver.

### 6. Documentation, Testing, and Final Touches
- **Memo and Usage Instructions:**  
  Provide a detailed memo that explains the problem formalization, methodology, and how to run the notebook.
- **Testing:**  
  Validate the solver with multiple game scenarios and review performance evaluation results.
- **Code Clean-Up:**  
  Ensure that the code is well-commented and organized for clarity and reproducibility.

---

## Libraries and Frameworks

- **Solver Libraries:**  
  - [PySAT](https://pysathq.github.io/) (for SAT, MAX-SAT, and pseudo-Boolean solving)
  - [Z3](https://github.com/Z3Prover/z3) (optional alternative)
  
- **Visualization Tools:**  
  - [Matplotlib](https://matplotlib.org/) for plotting graphs and histograms.
  - [NetworkX](https://networkx.org/) for building argumentation graphs.
  - [ipywidgets](https://ipywidgets.readthedocs.io/) for interactive notebook components.
  
- **Optional Tools:**  
  - [Plotly](https://plotly.com/) for enhanced interactive visualizations.

---

## How to Run the Project

1. **Environment Setup:**
   - Ensure Python 3 is installed.
   - Install required libraries using `pip`:
     ```bash
     pip install pysat z3-solver matplotlib plotly ipywidgets networkx
     ```
   - Optionally, install additional libraries as needed.

2. **Launch the Notebook:**
   - Open the Jupyter Notebook (`Mastermind_Solver.ipynb`) in your preferred environment.
   - Follow the sequential code cells to initialize the solver, run interactive simulations, and visualize results.

3. **Interactive Use:**
   - Use the provided widgets to simulate a Mastermind game by manually entering feedback.
   - Observe real-time visualizations of the candidate space and argumentation graph.

4. **Performance Evaluation:**
   - A dedicated cell runs multiple simulations (e.g., 100 games) and displays the average number of iterations and a histogram of iteration counts. This provides quantitative performance metrics for the solver.

5. **Review Documentation:**
   - Refer back to this README and the inline comments within the notebook for further explanations and project insights.

---

## Expected Outcomes

- **Automated Mastermind Solver:**  
  A working solver that identifies the secret code through iterative reasoning using SAT, PB, and MAX-SAT techniques.
  
- **Interactive Visualizations:**  
  Real-time displays that show the evolution of the candidate pool, an argumentation graph of guesses, and performance histograms.
  
- **Comprehensive Performance Metrics:**  
  Quantitative analysis (average iterations, standard deviation) from multiple simulations to assess solver efficiency.
  
- **Detailed Documentation:**  
  Clear explanations of the problem formalization, methodology, and instructions for running the project.

---

## Concluding Remarks

This project effectively combines theoretical foundations of reasoning under uncertainty with practical problem solving. By applying formal reasoning techniques from the course to an engaging game like Mastermind, it demonstrates technical proficiency, creativity, and an in-depth performance evaluation. The integration of SAT, pseudo-Boolean constraints, MAX-SAT, decision theory, and argumentation frameworks makes this project a comprehensive and advanced application of the course concepts.
