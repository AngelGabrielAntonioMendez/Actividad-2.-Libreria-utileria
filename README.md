<img width="825" height="783" alt="image" src="https://github.com/user-attachments/assets/ae2a1994-566e-4069-b455-10aa7f409228" />

## Problema a resolver:
Esta es una librería de utilería en JavaScript diseñada para facilitar tareas comunes en el desarrollo web, como la validación de formularios, el cálculo de fechas, el formateo de cadenas de texto y la preparación de datos de autenticación.

La librería se encapsula de forma segura y expone un único objeto global llamado `window.logicApp` para evitar conflictos en el scope global.

## Instalación

Para utilizar esta librería en tu proyecto, simplemente debes incluir el archivo `utileria.js` en tu documento HTML antes de los scripts que dependan de ella.

Añade la siguiente etiqueta dentro de tu `<head>` o al final del `<body>`:

```html
<script src="js/utileria.js"></script>
<script src="js/login.js"></script>

Uso y Ejemplos de Código
La librería está dividida en cuatro módulos principales: Tiempo, Formato, Validador y Auth. A continuación, se muestran ejemplos de cómo utilizar cada uno de ellos. Para probarlos, puedes abrir la consola de tu navegador y ejecutar el código.

1. Módulo Tiempo
Maneja operaciones relacionadas con fechas, como calcular la edad exacta o formatear fechas a un texto legible en español.

JavaScript
// Extraemos el módulo Tiempo del objeto global
const { Tiempo } = window.logicApp;

// Ejemplo 1: Calcular la edad en base a una fecha de nacimiento
const edad = Tiempo.calcularEdad("2000-05-15");
console.log("Edad calculada:", edad); 
// Resultado esperado: Edad calculada: 26 (dependiendo del año actual)

// Ejemplo 2: Formatear una fecha a texto en español
const fechaFormateada = Tiempo.formatearFecha("2026-07-05");
console.log("Fecha legible:", fechaFormateada); 
// Resultado esperado: Fecha legible: 5 de julio de 2026
2. Módulo Formato
Se encarga de la manipulación y limpieza de cadenas de texto.

JavaScript
const { Formato } = window.logicApp;

// Ejemplo: Capitalizar correctamente un nombre mal escrito (con minúsculas y espacios extra)
const nombreLimpio = Formato.capitalizarPalabras("juan carlos   perez");
console.log("Nombre formateado:", nombreLimpio); 
// Resultado esperado: Nombre formateado: Juan Carlos Perez
3. Módulo Validador
Proporciona múltiples funciones para validar correos, teléfonos, contraseñas y otros datos de entrada del usuario.

JavaScript
const { Validador } = window.logicApp;

// Ejemplo 1: Validar un número de teléfono (debe tener exactamente 10 dígitos)
const telefonoValido = Validador.telefono("9511234567");
console.log("¿Teléfono válido?:", telefonoValido); 
// Resultado esperado: ¿Teléfono válido?: true

// Ejemplo 2: Verificar si una fecha corresponde a alguien mayor de 18 años
const esMayor = Validador.esMayorDeEdad("2012-01-01");
console.log("¿Es mayor de edad?:", esMayor); 
// Resultado esperado: ¿Es mayor de edad?: false

// Ejemplo 3: Análisis profundo de una contraseña que no cumple los requisitos
const analisis = Validador.analizarPassword("clave123");
console.log("Análisis de contraseña:", analisis);
/* Resultado esperado en consola:
{
  esValida: false,
  detalles: [
    "Falta una letra mayúscula.",
    "Falta un caracter especial."
  ]
}
*/
4. Módulo Auth
Prepara los datos de inicio de sesión validando previamente el formato del correo y la fortaleza de la contraseña.

JavaScript
const { Auth } = window.logicApp;

try {
    // Intentamos preparar los datos con información válida
    const datosLogin = Auth.prepararDatosLogin("usuario@correo.com", "SuperPassword123!");
    console.log("Datos listos para enviar:", datosLogin);
    /* Resultado esperado:
    {
      email: "usuario@correo.com",
      pwd: "SuperPassword123!",
      timestamp: "2026-07-05T01:34:00.000Z" (fecha actual)
    }
    */
} catch (error) {
    console.error("Error de validación:", error.message);
}
Capturas de pantalla
A continuación, se muestran las pruebas de la librería ejecutándose directamente en la consola del navegador:

Prueba del módulo Tiempo y Formato:

Prueba del módulo Validador (Analizador de contraseñas):

Prueba del módulo Auth generando el timestamp:
