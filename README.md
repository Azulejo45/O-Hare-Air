

# ┕━━O-Hare-Air━━┙ 
- Proyecto de sistema de ventilación automatizado y controlado por ESP32-C3 Super Mini. Equipado con control PWM mediante MOSFET, sensor de temperatura DS18B20 y regulación de voltaje eficiente.
.

### -----〈 Autores  〉-----\

> ⋆ˊˎ-Velazquez Joaquim

> ---30/09/2026---\


### •---Especificaciones generales 
\
˚₊· ͟͟͞͞  Control de velocidad: PWM por MOSFET (IRLZ44N).\

˚₊· ͟͟͞͞  Alimentación principal: 12V / 2A (Entrada Jack DC).\

˚₊· ͟͟͞͞  Regulación interna: 5V mediante módulo Mini360.\

˚₊· ͟͟͞͞  Material de la estructura/gabinete: PLA.

________________________________ \
\
\
.
### Objetivo del proyecto
\
El objetivo principal de este proyecto es diseñar e implementar un sistema de ventilación inteligente regulado por temperatura. Utilizando un microcontrolador ESP32-C3 Super Mini, una etapa de potencia con MOSFET y un sensor DS18B20, el sistema ajusta dinámicamente las revoluciones del ventilador de forma automática para mantener una temperatura óptima de manera eficiente.

# ⌒⌒⌒⌒⌒⌒⌒⌒┈୨•୧┈⌒⌒⌒⌒⌒⌒⌒⌒
\
\
\
\
### ˗ˏˋ ꒰ Este proyecto fue realizado con algunos componentes en donde se puede llegan a encontrar: ꒱ ˎˊ˗

 -  ESP32-C3 Super Mini.

> Memoria: 400 KB SRAM, 4 MB Flash. Conectividad: Wi-Fi (2,4 GHz).

> Bluetooth 5.0 LE (Low Energy).

### Alimentación: Funciona a 3,3 V con entrada USB-C de 5 V.

- Sensor de Temperatura: DS18B20 (KY-001).

> Voltaje de operación: 3.0V - 5.5V.

> Rango de medición: -55°C a +125°C.

-  MOSFET de Potencia: IRLZ44N.

> Tipo: Canal N (Logic-Level).

> Voltaje Drain-Source max: 55V.

> Corriente continua de Drain: 47A.

- Diodo de protección: 1N4007.

> Uso: Diodo flyback en antiparalelo con el motor para suprimir picos inductivos.

> Regulador de voltaje: Módulo Mini360.

> Tipo: Step-Down Buck Converter.

> Voltaje de entrada: 4.75V - 23V.

> Voltaje de salida ajustable: 5V.
\
\
## ────────────∘₊✧────────────
\
\
.
## ╔════╡Componentes utilizados╞════╗
➸ ESP32-C3 Super Mini.

➸ Sensor DS18B20.

➸ MOSFET IRLZ44N.

➸ Diodo 1N4007.

➸ Módulo Mini360 (Step-Down 5V).

➸ Jack DC y Borneras de conexión.

\
\
\
.
## Diseño del circuito
<img width="920" height="514" alt="Captura desde 2026-09-30 07-56-40" src="https://github.com/user-attachments/assets/d9188fee-6da7-4d08-b692-8fa9af606d3c" />
\

### Descripcion del funcionamiento
\
El sistema monitorea de manera constante la temperatura ambiental o del componente a través del sensor DS18B20 conectado al ESP32-C3. Mediante un algoritmo de control, el microcontrolador varía el ciclo de trabajo de la señal PWM aplicada a la compuerta (Gate) del MOSFET IRLZ44N.
De esta forma, la velocidad del ventilador de 12V aumenta o disminuye de forma proporcional a la temperatura registrada, garantizando una disipación eficiente y un funcionamiento automatizado. El diodo 1N4007 protege al circuito de las corrientes inversas generadas por el motor al apagarse o variar su velocidad.

## Esquematico

<img width="511" height="418" alt="Captura desde 2026-09-30 07-56-06" src="https://github.com/user-attachments/assets/0e5f66bd-74d3-4031-bc84-999195ec9045" /> /

## Layout de PCB

<img width="870" height="517" alt="Captura desde 2026-09-30 08-55-36" src="https://github.com/user-attachments/assets/d040f0bd-a03c-40d3-9ced-9f8c89b9ab27" />

\

## Pasos a seguir para el armado del sistema

### -|Soldar los componentes en la PCB en el siguiente orden recomendado:

1. Resistencias y diodos SMD/THT (incluyendo el diodo 1N4007).

2. Borneras de conexión y Jack DC.

3. Módulo Mini360 (previamente calibrado a 5V de salida).

4. Zócalos o pines para el ESP32-C3 Super Mini y el MOSFET.

# Medidas de seguridad.
## .°-> Verifique la polaridad de la fuente de alimentación de 12V antes de conectarla al Jack DC para evitar daños en los reguladores.

## .°-> Asegúrese de que el diodo 1N4007 esté correctamente orientado (con el cátodo apuntando hacia la línea positiva de alimentación del motor).

# -|Gabinete y Montaje 3D
Descargar el modelo 3D del soporte o gabinete ubicado en la carpeta de HARDWARE.

Imprimir la pieza en PLA.

Ensamblar la placa de circuito impreso dentro de la estructura junto con el ventilador y el sensor DS18B20 en la zona de medición.

## -|Código y Firmware
El código establece las lecturas del sensor de temperatura y calcula la salida PWM necesaria para gobernar el MOSFET.

Principales tareas del programa:
.°-> Lectura periódica de temperatura mediante la librería 1-Wire / DallasTemperature.
.°-> Mapeo de la temperatura leída a un rango de ciclo de trabajo PWM (0% a 100%).
.°-> Aplicación de la señal de control hacia el pin correspondiente del ESP32-C3.

## -|Compilacion/Carga
Utilice un cable USB tipo C para conectar el ESP32-C3 a un ordenador. Se recomienda utilizar el entorno de desarrollo PlatformIO o Arduino IDE.\

Seleccione la placa ESP32-C3 Dev Module (o Super Mini equivalente) y el puerto COM correspondiente.\

Verifique que estén instaladas las librerías necesarias para el manejo del sensor de temperatura.\

Compile y cargue el código en el microcontrolador.

## -[Librerías principales
OneWire

DallasTemperature

## -[Datasheets/Referencias
