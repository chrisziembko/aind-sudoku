# Artificial Intelligence Nanodegree
## Introductory Project: Diagonal Sudoku Solver

# Question 1 (Naked Twins)
Q: How do we use constraint propagation to solve the naked twins problem?  
A: The naked twins strategy enforces that, for each unit, the values in the naked twin boxes cannot appear in any other boxes in the unit.  So we implement this by looping through the constraints (i.e. units), looking for naked twins, and if found, removing their values from peers in the unit.

In the code, the naked twins strategy is implemented along with "eliminate" and "only choice" as methods in the puzzle reduction (i.e. the sweepp through the puzzle reducing the possibility of values).  It should be implemented as its own function for encapsulation.  The naked twins must be identified by unit, which I did by seeing if there are two-digit values in the unit that appear twice.  If a naked twin value is found, these values are removed from other boxes in the unit.

NOTE:  I changed my answer to confrom with how udacity is interpreting constraint propagation as applied to sudoku.  I'm not wild about this interpretation however.  You guys refer to the constraints as e.g. the fact that the values 1-9 must be in a row uniquely.  I view this by simply part of the problem domain. Even though this technically is "constraining" the values, it is simply defining the problem/puzzle.  I view the strategies e.g. the "only_choice" and "naked_twins" as the constraints since these are the insights that cause the values in the boxes to be constrained, and these strategies are quite literally the constraints that we are propagating.  It doesn't really make sense to say that the unit constraints (i.e. fact that 1-9 appear in a row uniquely) propagated because the strategies are applied on different domains.  For instance "eliminate" is applied on all peers whereas "naked_twins" is applied on individual units.

# Question 2 (Diagonal Sudoku)
Q: How do we use constraint propagation to solve the diagonal sudoku problem?  
A: Since general constraint propagation as applied to sudoku has been discussed extensively in the module, I'm assuming the question means what adjustments are required by the inclusion of diagonal units.  The fact that the digits 1-9 must appear in the diagonal units only once simply gives us more constraints to enforce.  Another way to say this is that it increases the 'constraint domain' on which we apply constraint propagation.  That is, the diagonal units must be included with the row units, column units, and square units when implementing puzzle reduction strategies.  So the only change required in the code is to include the diagonal units in the unitlist, i.e. the units on which to apply constraint propagation.

### Install

This project requires **Python 3**.

We recommend students install [Anaconda](https://www.continuum.io/downloads), a pre-packaged Python distribution that contains all of the necessary libraries and software for this project. 
Please try using the environment we provided in the Anaconda lesson of the Nanodegree.

##### Optional: Pygame

Optionally, you can also install pygame if you want to see your visualization. If you've followed our instructions for setting up our conda environment, you should be all set.

If not, please see how to download pygame [here](http://www.pygame.org/download.shtml).

### Code

* `solution.py` - Fill in the required functions in this file to complete the project.
* `test_solution.py` - You can test your solution by running `python -m unittest`.
* `PySudoku.py` - This is code for visualizing your solution.
* `visualize.py` - This is code for visualizing your solution.

### Visualizing

To visualize your solution, please only assign values to the values_dict using the `assign_value` function provided in solution.py

### Submission
Before submitting your solution to a reviewer, you are required to submit your project to Udacity's Project Assistant, which will provide some initial feedback.  

The setup is simple.  If you have not installed the client tool already, then you may do so with the command `pip install udacity-pa`.  

To submit your code to the project assistant, run `udacity submit` from within the top-level directory of this project.  You will be prompted for a username and password.  If you login using google or facebook, visit [this link](https://project-assistant.udacity.com/auth_tokens/jwt_login) for alternate login instructions.

This process will create a zipfile in your top-level directory named sudoku-<id>.zip.  This is the file that you should submit to the Udacity reviews system.

