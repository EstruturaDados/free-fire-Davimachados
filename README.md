#include <stdio.h>
#include <string.h>
#include <stdlib.h>

typedef struct {
    char nome[50];
    char tipo[30];
    int quantidade;
} Item;

#define CAPACIDADE_MAXIMA 10

void exibirMenu();
void adicionarItem(Item inventario[], int *totalItens);
void removerItem(Item inventario[], int *totalItens);
void listarItens(const Item inventario[], int totalItens);
void limparBuffer();

int main() {
    Item mochila[CAPACIDADE_MAXIMA];
    int totalItens = 0;
    int opcao;

    printf("🎒 Desafio Código da Ilha - Nível Novato\n");
    printf("Sistema de Inventário Básico (Capacidade: %d itens)\n", CAPACIDADE_MAXIMA);

    do {
        exibirMenu();
        printf("Escolha uma opção: ");
        
        if (scanf("%d", &opcao) != 1) {
            opcao = -1;
            limparBuffer();
        }

        switch (opcao) {
            case 1:
                adicionarItem(mochila, &totalItens);
                break;
            case 2:
                removerItem(mochila, &totalItens);
                break;
            case 3:
                listarItens(mochila, totalItens);
                break;
            case 0:
                printf("\nSobrevivente, você está fora de perigo. O programa será encerrado.\n");
                break;
            default:
                printf("\nOpção inválida. Tente novamente.\n");
        }
    } while (opcao != 0);

    return 0;
}

void exibirMenu() {
    printf("\n--- MOCHILA VIRTUAL ---\n");
    printf("1. Adicionar Item\n");
    printf("2. Remover Item (pelo nome)\n");
    printf("3. Listar Itens\n");
    printf("0. Sair\n");
    printf("-------------------------\n");
}

void limparBuffer() {
    int c;
    while ((c = getchar()) != '\n' && c != EOF);
}

void adicionarItem(Item inventario[], int *totalItens) {
    if (*totalItens >= CAPACIDADE_MAXIMA) {
        printf("\n⚠️ ERRO: A mochila está cheia! Remova itens para adicionar mais.\n
> Equipe de Ensino – MateCheck
