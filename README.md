import random

def hangman():
    # List of words to choose from
    words = ['python', 'hangman', 'programming', 'development', 'challenge']
    # Randomly select a word
    word_to_guess = random.choice(words)
    guessed_letters = []
    incorrect_guesses = 0
    max_incorrect_guesses = 6

    # Display the initial state
    print("Welcome to Hangman!")
    print("_ " * len(word_to_guess))
    
    while incorrect_guesses < max_incorrect_guesses:
        guess = input("Guess a letter: ").lower()
        
        # Check if the input is a single letter
        if len(guess) != 1 or not guess.isalpha():
            print("Please enter a single letter.")
            continue

        if guess in guessed_letters:
            print("You've already guessed that letter.")
            continue

        guessed_letters.append(guess)

        if guess in word_to_guess:
            print(f"Good guess! The letter '{guess}' is in the word.")
        else:
            incorrect_guesses += 1
            print(f"Sorry, the letter '{guess}' is not in the word. You have {max_incorrect_guesses - incorrect_guesses} guesses left.")

        # Display the current state of the word
        current_state = ''.join([letter if letter in guessed_letters else '_' for letter in word_to_guess])
        print(' '.join(current_state))

        if '_' not in current_state:
            print("Congratulations! You've guessed the word:", word_to_guess)
            break
    else:
        print("You've run out of guesses. The word was:", word_to_guess)

if __name__ == "__main__":
    hangman()
