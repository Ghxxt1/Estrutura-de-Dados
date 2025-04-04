##1 Introdução às Listas Dinâmicas
Listas Estáticas vs. Dinâmicas:
•	Estáticas (Arrays): Tamanho fixo, dificultando a adaptação a mudanças no número de elementos.
•	Dinâmicas: Tamanho flexível, com alocação e liberação de memória conforme necessário.
Vantagens e Desvantagens:
•	Vantagens: Flexibilidade e eficiência no uso de memória.
•	Desvantagens: Maior complexidade e custo para gerenciar ponteiros e memória.
2 Estrutura de uma Lista Dinâmica
A lista dinâmica é formada por nós, onde cada nó contém:
•	Dado: O valor armazenado.
•	Ponteiro: Aponta para o próximo nó, criando o encadeamento.
Representação típica de um nó:
struct No {
    int dado;
    struct No* proximo;
};
3 Operações Básicas
Criação e Inicialização: Uma lista começa com um ponteiro NULL, indicando que está vazia.
struct No* lista = NULL;  // Lista vazia
Inserção: A inserção no início da lista envolve a alocação de memória para um novo nó e a atualização do ponteiro da lista.
void inserir_inicio(struct No** lista, int valor) {
    struct No* novo = (struct No*) malloc(sizeof(struct No));
    novo->dado = valor;
    novo->proximo = *lista;
    *lista = novo;
}
Remoção: A remoção do início da lista envolve a atualização do ponteiro da lista para o próximo nó e a liberação da memória do nó removido.
void remover_inicio(struct No** lista) {
    if (*lista != NULL) {
        struct No* temp = *lista;
        *lista = (*lista)->proximo;
        free(temp);
    }
}
4 Implementação em C
Exemplo simples de implementação de uma lista dinâmica com inserção e remoção:
#include <stdio.h>
#include <stdlib.h>

struct No {
    int dado;
    struct No* proximo;
};

void inserir_inicio(struct No** lista, int valor) {
    struct No* novo = (struct No*) malloc(sizeof(struct No));
    novo->dado = valor;
    novo->proximo = *lista;
    *lista = novo;
}

void remover_inicio(struct No** lista) {
    if (*lista != NULL) {
        struct No* temp = *lista;
        *lista = (*lista)->proximo;
        free(temp);
    }
}

void imprimir_lista(struct No* lista) {
    struct No* temp = lista;
    while (temp != NULL) {
        printf("%d -> ", temp->dado);
        temp = temp->proximo;
    }
    printf("NULL\n");
}

int main() {
    struct No* lista = NULL;
    inserir_inicio(&lista, 10);
    inserir_inicio(&lista, 20);
    imprimir_lista(lista);
    remover_inicio(&lista);
    imprimir_lista(lista);
    return 0;
}
5 Referências: Livro: Victorine Viviane Mizrahi, Treinamento em Linguagem C.
