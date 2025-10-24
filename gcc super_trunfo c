#include <stdio.h>
#include <string.h>
#include <ctype.h>

#define MAX_CIDADE 50
#define MAX_CODIGO 5

// Estrutura para representar uma carta do Super Trunfo
struct Carta {
    char estado;
    char codigo[MAX_CODIGO];
    char cidade[MAX_CIDADE];
    int populacao;
    float area;
    float pib;
    int pontos_turisticos;
};

// Função para limpar o buffer de entrada
void limparBuffer() {
    int c;
    while ((c = getchar()) != '\n' && c != EOF);
}

// Função para validar o estado (A-H)
int validarEstado(char estado) {
    estado = toupper(estado);
    return (estado >= 'A' && estado <= 'H');
}

// Função para validar o código da carta
int validarCodigo(char codigo[], char estado) {
    if (strlen(codigo) != 3) return 0;
    
    // Verifica se a primeira letra é o estado correto
    if (toupper(codigo[0]) != toupper(estado)) return 0;
    
    // Verifica se os dois últimos caracteres são dígitos
    if (!isdigit(codigo[1]) || !isdigit(codigo[2])) return 0;
    
    // Converte os dígitos para número e verifica se está entre 01-04
    int numero = (codigo[1] - '0') * 10 + (codigo[2] - '0');
    return (numero >= 1 && numero <= 4);
}

// Função para ler uma carta do usuário
void lerCarta(struct Carta *carta, int numero_carta) {
    printf("\n=== DADOS DA CARTA %d ===\n", numero_carta);
    
    // Ler estado
    do {
        printf("Estado (A-H): ");
        scanf(" %c", &carta->estado);
        limparBuffer();
        
        if (!validarEstado(carta->estado)) {
            printf("Estado inválido! Digite uma letra de A a H.\n");
        }
    } while (!validarEstado(carta->estado));
    
    // Converter estado para maiúsculo
    carta->estado = toupper(carta->estado);
    
    // Ler código da carta
    do {
        printf("Código da Carta (ex: %c01): ", carta->estado);
        scanf("%3s", carta->codigo);
        limparBuffer();
        
        if (!validarCodigo(carta->codigo, carta->estado)) {
            printf("Código inválido! Use o formato: %c seguido de 01-04 (ex: %c02).\n", 
                   carta->estado, carta->estado);
        }
    } while (!validarCodigo(carta->codigo, carta->estado));
    
    // Ler nome da cidade
    printf("Nome da Cidade: ");
    fgets(carta->cidade, MAX_CIDADE, stdin);
    carta->cidade[strcspn(carta->cidade, "\n")] = '\0'; // Remove o \n
    
    // Ler população
    printf("População: ");
    scanf("%d", &carta->populacao);
    
    // Ler área
    printf("Área (em km²): ");
    scanf("%f", &carta->area);
    
    // Ler PIB
    printf("PIB: ");
    scanf("%f", &carta->pib);
    
    // Ler número de pontos turísticos
    printf("Número de Pontos Turísticos: ");
    scanf("%d", &carta->pontos_turisticos);
    
    limparBuffer(); // Limpar buffer após o último scanf
}

// Função para exibir uma carta
void exibirCarta(struct Carta *carta, int numero_carta) {
    printf("\n=== CARTA %d ===\n", numero_carta);
    printf("Estado: %c\n", carta->estado);
    printf("Código: %s\n", carta->codigo);
    printf("Cidade: %s\n", carta->cidade);
    printf("População: %d habitantes\n", carta->populacao);
    printf("Área: %.2f km²\n", carta->area);
    printf("PIB: %.2f\n", carta->pib);
    printf("Pontos Turísticos: %d\n", carta->pontos_turisticos);
}

int main() {
    struct Carta carta1, carta2;
    
    printf("=== SUPER TRUNFO - CADASTRO DE CARTAS ===\n");
    
    // Ler os dados das duas cartas
    lerCarta(&carta1, 1);
    lerCarta(&carta2, 2);
    
    // Exibir as cartas cadastradas
    printf("\n=== CARTAS CADASTRADAS ===\n");
    exibirCarta(&carta1, 1);
    exibirCarta(&carta2, 2);
    
    printf("\nCadastro concluído! As cartas estão prontas para o jogo.\n");
    
    return 0;
}
