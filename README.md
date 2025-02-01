# code_alpha_hangmanproject
import random

# List of possible words
word_list = ['python', 'hangman', 'programming', 'developer', 'computer', 'algorithm', 'language', 'software', 'data']

def hangman():
    # Choose a random word
    word = random.choice(word_list)
    word_length = len(word)
    
    # Create a list to track the current state of the word
    guessed_word = ['_'] * word_length
    guessed_letters = []
    
    # Set a limit on the number of incorrect guesses
    max_incorrect_guesses = 6
    incorrect_guesses = 0
    
    print("Welcome to Hangman!")
    print("Try to guess the word.")
    print("The word has", word_length, "letters.")
    print("You have", max_incorrect_guesses, "incorrect guesses remaining.")
    
    while incorrect_guesses < max_incorrect_guesses:
        # Display the current state of the word
        print("Current word: " + " ".join(guessed_word))
        
        # Display the guessed letters
        print("Guessed letters:", ", ".join(guessed_letters))
        
        # Ask the player to input a letter
        guess = input("Guess a letter: ").lower()
        
        # Check if input is valid (one letter and not already guessed)
        if len(guess) != 1 or not guess.isalpha():
            print("Invalid input. Please enter a single letter.")
            continue
        if guess in guessed_letters:
            print(f"You already guessed '{guess}'. Try again.")
            continue
        
        # Add guessed letter to the list of guessed letters
        guessed_letters.append(guess)
        
        # Check if the letter is in the word
        if guess in word:
            print(f"Good guess! '{guess}' is in the word.")
            # Update the guessed_word list to show the correct letter
            for i in range(word_length):
                if word[i] == guess:
                    guessed_word[i] = guess
        else:
            incorrect_guesses += 1
            print(f"Oops! '{guess}' is not in the word. You have {max_incorrect_guesses - incorrect_guesses} incorrect guesses left.")
        
        # Check if the player has guessed the word correctly
        if "_" not in guessed_word:
            print("Congratulations! You guessed the word:", word)
            break
    else:
        print("Game Over! The word was:", word)

# Start the game
if __name__ == "__main__":
    hangman()
