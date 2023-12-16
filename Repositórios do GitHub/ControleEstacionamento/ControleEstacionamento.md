#include <stdio.h>
#include <locale.h>//Brazilian Portuguese
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
        y=0;}