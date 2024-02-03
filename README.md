# Mini-PIC18F-TRAINER
Tarjeta entrenadora de desarrollo básica con pines libres GPIO, puerto USB CDC Host , pines de programación para PICKIT3 ICSP seleccionables como se muestra a continuacion:

![image](https://github.com/SerCandio/Mini-PIC18F-TRAINER/assets/106831539/cd642af2-6dcd-42de-b466-ebb15fab4111)

<B><I>Figura 1.- Vista general de la entrenadora basica de PIC</I></B>

<h2 dir="auto" tabindex="-1">DESCRIPCION Y CARACTERISTICAS</h2>
<P>Puede visualizar una referencia del plano esquematico de la PCB aqui: <B><A HREF="https://github.com/SerCandio/Mini-PIC18F-TRAINER/blob/main/Esquemas%20Schematic/Min_PIC_Trailer_PDF_BN.pdf">Min_PIC_Trailer_PDF_BN.pdf</A></B></P>

<B>1.-Entrada de Voltaje</B>

La placa Mini-PIC18F-TRAINER se alimenta desde la bornera verde +5V utilizando una fuente externa. No debe usar otro voltaje diferente de 4.9 ~ 5.0 V

<B>2.-Oscilador primario XTAL</B>

Entre los pines OSC1 y OSC2 (RA7 y RA6) esta conectado un cristal de cuarzo de 16MHz para una mayor exactitud en la base de tiempo del ciclo de instruccion(<B>4/FOSC</B>), siendo de rapida ejecucion Aunque este puede ser cambiado por otros cristales de menor frecuencia, un XTAL de 16MHz permite usar todos los perifericos incluido el puerto <B>USB</B> que require una frecuencia derivada de <B>48MHz</B> para alta velocidad(<B>HIGH Speed</B>) y otra de 6MHz para baja velocidad (<B>LOW Speed</B>)

<B>3.-Oscilador secundario</B>

Entre los pines SOSCO y SOSCI (RC0 y RC1) esta conectado un cristal de 32.768KHz que alimenta el temporizador 1 o TIMER 1 del microcontrador PIC18F. Permite un calculo preciso de bases de tiempo real de 1 segundo o submultiplos (ex. 1ms) , lo que es de utilidad para la temporizacion de tareas cuando se trabaja con RTOS (ver <B><A HREF="https://github.com/SerCandio/Microcontrolador-PIC18F/blob/main/LIBRERIAS%20PIC18/RTOS.h">Libreria RTOS</A></B>) dado que incluso en modo SLEEP puede temporizar eventos de interrupcion donde se despierta la CPU (ver <B><A HREF="https://github.com/SerCandio/Microcontrolador-PIC18F/blob/main/LIBRERIAS%20PIC18/TMR1.h">Libreria Timer 1</A></B>)

<B>4.-Boton de RESET</B>

Se utiliza para re-iniciar el programa en ejecucion. Esta etiquetado como <B>RESET</B>. Esta entrada esta compartida con el PICKIT3 -- > MCLR

<B>5.-LED indicador encendido</B>

Este LED1 de color verde nos indica que la tarjeta por consiguiente el microcontrolador PIC esta siendo aliementado. 

<B>6.-Conector USB Mini Type B </B>

Este USB plug esta directamente conectado a los pines  <B>D+</B> y <B>D-</B> o 24 y 23 del PIC18F. Provee una interfaz de comunicacion de alta velocidad tipo USB- CDC del PIC con la PC que puede actuar como host. Tenga en cuenta que este tipo de comunicacion se monta en un puerto COM de la PC como si se tratase de comunicacion serie UART . 

En este <B><A HREF="https://www.usb.org/">Link</A></B> se habla mas acerca de la especificacion USB.

<B>7.-Pines de programacion ICSP</B>

El DIP SWITCH SW1 permite dar salida a los pines de programacion mediante la PICKIT3 de encontrarse en la posicion ON. Si no se require re-programar pueden permanecer en OFF , quedando asi protejidos frente a contactos externos no deseados

<B>8.-LED de prueba enchufable</B>

Este USER LED de color azul puede ser conectado  directamente  al pin RD0 si se coloca el jumper encima, permite hacer codigos de prueba (ex. blinkeo ON/OFF), como bandera de error o algun otro uso personalizado que el usuario le pueda dar.

<B>9.-JUMPER Selector de Volaje</B>

Este jumper de tipo <B><I>pin header</I></B> es capaz de seleccionar el voltaje de suministro, la tarjeta <B>Mini-PIC18F Trainer</B> para que sea alimentado por fuente externa (bornera color verde), por la PICKIT 3 o por el USB proveniente de la PC. En nuestro caso :

- Alimentacion por fuente externa (<B>SI</B>)
- Alimentacion por PICKIT (<B>SI</B>)
- Alimentacion por USB (<B>NO</B>)

<h2 dir="auto" tabindex="-1">PRECAUCION <img src="https://github.com/SerCandio/Mini-PIC18F-TRAINER/assets/106831539/ca45f6f3-578d-45d0-bedd-07b2afdd2be8"></h2>

Debe asegurarse que el PICKIT 3 actue como sensor de voltaje en su pin <B><I>VDD</I></B> haciendo en MPLAB (IDE /IPE) como se muestra:

![image](https://github.com/SerCandio/Mini-PIC18F-TRAINER/assets/106831539/b7142562-cb13-4e22-96e4-63deb5a92e8c)

<B><I>Figura 2.- Opciones de alimentacion del apartado "POWER" del IDE</I></B>
<p>Asegurese que la opcion <B><I>Power Tarjet from PICkit3</B></I> este deshabilitada. Caso contrario, podria dañarse el programador o incluso la PC.</p>

<h2 dir="auto" tabindex="-1">COMPONENTES EN PLACA(Descripcion grafica)</h2> 

Podemos visualizar de forma grafica los compoentes en placa incorporados en nuesta entrenadora Mini de PIC18 :

![image](https://github.com/SerCandio/Mini-PIC18F-TRAINER/assets/106831539/3fc8c751-18cd-4fac-ad2a-d8b89baff10f)
<center><B><I>Figura 3.- Componentes basicos: entrenadora basica de PIC</I></B></center>

<h2 dir="auto" tabindex="-1">PRUEBAS Y FUNCIONAMIENTO</h2>
En el siguiente video incrustado podemos ver una prueba de funcionamiento de la placa entrenadora:

[![VIDEO](https://img.youtube.com/vi/uNbUmXdRPzk/0.jpg)](https://www.youtube.com/watch?v=uNbUmXdRPzk)

<h2 dir="auto" tabindex="-1">Nota</h2>
Los archivos de proyecto de EAGLE para poder modificar y/o manufacturar esta PCB estan <B><A HREF="https://github.com/SerCandio/Mini-PIC18F-TRAINER/tree/main/EAGLE%20CAD%20FILES">aqui</A></B>
<h2 dir="auto" tabindex="-1">AUTOR</h2>
- Candiotti L. Sergio (Lima, Peru)
