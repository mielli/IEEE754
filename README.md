#include <stdio.h>
#include <math.h>
int sinal, expoente[15]={0}, mantissa[64]={0};
float numero;
//expoente32 = 8  || mantissa32 = 23
//expoente64 = 11 || mantissa64 = 52

void main(){
  printf("Insira o numero a ser convertido no padrão IEEE754: ");
  scanf("%f", &numero);
  int inteiro;
  float decimal;
    if(numero < 0)
    sinal = 1;
    else
    sinal = 0;

      if(numero < 0)
        numero *= -1;

      inteiro = numero;
      decimal = numero-inteiro;

        printf("inteiro: %d\n", inteiro);
        printf("decimal: %f\n", decimal);

        int i, j, contI=0, contJ=0;
        int inteiroA, inteiroB;
        inteiroA = inteiro;

        do{
          printf("inteiro: %d // inteiro%%2: %d // i: %d\n", inteiroA, inteiroA%2, contI);
            if(inteiroA % 2 == 0)
              mantissa[contI] = 0;
            else if(inteiroA % 2 == 1)
              mantissa[contI] = 1;
              inteiroA = inteiroA/2;
                contI++;
        }while(inteiroA>=1);

            int aux=0, aux2=0;

          for(j=0; j<=contI; j++){
            aux=mantissa[j];
            mantissa[j]=mantissa[aux2];
            mantissa[aux2]=aux;
            aux2++;
          }

        printf("\tinteiro: %d, i: %d\n", inteiroA, contI);

                    printf("\n\n");
        printf("\n\t==============32 bits==============\n");

              int help;
              printf("%d|   ", sinal);

              for(i=0; i<8; i++)
                printf("%d|", expoente[i]);
                printf("   ");

          for(i=0; i<contI; i++)
            printf("%d|", mantissa[i]);

              printf(",");

          for(help=23; help>contI; help--)
            printf("%d|", mantissa[help]);


                  printf("\n\n");

                printf("\n\t==============64 bits==============\n");
                  printf("%d|   ", sinal);

                  for(i=0; i<11; i++)
                    printf("%d|", expoente[i]);
                    printf("   ");

                  for(i=0; i<contI; i++)
                  printf("%d|", mantissa[i]);

                  printf(",");


                for(help=52; help>contI; help--)
                  printf("%d|", mantissa[help]);


                              printf("\n\n");

                      printf("\n\t==============80 bits==============\n");
                      printf("%d|   ", sinal);

                        for(i=0; i<15; i++)
                          printf("%d|", expoente[i]);
                          printf("   ");

                      for(i=0; i<contI; i++)
                        printf("%d|", mantissa[i]);

                        printf(",");

                      for(help=63; help>contI; help--)
                        printf("%d|", mantissa[help]);



printf("\n\n");
}
