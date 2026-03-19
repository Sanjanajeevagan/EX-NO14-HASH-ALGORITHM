# EX-NO14-HASH-ALGORITHM

## AIM:
To implement HASH ALGORITHM

## ALGORITHM:

1. Hash Algorithm is used to convert input data (message) into a fixed-size string, typically a hash value, which uniquely represents the original data.

2. Initialization:
   - Choose a hash function \( H \) (e.g., SHA-256, MD5, etc.).
   - The message \( M \) to be hashed is input.

3. Message Preprocessing:
   - Break the message \( M \) into fixed-size blocks. If necessary, pad the message to make it compatible with the block size required by the hash function.
   - For example, in SHA-256, the message is padded to ensure that its length is a multiple of 512 bits.

4. Hash Calculation:
   - Process the message block by block, applying the hash function \( H \) iteratively to produce an intermediate hash value.
   - For SHA-256, each block is processed through a series of logical operations, bitwise manipulations, and modular additions.

5. Output:
   - After all blocks are processed, the final hash value (digest) is produced, which is a fixed-size output (e.g., 256-bit for SHA-256).
   - The resulting hash is unique to the input message, meaning even a small change in the message will result in a completely different hash.

6. Security: The strength of the hash algorithm lies in its collision resistance, ensuring that it is computationally infeasible to find two different messages that produce the same hash value.


## Program:
``` py
#include <stdio.h>
#include <string.h>

#define PRIME 31
#define MOD 1000000007

// Function to generate hash
long long generateHash(char message[]) {
    long long hash = 0;
    long long power = 1;

    for(int i = 0; message[i] != '\0'; i++) {
        int value = message[i] - 'a' + 1;  // Convert char to number
        hash = (hash + value * power) % MOD;
        power = (power * PRIME) % MOD;
    }

    return hash;
}

int main() {
    char message[100];
    long long hashValue;

    // Input
    printf("Enter message: ");
    scanf("%s", message);

    // Generate hash
    hashValue = generateHash(message);

    // Display result
    printf("Generated Hash Value: %lld\n", hashValue);

    // Demonstration: small change → different hash
    printf("\n--- Testing Sensitivity ---\n");
    message[0] = message[0] + 1;  // Modify first character

    long long newHash = generateHash(message);
    printf("Modified Message Hash: %lld\n", newHash);

    return 0;
}
```

## Output:

<img width="505" height="277" alt="image" src="https://github.com/user-attachments/assets/6cfb2e66-d2bd-4c69-954a-0bde3d942386" />

## Result:
The program is executed successfully.
