# Fila Estática em C
Neste tópico, será falado sobre o que é uma fila estática e apresentaremos um exemplo de código completo e totalmente funcional na linguagem de programação C.

# O que é uma Fila Estática?

As filas (queue, em inglês) são um tipo de estrutura de dados onde os elementos estão arranjados em lista que obedece as seguintes regras:
- Ao inserir um elemento, ele vai para a última posição da estrutura;
- Ao retirar um elemento, é tirado o primeiro elemento da estrutura.

Este tipo de estrutura de dados é dita FIFO (First in, first out), ou seja, o primeiro elemento a entrar na estrutura é o primeiro a sair.

Por exemplo, uma fila de um banco, onde possui uma fila para efetuar pagamento de boleto em um caixa. Suponhamos que a fila do caixa possui 5 pessoas, consequentemente se uma outra pessoa deseja entrar nessa fila, ela será a sexta da fila, ou seja, ela estará na última posição da estrutura. A primeira pessoa desta fila será atendida e irá se retirar, ou seja, irá retirar o primeiro elemento da estrutura. E assim subsequentemente até não possui mais ninguém na fila.

Ou seja, sempre que inserimos elementos nessa fila, inserimos ao final. E sempre que retiramos, estamos retirando o primeiro elemento da fila (o mais antigo), pois o que está na frente que vai sair antes.

Em outras palavras, inserimos ao fim, e retiramos do começo.

# Como programar uma Fila em C
Ok. Como já sabemos o que é uma fila e como funciona, iremos implementar um FIFO na liguagem C partindo do início.

Definição das Variáveis Globais:
- int array[MAX]: Tamanho máximo da fila;
- inicio: Inicializada com o valor 0, ela define em qual posição do vetor é o primeiro valor a ser removido da fila.
- final: Inicializada com o valor 0, ela define em qual posição do vetor é o último valor, para que o proximo valor a inserido na fila esteja na última posição do array.

A função inserir(), irá receber um parâmetro do tipo inteiro (int) que será alocado no final da fila. Caso a fila estiver cheia o parâmetro recebido não será inserido.

Função listar(), irá listar os valores em ordem de inserção, caso o início e o final da fila tem o mesmo valor a fila está.

A função remover(), irá remover o primeiro elemento da fila, caso o início e o final da fila tem o mesmo valor a fila está.

<pre>
<code>
#include<stdio.h>
#include<stdlib.h>
#define MAX 10
 
int array[MAX];
int inicio = 0;
int fim = 0;
 
void inserir(int elemento)
{
    if((fim+1)%MAX==inicio)
    {
        printf("Erro ao inserir\nFila cheia!!\n\n");
        system("pause");
    }
    else
    {
        array[fim]=elemento;
        fim=(fim+1)%MAX;
    }
}
void listar()
{
    int i=inicio;
    if(inicio==fim)
    {
        printf("Fila vazia.\n\n");
        system("pause");
    }
    else
    {
        while(i!=fim)
        {
            if(i+1==fim)
            {
                printf("%d",array[i]);
            }
            else
            {
                printf("%d - ",array[i]);
            }
            i=(i+1)%MAX;
        }
        printf("\n");
        system("pause");
    }
}
 
int remover()
{
    int resp;
    if(inicio==fim)
    {
        printf("Erro ao remover\nFila vazia\n\n");
        system("pause");
    }
    else
    {
        resp=array[inicio];
        inicio=(inicio+1)%MAX;
    }
}
 
void msn()
{
    printf("\t\tBem vindo ao programa Fila!!\n\n");
    printf("1: Inserir.\n");
    printf("2: Remover.\n");
    printf("3: Listar.\n");
    printf("4: Sair.\n\n");
    printf("Digite a opcao desejada: ");
}
 
void Menu()
{
    int op, n;
 
        system("cls");
        msn();
        scanf("%d",&op);
 
        if(op==1)
        {
            printf("Digite o elemento que deseja inserir: ");
            scanf("%d",&n);
            inserir(n);
            printf("Elemento inserido com sucesso\n");
            system("pause");
            Menu();
        }
        else if(op==2)
        {
            remover();
            printf("Elemento removido com sucesso\n\n");
            system("pause");
            Menu();
        }
        else if(op==3)
        {
            listar();
            printf("Precione qualquer tecla para continuar usando o programa.\n");
            system("pause");
            Menu();
        }
        else if(op==4)
        {
            printf("Obrigador por usar nosso programa.\n");
            system("pause");
            return 0;
        }
        else
        {
            printf("Digite a tecla 'serta'\n");
            system("pause");
            Menu();
        }
}
 
int main(int argc,char**argv)
{
    Menu();
 
    system("pause");
    return 0;
}
</code>
</pre>

O código acima, é apenas um exemplo prático de fila estática na linguagem de programação C. Este código pode ser melhorado ainda mais, uma vez que a função <i>Menu();</i> está chamando ela a todo instante. Vemos então que está tendo uma recursão e consumindo memória, a memória só é liberada quando o aplicação é encerrada.
