# CMPSC 442 Final Project

Title: MATHstermind  
Group: AI & Education 1  
Names: Alex Baptista, Cameron Eby, Brendan Gibbons, Evan Kunkel, Jordan Motter, Nick Wentworth  
Inst: The Pennsylvania State University, School of Electrical Engineering and Computer Science  
Term: Spring 2023  
Crse: CMPSC442/DS442  
Prof: Chris Dancy  

## Description

The following describes the code used in rl_tutor.py  

Has there ever been a moment where you have been math homework and just had no idea what to do? Do you feel like you are never prepared to do any quiz or homework? Does mathematics give anxiety? Well, we think we have the solution for you. If you ask young students what their favorite course is, they most likely won't tell you mathematics. This can be due to a variety of reasons but what if there was an easy-to-access tool that will offer the student a way to learn and improve their math skills but also make it fun. Our solution is MATHstermind.

If there is anything that any young student enjoys doing, it is playing video games. In a lot of video games, you want to be able to achieve the highest score. Well in MATHstermind, our application is set up such that each user is able to select levels and try to get the highest score for each one of those levels. Now, not every level is easy as the levels become more and more difficult. While the user uses the program more often, the questions will be skewed to focus on the user's strengths and weaknesses. This way the user isn't always given questions they can get right away. We hope that this tool engages your student(s) to make them enjoy and improve on their weaknesses in mathematics.

The code presents the user with arithmetic math problems, ranging from including 2 to 4 numbers. The numbers in the problems are integers between 1 and 12 (inclusive). The operations that may appear in the problem are addition, subtraction, multiplication, and division. In the case of division, the problem is checked to make sure there is an integer solution. The user enters their integer solution (which may be negative) and is told if they are correct or incorrect. 

For each level, the user is given a number of problems. The user is rewarded with a scored based on the number of correct answers.

## GEA:

### Goals:

The goal of the system is to help the user improve their math skills, specifically in arithmetic, and become confident in their abilities. This includes providing a range of problems at different difficulty levels, tracking the user's progress over time, and offering feedback about how they are performing.

### Environment:

The environment of our system is the terminal, where messages are printed and the user can enter answers to problems. Ideally, The environment would include all levels of mathematics, different types of problems (multiple choice, work, etc.), and be integrated into a classroom environment. 

### Adaptation:

The adaptation involves adjusting the difficulty level and types of problems based on the user's performance and progress. For example, if the user is proficient in addition and subtraction, but struggles with multiplication and division, the program will generate more multiplication and division problems. Similarly, if the user is proficient at problems with one operation, the program will suggest trying problems with two. Overall, the system aims to provide a personal learning experience tailored to the user.

## Details of Artificial Intelligence (AI) System:

 ### Methods:
   In our application, we wanted to use an AI model that would focus on making an application that felt personalized to the user. We wanted to avoid the potential threat of an AI model comparing performances of one student to another as that is ethically not correct. For such goals to be achieved, we settled with trying to make a math tutor using the concepts from reinforced learning. To construct a reinforced learning model, you need to be able to define a few different elements: environment, state(s), reward(s), policy, and value. Let's take a look at the progress I took when constructing this model. To begin, the motivation and influence came from reading different examples of how video games were connected with using reinforced learning.
#### Enviroment: 
   The environment of our application is the virtual math tutor itself. When I say that, the math tutor currently has three different "maps" or environments that the user can use. In each environment, the agent is asked ten different questions that are generated based upon the weights of the numbers and operations. For each question you get correct, the agent receives a reward and the weights for the respective numbers and operation(s) for that question will decrease. However, if the agent gets the question wrong, it does not receive a good reward and the weights for the respective numbers and operation(s) will increase. The higher the weights, the more likely they will appear in an equation.
#### State: 
   The states of our environment would be the ten different questions that the agent will need to answer in each level (environment) to earn a reward. Each state is randomly generated based upon the weights of the numbers and operations. The higher the weight, the more likely that specific number and operation will appear.
#### Reward: 
   The reward for each question will depend on if the user is able to get the answer correct or not. If the agent or user gets one answer correct, they earn one point as a reward. If they get the answer wrong, they only receive 0.5 points in credit. In the end, the agent's score is kept tracked so the user is able to keep track of their highest score. For the agent to get the highest score or reward, the agent must get each question correct.
   
#### Policy: 
   The policy is an iterative one. Once the agent enters an environment, the action that the agent must take is one that is an iterative one. The agent will go to state or question and then answer that question or do an action that will then move the agent to the next question or state. This will be done iteratively until there are no more states to step to.
 
 ### Dataset:
   The current dataset is a list of numbers from a range of 0 to 11 and a list of operators which include addition, subtraction, multiplication, and division. The reason for this dataset at this current moment is due to our specific goal at this current stage in the development. We wanted to focus more on basic arithmetic with smaller numbers to allow students who are beginning to learn mathematics to use this tool. In the near future, there will be additional branches of math added such as algebra and geometry.
   
