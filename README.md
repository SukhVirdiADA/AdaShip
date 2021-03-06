# AdaShip
by Sukh Virdi
 
Locate to my AdaShip src code on the Repl.it compiler using this [link](https://replit.com/join/rkvhunvh-sukhvirdi7) 

## Table of Contents
- [Challenge Outline](#1-challenge-outline)
  - [1a. Summary and review of the problem, overall proposed solution.](#-11-summary)
  - [1b. UML style diagram illustrating initial overall solution (linked to 1a)](#-12-uml-style-diagram)
  - [1c. Initial working plan, overall approach, development strategy and approach to quality (linked to 1a, 1b).](#-13-initial-working-plan)
  - [1d. Analysis and decomposition of the overall problem into key ‘epic’ style tasks (linked to 1b, 1c).](#-14-analysis-decomposition)
  - [1e. Initial object-oriented design ideas and plan of phased breakdown into smaller tasks (linked to 1d).](#-14-design-ideas)
- [Evaluation](#2-evaluation)
  -   [2a. Reflective review, opportunities to improve and continued professional development.](#-15-reflective-review)
 
## 1. Challenge Outline
 
### 1a. Summary and review of the problem, overall proposed solution.
 
AdaShip is a command-line game, which is essentially a clone of the traditional board game "battleship". Players take turns trying to destroy each other's battleships placed along a grid. This means that the boards created will have to hold data relating to placed boats, fired shots and missed shots. The player (you) also needs to be able to fire torpedo shots, and receive information on the result of the shot (hit/miss). Once all of the AI/Computer ships are destroyed then the player wins the game or if the Computer destroys all of your ships they would win. The AI/Computer board is autocreated and their torpedo shots are fired at a random location on your playerboard. Hits/Misses for both your targetboard and the playerboard is displayed to the end-user to keep a log of the game progress. The game needs to prevent invalid input but also permit auto placing & manual placements when setting up the game.

---

####  My Overall Proposed Solution

After analysing the assignment document I chose to focus on the PASS requirements in order to achieve a passable solution. I ended up implementing the following requirements and it represents a fully functional AdaShip Game, the screenshots below provides evidence corresponding to the requirement it matches in that sub-section: 

---

##### Set-Up Interface

A usable, intuitive and highly efficient Set-Up interface in which a player can with minimal effort:
Select from a game menu to a start a:
One player v computer game
Quit

![menu](https://user-images.githubusercontent.com/56550489/112157955-9e9d2a00-8bdf-11eb-9aa3-0cba1414a50f.png)

---

##### Placed/Non-Placed Ships and Seeing the Shipboard

Select and place any of their non-placed or placed ships at any valid position on their shipboard.
Clearly indicate the current non-placed and placed ships.
See their current shipboard.

![second](https://user-images.githubusercontent.com/56550489/112158512-2420da00-8be0-11eb-89af-caee6a5d0cf7.png)

---

##### Robustness - Illegal Placements and Invalid Behaviours

Be robust enough to prevent any invalid behaviours, prevent or correct any illegal placements and avoid system issues or errors related to user input.

![3](https://user-images.githubusercontent.com/56550489/112158825-73ffa100-8be0-11eb-960e-29450f5669bd.png)

---

##### Auto-place mechanism

Auto-place all ships.

![4](https://user-images.githubusercontent.com/56550489/112161359-fbe6aa80-8be2-11eb-8af1-f76f60c9b45a.png)

---

##### Quit and Reset Option

Support a ‘quit’ game and ‘reset’ shipboard option.

![18](https://user-images.githubusercontent.com/56550489/112289742-79172b80-8c86-11eb-9832-08b1a5192e41.png)

---

##### Continue Option 

Support a ‘continue’ option if all ships have been placed and the user has confirmed they are happy with the current placements.

![16](https://user-images.githubusercontent.com/56550489/112289011-cfd03580-8c85-11eb-98a2-9f91722faa58.png)

---

##### Computer Auto-Complete Set-Up

A computer-based opponent than can automatically complete a valid setup process using a random strategy (i.e., place all their ships at valid but constantly differing positions on their own shipboard); essentially this should utilise the auto-place feature outlined above.

![17](https://user-images.githubusercontent.com/56550489/112289533-4c631400-8c86-11eb-94d9-aaeffcc65d77.png)

---

##### Turn based Process and Targetboard

A usable, intuitive and highly efficient Turn based process supported with a minimal user effort interface in which game turns are played.

Player’s turn
Their own, current and up to date ship and targetboards are displayed as well aligned tables (rows and columns).

![13](https://user-images.githubusercontent.com/56550489/112164762-10787200-8be6-11eb-8fed-a43f0c556e22.png)

---

##### Firing Torpedoes

Players are able to ‘fire’ a single torpedo at a valid location (i.e., not previously targeted and within the board boundary) using the single notation coordinate (e.g., F2, etc.); if the location is invalid the player is asked to re-try.

![11](https://user-images.githubusercontent.com/56550489/112163756-3a7d6480-8be5-11eb-8219-dcbf2aafa8c9.png)

---

##### Notification outcome result

Players are clearly notified of a ‘hit’ or ‘miss’ (or win) based on the outcome of their turn.

![8](https://user-images.githubusercontent.com/56550489/112163226-baef9580-8be4-11eb-9cd2-d83986162fa0.png)

![9](https://user-images.githubusercontent.com/56550489/112163337-d8246400-8be4-11eb-8223-5f0abdeffbde.png)

---

##### Quit 

Players are able to quit the game (if not already won).

![18](https://user-images.githubusercontent.com/56550489/112289742-79172b80-8c86-11eb-9832-08b1a5192e41.png)

---

##### Computer’s turn

Its own, current and up to date ship and target boards are displayed as well aligned tables (rows and columns).

![14](https://user-images.githubusercontent.com/56550489/112201548-43cbf880-8c08-11eb-9583-a5aacb5aef23.png)

---

##### Computer’s Turn Targetboard (Player Target Board)

It uses its own up to date ‘targetboard’ to randomly ‘fire’ a torpedo at a valid location (i.e., not previously targeted and within the board boundary). A clear notification of a ‘hit’ or ‘miss’ (or win) based on the outcome is shown.

A user based ‘press a key’ interaction is required to end the computer’s turn.

![19](https://user-images.githubusercontent.com/56550489/112290309-02c6f900-8c87-11eb-8a2f-d50cdce2be68.png)

---

### 1b. UML style diagram illustrating initial overall solution (linked to 1a)

This is the Class Diagram for my AdaShip program illustrating all of the different classes present within the header files, with a main file (containing menu) - determines whether to initiate the function within my OnePlayerVComputer.cpp file which acts as a controller retrieving the relevant attributes and methods from the game files. 

In theory, I designed the program to start with the INIReader file to retrieve the boat data from the INI config file. There is a one-to-one relationship between AdaShipGrid and INIReader, followed by another one-to-one relationship between AdaShip and AdaShipGrid. There is one to many relationships between OnePlayerVComputer and AdaShip as a player has many AdaShips. 

The boat data is then meant to be parsed into the AdaShip file to hold within its class to then place the instructed ship coordinates into the grid, however it is not extensively used as most of the work is processed within the controller. 

AdaShipGrid attributes and methods are frequently used within the OnePlayerVComputer file in order to make changes to the grid and continue with the game progress. 

The Colours header file is absent from the diagram as it does not contain a class however it is imported and used within some of the cpp files to improve the user interface.

![UML Diagram](https://user-images.githubusercontent.com/56550489/112293021-91d51080-8c89-11eb-81da-82dc7ccd4b4d.png)

---

### 1c. Initial working plan, overall approach, development strategy and approach to quality (linked to 1a, 1b).

##### Initial Working Plan

I adopted an interative approach when undertaking this project, as I aimed to firstly build the basic components of the program. When I had the fundamentals in order, this enabled me to build on them and meet the PASS requirements expressed in the project brief. 

##### Approach to Quality

A technique I utilised religiously was to pick a single epic to write code for, firstly as a function in a seperate repository with a mock-up version of my program. This was so that I could stress test the new code and refactor my work, testing it frequently for bugs and defects. I would then implement this part of my code with the rest of my code base and see if I had met this requirement.

##### Development Strategy 

My development strategy consisted of an object-orientated approach this would mean separating the logic into a class to contain data associated to its intended mechanism and functionality. I kept the code in separate files to ensure good coding standards and readability for example AdaShipGrid.h and AdaShip.h. 

To ensure that I fully understood the project and its planned user journey I designed the following Player V Computer Flow Diagram. This allowed me to visualise how I could decompose the program into various sub-parts and understand how a single user decision would affect their journey. I found this useful as there are various conditions and loops within my program for validation purposes and because the player is free to dictate how they want to continue with the program (e.g. quit program). 

![Untitled Diagram-Page-2](https://user-images.githubusercontent.com/56550489/112168095-ea080600-8be8-11eb-9347-7f23f635a60a.png)

---

### 1d. Analysis and decomposition of the overall problem into key ‘epic’ style tasks (linked to 1b, 1c).

After reading the project requirements, I noticed that the requirements were already split up into various epic style tasks, an example being: "Select from a game menu to a start a: One player v computer game, Quit". After creating and posting all of my epic style tasks to GitHub I progressed until I created a functional prototype that met most of the requirements expressed in the "Pass Section" of the Project Brief.

When analysing a epic that has been decomposed from the initial requirements in my project board I would aim to utilise my analytical skills by applying a systematic technique for epic analysis. I listed the following headings in my notebook: TASK | Data Types | Algorithms | Functions | Code. Under the headings I would aim to fill out each column displayed for the epic I was working on to enable me to structure the program before writing any code.

![epics](https://user-images.githubusercontent.com/56550489/112197575-2563fe00-8c04-11eb-8897-26f304b61ec3.png)

---

### 1e. Initial object-oriented design ideas and plan of phased breakdown into smaller tasks (linked to 1d).

#### OOP Considerations

Main

When the application is runs the game menu is generated for the end user, if the end user chooses to continue to the game application then it will run the OnePlayerVComputer function in the next file.

OnePlayerVComputer

The OnePlayerVComputer file controls the flow of the game and ultimately determines  whether the Player or the AI has won the game. It retrieves most of its methods from the AdaShipGrid Class and also contains some of its own generated objects for instance the ones used to hold the battleships data that is then parsed into the adaship file to place it into the grid. 

AdaShipGrid

As mentioned above AdaShipGrid Class contains many instrumental methods that are needed for the program to run such as displayGrid() and editGrid() which are used in controller. Based on the user input retrieved for the ship placement the cpp function created will convert the string to an int to place the ship within the grid which is essentially a 2-D Array. It also contains the logic for the torpedo firing requirement depending on whether the controller has called for this method.

AdaShip

Similar to AdaShipGrid it has it's own header file (to reduce code reuse) but the class is not used extensively in actual gameplay - when the grid object is passed a ship, it places the ships coordinates into the grid. The cpp file is utitlised when the player chooses to orient their ship and to manually input their coordinates for their ship.

Colours

I also created my own colours header file to then be reused within the application and display a range of colours within the terminal. 

#### Plan of phased breakdown into smaller tasks

The following tables represent my project plan calendar, consisting of 3 weeks worth of work. The first week representing the design stage of my project in which I split up the 5 epic issues displayed in the project requirements into the 5 working days of the week. The following week displays the same pattern however this time I would be developing the program. The final week represents the time I aimed to spend writing the documentation/readme file with 4 days dedicated to the challenge outline section and the final day for the evaluation section.

| 1 March            | 2 March            | 3 March            | 4 March            | 5 March            | 
| ------------------ | ------------------ | ------------------ | ------------------ | ------------------ |
| Design             | Design             | Design             | Design             | Design             |
| Run Time File      | Set-Up Interface   | AI Opponent        | Turn-Based Process | AI's Turn          |

| 8 March            | 9 March            | 10 March           | 11 March           | 12 March           | 
| ------------------ | ------------------ | ------------------ | ------------------ | ------------------ |
| Development        | Development        | Development        | Development        | Development        |
| Run Time File      | Set-Up Interface   | AI Opponent        | Turn-Based Process | AI's Turn          |


| 15 March           | 16 March           | 17 March           | 18 March           | 19 March           | 
| ------------------ | ------------------ | ------------------ | ------------------ | ------------------ |
| Documentation      | Documentation      | Documentation      | Documentation      | Documentation      |
| Challenge Outline  | Challenge Outline  | Challenge Outline  | Challenge Outline  | Evaluation         |

---

## 2. Evaluation

### 2a. Reflective review, opportunities to improve and continued professional development.

Overall, I am satisfied with the final outcome of my assignment as I aimed to complete all of the PASS requirements displayed within the project requirement brief. I managed to fulfil most of the listed requirements however I failed to complete one of the initial requirements which was to provide a run-time file that the data is read from. This assignment was a challenge for me as I was never sure of what best practices and design patterns were suited for this type of assignment. Ultimately, if I was to complete this project again or a similar assignment I would aim to rectify the problems I found with the vector template class and aim to have a bit more practice with object-orientated programming.

---