# Random-Password-Generator
import random
import string

def generate_password(length, use_letters, use_numbers, use_symbols):
    character_pool = ""

    if use_letters:
        character_pool += string.ascii_letters
    if use_numbers:
        character_pool += string.digits
    if use_symbols:
        character_pool += string.punctuation

    if not character_pool:
        raise ValueError("At least one character type must be selected.")

    return ''.join(random.choices(character_pool, k=length))

def main():
    print("Welcome to the Password Generator!")

    try:
        length = int(input("Enter the desired password length: "))
        if length <= 0:
            print("Password length must be a positive integer.")
            return

        use_letters = input("Include letters? (yes/no): ").strip().lower() == "yes"
        use_numbers = input("Include numbers? (yes/no): ").strip().lower() == "yes"
        use_symbols = input("Include symbols? (yes/no): ").strip().lower() == "yes"

        password = generate_password(length, use_letters, use_numbers, use_symbols)

        print(f"Your generated password is: {password}")

    except ValueError as e:
        print(f"Error: {e}")

if __name__ == "__main__":
    main()
