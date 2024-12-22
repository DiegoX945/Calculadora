``` bash
<?php
session_start();  // Inicia la sesión

// Inicializa la variable pantalla si no existe
if (!isset($_SESSION['pantalla'])) {
    $_SESSION['pantalla'] = '0';  // Si no hay nada, establece '0'
}

// Verifica si se ha enviado el formulario
if ($_SERVER['REQUEST_METHOD'] === 'POST') {
    $pantalla = $_SESSION['pantalla'];  // Obtén el valor actual en pantalla
    $operacion = $_POST['operacion'];   // Obtén la operación que se ha seleccionado

    // Si la operación es C, limpia la pantalla
    if ($operacion === 'C') {
        $_SESSION['pantalla'] = '0';
    }
    // Si la operación es un número, concatena el número a la pantalla
    elseif (is_numeric($operacion)) {
        if ($pantalla == '0') {
            $_SESSION['pantalla'] = $operacion;  // Si es 0, reemplaza
        } else {
            $_SESSION['pantalla'] .= $operacion;  // De lo contrario, concatena
        }
    }
    // Si la operación es una operación aritmética
    elseif (in_array($operacion, ['+', '-', '*', '/'])) {
        $_SESSION['pantalla'] .= " $operacion ";  // Agrega la operación a la pantalla
    }
    // Si la operación es igual (=), evalúa la operación
    elseif ($operacion === '=') {
        try {
            $_SESSION['pantalla'] = eval('return ' . $_SESSION['pantalla'] . ';');  // Evalúa la expresión
        } catch (Exception $e) {
            $_SESSION['pantalla'] = 'Error';
        }
    }
    // Si la operación es raíz cuadrada
    elseif ($operacion === '√') {
        $_SESSION['pantalla'] = sqrt($_SESSION['pantalla']);
    }
}

// Redirige al archivo calculadora.php para mostrar el resultado actualizado
header("Location: calculadora.php");
exit();
?>
```
