[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=19351781&assignment_repo_type=AssignmentRepo)
# Proyecto final 


 

## Intregrantes

[Juan Esteban Monroy Moya - 136851](https://github.com/Juanes20feb)

[Shirley Katherin Bohorquez Gil - 131164](https://github.com/Shirleyb0440)

[Alison Daniela Vera Rocha - 131212](https://github.com/Alisondaniela-bot)


## Documentación


### Introducción

Este proyecto presenta el diseño e implementación de un sistema de monitoreo de temperatura basado en el microcontrolador PIC18F45K22. Se emplea un sensor analógico LM35, una pantalla LCD 16x2, un buzzer y un LED como alerta sonora y visual. El objetivo es activar una alarma cuando la temperatura supere los 40 °C. El sistema se desarrolló inicialmente en Proteus para pruebas de simulación y posteriormente fue implementado en una protoboard. Aunque no ofrece medición en tiempo real de alta precisión, cumple una función educativa y prototípica.


## Objetivo general

Diseñar e implementar un sistema de advertencia de temperatura de bajo costo, basado en un microcontrolador PIC18F45K22 y un sensor LM35, que permita visualizar el valor de temperatura en una pantalla LCD y activar una alarma y un led cuando se supere un umbral definido (40 °C).

## Objetivos especificos

-Desarrollar la simulación del circuito en Proteus, integrando el sensor LM35, el microcontrolador PIC18F45K22, una pantalla LCD 16x2, un buzzer y un LED.

-Programar el microcontrolador para adquirir la señal analógica del LM35 mediante el módulo ADC, convertirla a temperatura en grados Celsius y mostrarla en la pantalla LCD.

-Establecer una lógica de control que active el buzzer y el LED cuando la temperatura supere los 40 °C.

-Implementar físicamente el circuito en protoboard para verificar su funcionamiento práctico y compararlo con la simulación.

## Metodología

### Componentes utilizados

Sensor de temperatura LM35: Dispositivo analógico que proporciona una salida lineal proporcional a la temperatura ambiente. Su sensibilidad es de 10 mV por grado Celsius.

Microcontrolador PIC18F45K22: Unidad de control principal del sistema. Se encarga de adquirir la señal analógica del sensor mediante su conversor analógico-digital (ADC), procesarla y tomar decisiones lógicas de salida.

Pantalla LCD 16x2: Módulo de visualización donde se muestra el valor de temperatura en grados Celsius.

Buzzer (zumbador piezoeléctrico) y LED rojo: Actúan como indicadores de alerta. Se activan simultáneamente cuando la temperatura medida supera el umbral de 40 °C.

### Diseño y montaje del sistema

El proceso de desarrollo del sistema se dividió en dos fases:

## Simulación

Se realizó inicialmente un diseño del circuito en el entorno de simulación Proteus, permitiendo validar la lógica del sistema sin necesidad de hardware físico. En primeer monto se uso DS18820 se conectó a una de las entradas analógicas del PIC18F45K22. La señal analógica fue digitalizada utilizando el módulo ADC del microcontrolador y convertida internamente a grados Celsius. El valor resultante se mostró en la pantalla LCD, y si superaba los 40 °C, el microcontrolador activaba una salida digital para encender el buzzer y el LED.

## Implementación física

Tras validar el sistema en simulación, se construyó el circuito en una protoboard. El PIC18F45K22 se ubicó en el centro, conectado a los demás componentes con jumpers. El sensor LM35, posicionado para medir la temperatura ambiente, se enlazó al ADC del microcontrolador.

Una LCD 16x2 externa muestra la temperatura en °C, con un potenciómetro para ajustar el contraste. Un buzzer y un LED rojo, conectados a una salida digital, se activan si la temperatura supera los 40 °C.

## Resultados

Durante las pruebas en simulación y en protoboard, se verificó que el sistema puede mostrar correctamente temperaturas aproximadas. Por ejemplo, en una prueba, se mostró un valor de 24.4 °C. Cuando se aumentó la temperatura (simulada), el buzzer y el LED se activaron como respuesta. Aunque no se trata de un sistema de precisión profesional, demuestra el funcionamiento esperado

#### Visualización del código - Parte 1

* Si deseas visualizar el código del programa principal [Haz clic aquí](main_parte1.c)

* Si deseas visualizar el código que contiene las funciones necesarias para configurar y operar el PWM en el PIC [Haz clic aquí](pwm_parte1.c)

* Si deseas visualizar el código que contiene el encabezado con los prototipos de las funciones [Haz clic aquí](pwm_parte1.h)

* * Si deseas visualizar el código del programa principal de la parte 1 [Haz clic aquí](main_parte1.c)

#### Visualizacion del codigo - Parte 2

* Si deseas visualizar el código del programa principal [Haz clic aquí](main_parte2.c)

* Si deseas visualizar el código que contiene las funciones necesarias para configurar y operar el PWM en el PIC [Haz clic aquí](pwm_parte2.c)

* Si deseas visualizar el código que contiene las funciones necesarias para configurar y operar el ADC en el PIC [Haz clic aquí](ADC_parte2.c)

* Si deseas visualizar el código que contiene el encabezado con los prototipos de las funciones del PWM [Haz clic aquí](pwm_parte2.h)

* Si deseas visualizar el código que contiene el encabezado con los prototipos de las funciones del ADC [Haz clic aquí](ADC_parte2.h)

#### EXPLICACIÓN CÓDIGO:

##### PWM_PARTE1.H

* `#include <xc.h>`: Es la librería principal del compilador XC8, la cual proporciona acceso a todos los registros especiales del microcontrolador como TRIS, PORT, LAT, TMR0, PR2, etc.

* `#define _XTAL_FREQ 64000000UL`: Definicion de la frecuencia del oscilador a 64 MHz. `UL` indica que es un número unsigned long.

* `#define PWM_OUTPUT_TRIS  TRISC2`: Definición del pin de salida C2 que en este caso se usara para la salida del PWM.

###### Declaración de funciones

`void setupPWM(void);`  
`void setDuty(unsigned char val);`  
`void setupTimer0(void);`  

Estas líneas son declaraciones de funciones, también conocidas como prototipos, las cuales se implementarán en el archivo pwm_parte1.c. En primer lugar, la función `setupPWM(void)` será la encargada de configurar el módulo PWM. Por otro lado, la función `setDuty(unsigned char val)` se encargará de cambiar el duty cycle, es decir, el ciclo de trabajo. Finalmente, la función `setupTimer0(void)` será la responsable de realizar las interrupciones.

##### PWM_PARTE1.C

* `#include "pwm.h"`: Libreria personalizada creada en el cual se definieron funciones tales como `setupPWM()` y `setDuty()`.

* `volatile unsigned char duty = 0;`: //Variable global la cual va a definir el ancho que tiene el PWM

###### Creación de la rutina de interrupciones

`void __interrupt() ISR(void) {` // Es la función que se ejecuta cuando ocurre una interrupción.  
    `if (INTCONbits.TMR0IF) {` // Verifica si la interrupción fue generada por el Timer0.  
        `TMR0 = 3036;` // Reinicia el contador para que vuelva a contar el tiempo para generar otra interrupción en 100ms.                 
        `duty += 20;` // Aumenta el ciclo de trabajo.                
        `if (duty > 255) duty = 0;` // Si el ciclo de trabajo sobrepasa 255, se reinicia a 0 el PWM de 8 bits.  
        `setDuty(duty);` // Actualiza el PWM con el nuevo valor.            
        `INTCONbits.TMR0IF = 0;` //Limpia la bandera de interrupción.     
    `}`  
`}`  

Esta parte del código define una rutina de interrupción que se ejecuta automáticamente cuando Timer0 alcanza un valor que indica que han transcurrido aproximadamente 100 ms. En la rutina, se realiza una verificación para ver si la interrupción fue causada por Timer0, y si es así, el temporizador se recarga con el valor 3036 para mantener el intervalo constante. Luego, la variable duty, que representa el ciclo de trabajo de la señal PWM, aumenta en 20 unidades. Si el valor supera 255 (el límite de PWM de 8 bits), se restablecerá a 0 y comenzará de nuevo. Luego, el valor PWM se actualiza utilizando la función setDuty(duty) para reflejar el nuevo ciclo de trabajo en la señal de salida. Finalmente, cuando Timer0 alcanza nuevamente el tiempo programado, el indicador de interrupción (TMR0IF) se borra para permitir que la rutina se ejecute nuevamente.

###### Configuración del PWM

`void setupPWM(void) {`  
    `PWM_OUTPUT_TRIS = 0;`           // Se establece RC2 como salida  
    `PR2 = 255;`                     // Es el máximo valor del periodo PWM  
    `CCP1CON = 0b00001100;`          // Modo PWM en CCP1  
    `CCPR1L = 0;`                    // Se establece que el PWM comienza en 0% duty  
    `T2CON = 0b00000111;`           
`}`  

En esta parte del código se establece la funcion setupPWM(void) para configurar el módulo PWM del microcontrolador. Además, se establece el pin RC2 como salida. Luego, se asigna el valor máximo (255) al registro PR2, lo que define el periodo del PWM. A continuación, se configura el módulo CCP1 en modo PWM mediante el registro CCP1CON = 0b00001100. El registro CCPR1L se inicializa en 0, lo que significa que el ciclo de trabajo (duty cycle) comienza en 0%, es decir, sin salida activa. Finalmente, el registro T2CON = 0b00000111 habilita el temporizador 2 y configura su prescaler, el cual es necesario para que funcione el PWM, ya que este temporizador determina la frecuencia de la señal.

* `void setDuty(unsigned char val) {`
    `CCPR1L = val;`
`}` 

Esta pequeña parte Cambia el valor de CCPR1L, que es el registro que define el ciclo de trabajo del PWM.

###### Configuración del Timer 

`void setupTimer0(void) {`
    `T0CON = 0b10000111;`         // Timer0 ON, en prescaler 1:256
    `TMR0 = 3036;`                // Carga inicial para generar 100ms
    `INTCONbits.TMR0IE = 1;`      // Habilita interrupción por Timer0
    `INTCONbits.TMR0IF = 0;`      // Limpia la bandera
    `INTCONbits.GIE = 1;`         // Habilita todas las interrupciones
`}`

En esta parte del código la función setupTimer0(void) sirve para configurar el temporizador Timer0 y hacer que genere una interrupción cada 100 milisegundos. Primero, se activa el temporizador y se ajusta para que cuente más lento usando una división del reloj (T0CON = 0b10000111). Luego, se le da un valor inicial (TMR0 = 3036) para que, al llegar al límite, se cumpla el tiempo deseado. Después, se habilita la interrupción del Timer0 (TMR0IE = 1) y se limpia una bandera (TMR0IF = 0) que indica si ya ocurrió una interrupción. Por último, se activan todas las interrupciones del sistema con GIE = 1, lo que permite que el programa pueda reaccionar cuando se cumplan los 100 milisegundos.

##### Main_parte1.C

###### Configuraciones del pic

* `#pragma config FOSC = INTIO67`:Indica que se usará el oscilador interno y los pines 6 y 7 estarán disponibles como entradas/salidas digitales.
* `#pragma config PLLCFG = ON`: Habilita el uso del PLL para aumentar la velocidad del sistema. El Pll signfica Phase-Locked Loop (Bucle de Enganche de Fase), el cual es un circuito electrónico que permite multiplicar la frecuencia de una señal de reloj. 
* `#pragma config WDTEN = OFF`: Indica desactivar el Watchdog Timer, que es un temporizador de seguridad que podría resetear el sistema si no se reinicia periódicamente.

###### Función main

`void main(void) {`
    `OSCCON = 0b01110000;`         // Se establece el cscilador interno 16MHz
    `OSCTUNEbits.PLLEN = 1;`        // Activa el PLL para pasar 16MHz a 64 MHz
    `setupPWM();`
    `setupTimer0();`
    `while (1) {`
    `}`
`}`

En esta parte del codigo la La función main se encarga de iniciar el sistema del microcontrolador. Primero configura el oscilador interno a 16 MHz, y luego activa el PLL con `OSCTUNEbits.PLLEN = 1` para multiplicar esa frecuencia por 4, alcanzando así 64 MHz. Después, llama a la función `setupPWM()` para configurar el módulo PWM y a `setupTimer0()` para configurar el temporizador que generará interrupciones periódicas. Finalmente, entra en un bucle infinito `while(1)` que mantiene el programa en ejecución, permitiendo que el funcionamiento del PWM y el temporizador ocurra en segundo plano mediante interrupciones.

## Diagramas de flujo - PARTE 1

### DECLARACIÓN DE VARIABLES

![Diagrama Declaracion de variables](PWM_H.jpeg)

### FUNCIONAMIENTO Y CONFIGURACION PWM

![Diagrama FUNCIONAMIIENTO Y CONFIGURACION PWM](PWM_PARTE1.jpeg)

### FUNCION MAIN

![Diagrama Programa principal](FUNCION_MAIN1.jpeg)


## Diagramas de flujo - PARTE 2

### FUNCIONAMIENTO Y CONFIGURACION PWM

![Diagrama FUNCIONAMIIENTO Y CONFIGURACION PWM](CONFIGURACION_PWM2.jpeg)

### FUNCIONAMIENTO Y CONFIGURACION ADC

![Diagrama FUNCIONAMIIENTO Y CONFIGURACION PWM](ADC_C.PNG)

### FUNCION MAIN

![Diagrama Programa principal](FUNCION_MAIN2.jpeg)

## Diagramas obtenidos por el osciloscopio parte 1

### Ciclo de trabajo al 6.247%

![Diagrama 1 - Ciclo de trabajo al 6.247%](scope_5.png)

Para verificar que los datos obtenidos en el osciloscopio concuerdan vamos a realizar el siguiente calculo:

$$ 
\text{Ciclo de trabajo} = \left( \frac{\text{Ancho de pulso}}{\text{Periodo}} \right) \times 100 
$$

Reemplazamos los valores y obtenemos lo soguiente:

$$ 
\text{Ciclo de trabajo} = \left( \frac{\text{16.01uS}}{\text{256.27uS}} \right) \times 100 
$$

$$
\text{Ciclo de trabajo} = 6.247\%
$$ 

Al rectificar el resultado obtenido con el osciloscopio, se puede concluir que el ciclo de trabajo se encuentra en estado alto, durante un 6.247% del tiempo total del periodo.

### Ciclo de trabajo al 26.561%

![Diagrama 2 - Ciclo de trabajo al 26.561%](scope_6.png)

$$ 
\text{Ciclo de trabajo} = \left( \frac{\text{68.04uS}}{\text{256.17uS}} \right) \times 100 
$$

$$
\text{Ciclo de trabajo} = 26.561\%
$$ 

En este caso el ciclo de trabajo se encuentra en estado alto, durante un 26.561% del tiempo total del periodo.

### Ciclo de trabajo al 51.56%

![Diagrama 3 - Ciclo de trabajo al 51.56%](scope_7.png)

$$ 
\text{Ciclo de trabajo} = \left( \frac{\text{132.1uS}}{\text{256.22uS}} \right) \times 100 
$$

$$
\text{Ciclo de trabajo} = 51.56\%
$$ 

En este caso el ciclo de trabajo se encuentra en estado alto, durante un 51.56% del tiempo total del periodo.

### Ciclo de trabajo al 76.563%

![Diagrama 4 - Ciclo de trabajo al 76.563%](scope_8.png)

$$ 
\text{Ciclo de trabajo} = \left( \frac{\text{196.16uS}}{\text{256.21uS}} \right) \times 100 
$$

$$
\text{Ciclo de trabajo} = 76.563\%
$$ 

En este caso el ciclo de trabajo se encuentra en estado alto, durante un 76.563% del tiempo total del periodo.

### Ciclo de trabajo al 93.749%

![Diagrama 5 - Ciclo de trabajo al 93.749%](scope_9.png)

$$ 
\text{Ciclo de trabajo} = \left( \frac{\text{240.2uS}}{\text{256.22uS}} \right) \times 100 
$$

$$
\text{Ciclo de trabajo} = 93.749\%
$$ 

En este caso el ciclo de trabajo se encuentra en estado alto, durante un 93.749% del tiempo total del periodo.

## Diagramas obtenidos por el osciloscopio parte 2

### Ciclo de trabajo al 20% aproximadamente

![Diagrama 1 - Ciclo de trabajo al 20% aproximadamente](scope_0.png)

$$ 
\text{Ciclo de trabajo} = \left( \frac{\text{55.01uS}}{\text{256.09uS}} \right) \times 100 
$$

$$
\text{Ciclo de trabajo} = 21.48\%
$$ 

En este caso el ciclo de trabajo se encuentra en estado alto, durante un 21.48% del tiempo total del periodo.

### Ciclo de trabajo al 40% aproximadamente

![Diagrama 2 - Ciclo de trabajo al 40% aproximadamente](scope_1.png)

$$ 
\text{Ciclo de trabajo} = \left( \frac{\text{103.05uS}}{\text{256.14uS}} \right) \times 100 
$$

$$
\text{Ciclo de trabajo} = 40.23\%
$$ 

En este caso el ciclo de trabajo se encuentra en estado alto, durante un 40.23% del tiempo total del periodo.

### Ciclo de trabajo al 60% aproximadamente

![Diagrama 3 - Ciclo de trabajo al 60% aproximadamente](scope_2.png)

$$ 
\text{Ciclo de trabajo} = \left( \frac{\text{155.11uS}}{\text{256.18uS}} \right) \times 100 
$$

$$
\text{Ciclo de trabajo} = 60.548\%
$$ 

En este caso el ciclo de trabajo se encuentra en estado alto, durante un 60.548% del tiempo total del periodo.

### Ciclo de trabajo al 80% aproximadamente

![Diagrama 4 - Ciclo de trabajo al 80% aproximadamente](scope_3.png)

$$ 
\text{Ciclo de trabajo} = \left( \frac{\text{206.19uS}}{\text{256.25uS}} \right) \times 100 
$$

$$
\text{Ciclo de trabajo} = 80.466\%
$$ 

En este caso el ciclo de trabajo se encuentra en estado alto, durante un 80.466% del tiempo total del periodo.

### Ciclo de trabajo al 100% aproximadamente

![Diagrama 5 - Ciclo de trabajo al 100% aproximadamente](scope_3.png)

$$ 
\text{Ciclo de trabajo} = \left( \frac{\text{249.22uS}}{\text{256.22uS}} \right) \times 100 
$$

$$
\text{Ciclo de trabajo} = 97.265\%
$$ 

En este caso el ciclo de trabajo se encuentra en estado alto, durante un 97.265% del tiempo total del periodo.

## IMPLEMENTACION PARTE 1

![IMPLEMENTACION PARTE 1](IMPLEMENTACION_1.jpeg)

## IMPLEMENTACION PARTE 2

![IMPLEMENTACION PARTE 2](IMPLEMENTACION_2.png)

## Referencias

[1] [ECCI-Microprocesadores-2025-I](https://github.com/DianaNatali/ECCI-Microprocesadores-2025-I-/blob/main/laboratorios/3_lab03/README.md?plain=1)
