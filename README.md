# Blackjack_game
Single-deck blackjack game written in SystemVerilog
Modules include:

deck
  Creates a memory array that keeps track of a single deck. Resets only on masterreset.

user
  Recieves and handles data for a player such as the user or the dealer. For each
  intermediate game, the hand is calculated. A feedback signal communicates with the 
  deck module in the event that an "empty" card is chosen. Resets on masterreset or 
  localreset.
  
userInput
  "Filters" input signals that are off the clock (eg user pressing a button; this module 
  such an input as one true even if the button is held for multiple clock cycles.

distribute
  Distributes randomly selected (via LFSR random card selector) card to either the user
  or the dealer, giving the dealer priority. Feedback signals and button presses 
  influence the distribution of said randomly selected card.
  
dealerModModMod
  Ensures that the dealer/computer player always stands at a hand of 17 or higher.
  
aceOptimizer
  Before calculating the value of the hand, this module optimizes the use of ace cards
  (eg whether a 1 or 11 is more beneficial for the user).
  
winner
  Evaluates the winner by comparing the hands of the dealer and the user. Considers advanced
  cases such as when either the dealer or the user bust (or if both bust).
  
moneyMover
  Executes the transfer of money based on which player won the hand and the type of bet that
  was placed (high or low).
  
LEDreader
  Continuously connected to the memory (aka the deck) and evaluates how many cards are remaining 
  in the deck for each type (such as Ace, ones, twos, etc).
  
LEDblinker
  Activates with the specified switch. When activated, the rate of flashing (output for LED) 
  corresponds to the amount of cards remaining in the deck for a specified card type. 
  Solid color: four cards remaining
  Slow blinking: 3 cards remaining
  Medium blinking: 2 cards remaining
  Fast blinking: 1 card remaining
  No color: no cards remaining
  
binary2dec
  Decomposes binary values into 3 four-bit values. This is in order to display the binary values
  in thier decimal form on the HEX display
  
controlPanel
  Each switch controls a different value to be displayed on the HEX display.
  
seg7
  Converts 4-bit binary values for output for the HEX display.
