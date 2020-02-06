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

======================================================================================

<strong> 2. Poker Game (Using the tester file provided by Prof. Adam Cannon) - <i>all codes are located under Poker Game Repository</i> </strong>

- Card Class

final String str_suit[] - To convert suit that is integer data type into String.
The reason why I did not choose to convert into character is that it is easy to use String in order to utilize
toString() method.

CompareTo() - In order to sort player's hand later, I decided to use CompareTo() method.
I designed this code to be sorted by ascending order.

ToString() - I used this method to create String that each represents a poker card. e.g. h1, h2
Initially, there are suits and ranks given in integer data types, but by utilizing this method, these two
integers could form one String that is equivalent to a poker card.

- Deck Class

Deck() - Constructor. It is for assigning all 52 poker cards seperately for each 52 spots of poker card deck.

Shuffle() - It swaps 52 cards in a random way by using Math.random() method

- Player Class

addCard() - add Card to hand, which is an ArrayList.

removeCard() - remove Card from hand, which is an ArrayList.

winnings() - it stores the value of bets * payout to bankroll.

discardAll() - By using the method clear(), it remove all cards that hand currently has.

sortHand() - it is possible to sort hand by using Collections.sort(). In this sense, CompareTo() method
that is in Card class is used 

- Game Class

Game(String[] testHand) - Initialize player's hand(init hand) by testhand that is parameter of constructor

Game() - constructor. It consist of deck, and picks up 5 cards from the shuffled deck in order to form player's hand.

play() - the method that runs the game overall. In this method, player can change the card in one's hand until one reveals them.

checkHand() - the method evaluates hand of player, and return String. e.g. "One Pair!"

checkPair() - receive ArrayList hand as a parameter, and count how many cards that have same rank in the hand.
e.g. One Pair, Two Pair, Three of a Kind, Full House, Four of a Kind

checkStraight() - To evaluate whether or not hand is straight. From the beginning of the index, this method checks if rank increments by 1 as index increments by 1.
return 0; - No Straight / return 1; - Straight / return 2; - Royal Straight

checkFlush() - this method compares all suits in hand. If all suits have the same value = True, if any of them are different than others = False.
