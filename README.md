Copy code
import random

def hangman():
    """Simple Hangman game to guess a fruit name."""
    
    words = ["apple", "banana", "orange", "grape", "strawberry", "pineapple", "watermelon"]
    word = random.choice(words).upper()
    display = ["_"] * len(word)
    guessed = set()
    attempts = 6

    print("🎮 Welcome to Hangman! 🍎 Guess the name of a fruit!")

    while attempts > 0 and "_" in display:
        print("\n" + " ".join(display))
        print(f"Attempts left: {attempts} | Guessed: {', '.join(sorted(guessed))}")
        guess = input("Guess a letter: ").upper()

        if not (guess.isalpha() and len(guess) == 1):
            print("❌ Enter a single letter.")
            continue
        if guess in guessed:
            print("⚠️ Already guessed!")
            continue

        guessed.add(guess)
        if guess in word:
            print("✅ Good guess!")
            for i, ch in enumerate(word):
                if ch == guess:
                    display[i] = guess
        else:
            print("❌ Wrong guess.")
            attempts -= 1

    print("\n" + " ".join(display))
    print("🎉 You guessed it!" if "_" not in display else f"💀 Out of attempts! Word: {word}")

if __name__ == "__main__":
    hangman()