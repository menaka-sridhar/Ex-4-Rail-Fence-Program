# Ex-4 Rail-Fence-Program

# IMPLEMENTATION OF RAIL FENCE – ROW & COLUMN TRANSFORMATION TECHNIQUE

# AIM:
To write a C program to implement the rail fence transposition technique.

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

int main()
{
    char text[100];
    char rail[10][100];
    int len, key;
    int i, j;
    int row = 0, dir = 1;

    printf("Enter the plaintext: ");
    scanf("%s", text);

    printf("Enter the number of rails: ");
    scanf("%d", &key);

    len = strlen(text);

    // Initialize rail matrix
    for(i = 0; i < key; i++)
        for(j = 0; j < len; j++)
            rail[i][j] = '\n';

    // Fill zigzag pattern
    for(i = 0; i < len; i++)
    {
        rail[row][i] = text[i];

        if(row == 0)
            dir = 1;
        else if(row == key - 1)
            dir = -1;

        row = row + dir;
    }

    printf("\nEncrypted Text: ");

    // Read row by row
    for(i = 0; i < key; i++)
    {
        for(j = 0; j < len; j++)
        {
            if(rail[i][j] != '\n')
                printf("%c", rail[i][j]);
        }
    }

    printf("\n");

    return 0;
}
```

# OUTPUT
<img width="408" height="150" alt="image" src="https://github.com/user-attachments/assets/2de241ca-68d7-475b-a49e-6ab4898a1d9e" />

# RESULT
Thus, successfully write a C program to implemented the rail fence transposition technique.
