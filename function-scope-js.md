# Identificación de funciones

## Objetivo

- Identificar las funciones globales, locales, funciones de callback, expresions, statement, closure, scope, contextos de ejecucion, funciones que forman parte de la pila de ejecucion (stack execution) y funciones que forman parte de la cola de eventos (event queue).

## Corrección de variables

- Según la convencion de codificación de JavaScript, las variables y los nombres de las funciones deben ser denominadas y declaradas en inglés, utilizar camelCase y tener relación con lo que hacen o se refieren. Esto nos ayudará a mejorar la legibilidad del código, así como tambien hacer más facil el mantenimiento del mismo.

- Habiendo dejado en claro lo anterior, pasaremos las variables y nombres de las funciones escritas en español del archivo app.js al inglés.

<center>

|   INCORRECTO   |    CORRECTO   |
|:--------------:|:-------------:|
|    longitud    |    length     |
|   soloNumeros  |  onlyNumbers  |
|    sumaTotal   |  totalAmount  |
|      input     |  numberCard   |

</center>

## Funciones globales 

- Solo hay una función global y es **global execution context**, las demás funciones no son globales, ya que estan dentro de la función anonima que se ejecuta cuando el DOM ya esta cargado.

```js
$(document).ready(function() {});
```

## Funciones locales

- Son 7 las funciones locales, una de ellas se ejecuta cuando se escucha el evento (input) y es **anonima**, las demás son:
    - **activeButton**
    - **desactiveButton**
    - **length**
    - **onlyNambers**
    - **isValidCreditCard**
    - **creditCardNumber**

## Funciones de callback

- Solo hay una función que se pasa dentro de otra función (**onlyNumbers**) como argumento y es la función **length**.

```js
onlyNumbers(length(numberCard))
```

## Funciones expresions

- La función **creditCardNumber** vendria a ser una función expresion por que esta siendo declarada por una variable y creada por la función onlyNumber, tambien se puede agregar que tiene un scope de alcance local.

```js
var creditCardNumber = onlyNumber(length(numberCard));
```

## Funciones statement

- Las funciones statement, son aquellas que no han sido declaradas en variables y son 5:
    - **activeButton**, tiene un scope de alcance global.
    - **desactiveButton**, tiene un scope de alcance global.
    - **length**, tiene un scope de alcance global.
    - **onlyNambers**, tiene un scope de alcance global.
    - **isValidCreditCard**, tiene un scope de alcance global.

## Funciones closures

- Se le llama funciones closures a las que "recuerdan" el entorno en el que se han creado y vendrian a ser las siguientes:
    - **activeButton**
    - **desactiveButton**    
```js
  function activeButton() {
    $buttonNext.attr('disabled', false);
  } 
 
  function desactiveButton() {  
    $buttonNext.attr('disabled', true);
  } 
```

## Funciones que forman parte de la pila de ejecucion (stack execution)

- Cuando hablamos de la pila de ejecucón o stack execution, nos referimos al orden en el que se cargan las funciones, y seria en el siguiente orden (se deberá leer de abajo hacia arriba).
    - **isValidCreditCard**
    - **onlyNumbers**
    - **length**
    - **desactiveButton**
    - **activeButton**
    - **funcion anonima (se ejecuta cuando el DOM ya este cargado)**
    - **global execution context**

## Funciones que forman parte de la cola de eventos (event queue)

- Son las aquellas funciones que se cargan solo cuando se produce el evento, y en este caso seria la función **anonima** que escucha el evento input.