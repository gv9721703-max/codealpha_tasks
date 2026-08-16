# codealpha_tasks1
TASK 1: HANGMAN Game
"""
TASK 1: Hangman Game
---------------------
Goal: A simple text-based Hangman game where the player guesses a word
one letter at a time.

Simplified Scope:
  - Uses a small list of 5 predefined words (no file or API needed).
  - Limits incorrect guesses to 6.
  - Basic console input/output only (no graphics or audio).

Key Concepts Used: random, while loop, if-else, strings, lists.
"""

import random

# ---------------------------------------------------------
# 1. List of predefined words (list)
# ---------------------------------------------------------
WORD_LIST = ["python", "hangman", "computer", "keyboard", "program"]

# Hangman stages shown as incorrect guesses increase (0 to 6 wrong guesses)
HANGMAN_STAGES = [
    """
       ------
       |    |
       |
       |
       |
       |
    --------
    """,
    """
       ------
       |    |
       |    O
       |
       |
       |
    --------
    """,
    """
       ------
       |    |
       |    O
       |    |
       |
       |
    --------
    """,
    """
       ------
       |    |
       |    O
       |   /|
       |
       |
    --------
    """,
    """
       ------
       |    |
       |    O
       |   /|\\
       |
       |
    --------
    """,
    """
       ------
       |    |
       |    O
       |   /|\\
       |   /
       |
    --------
    """,
    """
       ------
       |    |
       |    O
       |   /|\\
       |   / \\
       |
    --------
    """,
]

MAX_WRONG_GUESSES = 6


def choose_word(word_list):
    """Randomly picks a word from the list (random)."""
    return random.choice(word_list)


def display_word(word, guessed_letters):
    """
    Builds and returns the current state of the word,
    showing guessed letters and underscores for the rest (strings).
    """
    display = ""
    for letter in word:
        if letter in guessed_letters:
            display += letter + " "
        else:
            display += "_ "
    return display.strip()


def play_hangman():
    word = choose_word(WORD_LIST)
    guessed_letters = []      # list of all letters guessed so far
    wrong_guesses = 0
    game_over = False

    print("=" * 40)
    print("   WELCOME TO HANGMAN!")
    print("=" * 40)
    print(f"The word has {len(word)} letters. You have {MAX_WRONG_GUESSES} wrong guesses allowed.\n")

    # ---------------------------------------------------------
    # Main game loop (while loop)
    # ---------------------------------------------------------
    while not game_over:
        print(HANGMAN_STAGES[wrong_guesses])
        print("Word: ", display_word(word, guessed_letters))
        print(f"Wrong guesses left: {MAX_WRONG_GUESSES - wrong_guesses}")
        print(f"Guessed letters: {', '.join(guessed_letters) if guessed_letters else 'None'}")

        guess = input("\nGuess a letter: ").lower().strip()

        # --- Input validation (if-else) ---
        if len(guess) != 1 or not guess.isalpha():
            print("\n⚠️  Please enter a single alphabet letter.\n")
            continue

        if guess in guessed_letters:
            print(f"\n⚠️  You already guessed '{guess}'. Try a different letter.\n")
            continue

        guessed_letters.append(guess)

        if guess in word:
            print(f"\n✅ Good guess! '{guess}' is in the word.\n")
        else:
            wrong_guesses += 1
            print(f"\n❌ Wrong guess! '{guess}' is not in the word.\n")

        # --- Check win condition ---
        if all(letter in guessed_letters for letter in word):
            print(HANGMAN_STAGES[wrong_guesses])
            print(f"Word: {display_word(word, guessed_letters)}")
            print("\n🎉 Congratulations! You guessed the word correctly!")
            print(f"The word was: '{word}'")
            game_over = True

        # --- Check lose condition ---
        elif wrong_guesses == MAX_WRONG_GUESSES:
            print(HANGMAN_STAGES[wrong_guesses])
            print("\n💀 Game Over! You've run out of guesses.")
            print(f"The word was: '{word}'")
            game_over = True
"""
TASK 1: Hangman Game
---------------------
Goal: A simple text-based Hangman game where the player guesses a word
one letter at a time.

Simplified Scope:
  - Uses a small list of 5 predefined words (no file or API needed).
  - Limits incorrect guesses to 6.
  - Basic console input/output only (no graphics or audio).

Key Concepts Used: random, while loop, if-else, strings, lists.
"""

