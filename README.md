# WordleHacker
This uses the Wordle guess list to perform a handful of functions based on probabilities.

By inputting the results of your initial guess, the nextGuess function will eliminate words from the list of possible guesses based on correct and incorrect letters, then it ranks the possible next guess by the relative letter frequency of each letter in that particular place. So if a couple of next possible guesses are, say, STRAY and JAZZY, STRAY gets ranked higher because S is a very common first letter, R is more common than Z, etc. Each letter in the word adds weight to that word's priority in the ranking based on its frequency in that place among the remaining valid guesses. 

The playWordle function will just let the guessing algorithm play the game, the argument entered being the puzzle's answer. This serves as the basis for the additional functions which will test the value of first guesses in their likelihood to produce a lower score on average. By entering a first guess word, then iterating over the entire word list, with the bot playing the game using its probability algorithm, I can find the average number of guesses the bot would take with a first word. The word list is about 2300 words long, so the bot will play about 2300 games and average its scores. It takes about 30 seconds, as it is an O(n) function. Then, in order to find the best possible first guess (at least using the bot's particular strategy), I iterated each word from the wordlist as a first word over the word list with the playWordle function and outputted all scores, then averaged them. This took about 20 hours, as it was an O(n²) function where n~2300. 

I'd like to add a second guessing algorithm, one that takes an alternate path on the second guess, depending on the first guess results. A first guess with a very common vowel in the middle that is in the correct place, while helpful, does little to reduce the guess list, and thus the probability of a correct second guess is incredibly low. So in order to facilitate greater whittling down of the guess list on the second guess, the second guess will not include any correct letters from the first, but will try to include the most common letters not in the first guess. This is a common human strategy, to eliminate common letters as a means of narrowing possible word choices. Eliminating a high-value letter is not quite as valuable as finding out it is in the answer, but is more valuable than guessing a low value letter in order to shape the second guess around a correct, but common less (say an E at the end of a word, or an A in the second spot).
