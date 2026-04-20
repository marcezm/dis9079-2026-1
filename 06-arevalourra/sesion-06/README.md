# sesion-06

lunes 13 abril 2026

# Clase: Sensor Capacitivo con Arduino

## Concepto base: Capacitancia

Entre dos elementos (ej: manos) existe **aire**, que actúa como medio.
  
El **área** puede ser constante, pero la **distancia es variable**.
  
La **capacitancia cambia según la distancia**.
  
Esto permite **medir proximidad o contacto**.

### Idea clave

> Podemos usar la capacitancia como una forma de medir distancia.



## Ejemplo cotidiano
- Pantallas táctiles de teléfonos:
  
  Detectan cuando te acercas o tocas.
    
  Funcionan midiendo cambios en la capacitancia.
    
- No requiere placas metálicas:
  
  Puede funcionar con el cuerpo humano.
    
  Incluso con objetos con humedad (ej: frutas).



## Aplicaciones

- Sensores táctiles
  
- Interfaces interactivas
  
- Pantallas capacitivas
  
- Instalaciones (ej: museos)



## Arduino y sensor capacitivo

### Placa utilizada
- Arduino Uno R4 WiFi


## Materiales necesarios

- Arduino Uno R4
  
- Cable (conductor simple)
  
- Elementos que alteren el campo eléctrico:
  
  - Mano
    
  - Metal
    
  - Etc.



## Funcionamiento general del sensor

### Rango de valores

- Lejos: ~0
  
- Cerca: ~200
  
- Tocando: ~2000 o más

### Interpretación

Permite definir **rangos de interacción**:
  
  - Lejos
    
  - Cerca
    
  - Contacto



## Concepto clave: Umbral (Threshold)

Define cuándo se considera "contacto".
  
Ejemplo:
  
  - Si valor > 2000 → contacto
    
  - Si valor < 2000 → no contacto

### Importante

El umbral depende del contexto:

  - Humedad
    
  - Entorno
    
 Puede ajustarse dinámicamente.



## Estructura de un proyecto con sensores

### Pasos generales

1. Definir el pin
   
2. Inicializar el sensor
   
3. Leer valores
   
4. Procesar datos
   
5. Tomar decisiones


# Conceptos importantes del código

*include* -> Importa la librería necesaria.


*begin()* -> Inicializa el sensor.


*read()* -> Entrega el valor crudo del sensor.

*print vs println*

- print: imprime en la misma línea
- 
- println: imprime y salta de línea

  
*delay(100)* -> Pausa de 0.1 segundos.

Evita lecturas demasiado rápidas.


## Observaciones importantes

El sensor no solo detecta contacto, también detecta proximidad, incluso con un cable aislado se detecta el cambio de capacitancia

El sistema responde a:

- Distancia
  
- Cambio de campo eléctrico


### Limitaciones

No todos los pines sirven para sensores capacitivos.

Cada pin puede tener múltiples funciones.

Hay límites en cuántos sensores usar simultáneamente.


### Errores comunes

Usar el pin incorrecto

No instalar la librería

No ajustar el umbral

Confundir velocidad del monitor serial (9600 vs 115200)

Pensar que Arduino depende del computador -> El código queda guardado en la placa



## Referente: Theremin

Instrumento electrónico que se toca sin contacto físico

Funciona mediante sensores capacitivos

Se controla con las manos en el aire

Permite modificar sonido a partir de la distancia


## Funcionamiento del Theremin

Antena horizontal controla el volumen

Mano lejos aumenta volumen

Mano cerca disminuye volumen

Contacto genera silencio

Antena vertical controla la frecuencia

La distancia define la altura del sonido

Genera oscilación continua tipo vibrato


## Observación personal — Theremin

![Theremin](./imagenes/etherwave_website_13.jpg)

El Theremin surge como un referente que no solo aparece en la clase, sino también como resultado de una búsqueda personal adicional en torno a formas de interacción no tradicionales. Me interesa particularmente porque rompe completamente con la lógica del contacto físico: no hay botones, no hay superficie, solo un campo invisible que responde al cuerpo. Esto lo convierte en una interfaz extremadamente sensible, donde el gesto, la distancia y la precisión corporal pasan a ser el lenguaje principal.

Desde esa exploración, el Theremin no lo veo solo como un instrumento musical, sino como un sistema de relación entre el cuerpo y el espacio. La mano deja de “tocar” y pasa a “habitar” un rango de influencia, lo que abre posibilidades para pensar en objetos o dispositivos que reaccionen sin necesidad de contacto directo. Esto desplaza la interacción hacia algo más intuitivo, pero también más inestable, donde pequeñas variaciones generan grandes cambios.

Lo que más me interesa es cómo traduce una variable invisible como la capacitancia en algo perceptible como el sonido. Esa transformación me parece clave para el desarrollo de proyectos propios, ya que permite pensar en cómo datos abstractos pueden convertirse en experiencias sensoriales. En ese sentido, el Theremin funciona como un punto de partida conceptual para explorar interfaces más sensibles, expresivas y menos evidentes en su funcionamiento.


## Idea central

Sensores capacitivos permiten controlar variables continuas

Volumen

Frecuencia

Distancia

El cuerpo humano forma parte del circuito



## Aplicación en Arduino

Replicar lógica del Theremin

Uso de sensor capacitivo para detectar proximidad

Traducción de datos en control de sonido


## Problema

No se conocen valores mínimos ni máximos del sensor

Dificulta definir umbrales

Los datos dependen del contexto


## Estrategia de calibración

Definir valor mínimo de lectura

Definir valor máximo de lectura

Inicializar mínimo con valor alto

Inicializar máximo con valor bajo

Actualizar constantemente según lecturas


## Lógica

Si la lectura es menor al mínimo -> Actualizar mínimo

Si la lectura es mayor al máximo -> Actualizar máximo


## Observación

- El sistema se adapta automáticamente

- El rango depende del entorno

> Permite trabajar sin valores fijos


## Visualización

- Mostrar valor actual

- Mostrar valor mínimo

- Mostrar valor máximo

> Permite entender comportamiento del sensor


## Problema del valor crudo

El valor instantáneo es inestable

Puede generar errores

No es confiable por sí solo


## Solución

Uso de promedios

Promedio de últimas lecturas

Suavizado de datos

Reducción de ruido


## Umbral dinámico

Se calcula a partir del contexto


Permite detectar interacción de forma adaptativa


## Variaciones

Uso de porcentajes del rango

Uso de promedios móviles

Uso de acumulación de lecturas


## Estrategias avanzadas

Reset periódico del sistema

Evita valores extremos permanentes

Ajuste automático según entorno


## Interpretación

Toque fuerte supera fácilmente el umbral

Toque leve puede no detectarse

Proximidad genera cambios sin contacto


## Insight

No se trabaja con el valor crudo

Se procesa la información antes de tomar decisiones

El sensor se interpreta, no solo se lee


## Proyección

Uso de múltiples sensores

Integración con actuadores

Traducción de datos en acciones físicas o sonoras


## Reflexión

Lo capacitivo no es solo tacto

También es distancia

También es variación continua

Permite diseñar interfaces invisibles e intuitivas


## Idea final

Un cable más el cuerpo humano puede transformarse en un sensor

Un sistema simple puede convertirse en instrumento

La interacción ocurre sin contacto físico

