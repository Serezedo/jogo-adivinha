#include <stdio.h>
#include <stdlib.h>
#include <time.h>
#include <locale.h>


int main() {

    setlocale(LC_ALL,"Portuguese");
    char dificuldade;
    int numero, tentativa, a;
    int maxTentativas, limite;
    int estatisticas;

    // Semente o gerador de números aleatórios uma vez
    srand(time(NULL));

    // Selecionar nível de dificuldade
    printf("JOGO DE ADIVINHA\n");

do {  // Loop para permitir que o usuário jogar novamente
    do { // Loop para garantir que o usuário insira uma dificuldade válida
        printf("Consulta estatisticas: - imprime 1 \n");
        printf("Iniciar jogo: - imprime qualquer outro número: \n");
        scanf("%i", &estatisticas);
        if (estatisticas != 1) {

            printf("Cada dificuldade tem um número máximo de tentativas.\n");
            printf("Fácil: 5 tentativas, número entre 1 e 10.\n");
            printf("Médio: 7 tentativas, número entre 1 e 50.\n");
            printf("Difícil: 10 tentativas, número entre 1 e 100.\n");



            printf("Escolha a dificuldade:\nfácil - f;\nmédio - m;\ndifícil - d: ");
            scanf(" %c", &dificuldade); // Use " %c" para ignorar quaisquer caracteres de nova linha deixados no buffer de entrada
        }
        else {
            printf("O número total de jogos jogados: \n");
            printf("A média do número tentativas utilizadas em todos os jogos, distribuída por níveis de dificuldade distribuídas pelos níveis de dificuldade: \n");
            printf("O número mínimo e máximo de tentativas usadas para acertar no número secreto: \n");

        }
    } while(dificuldade != 'f' && dificuldade != 'F' &&
              dificuldade != 'm' && dificuldade != 'M' &&
              dificuldade != 'd' && dificuldade != 'D');

    // Definir parâmetros do nível de dificuldade
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
} while (maxTentativas == 0);

    // Gerar número aleatório com base na dificuldade
    int numAleatorio = (rand() % limite) + 1;

        // Solicitar palpite do usuário
        printf("Adivinhe o número entre 1 e %i\n", limite);
    for (tentativa = 1; tentativa <= maxTentativas; tentativa++) {
        printf("Tentativa %i de %i: ", tentativa, maxTentativas);
        scanf("%i", &a);

        if (a == numAleatorio) {
            printf("CERTO! Adivinhaste o número correto! \n");
            return 0; // Terminar o programa se adivinhado corretamente
        } else if (a < numAleatorio) {
            printf("O número é maior.\n");
        } else {
            printf("O número é menor.\n");
        }
    }

    // Se o usuário esgotar as tentativas sem adivinhar corretamente
    printf("Esgotou as suas tentativas! O número era: %i.\n", numAleatorio);

    return 0;
}
