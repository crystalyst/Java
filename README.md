# Java
Repository for self-studying Java

<strong> 1. Nim game (Using the tester file provided by Prof. Adam Cannon) - <i>all codes are located under Nim-Game Repository</i> </strong>

- Game Class

int getRandomValue(int min, int max) - the method returns random values from minimum to maximum from parameter. I used random method in math class. Math.random() returns a double value that is bigger or equal to 0.0, and smaller or equal to 1.0. To designate the scope specifically, I used (int)(Math.random() * (max-min+1)) + min.

boolean updateMarbles(int playerChoice) - the method updates the number of marbles and returns the result. This method checks if player's input is valid; if valid, it deducts the number of marbles by the amount of playerChoice, and returns true. If not, it returns false.

void printWinner(int turnNumber) - the method decides and prints out who is the winner by checking turnNumber. To do this, I clarified one variable to store winner's value: if turnNumber = 0, saves and prints out Human win!!. If turnNumber = 1, saves and prints out Computer Win!!

void play() - the method proceeds the nim game. After deciding the turn by using getRandomValue(0,1), proceed the game only if there is more than 1 marble. If turn = 0 , Human proceeds the game, and if turn = 1, computer proceeds the game. Each turn, either computer or human inputs the number of marbles they need to bring. After these inputs are stored, I used updateMarbles method to update the number of marbles and change the turn. If any player chooses the invalid number of marbles, it does not change the turn and let player to make an input again. In conclusion, if the number of marbles becomes 0, which means the game has ended, call printWinner method to print who is the winner.

- Computer class

int getStupidChoice(int marblesLeft) - the method that returns the number of marbles if in stupid mode. I used the random method in Math class in order to obtain random value between 1 and marblesLeft/2. I designated the scope of this as the same way I did at Game class(getRandomValue at Game class)

int findSmartChoice(int marblesLeft) - the method that returns the number of marbles in smart mode. This method calculates and returns the number of marbles to bring in order to make the number of marbles changed becomes power of 2 -1. If marblesLeft = 1, which means there is only one choice to make for player, returns = 1. If not, proceeds the calculation. First of fall, since the maximum value of marblesLeft is 100, I figured out that the maximum value of power of 2 -1 is 63. So, I decided to look over only 6 cases(when power of 2 -1 is 63, 31, 15, 7, 3, 1). In order to find something power of 2 -1, I used the shift in order to return the value of marblesLeft - (power of 2 - 1) if that value is in the scope between 0 and marblesLeft/2. (I used the same strategy by the time when I construct Human class: if Computer cannot find the value, returns the value of getStupidChoice)

void move(int marblesLeft) - the method that decides choice(the number of marbles to bring). If mode = 2, find choice by using findSmartChoice method. If mode = 1, find choice by using getStupidChoice method.

- Human class

void move() - the method that stores the user's input into choice. I designed this to store initial value = -1, if the input is not an integer.
