# Hangman
import random  # Importing random module to select a random word

def hangman():
    """A simple Hangman game where the player guesses the name of a fruit."""
    
    # Step 1: Create a list of words to choose from
    word_list = ["apple", "banana", "orange", "grape", "strawberry", "pineapple", "watermelon"]
    
    # Step 2: Randomly select one word and convert it to uppercase for consistency
    chosen_word = random.choice(word_list).upper()
    
    # Step 3: Create a display list of underscores (_) for each letter in the chosen word
    word_display = ["_" for _ in chosen_word]
    
    # Step 4: Initialize an empty list to store the guessed letters
    guessed_letters = []
    
    # Step 5: Set the number of incorrect guesses allowed
    attempts = 6

    # Step 6: Display welcome message
    print("🎮 Welcome to Hangman!")
    print("🍎 Guess the name of a fruit!")

    # Step 7: Game loop — continues until attempts run out or the word is fully guessed
    while attempts > 0 and "_" in word_display:
        # Display the current progress of the guessed word
        print("\n" + " ".join(word_display))
        
        # Show remaining attempts and previously guessed letters
        print(f"Attempts left: {attempts}")
        print(f"Guessed letters: {', '.join(guessed_letters)}")

        # Step 8: Take input from the user and convert it to uppercase
        guess = input("Guess a letter: ").upper()

        # Step 9: Validate the input
        if len(guess) != 1 or not guess.isalpha():
            print("❌ Invalid input. Please enter a single letter.")
            continue  # Skip this round and ask again

        # Step 10: Check if the letter has already been guessed
        if guess in guessed_letters:
            print("⚠️ You already guessed that letter. Try another one.")
            continue

        # Step 11: Add the guessed letter to the list
        guessed_letters.append(guess)

        # Step 12: Check if the guessed letter is in the chosen word
        if guess in chosen_word:
            print("✅ Good guess!")
            # Replace the underscore with the guessed letter in all correct positions
            for i in range(len(chosen_word)):
                if chosen_word[i] == guess:
                    word_display[i] = guess
        else:
            # If guess is wrong, reduce the number of attempts
            print("❌ Incorrect guess.")
            attempts -= 1

    # Step 13: Check the final result
    if "_" not in word_display:
        # If no underscores remain, player has won
        print("\n" + " ".join(word_display))
        print("🎉 Congratulations! You guessed the word!")
    else:
        # If attempts run out, player loses
        print("\n" + " ".join(word_display))
        print(f"💀 You ran out of attempts! The correct word was: {chosen_word}")

# Step 14: Run the game only if the file is executed directly
if __name__ == "__main__":
    hangman()
