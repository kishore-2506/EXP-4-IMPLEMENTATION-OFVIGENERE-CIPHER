## EXP : 4 IMPLEMENTATION OFVIGENERE CIPHER

## AIM :
To develop a simple C program to implement Vigenere Cipher.
## DESIGN STEPS :
Step 1 :
Design of Vigenere Cipher algorithnm
Step 2 :
Implementation using C or pyhton code
Step 3 :
1.	The Vigenère cipher uses a series of Caesar ciphers based on letters from a repeating keyword to encrypt text.
2.	A Vigenère square or table is created with 26 rows of the alphabet, each shifted one position left, representing different Caesar cipher shifts.
3.	To encrypt, each letter of the plaintext is matched with a corresponding letter in the keyword, repeated to match the message length.
4.	The letter in the Vigenère table is selected by intersecting the row starting with the keyword letter and the column with the plaintext letter.
5.	The resulting encrypted text is a combination of letters taken from various rows of the Vigenère square, based on the keyword.
6.	Decryption reverses this process by identifying the original plaintext letter from the appropriate row based on the keyword letter.

## PROGRAM :
```
#include <stdio.h>
#include <ctype.h>
#include <string.h>
#include <stdlib.h>

void encipher();
void decipher();

int main() {
    int choice;
    while (1) {
        printf("\n1. Encrypt Text");
        printf("\t2. Decrypt Text");
        printf("\t3. Exit");
        printf("\n\nEnter Your Choice: ");
        scanf("%d", &choice);

        if (choice == 3)
            return 0; // Proper exit
        else if (choice == 1)
            encipher();
        else if (choice == 2)
            decipher();
        else
            printf("Please Enter a Valid Option.\n");
    }
}

void encipher() {
    unsigned int i, j;
    char input[50], key[10];

    printf("\n\nEnter Plain Text: ");
    scanf("%s", input);

    printf("\nEnter Key Value: ");
    scanf("%s", key);

    printf("\nResultant Cipher Text: ");
    for (i = 0, j = 0; i < strlen(input); i++, j++) {
        if (j >= strlen(key)) {
            j = 0; // Reset key index if it exceeds length
        }
        printf("%c", 65 + (((toupper(input[i]) - 65) + (toupper(key[j]) - 65)) % 26));
    }
    printf("\n");
}

void decipher() {
    unsigned int i, j;
    char input[50], key[10];
    int value;

    printf("\n\nEnter Cipher Text: ");
    scanf("%s", input);

    printf("\nEnter the Key Value: ");
    scanf("%s", key);

    printf("\nDecrypted Plain Text: ");
    for (i = 0, j = 0; i < strlen(input); i++, j++) {
        if (j >= strlen(key)) {
            j = 0; // Reset key index
        }
        value = (toupper(input[i]) - 65) - (toupper(key[j]) - 65);
        if (value < 0) {
            value += 26; // Handle negative wrap-around
        }
        printf("%c", 65 + (value % 26));
    }
    printf("\n");
}
```
## OUTPUT :

<img width="681" height="680" alt="Screenshot 2025-09-08 141306" src="https://github.com/user-attachments/assets/81ad8bad-219c-4703-8673-946e1e108faf" />

## RESULT:
The program implementing the Vigenère cipher for encryption and decryption has been successfully	executed,	and	the	results	have	been	verified.
