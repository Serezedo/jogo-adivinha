#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int main() {
    char dificuldade;
    int numero, tentativa, a;
    int maxTentativas, limite;

    // Seed the random number generator once
    srand(time(NULL));

    // Select difficulty level
    do {
        printf("Escolha a dificuldade:\nfacil - f;\nmedio - m;\ndificil - d: ");
        scanf(" %c", &dificuldade); // Use " %c" to ignore any newline characters left in input buffer
    } while(dificuldade != 'f' && dificuldade != 'F' &&
              dificuldade != 'm' && dificuldade != 'M' &&
              dificuldade != 'd' && dificuldade != 'D');

    // Set difficulty level parameters
    switch(dificuldade) {
        case 'f':
        case 'F':
            maxTentativas = 5;
        limite = 10;
        break;
        case 'm':
        case 'M':
            maxTentativas = 7;
        limite = 50;
        break;
        case 'd':
        case 'D':
            maxTentativas = 10;
        limite = 100;
        break;
    }

    // Generate random number based on difficulty
    int numAleatorio = (rand() % limite) + 1;

    // Prompt user for guesses
    printf("Adivinhe o número entre 1 e %d\n", limite);
    for (tentativa = 1; tentativa <= maxTentativas; tentativa++) {
        printf("Tentativa %d de %d: ", tentativa, maxTentativas);
        scanf("%i", &a);

        if (a == numAleatorio) {
            printf("CERTO! Você adivinhou o número!\n");
            return 0; // End program if guessed correctly
        } else if (a < numAleatorio) {
            printf("O número é maior.\n");
        } else {
            printf("O número é menor.\n");
        }
    }

    // If user exhausts attempts without guessing correctly
    printf("Você esgotou suas tentativas! O número era %d.\n", numAleatorio);

    return 0;
}
