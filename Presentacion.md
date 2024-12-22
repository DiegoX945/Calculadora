# Calculadora
Flujo general de la calculadora:
## 1.	Interfaz de usuario (HTML) y formulario:
El archivo calculadora.php contiene la interfaz de la calculadora. Es un formulario HTML que contiene un campo de texto (input) donde se muestra lo que el usuario ha escrito (el valor de la pantalla) y varios botones para los números y operaciones.
El formulario se envía al archivo calcular.php con el método POST cuando se presiona cualquier botón.
## 2.	Persistencia de datos con sesiones:
Sesión PHP (session_start()): En ambos archivos PHP, usamos session_start() al principio del código. Esto es esencial porque PHP utiliza sesiones para almacenar datos entre diferentes solicitudes de página. Esto permite que el valor de la pantalla de la calculadora se mantenga a través de múltiples recargas de página, incluso después de enviar un formulario.
Almacenamiento de la pantalla: El valor de la pantalla (lo que el usuario ve en el campo de texto) se guarda en una variable de sesión llamada $_SESSION['pantalla']. Esto asegura que el valor no se pierda cuando se recarga la página después de realizar una operación.
## 3.	Procesamiento de la entrada del usuario (archivo calcular.php):
Cuando el usuario presiona un botón en el formulario, el valor del botón se envía a través de un formulario POST. Este valor se guarda en la variable $_POST['operacion'].
En el archivo calcular.php, procesamos lo que el usuario ha presionado: 
Si el botón es un número (es decir, es un valor numérico), concatenamos ese número a lo que ya está en la pantalla. Si la pantalla tiene un 0, lo reemplazamos con el número presionado (para evitar tener un 0 al principio).
Si el botón es una operación aritmética (como +, -, *, /), la operación se agrega a la pantalla, de modo que podemos construir la expresión completa (por ejemplo, 2 + 3).
Si el botón es el signo igual (=), usamos la función eval() para evaluar la expresión matemática. Esta función convierte una cadena de texto que contiene una expresión matemática en código PHP y lo ejecuta, devolviendo el resultado. Si hay algún error en la evaluación (por ejemplo, si hay una operación incorrecta), capturamos el error y mostramos "Error" en la pantalla.
Si el botón es el de raíz cuadrada (√), calculamos la raíz cuadrada del número en la pantalla y actualizamos el valor.
Si el botón es C, limpiamos la pantalla (reseteando el valor de $_SESSION['pantalla'] a 0).
## 4.	Redirección para actualizar la pantalla:
Después de procesar la operación, redirigimos de nuevo al archivo calculadora.php usando header("Location: calculadora.php");. Esto recarga la página para mostrar el resultado actualizado de la pantalla (valor calculado o actualizado).
La redirección se hace porque las sesiones persisten entre las solicitudes, así que después de realizar la operación en calcular.php, el valor de la pantalla se actualizará en calculadora.php.
## 5.	Actualización de la pantalla (valor de $_SESSION['pantalla']):
El valor que se muestra en la pantalla (<input type="text" name="pantalla" value="...">) se toma del valor almacenado en $_SESSION['pantalla']. Si no se ha realizado ninguna operación antes, muestra 0. Después de cada operación, este valor se actualiza para reflejar el nuevo número o el resultado de la operación.
## Resumen del flujo de trabajo:
1.	El usuario presiona un botón (número u operación).
2.	El formulario se envía a calcular.php con el valor del botón.
3.	En calcular.php, se procesan los datos y se realiza la operación correspondiente.
4.	La operación actualizada o el valor de la pantalla se guarda en la sesión ($_SESSION['pantalla']).
5.	Se redirige al archivo calculadora.php para que el valor actualizado de la pantalla se muestre.
## ¿Qué pasa con las operaciones?
•	Si presionas números y operaciones, la pantalla va acumulando la operación en una cadena de texto, como 2 + 3 o 5 * 4.
•	Cuando presionas el igual (=), la cadena de texto (por ejemplo, 2 + 3) se evalúa con la función eval(), y el resultado de la operación se muestra en la pantalla.
