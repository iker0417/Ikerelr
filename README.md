# Ikerelr
Proyect-Mi amigo Secreto
# Amigo Secreto

Una aplicación web sencilla para realizar sorteos de "Amigo Secreto". Los usuarios pueden agregar nombres de amigos y luego realizar un sorteo aleatorio para determinar al “amigo secreto”.

## Funcionalidades

- **Añadir Nombres**: Permite a los usuarios ingresar nombres de amigos mediante un campo de texto y un botón de añadir.
- **Validación de Datos**: Si el usuario intenta ingresar un nombre vacío, aparece un mensaje de alerta indicando que debe agregar un nombre.
- **Sorteo Aleatorio**: Al finalizar, la aplicación escoge un nombre aleatorio de la lista de amigos ingresados.

## Capturas de Pantalla

### Pantalla Principal

![Pantalla Principal](./screenshots/pantalla_principal.png)

### Añadir Nombres

![Añadir Nombres](./screenshots/añadir_nombres.png)

### Sorteo de Amigo Secreto

![Sorteo Amigo Secreto](./screenshots/sorteo_amigo_secreto.png)

## Instalación

Para ejecutar este proyecto de manera local, sigue los siguientes pasos:

1. Clona el repositorio:
    ```sh
    git clone https://github.com/tu_usuario/amigo-secreto.git
    ```

2. Navega al directorio del proyecto:
    ```sh
    cd amigo-secreto
    ```

3. Abre el archivo `index.html` en tu navegador.

## Uso

1. Ingresa el nombre de un amigo en el campo de texto.
2. Haz clic en el botón "Añadir" para agregar el nombre a la lista.
3. Repite los pasos 1 y 2 para todos los amigos que participarán en el sorteo.
4. Haz clic en el botón "Sortear Amigo Secreto" para seleccionar un nombre al azar de la lista.
5. Se mostrará el nombre del amigo secreto seleccionado.

## Problemas y Soluciones

### Problema: No se puede agregar un nombre vacío
- **Solución**: Asegúrate de ingresar un nombre en el campo de texto antes de hacer clic en el botón "Añadir".

### Problema: No se puede sortear sin nombres en la lista
- **Solución**: Agrega al menos un nombre a la lista antes de hacer clic en el botón "Sortear Amigo Secreto".

## Contribuciones

Las contribuciones son bienvenidas. Si deseas contribuir, por favor sigue los siguientes pasos:

1. Haz un fork del proyecto.
2. Crea una rama (`git checkout -b feature/nueva-funcionalidad`).
3. Realiza tus cambios y haz commit (`git commit -am 'Añadir nueva funcionalidad'`).
4. Haz push a la rama (`git push origin feature/nueva-funcionalidad`).
5. Abre un Pull Request.

## Licencia

Este proyecto está bajo la licencia MIT. Consulta el archivo [LICENSE](./LICENSE) para más detalles.





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
