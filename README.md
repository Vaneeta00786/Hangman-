# Hangman-
import random

def hangman():
    # List of words to choose from
    word_list = ["apple", "banana", "orange", "grape", "strawberry", "pineapple", "watermelon"]
    chosen_word = random.choice(word_list).upper()
    word_display = ["_" for _ in chosen_word]
    guessed_letters = []
    attempts = 6  # Number of incorrect guesses allowed

    print("Welcome to Hangman!")
    print("Guess the fruit!")

    while attempts > 0 and "_" in word_display:
        print("\n" + " ".join(word_display))
        print(f"Attempts left: {attempts}")
        print(f"Guessed letters: {', '.join(guessed_letters)}")

        guess = input("Guess a letter: ").upper()

        if len(guess) != 1 or not guess.isalpha():
            print("Invalid input. Please enter a single letter.")
            continue

        if guess in guessed_letters:
            print("You already guessed that letter. Try again.")
            continue

        guessed_letters.append(guess)

        if guess in chosen_word:
            print("Good guess!")
            for i in range(len(chosen_word)):
                if chosen_word[i] == guess:
                    word_display[i] = guess
        else:
            print("Incorrect guess.")
            attempts -= 1

    if "_" not in word_display:
        print("\n" + " ".join(word_display))
        print("Congratulations! You guessed the word!")
    else:
        print("\n" + " ".join(word_display))
        print(f"You ran out of attempts! The word was: {chosen_word}")

if __name__ == "__main__":
    hangman()
