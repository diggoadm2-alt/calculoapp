<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>Delivery Cost Pro</title>

<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap" rel="stylesheet">

<style>

*{
margin:0;
padding:0;
box-sizing:border-box;
font-family:'Poppins',sans-serif;
}

body{
background:#0b0b0b;
color:#fff;
min-height:100vh;
padding:20px;
background-image:
radial-gradient(circle at top left,#ff660020,transparent 25%),
radial-gradient(circle at bottom right,#ff000020,transparent 25%);
}

.container{
max-width:600px;
margin:auto;
}

.header{
text-align:center;
margin-bottom:25px;
}

.header h1{
font-size:32px;
font-weight:700;
color:#ff6600;
}

.header p{
opacity:.7;
margin-top:8px;
}

.card{
background:rgba(255,255,255,.05);
backdrop-filter:blur(10px);
border:1px solid rgba(255,255,255,.08);
padding:22px;
border-radius:24px;
margin-bottom:20px;
box-shadow:0 0 25px rgba(255,102,0,.08);
}

.card h2{
margin-bottom:18px;
font-size:20px;
color:#ff8800;
}

input,select{
width:100%;
padding:14px;
border:none;
outline:none;
border-radius:14px;
background:#1a1a1a;
color:#fff;
margin-bottom:14px;
font-size:15px;
transition:.3s;
}

input:focus,
select:focus{
border:1px solid #ff6600;
box-shadow:0 0 10px rgba(255,102,0,.3);
}

.tags{
display:flex;
flex-wrap:wrap;
gap:10px;
margin-bottom:18px;
}

.tag{
padding:10px 14px;
background:#ff6600;
border-radius:40px;
font-size:13px;
font-weight:600;
cursor:pointer;
transition:.3s;
}

.tag:hover{
transform:translateY(-3px);
box-shadow:0 0 15px rgba(255,102,0,.5);
}

button{
width:100%;
padding:16px;
border:none;
border-radius:16px;
background:linear-gradient(90deg,#ff6600,#ff3300);
color:#fff;
font-size:16px;
font-weight:700;
cursor:pointer;
transition:.3s;
}

button:hover{
transform:scale(1.02);
opacity:.95;
}

.dashboard{
display:grid;
grid-template-columns:1fr 1fr;
gap:15px;
margin-top:20px;
}

.box{
background:#121212;
padding:18px;
border-radius:18px;
text-align:center;
border:1px solid rgba(255,255,255,.05);
}

.box span{
display:block;
font-size:13px;
opacity:.6;
margin-bottom:6px;
}

.box strong{
font-size:20px;
color:#ff6600;
}

.result{
margin-top:20px;
padding:20px;
background:#111;
border-radius:18px;
border:1px solid rgba(255,255,255,.05);
line-height:1.8;
}

.footer{
text-align:center;
margin-top:20px;
opacity:.5;
font-size:13px;
}

@media(max-width:600px){

.dashboard{
grid-template-columns:1fr;
}

.header h1{
font-size:26px;
}

}

</style>
</head>

<body>

<div class="container">

<div class="header">
<h1>Delivery Cost Pro</h1>
<p>Sistema inteligente de custos para delivery</p>
</div>

<div class="card">

<h2>Dados da Empresa</h2>

<input type="text" id="empresa" placeholder="Nome da Lanchonete">

<input type="text" placeholder="WhatsApp">

<input type="text" placeholder="Endereço">

</div>

<div class="card">

<h2>Escolha o Lanche</h2>

<select id="lanche">
<option>X-Salada</option>
<option>X-Bacon</option>
<option>X-Tudo</option>
<option>X-Frango</option>
<option>X-Calabresa</option>
<option>Hot Dog</option>
<option>Personalizado</option>
</select>

<div class="tags">

<div class="tag">Queijo</div>
<div class="tag">Bacon</div>
<div class="tag">Hambúrguer</div>
<div class="tag">Catupiry</div>
<div class="tag">Cheddar</div>
<div class="tag">Tomate</div>
<div class="tag">Alface</div>

</div>

<input type="number" id="valorKg" placeholder="Valor do KG">

<input type="number" id="peso" placeholder="Peso usado em gramas">

<input type="number" id="lucro" placeholder="% Lucro desejado">

<button onclick="calcular()">
Calcular Agora
</button>

<div class="dashboard">

<div class="box">
<span>Custo</span>
<strong id="custo">R$ 0,00</strong>
</div>

<div class="box">
<span>Venda</span>
<strong id="venda">R$ 0,00</strong>
</div>

<div class="box">
<span>Lucro</span>
<strong id="lucroValor">0%</strong>
</div>

<div class="box">
<span>Status</span>
<strong>Ativo</strong>
</div>

</div>

<div class="result" id="resultado">
Aguardando cálculo...
</div>

</div>

<div class="footer">
Delivery Cost Pro © 2026
</div>

</div>

<script>

function calcular(){

let valorKg =
parseFloat(document.getElementById('valorKg').value);

let peso =
parseFloat(document.getElementById('peso').value);

let lucro =
parseFloat(document.getElementById('lucro').value);

if(!valorKg || !peso || !lucro){

alert("Preencha todos os campos");

return;

}

let valorGrama = valorKg / 1000;

let custo = valorGrama * peso;

let venda = custo + (custo * lucro / 100);

document.getElementById('custo').innerHTML =
`R$ ${custo.toFixed(2)}`;

document.getElementById('venda').innerHTML =
`R$ ${venda.toFixed(2)}`;

document.getElementById('lucroValor').innerHTML =
`${lucro}%`;

document.getElementById('resultado').innerHTML =

`
<strong>Resultado Final</strong><br><br>

Produto calculado com sucesso.<br>

Custo total do produto:
<strong>R$ ${custo.toFixed(2)}</strong><br>

Preço ideal de venda:
<strong>R$ ${venda.toFixed(2)}</strong><br>

Margem aplicada:
<strong>${lucro}%</strong>
`;

}

</script>

</body>
</html>