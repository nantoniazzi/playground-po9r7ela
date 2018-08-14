# Vamos Praticar?

Exercício 1
---
Dado o seguinte exemplo:
``` C
FILE *farq 
farq = fopen (“arqdata.dat", “wb");
```

?[A função fopen() abre um arquivo retornando o ponteiro associado ao arquivo, como no exemplo acima, que podemos afirmar ?] 
-[ ] a criação de um arquivo binário chamado arqdata.dat, em que poderão ser realizadas operações de leitura e de escrita. 
-[ ] a criação de um arquivo chamado farq, em que poderão ser realizadas somente as operações de leitura.
-[x] a criação de um arquivo binário chamado arqdata.dat em que poderão ser realizadas somente as operações de escrita.
-[ ] a criação de um arquivo chamado farq.dat, em que poderão ser realizadas operações de leitura. 


?[A função fopen() abre um arquivo retornando o ponteiro associado ao arquivo, como no exemplo acima, que podemos afirmar?]
-[ ] There is no answer to that!
-[ ] Sleep and eat
-[x] Easy, this is 42
-[ ] Peace & Love

Exercício 2
---

<p>Crie um programa C que:</p>
<p>(a) crie/abra um arquivo texto de nome "arq.txt",</p>
<p>(b) permita que o usuario entre com diversos caracteres nesse arquivo, até que o usuario entre com o caractere ’0’ (fim da entrada de dados),</p>
<p>(c) Feche o arquivo e abra novamente o arq.txt, e</p>
<p>(d) lendo-o caractere por caractere, e escrevendo na tela (printf) todos os caracteres armazenados.</p>


@[IDE]({"stubs": ["./www/exercicio"],"command": "sh /project/target/www/exercicio.sh"
})

::: Solução

``` C
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
int main()
{
    FILE *farq;
    char car;


farq = fopen("arq.txt", "w");
if (farq == NULL) {
 fprintf(stderr,"\nfopen() failed in file %s at line # %d", __FILE__,__LINE__);
 exit(EXIT_FAILURE);
}
printf("\nEntre com um caracter qualquer ou 0 para terminar:");
car = getchar();
fflush(stdin); // limpa o caracter enter do teclado
while (car != '0')
{
   fputc(car,farq);
   printf("\nEntre com um caracter qualquer ou 0 para terminar:");
   car = getchar();
   fflush(stdin); // limpa o caracter enter do teclado
}
fclose(farq);
farq = fopen("arq.txt", "r");
if (farq == NULL)
{
   fprintf(stderr,"\nfopen() failed in file %s at line # %d", __FILE__,__LINE__);
   exit(EXIT_FAILURE);
}
printf("\n\nVou ler e mostrar o texto gravado....\n\n");
car=fgetc(farq);
while (car!=EOF)
{
   printf("%c",car);
   car =fgetc(farq);
}

fclose(farq);

}
```
:::