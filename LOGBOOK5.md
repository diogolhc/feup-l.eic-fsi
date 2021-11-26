# Trabalho realizado na Semana #5

## Tarefa 1
Como era de esperar, se não se tornasse o executável em *Set-UID*, a *shell*
aberta não tinha permissões de *root*:  
![/imgs5/shell_seed.png](/imgs5/shell_seed.png)  

Mesmo o executável sendo *root-owned* e *Set-UID*, caso não fosse compilado com a flag *execstack*, que dá
permissões para executar código da stack, acontence um *Segmentation fault*:  
![/imgs5/shell_segfault.png](/imgs5/shell_segfault.png)  

Com *execstack* e sendo o programa *Set-UID root-owned* a *shell* aberta tem permissões de *root*:  
![/imgs5/shell_root.png](/imgs5/shell_root.png)  

Não foram detetadas diferenças entre as versões de 32 e 64 *bits*.  


## Tarefa 2
Foi apresentado o código vulnerável e procedeu-se à sua compilação.  
Bastou executar:
```sh
make
```
Contudo, sem esquecer que a compilação teve que ser feita com as
flags
```
-z execstack -fno-stack-protector
```
de modo a ser possível executar código na *stack*, o *shellcode* que vamos injetar, e
não serem feitas verificações adicionais que impedem este tipo de ataques.  


O código apresentado tem uma vulnerabilidade de *buffer overflow* dado
que, copia um máximo de 517 *bytes* para um *buffer* de 100 *bytes*.  

De um modo geral, a *stack* do programa, quando estiver a executar a função *bof*,
terá um aspeto semelhante ao da figura abaixo:

![/imgs5/stack.png](/imgs5/stack.png)

Assim sendo, e dado que a vulnerabilidade do programa permite escrever
até 517 *bytes* para o buffer que só tem 100, os restantes 417 vão ser escritos
a partir de *buffer[100]*, ou seja, será possível substituir o conteúdo
do endereço de retorno e fazer com que, quando a função *bof* retornar, ela
o faça para o *shellcode* que pretendemos injetar.

## Tarefa 3

Para fazer o exploit, foi dado um *script* em python, *exploit.py*, que gera o *badfile*.  
Contudo, há várias informações que estão em falta e é preciso adicionar.  

Primeiramente, foi necessário o *shellcode* que vamos injetar. Para isso,
usámos o shellcode fornecido na tarefa 1 para a versão de 32 *bits* e que abre
uma *shell*:
```c
"\x31\xc0\x50\x68\x2f\x2f\x73\x68\x68\x2f"
"\x62\x69\x6e\x89\xe3\x50\x53\x89\xe1\x31"
"\xd2\x31\xc0\xb0\x0b\xcd\x80"
```

As variáveis que são necessárias fixar são então:  
1. Zona onde colocar o *shellcode*
2. Endereço de memória da zona onde vai ficar o *shellcode*
3. Diferença entre o endereço de retorno que se pretende dar *overwrite* e o início do *buffer*

Quanto ao ponto `1`, decidimos colocar o *shellcode* logo no início do buffer. Assim sendo:
```py
start = 0
```

Quanto ao ponto `2`, uma vez que temos acesso ao *source code*, inserimos um *printf()* do buffer
de modo a obter o seu endereço dentro da função *bof*:
```c
int bof(char *str) {
    char buffer[BUF_SIZE];
    printf("buffer pointer: %p\n", buffer);
    // The following statement has a buffer overflow problem 
    strcpy(buffer, str);
    return 1;
}
```

Ao executar o programa obtivemos então o valor `0xffffcadc`:  
![/imgs5/buffer_pointer.png](/imgs5/buffer_pointer.png)

Logo,
```py
ret = 0xffffcadc
```
Dado que é o endereço do *buffer* e estamos a colocar o *shellcode* no seu início.

Quanto ao ponto `3`, como sugerido no enunciado, recorremos ao *gdb*:  
![/imgs5/gdb_stack_l1_dbg.png](/imgs5/gdb_stack_l1_dbg.png)

De seguida, criámos um breakpoint na função *bof*:  
![/imgs5/b_bof_run.png](/imgs5/b_bof_run.png)

Após isso, corremos *next* de modo a entrar no contexto da função *bof*:  
![/imgs5/next.png](/imgs5/next.png)

Finalmente, obtivémos o endereço do *ebp* e do *buffer* para calcular a sua diferença:  
![/imgs5/ebp_buffer_diff.png](/imgs5/ebp_buffer_diff.png)

(Nota: o endereço do *buffer* aqui obtido não pode ser usado para fazer *exploit* ao
executável `stack-L1` devido a elementos extra que o executável de debug adiciona
à stack e que faz com que os endereços sejam diferentes.)

Deste modo, o *ebp* está 108 *bytes* acima de `buffer[0]`. Assim, e dado que o
endereço de retorno se encontra imediatamente acima do *ebp* basta adicionar 4 (versão de 32 *bits*) ao 108,
completando assim o *exploit.py*:
```py
offset = 112
```

Com o script de python completo, bastou executá-lo para gerar o *badfile*:
```sh
python3 exploit.py
```

e executar o programa, `stack-L1`, para por a prova o exploit:  
![/imgs5/exploit_root_access.png](/imgs5/exploit_root_access.png)

Como se pode confirmar, foi assim obtida a *shell* com permissõe de *root*.

## CTF
