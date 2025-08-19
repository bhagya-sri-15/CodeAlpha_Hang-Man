import random

def hangman():
    # Predefined words
    words = ["python", "java", "swift", "kotlin", "ruby"]
    word = random.choice(words)  # Pick a random word
    guessed = ["_"] * len(word)  # Display blanks for the word
    guessed_letters = []  # Store guessed letters
    attempts = 6  # Allowed wrong guesses
    
    print("🎮 Welcome to Hangman!")
    print("Word to guess:", " ".join(guessed))
    
    while attempts > 0 and "_" in guessed:
        guess = input("\nGuess a letter: ").lower()
        
        if len(guess) != 1 or not guess.isalpha():
            print("⚠️ Enter only a single letter.")
            continue
        
        if guess in guessed_letters:
            print("❗ You already guessed that letter.")
            continue
        
        guessed_letters.append(guess)
        
        if guess in word:
            print(f"✅ Good guess! '{guess}' is in the word.")
            for i in range(len(word)):
                if word[i] == guess:
                    guessed[i] = guess
        else:
            attempts -= 1
            print(f"❌ Wrong guess! Attempts left: {attempts}")
        
        print("Word:", " ".join(guessed))
        print("Guessed letters:", ", ".join(guessed_letters))
    
    if "_" not in guessed:
        print("\n🎉 Congratulations! You guessed the word:", word)
    else:
        print("\n💀 Game Over! The word was:", word)

# Run the game
hangman()
