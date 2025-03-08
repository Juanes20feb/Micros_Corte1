# Micros_Corte1
## Integrantes: Juan Esteban Monroy Moya - 136851 / Alison Daniela Vera Rocha - 131212 / Shirley Bohorquez Gil - 131164
### Introducción
En este laboratorio se llevó a cabo la implementación de una Unidad Aritmético-Lógica (ALU) utilizando el microcontrolador PIC18F45K22. La ALU es un componente fundamental en los sistemas digitales, ya que permite realizar operaciones matemáticas y lógicas esenciales para el procesamiento de datos.

### Objetivo General
Desarrollar una ALU en el microcontrolador PIC18F45K22 para ejecutar operaciones de suma, resta, multiplicación, división, AND y OR. La implementación se realizará en lenguaje C dentro del entorno MPLAB X, asegurando su correcto funcionamiento mediante pruebas prácticas.

### Objetivo Especifico
* Escribir y programar el código de la ALU en lenguaje C utilizando MPLAB X y el compilador XC8, garantizando que realice correctamente las operaciones aritméticas y lógicas especificadas.
* Aprender a transferir el código en el microcontrolador PIC18F45K22 mediante el programador PICkit 3.
* Conectar correctamente las conexiones entre el PICkit 3 y el microcontrolador, asegurando una alimentación adecuada, una correcta configuración de los pines y del entorno de programación para evitar errores en la comunicación y ejecución del código.
### Codigo

Para poder visualizar el codigo [Haz clic aquí](https://github.com/Juanes20feb/Micros_Corte1/blob/main/script.py)

#### Explicacion palabras reservadas

`#include <xc.h>`: Es una librería específica para los microcontroladores PIC. Esta librería contiene los registros y configuraciones necesarias para manejar los periféricos del PIC18F45K22.

`#define _XTAL_FREQ 4000000`: Define la frecuencia del oscilador en 4 MHz. Es necesaria para el uso de la función `__delay_ms()`.

`unsigned char`: Palabra clave para declarar una variable de 8 bits. Con esta palabra reservada se declararon 4 variables:

`main()`: Es la función principal que se ejecuta al iniciar el programa. En esta funcion se 

`Void()`: Es el encargado de llamar funciones.

`TRIS`: Registro que determinan si un pin es entrada (1) o salida (0).

`LAT`: Registro que controlan la salida de los pines.

`switch-case`: Evalúa una variable y ejecuta el código del `case` que coincida, usando `break` para evitar que siga ejecutando otros casos. Si no hay coincidencia, se usa `default`.

* case 0: F_S(); → Suma.
* case 1: F_R(); → Resta.
* case 2: F_A(); → AND.
* case 3: F_O(); → OR.
* case 4: F_M(); → Multiplicación.
* case 5: F_D(); → División.

`__delay_ms()`: Antirebote

### Explicación del código

El código implementa una ALU en un microcontrolador PIC18F45K22 usando leguaje C. Configura los puertos (`CONF_PUERTOS`), inicializa variables, y sigue una rutina (`RUTINA`) que espera una señal (`FUNCION_ENTER`), lee dos operandos (`LEER_OPERANDO_1` y `LEER_OPERANDO_2`), y selecciona una operación (`LEER_OPERACION`) usando `switch-case`. Según el valor de selector, realiza suma, resta, AND, OR, multiplicación o división. Finalmente, muestra los valores y el resultado en los puertos (`MOSTRAR_RESULTADO`).

`
