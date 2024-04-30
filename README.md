#include <stdio.h>
#include <string.h>

#define CIPHER_TEXT_SIZE 256
#define KEY "SECRETKEY"

// Function to encrypt the message
void encrypt(const char *message, char *encryptedMessage) {
    int i;
    int keyLength = strlen(KEY);
    for (i = 0; message[i]!= '\0'; i++) {
        encryptedMessage[i] = message[i] ^ KEY[i % keyLength];
    }
    encryptedMessage[i] = '\0'; // null-terminate the encrypted message
}

// Function to decrypt the message
void decrypt(const char *ciphertext, char *plaintext) {
    int i;
    int keyLength = strlen(KEY);
    for (i = 0; ciphertext[i]!= '\0'; i++) {
        plaintext[i] = ciphertext[i] ^ KEY[i % keyLength];
    }
    plaintext[i] = '\0'; // null-terminate the decrypted message
}

int main(){
    char message[] = "This is a confidential message";
    char encryptedMessage[CIPHER_TEXT_SIZE]; 
    char decryptedMessage[CIPHER_TEXT_SIZE];
    
    // Encrypt the message
    encrypt(message, encryptedMessage);
    printf("Encrypted message: %s\n", encryptedMessage);
    
    // Decrypt the message
    decrypt(encryptedMessage, decryptedMessage);
    printf("Decrypted message: %s\n", decryptedMessage);

    return 0;
}
