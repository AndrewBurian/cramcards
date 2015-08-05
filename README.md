# Cram Cards
CLI based study cards

Generating Decks
-----
Initially, you begin by creating the study cards file using the `createcramdeck` program. This program will allow you to specify question-answer pairs, along with the method that should be used to check the answer.  

The checktypes are:

type  | behavior
------|------------------
ask   | will prompt y/n for each question
match | will match the answer given to the card (case insensitive)
Match | Case sensitive match
regex | Match regular expression (case insensitive)
Regex | Case sensitive regex

Your deck of study cards is then written to a file that can be read by the `cramcards` program. This file is plain YAML format, and can be edited by hand if nessesary.


Memorizing
----------
Once you have your deck of cards, run `cramcards` and specify the deck and optionally the number of levels you wish to cram to.  

A cram level is essentially how many times in a row you have answered that card correctly. Initially, all cards start at level 0. The program them goes through the cards in level 0 until all cards have been answered correctly at least once.  

When a card is correctly answered, it is promoted to the next level. An incorrect answer will demote the card back into level 0. When a card is answered correctly at the maximum level, it is memorized, and is removed from the levels.  

When the current level of cards is exhausted, the program will return to the lowest level that still contains cards.


Break and Restore
-----------------
At any time, you may leave the cram session by inturrupting the program (ctrl+c). A cram.restore file will be created automatically in the current directory overwriting any existing file of the same name.  

If you wish to resume where you left off, envoke `cramcards` with the `--restore` option, and give it the restore file rather than the card deck file. The session will be exactly as you left it.


Acknowledgements
----------
The general idea for the cram levels was borrowed from cram.com
