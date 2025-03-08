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

`unsigned char`: Palabra clave para declarar una variable de 8 bits.