import random

# ---------------------------------------------------------
# 1. List of predefined words (list)
# ---------------------------------------------------------
WORD_LIST = ["python", "hangman", "computer", "keyboard", "program"]

# Hangman stages shown as incorrect guesses increase (0 to 6 wrong guesses)
HANGMAN_STAGES = [
    """
       ------
       |    |
       |
       |
       |
       |
    --------
    """,
    """
       ------
       |    |
       |    O
       |
       |
       |
    --------
    """,
    """
       ------
       |    |
       |    O
       |    |
       |
       |
    --------
    """,
    """
       ------
       |    |
       |    O
       |   /|
       |
       |
    --------
    """,
    """
       ------
       |    |
       |    O
       |   /|\\
       |
       |
    --------
    """,
    """
       ------
       |    |
       |    O
       |   /|\\
       |   /
       |
    --------
    """,
    """
       ------
       |    |
       |    O
       |   /|\\
       |   / \\
       |
    --------
    """,
]

MAX_WRONG_GUESSES = 6


def choose_word(word_list):
    """Randomly picks a word from the list (random)."""
    return random.choice(word_list)


def display_word(word, guessed_letters):
    """
    Builds and returns the current state of the word,
    showing guessed letters and underscores for the rest (strings).
    """
    display = ""
    for letter in word:
        if letter in guessed_letters:
            display += letter + " "
        else:
            display += "_ "
    return display.strip()


def play_hangman():
    word = choose_word(WORD_LIST)
    guessed_letters = []      # list of all letters guessed so far
    wrong_guesses = 0
    game_over = False

    print("=" * 40)
    print("   WELCOME TO HANGMAN!")
    print("=" * 40)
    print(f"The word has {len(word)} letters. You have {MAX_WRONG_GUESSES} wrong guesses allowed.\n")

    # ---------------------------------------------------------
    # Main game loop (while loop)
    # ---------------------------------------------------------
    while not game_over:
        print(HANGMAN_STAGES[wrong_guesses])
        print("Word: ", display_word(word, guessed_letters))
        print(f"Wrong guesses left: {MAX_WRONG_GUESSES - wrong_guesses}")
        print(f"Guessed letters: {', '.join(guessed_letters) if guessed_letters else 'None'}")

        guess = input("\nGuess a letter: ").lower().strip()

        # --- Input validation (if-else) ---
        if len(guess) != 1 or not guess.isalpha():
            print("\n⚠️  Please enter a single alphabet letter.\n")
            continue

        if guess in guessed_letters:
            print(f"\n⚠️  You already guessed '{guess}'. Try a different letter.\n")
            continue

        guessed_letters.append(guess)

        if guess in word:
            print(f"\n✅ Good guess! '{guess}' is in the word.\n")
        else:
            wrong_guesses += 1
            print(f"\n❌ Wrong guess! '{guess}' is not in the word.\n")

        # --- Check win condition ---
        if all(letter in guessed_letters for letter in word):
            print(HANGMAN_STAGES[wrong_guesses])
            print(f"Word: {display_word(word, guessed_letters)}")
            print("\n🎉 Congratulations! You guessed the word correctly!")
            print(f"The word was: '{word}'")
            game_over = True

        # --- Check lose condition ---
        elif wrong_guesses == MAX_WRONG_GUESSES:
            print(HANGMAN_STAGES[wrong_guesses])
            print("\n💀 Game Over! You've run out of guesses.")
            print(f"The word was: '{word}'")
            game_over = True
"""
TASK 1: Hangman Game
---------------------
Goal: A simple text-based Hangman game where the player guesses a word
one letter at a time.

Simplified Scope:
  - Uses a small list of 5 predefined words (no file or API needed).
  - Limits incorrect guesses to 6.
  - Basic console input/output only (no graphics or audio).

Key Concepts Used: random, while loop, if-else, strings, lists.
"""

import random

# ---------------------------------------------------------
# 1. List of predefined words (list)
# ---------------------------------------------------------
WORD_LIST = ["python", "hangman", "computer", "keyboard", "program"]

