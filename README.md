# exercicio-seguro-c
#include <stdio.h>
#include <stdlib.h>
#include <math.h>

int main()
{
    int tipoVeiculo, tipoSeguro, idade, eixos;
    float valorBase = 0, adicionalCat = 0, adicionalIdade = 0, custoCobertura = 0, valorTotal = 0;
    printf("--- SISTEMA DE CALCULO DE SEGURO ---");
    do {
         printf("Selecione o tipo do veiculo:\n");
    printf("1. Passeio\n 2. Carga pesada\n 3.Caminhonete\n 4. Motocicleta  (<1000cc)\n 5. Motocicleta (1000cc+)\n");
    if (scanf("%d", &tipoVeiculo)){
        while (getchar()!= '\n'); //limpar o erro se o usuario
    }
    if(tipoVeiculo <1 || tipoVeiculo > 5 ){
        printf("[ERRO] Opcao invalida! Tente novamente.\n");
    }
    }while (tipoVeiculo <1 || tipoVeiculo > 5 );

    if (tipoVeiculo >=4){
        valorBase = 1200.00;
        if (tipoVeiculo ==4) adicionalCat = valorBase * 0.80;
        else adicionalCat = valorBase * 0.90;
    } else{
    valorBase = 1000.00;
    if (tipoVeiculo == 1) adicionalCat = valorBase * 0.10;
        else if (tipoVeiculo == 2) adicionalCat = valorBase * 0.20;
        else adicionalCat = valorBase * 0.33;
    }

    //Perfil do Motorista
    do {
    printf("Digite sua idade.\n");
   if (scanf("%d", &idade)){
        while (getchar()!= '\n'); //limpar o erro se o usuario
    }
    if(idade <18){
        printf("[ERRO] Opcao invalida! Tente novamente.\n");
    }
    }while (idade<18);

    if (idade >=30){
        adicionalIdade = valorBase * 0.05;
    } else{
    if (idade <=29 ) adicionalIdade = valorBase * 0.10;
        else if (idade <= 25) adicionalIdade = valorBase * 0.15;
    }

    //Tipo de plano
        do {
    printf("Selecione seu tipo de plano\n");
    printf("1. Basico\n 2. Parcial\n 3. Completo\n");

   if (scanf("%d", &tipoSeguro)){
        while (getchar()!= '\n'); //limpar o erro se o usuario
    }
    if(tipoSeguro <1 || tipoSeguro > 3 ){
        printf("[ERRO] Opcao invalida! Tente novamente.\n");
    }
    }while (tipoSeguro <1 || tipoSeguro > 3 );

    //Pesados
    if(tipoVeiculo== 2 || tipoVeiculo==3){
       printf("Quantidade de eixos\n");
       scanf("%d",&eixos);
       if(tipoSeguro==1) custoCobertura = (valorBase*0.03) * eixos;
       else if (tipoSeguro==2) custoCobertura = (valorBase*0.05) * eixos;
       else custoCobertura= (valorBase * 0.10) * eixos;
    }
//Passeio
    else if (tipoVeiculo==1){
    if (tipoSeguro == 1) custoCobertura = (valorBase + adicionalCat + adicionalIdade)* (-0.02);
    else if (tipoSeguro == 2)custoCobertura = (valorBase + adicionalCat + adicionalIdade)* (0.02);
    else custoCobertura = (valorBase + adicionalCat + adicionalIdade)* (0.10);


    }//Motos
    else if (tipoVeiculo == 4 || tipoVeiculo == 5){

    if (tipoVeiculo == 4){   // moto até 1000cc

        if(tipoSeguro == 1)
            custoCobertura = (valorBase + adicionalCat + adicionalIdade) * (-0.05);
        else if (tipoSeguro == 2)
            custoCobertura = (valorBase + adicionalCat + adicionalIdade) * (0.15);
        else
            custoCobertura = (valorBase + adicionalCat + adicionalIdade) * (0.80);
    }

    else if(tipoVeiculo == 5){   // moto acima de 1000cc

        if(tipoSeguro == 1)
            custoCobertura = (valorBase + adicionalCat + adicionalIdade) * (0.10);
        else if(tipoSeguro == 2)
            custoCobertura = (valorBase + adicionalCat + adicionalIdade) * (0.20);
        else
            custoCobertura = (valorBase + adicionalCat + adicionalIdade) * (1.0);
    }
    }

    //Saida de dados
    valorTotal= valorBase + adicionalCat + adicionalIdade +custoCobertura;
    printf("\nValor Base: %.2f", valorBase);
printf("\nAdicional Categoria: %.2f", adicionalCat);
printf("\nAdicional Idade: %.2f", adicionalIdade);
printf("\nCusto do Plano: %.2f", custoCobertura);
printf("\nValor Total Final da Apolice: %.2f\n", valorTotal);




    return 0;
}
