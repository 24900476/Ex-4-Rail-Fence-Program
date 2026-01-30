# Ex-4 Rail-Fence-Program

# IMPLEMENTATION OF RAIL FENCE – ROW & COLUMN TRANSFORMATION TECHNIQUE

# AIM:

# To write a C program to implement the rail fence transposition technique.

# DESCRIPTION:

In the rail fence cipher, the plain text is written downwards and diagonally on successive "rails" of an imaginary fence, then moving up when we reach the bottom rail. When we reach the top rail, the message is written downwards again until the whole plaintext is written out. The message is then read off in rows.

# ALGORITHM:

STEP-1: Read the Plain text.
STEP-2: Arrange the plain text in row columnar matrix format.
STEP-3: Now read the keyword depending on the number of columns of the plain text.
STEP-4: Arrange the characters of the keyword in sorted order and the corresponding columns of the plain text.
STEP-5: Read the characters row wise or column wise in the former order to get the cipher text.

# PROGRAM
```
#include <stdio.h> 
#include <string.h> 
#include <stdlib.h> 
void encryptRailFence(char str[], int rails, char encrypted[]) { 
int i, j, len, count, code[100][1000]; 
len = strlen(str); 
// Initialize the code array to 0 
for (i = 0; i < rails; i++) { 
for (j = 0; j < len; j++) { 
code[i][j] = 0; 
} 
} 
count = 0; 
j = 0; 
while (j < len) { 
if (count % 2 == 0) { // Moving down the rails 
for (i = 0; i < rails && j < len; i++) { 
code[i][j] = (int)str[j]; 
j++; 
} 
} else { // Moving up the rails 
for (i = rails - 2; i > 0 && j < len; i--) { 
code[i][j] = (int)str[j]; 
j++; 
} 
} 
count++; 
} 
int pos = 0; 
for (i = 0; i < rails; i++) { 
for (j = 0; j < len; j++) { 
if (code[i][j] != 0) { 
encrypted[pos++] = code[i][j]; 
} 
} 
} 
encrypted[pos] = '\0';  
} 
void decryptRailFence(char str[], int rails, char decrypted[]) { 
int i, j, len, count, code[100][1000], pos = 0; 
len = strlen(str); 
// Initialize the code array to 0 
for (i = 0; i < rails; i++) { 
for (j = 0; j < len; j++) { 
code[i][j] = 0; 
} 
} 
count = 0; 
j = 0; 
while (j < len) { 
if (count % 2 == 0) {  
for (i = 0; i < rails && j < len; i++) { 
code[i][j] = 1; 
j++; 
} 
} else {  
for (i = rails - 2; i > 0 && j < len; i--) { 
code[i][j] = 1; 
j++; 
} 
} 
count++; 
} 
for (i = 0; i < rails; i++) { 
for (j = 0; j < len; j++) { 
if (code[i][j] == 1) { 
code[i][j] = str[pos++]; 
} 
} 
} 
pos = 0; 
count = 0; 
j = 0; 
while (j < len) { 
if (count % 2 == 0) { // Moving down the rails 
for (i = 0; i < rails && j < len; i++) { 
if (code[i][j] != 0) { 
decrypted[pos++] = code[i][j]; 
} 
j++; 
} 
} else { // Moving up the rails 
for (i = rails - 2; i > 0 && j < len; i--) { 
if (code[i][j] != 0) { 
decrypted[pos++] = code[i][j]; 
} 
j++; 
} 
} 
count++; 
} 
decrypted[pos] = '\0';  
} 
int main() { 
char str[1000], encrypted[1000], decrypted[1000]; 
int rails; 
printf("Simulating Rail Fence Cipher\n"); 
printf("Enter a Secret Message: "); 
fgets(str, sizeof(str), stdin); 
str[strcspn(str, "\n")] = 0;  
printf("Enter number of rails: "); 
scanf("%d", &rails); 
encryptRailFence(str, rails, encrypted); 
printf("Encrypted Message: %s\n", encrypted); 
decryptRailFence(encrypted, rails, decrypted); 
printf("Decrypted Message: %s\n", decrypted); 
return 0; 
}
```

# OUTPUT



<img width="1752" height="843" alt="Screenshot 2026-01-30 144357" src="https://github.com/user-attachments/assets/7aeeec06-26c0-4ab9-be36-9eb7f704754e" />



<img width="1716" height="868" alt="Screenshot 2026-01-30 144408" src="https://github.com/user-attachments/assets/f6fd656d-897a-4935-979d-32a9ea79b9e2" />



<img width="1652" height="887" alt="Screenshot 2026-01-30 144417" src="https://github.com/user-attachments/assets/9e198850-dbac-4238-b5f1-8cb793163eed" />



<img width="1656" height="841" alt="Screenshot 2026-01-30 144426" src="https://github.com/user-attachments/assets/7896dc8e-2891-45cf-bcb4-b6a747f1dff4" />


# RESULT
Thus the program executed successfully.
