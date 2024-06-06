# Project Description: Blackjack Game:-

This project is a text-based implementation of the classic card game Blackjack, designed to be played in a console or terminal. The game allows a single user to play against a computer dealer, with the goal of obtaining a hand value as close to 21 as possible without exceeding it. The game follows the standard rules of Blackjack, including handling special conditions such as the presence of Aces (which can be worth either 1 or 11 points) and Blackjacks (a hand totaling 21 with just two cards).

# Objective:-

The primary objective of this project is to provide a fun and interactive way to play Blackjack in a console environment while demonstrating the use of Python functions, control flow, and basic game logic.

# Features:-
- Card Dealing: Randomly deal cards to the user and the computer from a virtual deck.
- Score Calculation: Calculate the score of a hand based on the values of the cards.
- Blackjack Handling: Recognize and handle Blackjacks and adjust the value of Aces to prevent busting.
- Game Logic: Implement the game rules, including player decisions and computer actions.
- Replayability: Allow the user to play multiple games in a single session.
- Dependencies

# The project relies on the following Python modules:

- random: For random selection of cards from the deck.
- replit.clear: For clearing the console between games (specific to the Replit platform).
- art.logo: For displaying the game logo.

# How It Works
-Card Dealing: At the start of the game, both the user and the computer are dealt two cards each from the deck.
-User Turn: The user is shown their hand and the computer's first card. The user can choose to draw more cards or pass.
-Computer Turn: The computer draws cards until its hand is worth at least 17 points.
-Score Comparison: The final scores of both the user and the computer are compared to determine the winner.
-Replay Option: The user is given the option to play another game or exit.

# Functions
→ deal_card()
This function returns a randomly selected card from a predefined list of card values, simulating the drawing of a card from a deck.

→ calculate_score(cards)
This function calculates the score of a given hand of cards, taking into account the special values of Aces and the condition for a Blackjack.

→ compare(user_score, computer_score)
This function compares the scores of the user and the computer to determine the outcome of the game, handling all possible game scenarios (e.g., Blackjack, bust).

→ play_game()
This function manages the flow of a single game, including dealing cards, handling user input, executing the computer's turn, and displaying the final results.

→ Main Loop
The main loop allows the user to play multiple games consecutively by repeatedly invoking the play_game() function as long as the user wishes to continue.

# Table of Contents:-

1.Dependencies

2.Functions
  ~deal_card()
  ~calculate_score(cards)
  ~compare(user_score, computer_score)
  ~play_game()

3. Main Loop

- Dependencies:-

- Libraries:-

 ~random: Used to randomly select cards from the deck.

 ~replit.clear: Used to clear the console for a fresh game display.
 
~art.logo: A string containing the ASCII art for the game's logo.

# Import Statements:-
import random
from replit import clear
from art import logo

- Functions:-
deal_card()

def deal_card():
  """Returns a random card from the deck."""
  cards = [11, 2, 3, 4, 5, 6, 7, 8, 9, 10, 10, 10, 10]
  card = random.choice(cards)
  return card
  
This function returns a random card from the deck. The deck is represented by a list of integers where 11 is the Ace, and 10 is used four times to represent the face cards (Jack, Queen, King) and the 10 itself.

calculate_score(cards)

def calculate_score(cards):
  """Take a list of cards and return the score calculated from the cards"""
  if sum(cards) == 21 and len(cards) == 2:
    return 0
  if 11 in cards and sum(cards) > 21:
    cards.remove(11)
    cards.append(1)
  return sum(cards)

- This function takes a list of cards and calculates the score based on the standard Blackjack rules:

~If the score is 21 with exactly two cards (an Ace and a 10-value card), it returns 0 to represent a Blackjack.

~If the score exceeds 21 and the list contains an Ace (value 11), it replaces the Ace with a 1 to avoid busting.

~ Otherwise, it returns the sum of the card values.

compare(user_score, computer_score):-

- Then ,

def compare(user_score, computer_score):
  if user_score > 21 and computer_score > 21:
    return "You went over. You lose 😤"
  if user_score == computer_score:
    return "Draw 🙃"
  elif computer_score == 0:
    return "Lose, opponent has Blackjack 😱"
  elif user_score == 0:
    return "Win with a Blackjack 😎"
  elif user_score > 21:
    return "You went over. You lose 😭"
  elif computer_score > 21:
    return "Opponent went over. You win 😁"
  elif user_score > computer_score:
    return "You win 😃"
  else:
    return "You lose 😤"

- Description:

This function compares the user's score with the computer's score and returns a string indicating the result:

~If both scores are over 21, the user loses.

~If the scores are equal, it’s a draw.

~If the computer has a Blackjack, the user loses.

~If the user has a Blackjack, the user wins.

~If the user's score exceeds 21, the user loses.

~If the computer's score exceeds 21, the user wins.

~If none of the above conditions are met, the higher score wins.

~play_game()

- Definition:

def play_game():
  print(logo)
  user_cards = []
  computer_cards = []
  is_game_over = False

  for _ in range(2):
    user_cards.append(deal_card())
    computer_cards.append(deal_card())

  while not is_game_over:
    user_score = calculate_score(user_cards)
    computer_score = calculate_score(computer_cards)
    print(f"   Your cards: {user_cards}, current score: {user_score}")
    print(f"   Computer's first card: {computer_cards[0]}")

    if user_score == 0 or computer_score == 0 or user_score > 21:
      is_game_over = True
    else:
      user_should_deal = input("Type 'y' to get another card, type 'n' to pass: ")
      if user_should_deal == "y":
        user_cards.append(deal_card())
      else:
        is_game_over = True

  while computer_score != 0 and computer_score < 17:
    computer_cards.append(deal_card())
    computer_score = calculate_score(computer_cards)

  print(f"   Your final hand: {user_cards}, final score: {user_score}")
  print(f"   Computer's final hand: {computer_cards}, final score: {computer_score}")
  print(compare(user_score, computer_score))

- Description:-

This function orchestrates the main flow of the game:

~It prints the game logo.

~Deals two cards each to the user and the computer.

~Enters a loop where the user's score is calculated and displayed. The user is asked if they want another card.

~If the user's score is a Blackjack, exceeds 21, or the user chooses to pass, the loop ends.

~The computer then draws cards until its score is at least 17.

~Finally, the scores are compared, and the result is displayed.

- Main Loop:- 
while input("Do you want to play a game of Blackjack? Type 'y' or 'n': ") == "y":
  clear()
  play_game()

This documentation provides an overview and detailed explanation of each function and the main loop used in the Blackjack game. The functions handle card dealing, score calculation, and game logic, while the main loop manages the game's replayability.


# Example of Gameplay:-

~The game starts by displaying the logo.

~The user and the computer are each dealt two cards.

~The user sees their cards and the computer's first card, and decides whether to draw another card or pass.

~Once the user finishes their turn, the computer draws cards until it reaches at least 17 points.

~The scores are compared, and the result is displayed.

~The user is asked if they want to play another round. If yes, the console is cleared, and a new game starts.
# Output:-

<h1 align="center">
    <a href="https://google.com">
    <img src="./blackjack output .png">
   
    
</h1>
blackjack output .jpg
# Conclusion :-

This project provides a simple yet effective way to experience Blackjack in a console environment. It demonstrates key programming concepts such as random number generation, list manipulation, conditional logic, and user interaction, making it a valuable learning tool for beginner programmers.
