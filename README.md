# CMPSC 442 Final Project

Title: MATHstermind
Group: AI & Education 2
Names: Alex Baptista, Cameron Eby, Brendan Gibbons, Evan Kunkel, Jordan Motter, Nick Wentworth
Inst: The Pennsylvania State University, School of Electrical Engineering and Computer Science
Term: Spring 2023
Crse: CMPSC442/DS442
Prof: Chris Dancy

## Description

The following describes the code used in rl_tutor.py

The code presents the user with arithmetic math problems, ranging from including 2 to 4 numbers
The numbers in the problems are integers in the range of (number_range)
The operations that may appear in the problem are addition, subtraction, multiplication, and division
In the case of division, the problem is checked to make sure there is an integer solution

For each level, the user is given a number of problems
The user is rewarded with a scored based on the number of correct answers


## How to use

To use the code, simply run the file
Instructions will be printed to the terminal
Answers to problems should be entered as integers
To quit at any point, enter the letter 'q'

Upon start, the function startMenu will be called, which will run an initial quiz to train the system to understand better where to student struggles
After which, the menu will be printed and the user will be promted to enter the level which they want to do
Each level will ask a certain amount of questions, tracking scores and informing the user when the level has been mastered and they should try the next one

## Explanation of functions 

generate_num:
Input: None
Output: An integer number in range(number_range)
Algorithm: The number is generated semi-randomly using weights. The number list and associated weights are passed to random.choices from which the number is generated.

generate_op:
Input: None
Output: An operation in a string, e.g. '+' & the function associated with it , e.g. lambda a, b: a + b
Algorithm: The operation is generated semi-randomly using weights. The operations and associated weights are passed to random.choices from which the operation is generated.

calculate_reward:
Input:
Output:
Algorithm:

update_num_weights:
Input: A correct boolean & list of numbers
Output: None, weights of numbers in list adjusted accordingly
Algorithm: For each unique number in the list, increase or decrease the weight at its index in num_weights depending on if correct is False or True respectively

update_op_weights:
Input: A correct boolean & list of operation strings
Output: None, weights of operations in list adjusted accordingly
Algorithm: For each unique operation in the list, increase or decrease the weight, which is the value associated with the key in op_weights, depending on if correct is False or True respectively

gen_prob:
Input: Number of numbers to be in the generated problem. This function recursively calls itself. Inner calls include string of problem already generated, lists of numbers and operations in the problem already generated
Output: An arithmetic problem in the form of a string, the lists of numbers and operations included in the problem
Algorithm: First call: generate a number. Further calls: generate a number and operation to go before what is already generated. Base case: return  

gen_probs:
Input: Number corresponding to how many numbers will be in the generated problems
Output:
Algorithm:

gen_probs_init:
Input: Number corresponding to how many numbers will be in the generated problems
Output:
Algorithm:

startMenu:
Input: None
Output:
Algorithm:

################################