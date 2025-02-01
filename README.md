# 🎉 Sorteo de Amigos Secretos

Este es un proyecto simple en **JavaScript, HTML y CSS** que permite **agregar amigos a una lista** y **sortear aleatoriamente uno de ellos**. También incluye validaciones para evitar nombres vacíos, duplicados y caracteres inválidos.

---

## 🚀 **Características**
✅ Permite agregar nombres a la lista de amigos.  
✅ Valida que los nombres **no estén vacíos**.  
✅ No permite números ni símbolos en los nombres.  
✅ Evita nombres duplicados en la lista.  
✅ Muestra la lista de amigos en la página.  
✅ Realiza un **sorteo aleatorio** entre los amigos agregados.  
✅ Permite **reiniciar el juego** después del sorteo.  

---

## 🛠️ **Tecnologías Utilizadas**
- **HTML** → Estructura del sitio.  
- **CSS** → Estilos básicos (si se agregan).  
- **JavaScript** → Lógica de la aplicación.  

---

## 📥 **Instalación y Uso**
1️⃣ **Clona este repositorio** en tu máquina:
   ```sh
   git clone https://github.com/tu-usuario/sorteo-amigos.git
2️⃣ Abre el archivo index.html en tu navegador.
3️⃣ Ingresa los nombres de los amigos en el campo de texto.
4️⃣ Haz clic en "Agregar Amigo" para añadirlos a la lista.
5️⃣ Haz clic en "Sortear Amigo" para elegir un ganador aleatoriamente.
6️⃣ Haz clic en "Reiniciar Juego" para comenzar de nuevo.

// 1. Crear un array para almacenar los nombres de los amigos
let amigos = [];

// 2. Implementar función para agregar amigos
function agregarAmigo() {
    // Capturar el valor del campo de entrada
    let inputAmigo = document.getElementById("amigo");
    let nombreAmigo = inputAmigo.value.trim(); // Eliminar espacios en blanco

    // Expresión regular para validar solo letras y espacios (sin números ni símbolos)
    const regex = /^[A-Za-zÁáÉéÍíÓóÚúÑñ\s]+$/;

    // Validar que el campo no esté vacío, Validar el nombre antes de agregarlo, validar nombres repetidos o con simbolos
    if (nombreAmigo === "" || !regex.test(nombreAmigo) || amigos.includes(nombreAmigo.toLowerCase())) {
        const mensaje = nombreAmigo === "" ? "Por favor, inserte un nombre." 
                      : !regex.test(nombreAmigo) ? "El nombre solo puede contener letras." 
                      : "Este nombre ya está en la lista de amigos.";
        alert(mensaje);
        return;
    }

    // Agregar el nombre al array de amigos
    amigos.push(nombreAmigo);

    // Actualizar la lista o array de amigos en la página
    actualizarListaAmigos();

    // Limpiar el campo de entrada
    inputAmigo.value = "";

    }

// 3. Función para actualizar la lista de amigos en la página
function actualizarListaAmigos() {
    // Obtener el elemento de la lista donde se mostrarán los amigos
    const listaAmigos = document.getElementById("listaAmigos");

    // Limpiar la lista existente para evitar duplicados
    listaAmigos.innerHTML = "";

    // Recorrer el array amigos y agregar cada nombre como un <li>
    for (let i = 0; i < amigos.length; i++) {
        const li = document.createElement("li"); // Crear <li>
        li.textContent = amigos[i]; // Asignar el nombre del amigo

        listaAmigos.appendChild(li); // Agregar el <li> a la lista
    }
}

// 4. Función para sortear un amigo aleatoriamente
function sortearAmigo() {
    // Validar que haya amigos en la lista
    if (amigos.length === 0) {
        alert("No hay amigos en la lista para sortear.");
        return;
    }

    // Generar un índice aleatorio
    let indiceAleatorio = Math.floor(Math.random() * amigos.length);

    // Obtener el nombre sorteado
    let amigoSorteado = amigos[indiceAleatorio];

    // Mostrar el resultado en la página
    const resultado = document.getElementById("resultado");
    resultado.innerHTML = `<strong>🎉 El amigo secreto sorteado es: ${amigoSorteado}</strong>`;

    // Limpiar la lista de amigos en pantalla (no del array)
    document.getElementById("listaAmigos").innerHTML = "";

     //Vaciar el array de amigos para reiniciar el juego
     amigos = [];
}
    // 5. Función para reiniciar el juego manualmente
function reiniciarJuego() {
    // Vaciar el array de amigos
    amigos = [];

    // Limpiar la lista en pantalla
    document.getElementById("listaAmigos").innerHTML = "";
    
    // Limpiar el resultado en pantalla
    document.getElementById("resultado").innerHTML = "";

    alert("Juego reiniciado. Agrega nuevos amigos para empezar de nuevo.");

}
