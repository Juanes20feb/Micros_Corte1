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
