# ⋆⭒˚.⋆ └[∵┌] - Grupo 05 - Conexión sonora a distancia - [┐∵]┘ ⋆.˚⭒⋆

Lunes 13 Abril 2026

***

## Integrantes "Sonoridad":

* [Felipe Caurapan](https://github.com/felipecaurapan): 
* [Camila Parada](https://github.com/Camila-Parada): Código, Bill of Materials, Redacción de texto
* [Vania Paredes](https://github.com/paredesvania): Código, Circuito, Redacción de texto, Registro

## Descripción del proyecto

## Bill of materials

| Componentes         | Tipo  | Cantidad | Precio  | Enlace            |
| ------------------- | ----- | -------- | ------- | ----------------  |
| Arduino UNO R4 WiFi | Placa de desarrollo | 2   | $38.990 | <https://mcielectronics.cl/shop/product/43402/> |
| Mini Protoboard 400 Puntos | Placa prototipado | 2  | $1.500 | <https://afel.cl/products/mini-protoboard-400-puntos> |
| Potenciómetro 1K Ohm | Componente | 1 | $1.490 | <https://mcielectronics.cl/shop/product/potenciometro-1k-ohm/> |
| Cable Dupont Macho Macho 10cm | Cable | Pack 40 | $2.590 | <https://mcielectronics.cl/shop/product/cable-dupont-macho-macho-20cm-pack-40-unidades/> |
| Altavoz 8 Ohm 1W | Componente | 1 | $ 2.590 | <https://www.mechatronicstore.cl/altavoz-8-ohm-1w> |
| Transistores NPN 2N2222 | Componente | Pack 10 | $1.228 | <https://altronics.cl/pack-10-transistor-2n2222> |
| Resistencia 1k Ohm 1/2 watts | Componente | Pack 5 |  $500 | <https://triacs.cl/accesorios/1101-resistencia-1k-ohm-12w-5-unid-.html> |

## Conexiones de hardware

![conexiones](./imagenes/conexiones.png)

## Código usado con Adafruit IO

### código para enviar

```cpp
// ============================================================
// EMISOR - Lee potenciómetro y envía valor de volumen a Adafruit IO
// Arduino R4 WiFi
// ============================================================

#include "config.h"   // Credenciales WiFi y Adafruit IO

// --- CONFIGURACIÓN DEL POTENCIÓMETRO ---
// Conexión:
//   Pin izquierdo  → GND
//   Pin central    → A0  (señal analógica)
//   Pin derecho    → 5V
const int PIN_POTENCIOMETRO = A0;

// --- FEED DE ADAFRUIT IO ---
// Mismo nombre exacto que usa el receptor
AdafruitIO_Feed *feedVolumen = io.feed("paredesvania-volumen");

// --- VARIABLE GLOBAL ---
// Guarda el último valor enviado para no repetir envíos innecesarios
int ultimoVolumen = -1;

// ============================================================
void setup() {

  // Iniciar comunicación serial a 115200 baud
  Serial.begin(115200);

  // Esperar a que el Monitor Serial esté listo
  while (!Serial);

  Serial.print("Conectando a Adafruit IO...");

  // Conectar usando las credenciales del config.h
  io.connect();

  // Esperar hasta que la conexión sea exitosa
  while (io.status() < AIO_CONNECTED) {
    Serial.print(".");
    delay(500);
  }

  // Confirmar conexión
  Serial.println();
  Serial.println(io.statusText());
  Serial.println("Listo para enviar volumen!");
}

// ============================================================
void loop() {

  // Mantener conexión activa con Adafruit IO
  io.run();

  // --- LEER EL POTENCIÓMETRO ---
  // analogRead devuelve 0–1023 según la posición del potenciómetro
  int lecturaRaw = analogRead(PIN_POTENCIOMETRO);

  // Convertir 0–1023 a 0–100 (porcentaje de volumen)
  int volumen = map(lecturaRaw, 0, 1023, 0, 100);

  // Mostrar en Monitor Serial para verificar
  Serial.print("Lectura cruda: ");
  Serial.print(lecturaRaw);
  Serial.print(" -> Volumen: ");
  Serial.print(volumen);
  Serial.println("%");

  // --- ENVIAR SOLO SI EL VALOR CAMBIÓ ---
  // Evita saturar el feed de Adafruit IO con valores repetidos
  if (volumen != ultimoVolumen) {

    Serial.print("Enviando: ");
    Serial.println(volumen);

    // Publicar el valor en el feed
    feedVolumen->save(volumen);

    // Actualizar el último valor enviado
    ultimoVolumen = volumen;
  }

  // Pausa de 200ms entre lecturas
  delay(200);
}
```

### código para recibir

```cpp
// rellenar
```

## investigaciones individuales

rellenar en el mismo orden que los integrantes del grupo

[persona-01.md](./persona-01.md)
[persona-02.md](./persona-02.md)
[persona-03.md](./persona-03.md)

## bibliografía

* <https://learn.adafruit.com/series/adafruit-io-basics>
* <https://github.com/adafruit/Adafruit_IO_Arduino>
* <https://github.com/adafruit/Adafruit_IO_Arduino/blob/master/examples/adafruitio_01_subscribe/adafruitio_01_subscribe.ino>
