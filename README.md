<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Death Note</title>

<style>
*{
    margin:0;
    padding:0;
    box-sizing:border-box;
}

body{
    background:#000;
    font-family:Georgia, serif;
    width:100vw;
    height:100vh;
    overflow:hidden;
}

/* LOGIN */

#login{
    position:absolute;
    inset:0;
    display:flex;
    justify-content:center;
    align-items:center;
    background:black;
}

.login-box{
    width:350px;
    background:#111;
    border:3px solid #444;
    border-radius:10px;
    padding:25px;
    box-shadow:0 0 30px red;
    color:white;
}

.login-box h1{
    text-align:center;
    color:red;
    letter-spacing:5px;
    margin-bottom:20px;
}

.login-box input{
    width:100%;
    padding:12px;
    margin-bottom:10px;
    background:#222;
    color:white;
    border:1px solid #555;
    border-radius:5px;
}

.login-box button{
    width:100%;
    padding:12px;
    background:darkred;
    color:white;
    border:none;
    border-radius:5px;
    cursor:pointer;
    font-size:16px;
}

.login-box button:hover{
    background:red;
}

#erro{
    color:red;
    text-align:center;
    margin-top:10px;
}

/* CADERNO */

#app{
    display:none;
    width:100vw;
    height:100vh;
}

.book{
    width:100vw;
    height:100vh;
    background:#e8dfc5;
    padding:40px;
    box-shadow:inset 0 0 30px rgba(0,0,0,.3);
}

.book h1{
    text-align:center;
    color:black;
    font-size:40px;
    letter-spacing:8px;
    margin-bottom:20px;
}

#page{
    width:100%;
    height:calc(100vh - 120px);

    border:none;
    outline:none;
    resize:none;

    background:
    repeating-linear-gradient(
        transparent,
        transparent 38px,
        rgba(0,0,0,.15) 39px
    );

    font-family:"Times New Roman", serif;
    font-size:28px;
    line-height:39px;
    color:black;
}

.save{
    position:absolute;
    top:15px;
    right:20px;
    color:#444;
    font-size:14px;
}
</style>
</head>
<body>

<!-- LOGIN -->

<div id="login">
    <div class="login-box">

        <h1>DEATH NOTE</h1>

        <input
            type="password"
            id="senha"
            placeholder="Digite a senha">

        <button onclick="entrar()">
            Entrar
        </button>

        <div id="erro"></div>

    </div>
</div>

<!-- CADERNO -->

<div id="app">
    <div class="book">

        <div class="save">
            Salvamento automático
        </div>

        <h1>DEATH NOTE</h1>

        <textarea
            id="page"
            placeholder="Escreva aqui..."></textarea>

    </div>
</div>

<script>

// MUDE A SENHA AQUI
const SENHA = "ryuk123";

const area = document.getElementById("page");

// CARREGA O TEXTO SALVO
window.onload = () => {
    area.value =
    localStorage.getItem("deathnote_texto") || "";
};

// SALVA AUTOMATICAMENTE
area.addEventListener("input", () => {
    localStorage.setItem(
        "deathnote_texto",
        area.value
    );
});

// LOGIN
function entrar(){

    const senha =
    document.getElementById("senha").value;

    if(senha === SENHA){

        document.getElementById("login")
        .style.display = "none";

        document.getElementById("app")
        .style.display = "block";

    }else{

        document.getElementById("erro")
        .innerText = "Senha incorreta!";
    }
}

// APERTAR ENTER
document
.getElementById("senha")
.addEventListener("keypress", e => {

    if(e.key === "Enter"){
        entrar();
    }

});

</script>

</body>
</html>