# Hangman stages shown as incorrect guesses increase (0 to 6 wrong guesses)
HANGMAN_STAGES = [
    """
       ------
       |    |
       |
       |
       |
       |
    --------
    """,
    """
       ------
       |    |
       |    O
       |
       |
       |
    --------
    """,
    """
       ------
       |    |
       |    O
       |    |
       |
       |
    --------
    """,
    """
       ------
       |    |
       |    O
       |   /|
       |
       |
    --------
    """,
    """
       ------
       |    |
       |    O
       |   /|\\
       |
       |
    --------
    """,
    """
       ------
       |    |
       |    O
       |   /|\\
       |   /
       |
    --------
    """,
    """
       ------
       |    |
       |    O
       |   /|\\
       |   / \\
       |
    --------
    """,
]

MAX_WRONG_GUESSES = 6


def choose_word(word_list):
    """Randomly picks a word from the list (random)."""
    return random.choice(word_list)


def display_word(word, guessed_letters):
    """
    Builds and returns the current state of the word,
    showing guessed letters and underscores for the rest (strings).
    """
    display = ""
    for letter in word:
        if letter in guessed_letters:
            display += letter + " "
        else:
            display += "_ "
    return display.strip()


def play_hangman():
    word = choose_word(WORD_LIST)
    guessed_letters = []      # list of all letters guessed so far
    wrong_guesses = 0
    game_over = False

    print("=" * 40)
    print("   WELCOME TO HANGMAN!")
    print("=" * 40)
    print(f"The word has {len(word)} letters. You have {MAX_WRONG_GUESSES} wrong guesses allowed.\n")

    # ---------------------------------------------------------
    # Main game loop (while loop)
    # ---------------------------------------------------------
    while not game_over:
        print(HANGMAN_STAGES[wrong_guesses])
        print("Word: ", display_word(word, guessed_letters))
        print(f"Wrong guesses left: {MAX_WRONG_GUESSES - wrong_guesses}")
        print(f"Guessed letters: {', '.join(guessed_letters) if guessed_letters else 'None'}")

        guess = input("\nGuess a letter: ").lower().strip()

        # --- Input validation (if-else) ---
        if len(guess) != 1 or not guess.isalpha():
            print("\n⚠️  Please enter a single alphabet letter.\n")
            continue

        if guess in guessed_letters:
            print(f"\n⚠️  You already guessed '{guess}'. Try a different letter.\n")
            continue

        guessed_letters.append(guess)

        if guess in word:
            print(f"\n✅ Good guess! '{guess}' is in the word.\n")
        else:
            wrong_guesses += 1
            print(f"\n❌ Wrong guess! '{guess}' is not in the word.\n")

        # --- Check win condition ---
        if all(letter in guessed_letters for letter in word):
            print(HANGMAN_STAGES[wrong_guesses])
            print(f"Word: {display_word(word, guessed_letters)}")
            print("\n🎉 Congratulations! You guessed the word correctly!")
            print(f"The word was: '{word}'")
            game_over = True

        # --- Check lose condition ---
        elif wrong_guesses == MAX_WRONG_GUESSES:
            print(HANGMAN_STAGES[wrong_guesses])
            print("\n💀 Game Over! You've run out of guesses.")
            print(f"The word was: '{word}'")
            game_over = True

    play_again = input("\nDo you want to play again? (y/n): ").lower().strip()
    if play_again == "y":
        print("\n")
        play_hangman()
    else:
        print("\nThanks for playing Hangman! Goodbye 👋")


# ---------------------------------------------------------
# Entry point
# ---------------------------------------------------------
if __name__ == "__main__":
    play_hangman()

    play_again = input("\nDo you want to play again? (y/n): ").lower().strip()
    if play_again == "y":
        print("\n")
        play_hangman()
    else:
        print("\nThanks for playing Hangman! Goodbye 👋")


# ---------------------------------------------------------
# Entry point
# ---------------------------------------------------------
if __name__ == "__main__":
    play_hangman()

    play_again = input("\nDo you want to play again? (y/n): ").lower().strip()
    if play_again == "y":
        print("\n")
        play_hangman()
    else:
        print("\nThanks for playing Hangman! Goodbye 👋")


# ---------------------------------------------------------
# Entry point
# ---------------------------------------------------------
if __name__ == "__main__":
    play_hangman()

