# project hangman
coding for game
import random

def hangman():
    # List of words to guess
    word_list = ["apple", "banana", "cherry", "grape", "orange", "pear"]
    word = random.choice(word_list)
    guessed = "_" * len(word)
    guessed_letters = []
    tries = 6

    print("Let's play Hangman!")
    print(guessed)

    while tries > 0 and "_" in guessed:
        guess = input("Guess a letter: ").lower()

        if len(guess) != 1:
            print("Please enter a single letter.")
            continue

        if guess in guessed_letters:
            print("You already guessed that letter.")
            continue

        guessed_letters.append(guess)

        if guess in word:
            print("Good guess!")
            guessed = "".join([letter if letter in guessed_letters else "_" for letter in word])
        else:
            tries -= 1
            print(f"Wrong guess! You have {tries} tries left.")

        print(" ".join(guessed))

    if "_" not in guessed:
        print("Congratulations, you won!")
    else:
        print(f"You lost! The word was '{word}'.")

if __name__ == "__main__":
    hangman()
