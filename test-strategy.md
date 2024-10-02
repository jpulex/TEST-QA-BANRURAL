# Plan de ataque para testeo del Juego "Adivina tu Número"

## Objetivo
En el siguiente documento se documentan los errores encontrados, con su respectiva solución y o sugerencias de cambios.

## Bugs y Soluciones

1. **Error en la generación del número aleatorio**
   - **Descripción**: El número aleatorio se generaba incorrectamente, resultando en un rango de 0 a 10.
   - **Solución**: Se modificó la línea de código para generar un número entre 1 y 100:
     ```javascript
     let randomNumber = Math.floor(Math.random() * 100) + 1;
     ```

2. **Error en el selector de clase**
   - **Descripción**: Se utilizó un selector incorrecto para la clase `lowOrHi`, este no permitía mostrar mensajes.
   - **Solución**: Se corrigió el selector a:
     ```javascript
     const lowOrHi = document.querySelector('.lowOrHi');
     ```

3. **Error en la función de escucha de eventos**
   - **Descripción**: No se escribió correctamente `addeventListener`, esto causa que la función no se ejecute al hacer click en el botón.
   - **Solución**: Se corrigió a: `addEventListener`:
     ```javascript
     guessSubmit.addEventListener('click', checkGuess);
     ```

4. **Lógica incorrecta al ganar el juego**
   - **Descripción**: El mensaje de victoria se mostraba cuando se agotaban los intentos en lugar de cuando el usuario adivinaba el número correcto.
   - **Solución**: Se reformuló la condición en el `if`:
     ```javascript
     if(userGuess === randomNumber) {
         lastResult.textContent = '¡Felicitaciones! adivinaste el número!';
     }
     ```

5. **Uso incorrecto de `Math.random()` para reiniciar el juego**
   - **Descripción**: Al reiniciar, el número aleatorio no se generaba correctamente, manteniendo el mismo número.
   - **Solución**: Se corrigió la línea de código en la función, al cual se le dió lógica `resetGame`:
     ```javascript
     randomNumber = Math.floor(Math.random() * 100) + 1;
     ```

6. **El mensaje de "PERDER EL JUEGO"**
   - **Descripción**: El mensaje tenía errores ortográficos, también era confuso se cambió el: "!!!Pérdistes!!!" por un texto más comprensible.
   - **Solución**: Se modificó el mensaje obtenido al perder el juego:
     ```javascript
     lastResult.textContent = '¡Perdiste! El número era ' + randomNumber;
     ```
## Sugerencias:
1. Según mi experiencia de trabajo en Banco Industrial y acostumbrado a las metodologías, como Project Manager y QA, solo hacía sugerencias de cambios con las funciones a implementar si era necesario, es decir en el desarrollo presentado se observa que:

(Siguiendo las instrucciones no agregaré desarrollo nuevo, en el ámbito real por temas de roles no era una buena práctica)

a. Se evalúa que ingresan números negativos y positivos sin un límite de caracteres.
b. Se evalúa que se ingresan caracteres especiales, estos mismos si se reconocen como string pero en un futuro podría ser una vulnerabilidad para el desarrollo.
c. Se intentó ingresar una cadena <h1>123</h1> y esta misma la reconoce como string, en el desarrollo se sugiere que el campo se reconozca unicamente como numérico y que no acepte caracteres diferentes.
d. Si se realiza una operación matemática por ejemplo usar una practica de manejo de errores.


## Conclusión
Se realizaron pruebas exhaustivas desde el punto de vista desarrollador y también desde el punto de vista usuario, puesto que hay muchos usuarios que son atentos al detalle y el simple hecho de no empezar con mayúsculas, una palabra mal escrita o un botón que no funciona, hace desagradable su experiencia con la interacción del software.
