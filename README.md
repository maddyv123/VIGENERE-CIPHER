# VIGENERE-CIPHER
## EX. NO: 1(D)
 

## IMPLEMETATION OF VIGENERE CIPHER
 

## AIM:

To implement the Vigenere Cipher substitution technique using C program.

## DESCRIPTION:

To encrypt, a table of alphabets can be used, termed a tabula recta, Vigenère square,or Vigenère table. It consists of the alphabet written out 26 times in differnt rows, each
 
alphabet shifted cyclically to the left compared to the previous alphabet, corresponding to the 26 possible Caesar ciphers. At different points in the encryption process, the cipher uses adifferent alphabet from one of the rows. The alphabet used at each point repeating keyword.depends on a Each row starts with a key letter. The remainder of the row holds the letters A to Z. Although there are 26 key rows shown, you will only use as many keys as there are unique letters in the key string, here just 5 keys, {L, E, M, O, N}. For successive letters of the message, we are going to take successive letters of the key string, and encipher each message letter using its corresponding key row. Choose the next letter of the key, go along that row to find the column heading that	atches the message character; the letter at the intersection of
[key-row, msg-col] is the enciphered letter.


## ALGORITHM:

STEP-1: Arrange the alphabets in row and column of a 26*26 matrix.
STEP-2: Circulate the alphabets in each row to position left such that the first letter is attached to last.
STEP-3: Repeat this process for all 26 rows and construct the final key matrix.
STEP-4: The keyword and the plain text is read from the user.
STEP-5: The characters in the keyword are repeated sequentially so as to match with that of the plain text.
STEP-6: Pick the first letter of the plain text and that of the keyword as the row indices and column indices respectively.
STEP-7: The junction character where these two meet forms the cipher character.
STEP-8: Repeat the above steps to generate the entire cipher text.


## PROGRAM
def generate_key(text, key):
   
    key = list(key)
    if len(key) == len(text):
        return "".join(key)
    else:
        for i in range(len(text) - len(key)):
            key.append(key[i % len(key)])
    return "".join(key)


def vigenere_encrypt(plain_text, key):
    
    encrypted_text = []
    key = generate_key(plain_text, key)
    for i in range(len(plain_text)):
        if plain_text[i].isalpha():
            shift = ord(key[i].upper()) - ord('A')
            if plain_text[i].isupper():
                encrypted_text.append(chr((ord(plain_text[i]) + shift - ord('A')) % 26 + ord('A')))
            else:
                encrypted_text.append(chr((ord(plain_text[i]) + shift - ord('a')) % 26 + ord('a')))
        else:
            encrypted_text.append(plain_text[i])
    return "".join(encrypted_text)

def vigenere_decrypt(cipher_text, key):
    
    decrypted_text = []
    key = generate_key(cipher_text, key)
    for i in range(len(cipher_text)):
        if cipher_text[i].isalpha():
            shift = ord(key[i].upper()) - ord('A')
            if cipher_text[i].isupper():
                decrypted_text.append(chr((ord(cipher_text[i]) - shift - ord('A')) % 26 + ord('A')))
            else:
                decrypted_text.append(chr((ord(cipher_text[i]) - shift - ord('a')) % 26 + ord('a')))
        else:
            decrypted_text.append(cipher_text[i])
    return "".join(decrypted_text)

# Example Usage

plaintext = input("Enter the plaintext: ")

key = input("Enter the key: ")

encrypted = vigenere_encrypt(plaintext, key)

decrypted = vigenere_decrypt(encrypted, key)

print(f"Encrypted: {encrypted}")

print(f"Decrypted: {decrypted}")


## OUTPUT
![Screenshot 2025-03-27 090529](https://github.com/user-attachments/assets/9c989dbb-2857-4b85-a7ec-f226a0293c50)


## RESULT
The code executed successfully!
