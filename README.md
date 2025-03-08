# Micros_Corte1
## Integrantes: Juan Esteban Monroy Moya - 136851 / Alison Daniela Vera Rocha - 131212 / Shirley Bohorquez Gil - 131164

### INTRODUCCION

En este proyecto, desarrollamos un circuito basado en el microcontrolador **PIC18F4XK22**, montado en una **protoboard** para facilitar su prueba y experimentación. El objetivo principal es diseñar una base de hardware que permita implementar una **Unidad Aritmético-Lógica (ALU)**, aprovechando las capacidades del microcontrolador para realizar operaciones aritméticas y lógicas.  

Para el funcionamiento del PIC, utilizamos un **oscilador de cristal de 4 MHz**, que proporciona la señal de reloj necesaria. Además, incluimos un **programador PICkit**, que nos permite cargar el código en el microcontrolador. El circuito también cuenta con resistencias, capacitores y diodos LED, los cuales nos ayudan a verificar su correcto funcionamiento.  


### OBJETIVO GENERAL

Desarrollar una ALU en el microcontrolador PIC18F45K22 para ejecutar operaciones de suma, resta, multiplicación, división, AND y OR. La implementación se realizará en lenguaje C dentro del entorno MPLAB X, asegurando su correcto funcionamiento mediante pruebas prácticas.

### OBJETIVOS ESPECIFICOS

* Escribir y programar el código de la ALU en lenguaje C utilizando MPLAB X y el compilador XC8, garantizando que realice correctamente las operaciones aritméticas y lógicas especificadas.
* Aprender a transferir el código en el microcontrolador PIC18F45K22 mediante el programador PICkit 3.
* Conectar correctamente las conexiones entre el PICkit 3 y el microcontrolador, asegurando una alimentación adecuada, una correcta configuración de los pines y del entorno de programación para evitar errores en la comunicación y ejecución del código.
### MARCO TEORICO

La Unidad Aritmético-Lógica (ALU) es un componente fundamental dentro de los sistemas digitales y microprocesadores. Su función principal es ejecutar operaciones matemáticas y lógicas sobre los datos proporcionados por la memoria o los registros internos de un procesador. En el caso de una calculadora de 4 bits, la ALU es responsable de realizar operaciones como suma, resta, AND, OR y XOR, manejando operandos de 4 bits, en la siguiente tabla se reflejara las combinaciones para cada operacion:

![Tabla de operaciones](https://github.com/Juanes20feb/Micros_Corte1/blob/Alison/WhatsApp%20Image%202025-03-08%20at%2012.04.18%20AM.jpeg)

### DIAGRAMA

![Diagrama](https://github.com/Juanes20feb/Micros_Corte1/blob/Alison/imagen_2025-03-08_005011209.png)

##### Microcontrolador PIC18LF4XK22: 

Es el elemento principal del circuito, encargado de procesar datos y ejecutar instrucciones.

##### PICkit 3:  

Se usa para programar el microcontrolador y cargar el código de la aplicación.

##### Cristal de 4 MHz con condensadores de 33pF:

Se utiliza para proporcionar una señal de reloj estable al microcontrolador.

##### Resistencia de 2kΩ, condensador de 100nF y pulsador en el MCLR: 

Se implementa un circuito de reset para evitar que el PIC se reinicie accidentalmente.

##### Dip Switch: 
Se usan para asignar el numero de operacion 1 , 2 y la operacion.

##### pulador que esta en el Rb4:

Este ayuda guardar el valor asignado en el dip switch.

##### Leds y resistencias:

Indicadores visuales que representan el estado del sistema o los resultados de alguna de las operaciones.

### MONTAJE

![Diagrama](https://github.com/Juanes20feb/Micros_Corte1/blob/Alison/imagen_2025-03-08_010035213.png)

 ### CODIGO

Para poder visualizar el codigo [Haz clic aquí](https://github.com/Juanes20feb/Micros_Corte1/blob/main/script.py)

#### EXPLICACIÓN PALABRAS RESERVADAS

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

### Explicación del código de forma general

El código implementa una ALU en un microcontrolador PIC18F45K22 usando leguaje C. Configura los puertos (`CONF_PUERTOS`), inicializa variables, y sigue una rutina (`RUTINA`) que espera una señal (`FUNCION_ENTER`), lee dos operandos (`LEER_OPERANDO_1` y `LEER_OPERANDO_2`), y selecciona una operación (`LEER_OPERACION`) usando `switch-case`. Según el valor de selector, realiza suma, resta, AND, OR, multiplicación o división. Finalmente, muestra los valores y el resultado en los puertos (`MOSTRAR_RESULTADO`).

### Conclusiones
Se concluye que se logró comprender el funcionamiento teórico de una ALU de 4 bits. Sin embargo, por limitaciones de tiempo y dificultades en la interpretación del código, no se pudo verificar completamente su implementación en el microcontrolador.
