This is one of the most well known beginner projects. 
The program greets the user and asks them how long they want to their password to be, how complex and if they are satsfied with it.
If not the program will generate a new password based on their previous settings.
here is the code
-
import random

letters = list("abcdefghijklmnopqrstuvwxyz")
numbers = list("0123456789")
symbols = list("!@#$%^&*()_+-=[]{}|;:,.<>?")

def greeting():  # Greets the user
    print("Welcome to the random password generator!")
    print("Today we will generate a random password for you.")

def complexity():  # Asks the user how complex they want their password to be
    while True:
        print("How complex should the password be?")
        print("1. Simple")
        print("2. Medium")
        print("3. Complex")

        choice = input("Enter your choice: ").strip()

        if choice == "1":
            print("Simple password")
            return choice
        elif choice == "2":
            print("Medium password")
            return choice
        elif choice == "3":
            print("Complex password")
            return choice
        else:
            print("Invalid choice. Try again.")

def length():  # Asks the user how long they want their password to be
    while True:
        print("How long do you want your password to be? (4-25 characters)")

        try:
            length_val = int(input())

            if length_val < 4:
                print("Password too short")
            elif length_val > 25:
                print("Password too long")
            else:
                return length_val

        except ValueError:
            print("Please enter a whole number.")

def generate_password(complexity, length):  # Generates the password

    if complexity == "1":
        characters = letters

    elif complexity == "2":
        characters = letters + numbers

    else:
        characters = letters + numbers + symbols

    password = ""

    for _ in range(length):
        password += random.choice(characters)

    print("Your password is:", password)

def satisfied(complexity, length):  # Asks if the user is happy with their password
    while True:
        answer = input("Are you satisfied with your password? (yes/no) ").lower().strip()

        if answer == "yes":
            print("Great! Your password is ready!")
            break

        elif answer == "no":
            print("Let's generate another one.")
            generate_password(complexity, length)

        else:
            print("Please enter yes or no.")

greeting()
complexity_choice = complexity()
length_choice = length()
generate_password(complexity_choice, length_choice)
satisfied(complexity_choice, length_choice)
