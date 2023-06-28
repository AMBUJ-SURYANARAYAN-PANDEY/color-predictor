# color-predictor
color preidictor game 
import random

# List of color names and their corresponding RGB values
colors = {
    "red": (255, 0, 0),
    "green": (0, 255, 0),
    "blue": (0, 0, 255),
    "yellow": (255, 255, 0),
    "orange": (255, 165, 0),
    "purple": (128, 0, 128),
    # Add more colors as needed
}

def generate_question():
    # Select three random colors
    color_options = random.sample(list(colors.keys()), 3)
    # Select one color as the correct answer
    correct_color = random.choice(color_options)
    return color_options, correct_color

def get_rgb_value(color):
    return colors[color]

def check_answer(guess, correct_color):
    return guess.lower() == correct_color.lower()

def play_game():
    print("Welcome to the Color Predictor Game!")
    print("Guess the color based on its RGB values.")
    print("Enter 'quit' to exit the game.\n")

    score = 0
    while True:
        color_options, correct_color = generate_question()

        # Print the RGB values of the color options
        print("Color options:")
        for color in color_options:
            rgb = get_rgb_value(color)
            print(f"- {color.capitalize()}: {rgb}")

        # Ask for user's guess
        guess = input("\nEnter your guess: ")
        
        if guess.lower() == 'quit':
            break

        # Check if the guess is correct
        if check_answer(guess, correct_color):
            print("Correct answer! Well done.")
            score += 1
        else:
            print(f"Wrong answer. The correct color was {correct_color}.")

        print(f"Your current score: {score}\n")

    print("Thank you for playing the Color Predictor Game!")

# Start the game
play_game()

