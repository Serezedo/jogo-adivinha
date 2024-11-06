# jogo-adivinha
trabalho intro.programaçao
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int main(){
	char dificuldade;
	int numero;
	do {
       printf("escolha a dificuldade: \nfacil-f;\nmedio-m;\ndificil-d: ");
       scanf("%c", &dificuldade);
   } while(dificuldade != 'f' && dificuldade != 'F' &&
             dificuldade != 'm' && dificuldade != 'M' &&
             dificuldade != 'd' && dificuldade != 'D');


    switch(dificuldade) {
        case 'f':
        case 'F':{
            printf("escolha um numero entre 1 e 10\n");
            scanf("%i", &numero);

            srand(time(NULL));

            int numAleatorio100 = (rand() % (10-1+1))+1;
            printf("Número aleatório entre 1 e 10: %d\n", numAleatorio100);
            break;

        }
        case 'm':
        case 'M':{
            printf("escolha um numero entre 1 e 50\n");
            scanf("%i", &numero);

            srand(time(NULL));

            int numAleatorio100 = (rand() % (50-1+1))+1;
            printf("Número aleatório entre 1 e 50: %d\n", numAleatorio100);
            break;
        }
        case 'd':
        case 'D':{
            printf("escolha um numero entre 1 e 100\n");
            scanf("%i", &numero);

            srand(time(NULL));

            int numAleatorio100 = (rand() % (100-1+1))+1;
            printf("Número aleatório entre 1 e 100: %d\n", numAleatorio100);
            break;
        }


    }

}
