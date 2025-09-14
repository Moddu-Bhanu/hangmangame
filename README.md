import random

def hangman():

    # Step 1: Predefined word list
    
    words = ["python", "computer", "program", "hangman", "keyboard"]
    
    word = random.choice(words)  # Randomly select a word
    
    guessed_word = ["_"] * len(word)  # Display word with underscores
    guessed_letters = []  # Track letters already guessed
    attempts = 6  # Allowed wrong guesses

    print(" Welcome to Hangman Game!")
    print("You have 6 attempts to guess the word.")
    print("Word to guess:", " ".join(guessed_word))

    # Step 2: Main loop
    while attempts > 0 and "_" in guessed_word:
        guess = input("\nEnter a letter: ").lower()

        # Check if valid input
        if len(guess) != 1 or not guess.isalpha():
            print(" Please enter a single alphabet.")
            continue

        # Check if letter already guessed
        if guess in guessed_letters:
            print(" You already guessed that letter:", guess)
            continue
        else:
            guessed_letters.append(guess)

        # Step 3: Check guess
        if guess in word:
            print(" Correct guess!")
            for i in range(len(word)):
                if word[i] == guess:
                    guessed_word[i] = guess
        else:
            attempts -= 1
            print(" Wrong guess! Attempts left:", attempts)

        print("Word:", " ".join(guessed_word))
        print("Guessed letters:", ", ".join(guessed_letters))

    # Step 4: Game result
    if "_" not in guessed_word:
        print("\n Congratulations! You guessed the word:", word)
    else:
        print("\n Game Over! The word was:", word)

# Run the game

hangman()
