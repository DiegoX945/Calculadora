``` bash
<?php
session_start();
?>

<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Calculadora PHP</title>
    <link rel="stylesheet" href="css.css">
</head>
<body>
    <div class="calculator-container">
        <form action="calcular.php" method="POST">
            <!-- Pantalla de la calculadora -->
            <input type="text" name="pantalla" id="pantalla" value="<?php echo isset($_SESSION['pantalla']) ? htmlspecialchars($_SESSION['pantalla']) : '0'; ?>" readonly>

            <div class="button-container">
                <!-- Botones de operaciones -->
                <button type="submit" name="operacion" value="C" class="button clear">C</button>
                <button type="submit" name="operacion" value="√" class="button">√</button>
                <button type="submit" name="operacion" value="/" class="button">÷</button>
                <button type="submit" name="operacion" value="*" class="button">×</button>

                <!-- Botones numéricos -->
                <button type="submit" name="operacion" value="7" class="button">7</button>
                <button type="submit" name="operacion" value="8" class="button">8</button>
                <button type="submit" name="operacion" value="9" class="button">9</button>
                <button type="submit" name="operacion" value="-" class="button">-</button>

                <button type="submit" name="operacion" value="4" class="button">4</button>
                <button type="submit" name="operacion" value="5" class="button">5</button>
                <button type="submit" name="operacion" value="6" class="button">6</button>
                <button type="submit" name="operacion" value="+" class="button">+</button>

                <button type="submit" name="operacion" value="1" class="button">1</button>
                <button type="submit" name="operacion" value="2" class="button">2</button>
                <button type="submit" name="operacion" value="3" class="button">3</button>
                <button type="submit" name="operacion" value="=" class="button equal">=</button>

                <button type="submit" name="operacion" value="0" class="button">0</button>
            </div>
        </form>
    </div>
</body>
</html>
```
