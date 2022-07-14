# Pig Latin #
## Practice exercise 5 from Week2b - during class An Introduction to Interactive Programming in Python (Part 1) from Courcera.org (Rise Univercity). ##
Conditions:
>Write a program allows a user to enter a word in an input field, translates that word into Pig Latin and prints this translation in the console. 
For the sake of modularity, we suggest that you build a helper function that handles all of the details of translating a word to Pig Latin 

>Pig Latin is a language game that involves altering words via a simple set of rules. 
If the first letter in word is a consonant, append the consonant plus "ay" to the end of the remainder of the word. 
For example, pig_latin("pig") would return "igpay".
If the first letter in word is a vowel, append "way" to the end of the word.
For example, pig_latin("owl") returns "owlway".
In full Pig Latin, the leading consonant cluster is moved to the end of the word.

## My Project Code ##
      
      # Convert input text into Pig Latin
   
      import simplegui 
      
      # Pig Latin helper function
      def pig_latin(word):
      """Returns the (simplified) Pig Latin version of the word."""
      
      first_letter = word[0]
      rest_of_word = word[1 : ]
      
      if first_letter in ['a', 'e', 'i', 'o', 'u', 'y']:
        word = word + "way"
        print word
      else:
        word = str(rest_of_word) + str(first_letter) + "ay"
        print word
        
      # Handler for input field
      def get_input(input):
        word = input
        pig_latin(word)
      
      # Create frame and assign callbacks to event handlers
      frame = simplegui.create_frame("Pig Latin translator", 200, 200)
      frame.add_input("Enter", get_input, 100)
      
      # Start the frame animation
      frame.start()
      
      ###################################################
      # Test
      
      get_input("pig")
      get_input("owl")
      get_input("tree")
      
      ###################################################
      # Expected output from test
      #igpay
      #owlway
      #reetay
      
## Check the program in the CodeSculptor
https://py2.codeskulptor.org/practice.html#user49_NmVDWhA2Ra_0.py
