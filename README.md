# Ikerelr
Proyect-Mi amigo Secreto
document.getElementById('añadir').addEventListener('click', function() {
    const nombreInput = document.getElementById('nombre');
    const nombre = nombreInput.value.trim();

    if (nombre === '') {
        alert('Por favor, ingrese un nombre.');
        return;
    }

    const listaAmigos = document.getElementById('listaAmigos');
    const nuevoAmigo = document.createElement('li');
    nuevoAmigo.textContent = nombre;
    listaAmigos.appendChild(nuevoAmigo);

    nombreInput.value = '';
    nombreInput.focus();

    document.getElementById('sortear').disabled = false;
});

document.getElementById('sortear').addEventListener('click', function() {
    const listaAmigos = document.getElementById('listaAmigos');
    const amigos = listaAmigos.getElementsByTagName('li');

    if (amigos.length === 0) {
        alert('No hay nombres en la lista para sortear.');
        return;
    }

    const indiceAleatorio = Math.floor(Math.random() * amigos.length);
    const amigoSecreto = amigos[indiceAleatorio].textContent;

    document.getElementById('resultado').textContent = `El amigo secreto es: ${amigoSecreto}`;
});
