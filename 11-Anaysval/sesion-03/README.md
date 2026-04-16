# sesion-03

lunes 23 marzo 2026

El objetivo principal del proyecto es lograr comunicación entre dos dispositivos distintos, (Arduino Uno R4 WiFi) (Raspberry Pi Pico 2 W)

### Microcontroladores y plataformas

### Raspberry Pi Pico 2 W

Es una placa pensada para proyectos electrónicos e IoT, económica y eficiente.

Características:

- Chip: RP2350
- Doble núcleo
- WiFi (802.11n)
- Bluetooth 5.2

La fundación Raspberry Pi nace en 2009 con el objetivo de hacer la computación más accesible.

### Arduino vs Raspberry Pi

### Arduino

- Microcontrolador
- Más simple
- Ideal para tareas específicas
- Se programa en C++

### Raspberry Pi (Pico)

- Sistema más completo
- Más potente
- Permite procesos más complejos
- Se puede programar en Python o MicroPython
  
### Otras plataformas

Existen otras herramientas relacionadas con electrónica y arte digital:

- BeagleBoard - hardware open source
- Bela - audio en tiempo real
- Daisy (Electro-Smith) - audio avanzado
- Monome / Critter & Guitari - instrumentos digitales
- NIME - investigación en interfaces musicales
  
### Entorno de desarrollo

Se trabaja con Visual Studio Code.

Lenguajes usados:

- C++
- Python
- MicroPython

Conceptos importantes:

- Extensiones - agregan funciones
- SDK - herramientas para desarrollar
- Build - proceso de compilación del código
  
### Estructura de un proyecto

Archivos comunes:

- `.vscode` - configuración  
- `build` - archivos compilados  
- `.gitignore` - archivos no compartidos  
- `main.cpp` - archivo principal  
- `CMakeLists.txt` - configuración de compilación 

### Lógica de programación

### Arduino
 ```cpp
void setup() {
  // se ejecuta una vez
}

void loop() {
  // se repite siempre
}
```

### Raspberry Pi Pico

```cpp
int main() {
    while (true) {
        // bucle infinito
    }
}
```

En Arduino se usa setup() y loop(), mientras que en Raspberry Pi Pico todo comienza en main() y se ejecuta en orden.

### Protocolos de comunicación

### SPI

- Comunicación rápida
- Usa varios pines
- Ideal para pantallas
  
### I2C

- Usa menos cables
- Más simple
- Permite conectar varios dispositivos

### Para que la comunicación funcione:

- Ambos dispositivos deben estar conectados
- Deben usar el mismo protocolo o sistema de comunicación
- Uno envía datos y el otro los recibe correctamente

---

Solemne 1: 6 de abril

### Pauta

La nota tiene 1 punto base más 6 puntos evaluados.

Los 3 primeros puntos son criterios individuales, los 3 siguientes puntos son criterios grupales.

### Individual:

1 punto por calidad de la presentación oral

1 punto por bitácora personal textual y visual del trabajo en clases e investigación personal

1 punto por aportes al README.md grupal de texto y visuales explicativas, por las referencias

### Grupal:

1 punto por diagrama de flujo del proyecto

1 punto por calidad del código fuente para enviar y para recibir

1 punto por funcionamiento del sistema

1 punto: el sistema puede enviar y recibir mensajes

0.5 puntos: el sistema solamente envía o recibe mensajes

0.3 puntos: intentos de enviar o recibir mensajes, aunque no funcionen

0.0 puntos: los intentos no se entienden, no tienen comentarios, están desordenados
