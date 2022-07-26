This is my Week2 project during class 
An Introduction to Interactive Programming in Python (Part 1)
from Courcera.org.  
===================================================================================================
Guess the number game
---------------------------------------------------------------------------------------------------

One of the simplest two-player games is “Guess the number”. 
The first player thinks of a secret number in some known range while the second player attempts to guess the number. 
After each guess, the first player answers either “Higher”, “Lower” or “Correct!” depending on whether the secret number is higher, lower or equal to the guess. 
In this project, you will build a simple interactive program in Python where the computer will take the role of the first player while you play as the second player.

You will interact with your program using an input field and several buttons. 
For this project, we will ignore the canvas and print the computer's responses in the console. 
Building an initial version of your project that prints information in the console is a development strategy that you should use in later projects as well. 
Focusing on getting the logic of the program correct before trying to make it display the information in some “nice” way on the canvas 
usually saves lots of time since debugging logic errors in graphical output can be tricky.

In all of the mini-projects for this class, we will provide a walk through of the steps involved in building your project to aid its development. 
A template for your mini-project is available here. Please work from this template.

## My Project code: ##
      # Made with the template for "Guess the number" mini-project
      # input will come from buttons and an input field
      # all output for the game will be printed in the console
      import simplegui
      import random
      # helper function to start and restart the game
      range = 100  
      
      def new_game():
        # initialize global variables used in your code here
        global secret_number
        secret_number = random.randrange(0, range)
        global count
        count = 7
        if range == 100:
          count = 7
        else:
          count = 10
        print "New game. Range is from 0 to " + str(range)
        print "Number of remaining guesses is " + str(count) + "\n"
        
      # define event handlers for control panel
      def range100():
        # button that changes the range to [0,100) and starts a new game 
        global range
        range = 100
        global count
        count = 7
        new_game()
        
      def range1000():
        # button that changes the range to [0,1000) and starts a new game     
        global range
        range = 1000
        global count
        count = 10
        new_game()
      
      def input_guess(guess):
        # main game logic goes here	
        global number
        number = int(guess)
        print "Guess was " + str(number)
        
        global count
        count -= 1
        print "Number of remaining guesses is " + str(count)
        
        if number < secret_number and count > 0:
          print "Higher!" + "\n"
        elif number > secret_number and count > 0:
          print "Lower!" + "\n"
        elif number == secret_number and count > 0:
          print "Correct!" + "\n"
          new_game()
        else:
          print "You run out of guessing. The number was " + str(secret_number) + "\n"
          new_game()
          
      # create frame
      frame = simplegui.create_frame("Guess the number",200,200)
      
      # register event handlers for control elements and start frame
      frame.add_input("Enter your number", input_guess, 100)
      frame.add_button("Range is [0,100)",range100, 200)
      frame.add_button("Range is [0,1000)",range1000, 200)
      
      # call new_game 
      new_game()


To check my program in the Code Sculptor, use this URL https://py2.codeskulptor.org/#user49_cdyn8aPXNF_12.py
