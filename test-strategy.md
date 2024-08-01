#Errores de sintaxis

##EventListener
- Se enconetro mal escrito el seteo del event listener al input de submit, se el nombre correcto es addEventListerner. Corección:
```javascript
    guessSubmit.addEventListener('click', checkGuess);
```
- Se encontro mal escrita la llamada del elemento lowOrHi pues no recuperaba por clase. Corrección:
```javascript
  const lowOrHi = document.querySelector('.lowOrHi');
```

- En el metodo setGameOver, el add listner para el boton resetGame esta mal escrito. Corección:
```javascript
  	  resetButton.addEventListener('click', resetGame);
```

#Errores de negocio
##Logicos

- No existe validacion para caracteres que no sean un numeros, ni tampoco validacion para asegurar que el numero ingresado sea un entero. Corrección:
```javascript
    if( isNaN(Number(userGuess)) ){
        lastResult.textContent = 'Debes ingresar un valor numerico! ';
        lastResult.style.backgroundColor = 'red';
    }else if(!Number.isInteger(Number(userGuess))){
        lastResult.textContent = 'Debes ingresar un número entero! ';
        lastResult.style.backgroundColor = 'red';
    } // Las demas condiones para el nuemero
```

- El numero generado no es un entero entre 1 y 100. Corección:
```javascript
    let randomNumber = Math.floor(Math.random() * 100)+1;
```

- La constante de intentos esta establecida en 5, no en 10 como lo ocupa el requerimento. Corección:
```javascript
    const ATTEMPS = 10;
```

- La validación para comprobar si el numero ingresado es el correcto compara tipo de datos incorrectos con triple igual, por lo que siempre sera falso. Corrección:
```javascript
     //Validaciones agregadas en el item anterior
    }else if(Number(userGuess) === randomNumber) {
      //Setteo del mensaje ganador (Corrección en el siguiente item)
    }
```

- El mensaje y color de fondo mostrado cuando el usuario no advino el numero, se equivoco o se acabo los intentos, es incorrecto ademas de que suma un intento ignorando la logica de negocio. Corrección:
```javascript 
        //validacinoes previas 
    }else if(Number(userGuess) === randomNumber) {
      lastResult.textContent = 'Felicitaciones! adivinaste el número!';
      lastResult.style.backgroundColor = 'green';
      setGameOver(); 
    } else if(guessCount === ATTEMPS) {
      lastResult.textContent = '!!!Pérdistes!!!';
      lastResult.style.backgroundColor = 'red';
      lowOrHi.textContent = '';
      setGameOver();
    } else {
      guessCount++;
      guessField.value = '';
      guessField.focus();
      lastResult.textContent = 'Incorrecto! ';
      lastResult.style.backgroundColor = 'red';
      //Logica para mostrar si el numero es mayor o menor
    }
```

- La validación para agregar el ultimo numero ingresado solo debe ir si el valor ingresado es valido, es incorrecto y aun tiene intentos disponibles. Corrección:
```javascript 
        ///Previas validacioens
    } else if(guessCount === ATTEMPS) {
      lastResult.textContent = '!!!Pérdistes!!!';
      lastResult.style.backgroundColor = 'red';
      lowOrHi.textContent = '';
      setGameOver();
    } else {
      
      if(guessCount === 1) {
        guesses.textContent = 'Número aleatorio anterior: ';
      }
      guesses.textContent += userGuess + ' ';
      
      guessCount++;
      guessField.value = '';
      guessField.focus();
      
      lastResult.textContent = 'Incorrecto! ';
      lastResult.style.backgroundColor = 'red';
      if(userGuess < randomNumber) {
        lowOrHi.textContent = 'El número es mayor!';
      } else if(userGuess > randomNumber) {
        lowOrHi.textContent = 'El número es menor!';
      }
    }
```

- Al resetear el juego, el nuevo numero aleatorio generado no es entre 0y 10 de nuevo. Corrección:
```javascript 
    randomNumber = Math.floor(Math.random() * 100)+1;
```

- La logica para mostrar si estoy cerca del numero correcto  no muestra el texto correcto y compara tipos de datos distitintos, por lo que siempre sera falso. Corrección:
```javascript 
    randomNumber = Math.floor(Math.random() * 100)+1;
```
    