### Diagram:
 ![alt text](https://github.com/EvanKunkel/CMPSC442FinalProject/blob/main/Diagram_442.png)


## How to use:

To be able to use this code, you need to first download the make sure that you can use the code. First download the code and find the respective directory where you will be able to find `rl_tutor.py`. Once there, you should `pip install random` as this is an imported library in the Python file.  Now, you will be ready to run the code! To use the code, simply run the file. Instructions will be printed to the terminal. Answers to problems should be entered as integers. To quit at any point, enter the letter 'q'.

## Initialization of Code:
To understand how the code can start, we have a `startMenu()` function that will automatically start the application as soon as the Python file runs. Upon `startMenu()`, the function startMenu will be called, which will run an initial quiz to train the system to understand better where to student struggles. After these initial fifthteen questions, the starting menu will appear in the terminal and the user will be prompted to enter the level which they would like to test their knowledge on. Each level will ask a certain amount of questions, for example, Level 1 will consist of doing basic arithmetic with two numbers and Level 2 will consist of doing basic arithmetic with three numbers. Each level will ask a certain amount of questions, tracking scores and informing the user when the level has been mastered and they should try the next one. In addition, the application will be rewarding the user with getting an answer correct and keeping track of their highest scores.

## Explanation of functions: 

* `generate_num()`:  
    * **Input**: None  
    * **Output**: An integer number in range(number_range)  
    * **Algorithm**: The number is generated semi-randomly using weights. The number list and associated weights are passed to random.choices from which the number is generated.  

* `generate_op()`:  
    * **Input**: None  
    * **Output**: An operation in a string, e.g. '+' & the function associated with it , e.g. lambda a, b: a + b  
    * **Algorithm**: The operation is generated semi-randomly using weights. The operations and associated weights are passed to random.choices from which the operation is generated.  

* `calculate_reward(reslt)`:
  * **Input**: A boolean value. The value or variable `result` placed in here should be the result of checking to see if the user's input matches the answer from the question
  * **Output**: Returns an integer or the reward.
  * **Algorithm**: The function will check to see if the `result` parameter is `True` or `False`. Based upon the boolean value, if `result` is True, then the user will be rewarded with 1 point. If False, the user will be rewarded with 0.5 points.  

* `update_num_weights(correct, nums)`:  
    * **Input**: A correct boolean & list of numbers  
    * **Output**: None, weights of numbers in list adjusted accordingly  
    * **Algorithm**: For each unique number in the list, increase or decrease the weight at its index in num_weights depending on if correct is False or True respectively  

* `update_op_weights(correct, ops)`:  
    * **Input**: A correct boolean & list of operation strings  
    * **Output**: None, weights of operations in list adjusted accordingly  
    * **Algorithm**: For each unique operation in the list, increase or decrease the weight, which is the value associated with the key in op_weights, depending on if correct is False or True respectively  

* `gen_prob(c, RHS=None, num_list=None, op_list=None)`:  
    * **Input**: Number of numbers to be in the generated problem. This function recursively calls itself. Inner calls include string of problem already generated, lists of numbers and operations in the problem already generated  
    * **Output**: An arithmetic problem in the form of a string, the lists of numbers and operations included in the problem  
    * **Algorithm**: First call: generate a number. Further calls: generate a number and operation to go before what is already generated. Base case: return    


* `gen_probs(expr_num)`:
  * **Input**: Number corresponding to how many numbers will be in the generated problems
  * **Output**: Prints the questions that are required for the specific level and after reaching the last state or question, the user will be prompted with their scores.
  * **Algorithm**: This function consists of a hard coded number of questions that the user will be prompted to answer. The questions are dependent on the integer in `expre_num`. The number given in `expr_num` will notify the application which level the user has selected. From this point, the user will be allowed to answer the questions. After each question is answered, the function will check to see if the user is correct or not. Once we know the result, the application will run the functions `update_num_weights()`, `update_op_weights()`, and `calculate_reward()` which will again update each weight and the reward. This will halt once the user has answered the last question or state. It is here when the application will check to see if the user beat their previous scores or not. Continuing on, the function will print feedback on how well the user did on each level. For example, `"Level Complete! You scored: 7. You got a new high score!! Previous high score: 4.5"`. Once this is printed, the user will then see the highest scores of each level and then be prompted back to the starting menu or `startMenu()`.

* `gen_probs_init(expr_num)`:
  * **Input**: Number corresponding to how many numbers will be in the generated problems
  * **Output**: The initial quiz. Meaning, five questions per level which at the current stage of development is 15 questions.
  * **Algorithm**: Like `gen_probs()`, this will also generate a function. This has the same functionality except for being in a loop and stating the scores of the user. Without the loop and unnecessary prints, it allows the application to generate just EXACTLY one problem. This function's primary use is to generate problems for the initial quiz. This quiz will give five questions for each level to train the weights of the number and operators.

* `startMenu()`:
  * **Input**: None
  * **Output**: Prints the User-Interface (UI) of the program for the user to answer questions, select levels, and to leave the application.
  * **Algorithm**: This function will start by running a loop that iterates through the numbers 0 to 15 and uses modulus division to determine what level to test the user on for the initial quiz. This initial quiz is made to train the weights of the numbers and operations to allow the model to get a better understanding of the user's strengths and weaknesses. After the initial quiz, the user will be prompted with this message `Welcome to Mathstermind! Our virtual assistant is here to help you improve your math skills!
There are three levels to choose from Beginner to Advance. Pick the level that suits you. Type 'q' to leave a level or the application`. It after this message where the three level are displayed as such:
`
print("Level 1: Beginner (Two Numbers) -----> Type 1")
print("Level 2: Moderate (Three Numbers) -----> Type 2")
print("Level 3: Advanced (Four Numbers) -----> Type 3")
`
Depending on the user's response, the user will be taken to the function `gen_probs()` to enter the level they decided on or to leave the application. If they leave the application, they will be prompted with a goodbye message.

## Issues
