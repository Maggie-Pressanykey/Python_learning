This is my first project during class An Introduction to Interactive Programming in Python (Part 1)
from Courcera.org.  
===================================================================================================
Rock-paper-scissors-lizard-Spock game 2.0.
---------------------------------------------------------------------------------------------------

In our first mini-project, we will build a Python function rpsls(name) that takes as input the string name,
which is one of "rock", "paper", "scissors", "lizard", or "Spock". 
The function then simulates playing a round of Rock-paper-scissors-lizard-Spock by generating its own random choice 
from these alternatives and then determining the winner using a simple rule that we will next describe.

While Rock-paper-scissor-lizard-Spock has a set of ten rules that logically determine who wins a round of RPSLS, 
coding up these rules would require a large number (5x5=25) of if elif else clauses in your mini-project code.
A simpler method for determining the winner is to assign each of the five choices a number:

0 — rock  

1 — Spock  

2 — paper  

3 — lizard  

4 — scissors  


In this expanded list, each choice wins against the preceding two choices and loses against the following two choices 
(if rock and scissors are thought of as being adjacent using modular arithmetic).

In all of the mini-projects for this class, we will provide a walk through of the steps involved in building your project to aid its development. A template for your mini-project is available here. Please work from this template.

Mini-project development process
Build a helper function name_to_number(name) that converts the string name into a number between 0 and 4 as described above. 
This function should use a sequence of if/elif/else clauses. 
You can use conditions of the form name == 'paper', etc. to distinguish the cases. 
To make debugging your code easier, we suggest including a final else clause that catches cases when name does not match any of the five correct input strings and prints an appropriate error message. 

Next, you should build a second helper function number_to_name(number) that converts a number in the range 0 to 4 into its corresponding name as a string. 
Again, we suggest including a final else clause that catches cases when number is not in the correct range. 

Implement the first part of the main function rpsls(player_choice). 
Print out a blank line (to separate consecutive games) followed by a line with an appropriate message describing the player's choice.
Then compute the number player_number between 0 and 4 corresponding to the player's choice by calling the helper function name_to_number() using player_choice.

Implement the second part of rpsls() that generates the computer's guess and prints out an appropriate message for that guess.
In particular, compute a random number comp_number between 0 and 4 that corresponds to the computer's guess using the function random.randrange().
Then compute the name comp_choice corresponding to the computer's number using the function number_to_name() and print an appropriate message with the computer's choice to the console.

Implement the last part of rpsls() that determines and prints out the winner. Specifically, compute the difference between comp_number and player_number taken modulo five. 
Then write an if/elif/else statement whose conditions test the various possible values of this difference and then prints an appropriate message concerning the winner.

## My Project code: ##
      def name_to_number(name):
    if name == 'rock':
        return 0
    elif name == 'Spock':
        return 1
    elif name == 'paper':
        return 2
    elif name == 'lizard':
        return 3
    elif name == 'scissors':
        return 4
    else:
        print "Error: invalid name"  
        
      def number_to_name(number):
    if number == 0:
        return 'rock'
    elif number == 1:
        return 'Spock'
    elif number == 2:
        return 'paper'
    elif number == 3:
        return 'lizard'
    elif number == 4:
        return 'scissors'
    else:
        print "Error: invalid number" 
    
      import random  
      def rpsls(player_choice): 
    print "\n"
    print "Player chooses " + str(player_choice)
    name = player_choice
    player_number = name_to_number(name)
    
    comp_number = random.randrange(0,5)
    number = comp_number
    comp_choice = number_to_name(number)
    print "Computer chooses " + str(comp_choice)
    
    win_number = (player_number - comp_number) % 5
    if win_number == 0:
        print "Player and computer tie!" 
    elif win_number >=3:
        print "Computer wins!"
    elif win_number <=2:
        print "Player wins!"  
        
        \#Test your code  
        rpsls("rock")  
        rpsls("Spock")  
        rpsls("paper")  
        rpsls("lizard")  
        rpsls("scissors")  

To check my program in the Code Sculptor, use this URL https://py2.codeskulptor.org/#user49_W01ELGBntlEwpOh.py

## During Week 2 I made some changes to the code to make the game RPSLS interactive - YEAH!!))) ##

>Challenge: Add an interactive user interface for your implementation of "Rock-paper-scissors-lizard-Spock". Create an input field that takes a player's guess, generates a random computer guess, and prints out the player and computer choices as well as who won in the console. Make sure that your program checks for and correctly responds to bad input. 
Despite the task was to build an input field, i decided to add the buttons - cos printing every time is not fun at all. So, enjoy)

## My Project code: ##
    #GUI-based version of RPSLS
    import simplegui
    import random
    #Insert your solution for RPSLS here
    
    def name_to_number(name):
      if name == 'rock':
        return 0
      elif name == 'Spock':
        return 1
      elif name == 'paper':
        return 2
      elif name == 'lizard':
        return 3
      elif name == 'scissors':
        return 4
      else:
        print "Error: invalid name"  
    
    def number_to_name(number):
      if number == 0:
        return 'rock'
      elif number == 1:
        return 'Spock' 
      elif number == 2:
        return 'paper'
      elif number == 3:
        return 'lizard'
      elif number == 4:
        return 'scissors'
      else:
        print "Error: invalid number" 
    
    def rpsls(guess): 
      print "\n"
      print "Player chooses " + str(guess)
      name = guess
      player_number = name_to_number(name)
    
      comp_number = random.randrange(0,5)
      number = comp_number
      comp_choice = number_to_name(number)
      print "Computer chooses " + str(comp_choice)
    
    win_number = (player_number - comp_number) % 5
    if win_number == 0:
        print "Player and computer tie!" + "/n"
    elif win_number >=3:
        print "Computer wins!" + "/n"
    elif win_number <=2:
        print "Player wins!" + "/n"  
        
    # handler for buttons
    def rock():
      guess = "rock"
      rpsls(guess)
      
    def paper():
      guess = "paper"
      rpsls(guess)
    
    def scissors():
      guess = "scissors"
      rpsls(guess)
    
    def lizard():
      guess = "lizard"
      rpsls(guess)
    
    def Spock():
      guess = "Spock"
      rpsls(guess)
    
    #Create frame and assign callbacks to event handlers
    frame = simplegui.create_frame("GUI-based RPSLS", 200, 200)
    frame.add_button("rock", rock, 200)
    frame.add_button("paper", paper, 200)
    frame.add_button("scissors", scissors, 200)
    frame.add_button("lizard", lizard, 200)
    frame.add_button("Spock", Spock, 200)
    
    #Start the frame animation
    frame.start()
    
## PLAY GAME ##
To check my program in the Code Sculptor, use this URL https://py2.codeskulptor.org/#user49_TOIrd8Zkc3_1.py
