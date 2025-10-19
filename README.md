# Caesar-Cipher
def caesar_cipher(text, shift, mode='encrypt'):
    result = ""

    if mode == 'decrypt':
        shift = -shift  # Reverse the shift for decryption

    for char in text:
        if char.isalpha():
            base = ord('A') if char.isupper() else ord('a')
            # Shift character and wrap around the alphabet
            result += chr((ord(char) - base + shift) % 26 + base)
        else:
            # Leave non-alphabetic characters unchanged
            result += char

    return result

def main():
    print("=== Caesar Cipher Encryption/Decryption ===")
    message = input("Enter your message: ")
    
    while True:
        try:
            shift = int(input("Enter the shift value (0-25): "))
            if 0 <= shift <= 25:
                break
            else:
                print("Please enter a number between 0 and 25.")
        except ValueError:
            print("Invalid input. Please enter a valid integer.")

    while True:
        mode = input("Do you want to (E)ncrypt or (D)ecrypt the message? ").strip().lower()
        if mode in ['e', 'encrypt']:
            encrypted = caesar_cipher(message, shift, mode='encrypt')
            print("Encrypted message:", encrypted)
            break
        elif mode in ['d', 'decrypt']:
            decrypted = caesar_cipher(message, shift, mode='decrypt')
            print("Decrypted message:", decrypted)
            break
        else:
            print("Please enter 'E' to encrypt or 'D' to decrypt.")

if __name__ == "__main__":
    main()
