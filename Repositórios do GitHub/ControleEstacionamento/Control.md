#include <stdio.h>
#include <locale.h>
#include "Carros.h"
//Desenvolvido por João Paulo Ferreira e Augusto Gaspar Batista de Oliveira
struct motorista {
    char placa[10];
    int t;
};
int main() {
    int w, v = 0, h = 1, g = 20, y=0, x;
    FILE *f;
    char linha[100];
    struct motorista m;

    setlocale(LC_ALL, "portuguese");
   do{
        printf("\nTudo bem?\nBem vindo ao estacionamento Charles The Theacher, o melhor do Vale. Desejamos que sua estadia seja das melhores.\nSelecione a opção adequada:\nPara adentrar em uma vaga, digite 1.\nPara sair, digite 2.\nPara receber relatório de entrada digite 3.\nPara relatório de saída digite 4.\nPara saber a quantidade de vagas disponíveis digite 5.\nO sistema foi reiniciado? Caso precise preencher o número de vagas pressione 6.\n\t");
    scanf("%d", &w);
    if (w == 1) {
        do{
        printf("\nNosso preço por estadia é dado em hora, R$ 1.00.\nDigite a placa do carro:");
        scanf("%s", m.placa);
        printf("\nPor favor, o tempo de permanência.\n\t");
        scanf("%d", &m.t);
        v = valor(h, m.t);
        printf("\nObrigado, boa estadia.\n\t");
        f = fopen("Relatório de Entrada.txt", "a");
        fprintf(f, "\n\nCharles The Theacher Estacionamentos, a melhor do Vale.\nPlaca: %s", m.placa);
        fprintf(f, "\nTempo de permanência previsto, em horas: %d", m.t);
        fclose(f);
        g = g - 1;
        printf("\nVagas disponíveis: %d", g);
        printf("\nPretende continuar operação de entrada de vagas?\nSe sim, digite 1.\nSe não, digite 2.");
        scanf("%d",&y);
        }while (y<2);
        m.t=0;
    }
    if (w == 2) {
        y=0;
        do{printf("\nObrigado pela preferência.Por favor, digite a placa:");
        scanf("%s", m.placa);
        printf("\nDigite o tempo de permanência real:\n");
        scanf("%d",& m.t);
        v=valor(h, m.t);
        printf("\nValor a ser pago R$:%d", v);

        f=fopen("Relatório de saída.txt","a");
        fprintf(f,"\nEstacionamento Charles The Teacher, o melhor do vale.\nPlaca do Carro: %s", m.placa);
        fprintf(f,"\nTempo real de permanência em horas: %d", m.t);
        fprintf(f,"\nValor a ser pago R$: %d",v);
        fprintf(f,"\nObrigado, volte sempre.");
        fclose(f);
        g = g+1;
         if(g>20){
            g=20;
         }
        printf("\nDeseja continuar com as saídas do estacionamento?\nSe sim, digite 1.\nSe não, digite 2.\n\t");
        scanf("%d",&y);

        }while(y<2);
    }
    if ( w == 3){
        f=fopen("Relatório de Entrada.txt","r");
        if(f == NULL){
            printf("\nArquivo inexistente");
        }
        while(fgets(linha, sizeof(linha),f)!=NULL){
            printf("%s",linha);
        }
    }
    if ( w== 4){
        f=fopen("Relatório de saída.txt","r");
        if(f == NULL){
            printf("\nArquivo inexistente");
        }
        while(fgets(linha, sizeof(linha),f)!=NULL){
            printf("%s",linha);
        }
    }
    if ( w == 5){
        printf("Vagas disponíveis em nosso estacionamento: %d", g);
    }
    if ( w == 6 ){
        printf("\nDigite a quantidade de vagas ocupadas, por favor.\n\t");
        scanf("%d",&x);
        g=g-x;
        if(g>=20){
            g=20;
        }
    }
    y=0;
    printf("\nContinuar operação do sistema de gerenciamento do estacionamento?\nSe sim, digite 1.\nSe não, digite 2.\n\t");
    scanf("%d",&y);
   }while(y<2);

    return (0);
}
