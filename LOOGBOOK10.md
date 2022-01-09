# Trabalho realizado na Semana #10

## Tarefa 1
Efetuou-se o *log in* na plataforma http://www.seed-server.com sob o perfil de Alice forncido. Para efetuar o XSS, alterou-se a secção *Brief Description* para o código indicado. 

![/imgs10/alice_local_sql.png](/imgs10/brief.png)

Imediamente após o guardar das alterações, como esperado, obteve-se o *pop-up*:

![/imgs10/alice_local_sql.png](/imgs10/popup.png)

Experimentou-se também com o exemplo usando um *form* e apesar de apenas se usar um *link* exemplificativo, pode comprovar-se que efetivamente funcionaria: 

![/imgs10/alice_local_sql.png](/imgs10/withForm.png)

## Tarefa 2

Alterou-se novamente a secção *Brief Description* desta vez para:
``` js
<script>alert(document.cookie);</script>
```

Como resultado, surgiu o *pop up* com as *cookies* do utilizador mal as alterações foram guardadas.

![/imgs10/alice_local_sql.png](/imgs10/cookies.png)