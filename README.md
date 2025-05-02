<!DOCTYPE html>
<html lang="pt">
<head>
    <meta charset="UTF-8">
    <title>Catálogo MB WAY</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0; padding: 0;
            background-color: #f9f9f9;
        }
        header {
            background-color: #0073e6;
            color: white;
            padding: 1em;
            text-align: center;
        }
        .catalogo {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            padding: 2em;
        }
        .produto {
            background: white;
            border: 1px solid #ddd;
            margin: 1em;
            padding: 1em;
            width: 200px;
            text-align: center;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }
        .produto img {
            max-width: 100%;
            height: auto;
        }
        .formulario {
            display: none;
            position: fixed;
            top: 20%;
            left: 50%;
            transform: translateX(-50%);
            background: white;
            padding: 2em;
            box-shadow: 0 0 10px rgba(0,0,0,0.3);
            z-index: 999;
        }
        .formulario input {
            display: block;
            margin: 1em 0;
            padding: 0.5em;
            width: 100%;
        }
        .formulario button {
            background: #0073e6;
            color: white;
            border: none;
            padding: 0.7em;
            cursor: pointer;
        }
        .overlay {
            display: none;
            position: fixed;
            top: 0; left: 0;
            width: 100%; height: 100%;
            background: rgba(0,0,0,0.5);
            z-index: 998;
        }
    </style>
</head>
<body>

<header>
    <h1>Catálogo de Produtos</h1>
</header>

<div class="catalogo">
    <div class="produto">
        <img src="https://via.placeholder.com/150" alt="Produto 1">
        <h3>Produto 1</h3>
        <p>€15,00</p>
        <button onclick="abrirFormulario('Produto 1', 15)">Comprar</button>
    </div>
    <div class="produto">
        <img src="https://via.placeholder.com/150" alt="Produto 2">
        <h3>Produto 2</h3>
        <p>€22,50</p>
        <button onclick="abrirFormulario('Produto 2', 22.5)">Comprar</button>
    </div>
    <!-- Podes duplicar este bloco para mais produtos -->
</div>

<div class="overlay" id="overlay" onclick="fecharFormulario()"></div>

<div class="formulario" id="formulario">
    <h3 id="produtoSelecionado">Produto</h3>
    <form onsubmit="enviarPedido(event)">
        <input type="hidden" id="produto" name="produto">
        <input type="tel" id="telemovel" name="telemovel" placeholder="Nº Telemóvel MB WAY" required pattern="[0-9]{9}">
        <button type="submit">Enviar Pedido</button>
    </form>
</div>

<script>
    function abrirFormulario(produto, preco) {
        document.getElementById('formulario').style.display = 'block';
        document.getElementById('overlay').style.display = 'block';
        document.getElementById('produtoSelecionado').innerText = `${produto} - €${preco.toFixed(2)}`;
        document.getElementById('produto').value = produto;
    }

    function fecharFormulario() {
        document.getElementById('formulario').style.display = 'none';
        document.getElementById('overlay').style.display = 'none';
    }

    function enviarPedido(event) {
        event.preventDefault();
        const telemovel = document.getElementById('telemovel').value;
        const produto = document.getElementById('produto').value;
        alert(`Pedido para "${produto}" enviado para o número ${telemovel} via MB WAY (manual).`);
        fecharFormulario();
    }
</script>

</body>
</html>
