# Invernadero IoT · Cuaderno de prácticas

Nov 25, 2026 · @Carlos

En este proyecto del club de robótica vais a construir un invernadero automatizado de verdad. Primero lo simuláis en Tinkercad con Arduino UNO, después lo lleváis a un ESP32 conectado a internet en Wokwi y, al final, lo montáis físicamente con componentes reales. Cada práctica añade un componente o una idea a lo anterior y cabe en sesiones de 30 minutos. No hay entregas ni notas: la meta es que el invernadero funcione.

## Itinerario

&#91;embedded content: itinerario · dos líneas en paralelo, 21 sesiones\]

Las fases 1 a 3 (P0–P10) se hacen en Tinkercad con Arduino UNO, la fase 4 (P11–P12) en Wokwi con un ESP32 conectado a internet, y la fase 5 (M1–M4) con componentes reales. Como ya sabéis programar, la simulación va rápida: el esfuerzo está en la electrónica y en el diseño del código. Al trabajar en dos líneas en paralelo, el núcleo cabe en 21 sesiones y queda margen para imprevistos o para la P13 (la app), que es opcional.

## Cómo trabajamos

Sois un único equipo con un único invernadero, pero trabajáis en paralelo: el proyecto se divide en dos **líneas de trabajo**, A y B, que avanzan a la vez cada una en su propio diseño, y cada pocas sesiones hay una **sesión de integración** en la que se une todo en el diseño principal. Es como trabaja un equipo de desarrollo de verdad, y funciona porque el mapa de pines está fijado y cada clase tiene sus métodos definidos de antemano: cada uno sabe qué tiene que entregar al otro.

### Quién hace qué

- **Dos personas.** Una lleva la línea A y la otra la B. A partir de la P11 os intercambiáis, para que los dos hayáis trabajado con sensores y con actuadores.
- **Tres.** Dos llevan las líneas y la tercera es la integradora: prepara el diseño principal, hace las pruebas de los módulos que llegan y dirige las sesiones de integración. El papel de integrador rota en cada fase.
- **Más de tres.** Parejas por línea.
- **Si falta alguien,** los presentes trabajan en la línea más atrasada y la nota «Siguiente paso» del diario le pone al día cuando vuelva.

Cada uno hace el montaje, el código y las pruebas de su módulo. La única regla fija: **nadie da por bueno su propio módulo**. En la sesión de integración, cada uno pasa la tabla de comprobación del módulo del otro antes de unirlo, porque cuesta ver los errores propios.

### Plan de sesiones

El reparto sesión a sesión está en el itinerario del principio del cuaderno. En la P9, la línea A escribe `enviarEstado()` y la B, `LectorLineas` y `ejecutarComando()`; como todo va en el mismo archivo de Tinkercad, se unen copiando las funciones al diseño principal en la P10.

En la fase 4, A y B trabajan en archivos distintos, así que la unión consiste en copiar los `.h` y `.cpp` de cada uno al proyecto principal de Wokwi, al final de la sesión 13 y de la 15. En M2 se usa el Arduino UNO del centro para probar relés, bomba, ventilador y servo mientras el ESP32 está en M1; si hay presupuesto, un segundo ESP32 (unos 8 €) evita adaptar las pruebas.

### Una sesión de integración

1. Cada uno pasa la tabla de comprobación del módulo del otro, en el diseño de quien lo hizo.
2. Al diseño principal se añaden los componentes nuevos, en los pines del mapa, y las clases nuevas del código.
3. Se vuelven a pasar las dos tablas en el diseño principal. Si algo que funcionaba por separado falla junto, casi siempre es un pin repetido, un nombre de variable repetido o dos módulos que usan el mismo temporizador interno (como el `Servo` y el PWM de los pines 9 y 10).

### Ejemplo: sesiones 5 y 6

&#91;embedded content: cómo se trabaja en paralelo y cómo se une\]

1. **Al empezar la sesión 5,** cada uno duplica el diseño `P03 Principal` desde su ordenador. A renombra su copia como `P04 Pantalla - A` y B como `P05 Bomba - B`. Las dos copias parten de lo mismo, así que solo se diferenciarán en lo que cada uno añada.
2. **Durante la sesión 5,** A añade el LCD y su código en su copia, y B el relé, el transistor, el motor y la clase `Actuador` en la suya. Cada uno trabaja en un diseño distinto, así que no se pisan aunque estén en la misma cuenta.
3. **En la sesión 6,** cada uno pasa primero la tabla de comprobación del otro en el diseño del otro. Después, desde un solo ordenador, se duplica el `P03 Principal` como `P06 Principal` y se le añade lo nuevo de los dos:
   - **El código** se copia y se pega: es texto. Se parte del código de A y se le pegan las clases, variables y líneas de `setup()` y `loop()` que añadió B. Para encontrarlas rápido, cada uno marca lo suyo con un comentario como `/* ---- P5: bomba ---- */`.
   - **Los componentes** se vuelven a colocar en el principal siguiendo la tabla de montaje de cada práctica: son pocos (el LCD son cuatro cables) y el mapa de pines dice dónde va cada uno. Probad también a copiar y pegar componentes de un diseño a otro con Ctrl+C y Ctrl+V; si en vuestro navegador funciona, ahorra tiempo.
4. Se pasan las dos tablas de comprobación en `P06 Principal`, y ese es el punto de partida de las prácticas siguientes.

**¿Y con dos cuentas?** También funciona, porque el código se copia como texto y los componentes se recolocan igual. La diferencia es que el diseño principal tiene que vivir en una de las cuentas, y para empezar cada práctica el otro necesita una copia (el dueño se la comparte con un enlace). Con una cuenta del equipo os ahorráis ese paso, por eso es la opción recomendada.

### Una sesión de 30 minutos

1. **Minutos 0–3.** Leed el objetivo y la nota «Siguiente paso» que dejasteis en el diario.
2. **Minutos 3–25.** Trabajo en vuestra línea, o juntos si es sesión de integración. Si os atascáis más de 5 minutos, preguntad.
3. **Minutos 25–30.** Nota «Siguiente paso» en el diario, aunque la práctica no esté terminada.

### Dónde se guarda el trabajo

Todo el equipo usa la misma cuenta de Tinkercad y de Wokwi, para que el trabajo no dependa de quién venga cada día. En Tinkercad se entra por el [enlace de la clase](https://www.tinkercad.com/joinclass/UFHDMVQSP) (código `UFHDMVQSP`) con el alias del equipo que os dé el profesor.

- **El circuito y el código** se quedan en Tinkercad y en Wokwi. Cada práctica parte de la anterior: en Tinkercad, usad **Duplicar** sobre el diseño anterior y renombradlo con el número de la nueva práctica, así siempre podéis volver atrás.
- **El diario del equipo** es un documento compartido donde va todo lo demás: la nota «Siguiente paso» de cada sesión, las calibraciones, las tablas de comprobación y las fotos del montaje.
- **En la fase 5**, el código pasa de Wokwi a vuestro ordenador. Wokwi permite descargar el proyecto completo como `.zip`; guardad una copia cada vez que lo cambiéis.

**Dos ordenadores, una cuenta.** Podéis tener la cuenta del equipo abierta en dos ordenadores a la vez, siempre que **cada uno trabaje en un diseño distinto**. Ni Tinkercad ni Wokwi permiten que dos personas editen el mismo diseño al mismo tiempo: lo que guarda uno puede pisar lo que guarda el otro. Por eso cada línea trabaja en su propio diseño (por ejemplo, `P05 Bomba - B`) y el diseño principal solo se toca en las sesiones de integración, desde un único ordenador.

Si a alguien le apetece practicar Git, todo esto cabe en un repositorio de GitHub. Es opcional.

### Normas de código

- Cada clase lleva un comentario de documentación `/** … */` que dice qué hace, y cada método público, qué recibe y qué devuelve.
- Los pines y los umbrales son constantes con nombre al principio del archivo. Nada de números sueltos en el código.
- A partir de la P3 está prohibido `delay()`.
- Nombres en español, sin tildes ni eñes en el código.

### Mapa de pines del proyecto

Estos pines no cambian en todo el proyecto, para que cada práctica se sume a la anterior sin recablear nada.

| Pin | Conectado a | Desde |
| --- | --- | --- |
| A0 | Sensor de humedad del suelo | P1 |
| A1 | Fotorresistencia (LDR) | P2 |
| A2 | TMP36, temperatura del aire | P2 |
| A3 | Potenciómetro que simula la humedad del aire | P2 |
| A4 / A5 | Bus I2C (SDA / SCL) de la pantalla LCD | P4 |
| D2 | Interruptor que simula la boya del depósito | P7 |
| D3 | Pulsador de riego manual | P5 |
| D4 | Relé de la bomba, a través de un transistor | P5 |
| D5 | Ventilador con PWM, a través de un MOSFET | P6 |
| D6 | LED de cultivo con PWM | P8 |
| D8 | Zumbador de alarma | P7 |
| D9 | Servo de la trampilla | P6 |
| D13 | LED de estado (latido) | P0 |

### Estructura de cada práctica

Todas siguen el mismo orden: **objetivo**, **sesiones**, **componentes**, **montaje**, **pasos**, **código base** (con huecos marcados `TODO` que tenéis que completar), **comprobación**, **reto** opcional y **al terminar**, con lo que conviene apuntar en el diario. Las prácticas M1 a M4 de la fase 5 son de montaje real y cambian un poco el formato.

## Fase 1 · Sensores en Tinkercad

En esta fase el invernadero aprende a medir: suelo, temperatura, humedad del aire y luz, sin bloquear el programa y mostrándolo todo en una pantalla.

### P0 · Puesta en marcha

**Objetivo.** Tener la clase de Tinkercad, el repositorio y un primer circuito funcionando.

**Sesiones.** 1.

**Componentes.** Arduino UNO R3, placa de pruebas pequeña, LED rojo y resistencia de 220 Ω.

**Montaje.**

| Desde | Hasta |
| --- | --- |
| D13 | Resistencia de 220 Ω |
| Resistencia | Ánodo del LED (pata doblada, la larga) |
| Cátodo del LED | GND |

**El cálculo.** El LED rojo se queda con unos 2 V; el resto, hasta los 5 V del pin, cae en la resistencia. Con la ley de Ohm:

```latex
I = \frac{V_{pin} - V_{LED}}{R} = \frac{5 - 2}{220} \approx 0{,}0136\ \text{A} = 13{,}6\ \text{mA}
```

Está por debajo de los 20 mA que admite un pin. Para elegir la resistencia se despeja al revés: si queremos unos 15 mA, R = (5 − 2) / 0,015 = 200 Ω, y se toma el valor comercial siguiente, 220 Ω.

**Pasos.**

1. Entrad en Tinkercad por el [enlace de la clase](https://www.tinkercad.com/joinclass/UFHDMVQSP) (código `UFHDMVQSP`) con el alias del equipo.
2. Uno de vosotros crea el diario del equipo y apunta quién lleva cada línea.
3. Cada uno, en su ordenador, crea un circuito nuevo (**Circuitos → Crear**), lo llama `P00 Puesta en marcha` - A (o - B) y monta la tabla de arriba.
4. Abrid **Código**, cambiad de **Bloques** a **Texto**, borrad lo que haya y pegad el código base.
5. Pulsad **Iniciar simulación** y abrid el **Monitor serie** (abajo, en el panel de código).

**Código base.**

```cpp
/**
 * P0 · Latido del invernadero.
 * Hace parpadear el LED de estado y saluda por el monitor serie.
 */
const uint8_t PIN_LED_ESTADO = 13;

void setup() {
  pinMode(PIN_LED_ESTADO, OUTPUT);
  Serial.begin(9600);
  Serial.println(F("Invernadero listo"));
}

void loop() {
  digitalWrite(PIN_LED_ESTADO, HIGH);
  delay(500);
  digitalWrite(PIN_LED_ESTADO, LOW);
  delay(500);
}
```

**Comprobación.**

- [ ] El LED parpadea una vez por segundo.
- [ ] «Invernadero listo» aparece una sola vez en el monitor serie.
- [ ] La corriente que medís con el multímetro de Tinkercad, puesto en serie como amperímetro, se parece a la del apartado «El cálculo» (unos 13,6 mA).

**Reto.** Cambiad el parpadeo por un latido: dos destellos cortos y una pausa larga.

**Al terminar.** En el diario: la corriente calculada y la medida.

### P1 · Humedad del suelo

**Objetivo.** Leer un sensor analógico y convertir su lectura en un porcentaje fiable mediante calibración y promediado.

**Sesiones.** 1. Calibrad al principio y dedicad el resto a la conversión.

**Componentes.** Sensor de humedad del suelo.

**Montaje.** Duplicad vuestro diseño de la P0 y añadid:

| Pata del sensor | Pin del Arduino |
| --- | --- |
| VCC | 5V |
| GND | GND |
| SIG | A0 |

**Pasos.**

1. Cargad el código base tal cual e iniciad la simulación. Durante la simulación, haced clic en el sensor: aparece un control para cambiar la humedad.
2. Llevad el control al mínimo y al máximo y anotad la lectura cruda en cada extremo. Son vuestros valores de seco y mojado.
3. Escribid esos valores en `SUELO_SECO` y `SUELO_MOJADO`.
4. Completad `crudoAPorcentaje()` con `map()` y `constrain()`.
5. Abrid el gráfico del monitor serie y comprobad que la curva sigue al control sin saltos.

En el sensor capacitivo real, la lectura **baja** cuando el suelo está más húmedo. Si calibráis con `map(crudo, SUELO_SECO, SUELO_MOJADO, 0, 100)`, la misma función vale para los dos sentidos: solo cambian los valores de calibración.

**Código base.**

```cpp
/**
 * P1 · Humedad del suelo.
 * Lee el sensor, promedia y convierte a porcentaje calibrado.
 */
const uint8_t PIN_SUELO = A0;

/** Lecturas crudas medidas en la sesión 1 (calibración). */
const int SUELO_SECO = 0;      // TODO: valor medido con el sensor seco
const int SUELO_MOJADO = 1023; // TODO: valor medido con el sensor mojado

/**
 * Lee una entrada analógica varias veces y devuelve la media.
 * @param pin       Entrada analógica.
 * @param muestras  Número de lecturas a promediar.
 * @return Valor crudo medio, entre 0 y 1023.
 */
int leerMedia(uint8_t pin, uint8_t muestras) {
  long suma = 0;
  for (uint8_t i = 0; i < muestras; i++) {
    suma += analogRead(pin);
  }
  return suma / muestras;
}

/**
 * Convierte una lectura cruda en porcentaje con la calibración.
 * @return Humedad del suelo entre 0 y 100 %.
 */
int crudoAPorcentaje(int crudo) {
  // TODO: usa map() con SUELO_SECO y SUELO_MOJADO, y luego constrain()
  return 0;
}

void setup() {
  Serial.begin(9600);
}

void loop() {
  int crudo = leerMedia(PIN_SUELO, 10);
  Serial.print(F("Crudo: "));
  Serial.print(crudo);
  Serial.print(F("  Humedad: "));
  Serial.print(crudoAPorcentaje(crudo));
  Serial.println(F(" %"));
  delay(1000);
}
```

**Comprobación.**

| Caso | Esperado |
| --- | --- |
| Control al mínimo | 0 % |
| Control al máximo | 100 % |
| Control a media carrera | Entre 40 y 60 % |
| Cualquier posición | Nunca menos de 0 % ni más de 100 % |

**Reto.** Imprimid «¡Riega!» cuando la humedad baje del 30 %, pero solo una vez: no debe repetirse hasta que la humedad haya vuelto a superar el 40 %. Acabáis de inventar la histéresis, que usaremos en la P6.

**Al terminar.** Apuntad en el diario los valores de seco y mojado: los usaréis en las prácticas siguientes.

### P2 · Clima: temperatura, humedad del aire y luz

**Objetivo.** Medir el clima del invernadero detrás de una interfaz, de forma que el sensor se pueda cambiar más adelante sin tocar el resto del programa.

**Sesiones.** 1.

**Componentes.** Sensor de temperatura TMP36, potenciómetro, fotorresistencia y resistencia de 10 kΩ.

Tinkercad no tiene el sensor DHT22 que usaríamos en la realidad. Lo sustituimos por un TMP36 para la temperatura y un potenciómetro que hace de higrómetro: al girarlo, «cambia» la humedad del aire. En la P11, ya en Wokwi, el DHT22 real ocupará su lugar.

**Montaje.** Duplicad vuestro diseño de la P0 y añadid:

| Componente | Conexión |
| --- | --- |
| TMP36 | Pasad el ratón por las patas para ver su nombre: alimentación a 5V, Vout a A2, GND a GND |
| Potenciómetro | Un extremo a 5V, el otro a GND, el cursor (pata central) a A3 |
| Fotorresistencia y 10 kΩ | 5V → fotorresistencia → A1 → resistencia de 10 kΩ → GND |

La fotorresistencia y la resistencia forman un **divisor de tensión**. Con más luz, la fotorresistencia baja su resistencia y la tensión en A1 sube.

**El cálculo.** En un divisor, la tensión de salida es la parte de la tensión total que cae en la resistencia de abajo:

```latex
V_{A1} = 5 \cdot \frac{10\,000}{R_{LDR} + 10\,000}
```

Por ejemplo, si a oscuras la fotorresistencia tiene 100 kΩ, en A1 hay unos 0,45 V; si con mucha luz baja a 1 kΩ, hay unos 4,5 V. Por eso más luz da una lectura más alta. La resistencia fija se elige de un valor intermedio entre esos dos extremos para que la tensión recorra casi todo el margen de 0 a 5 V.

**Pasos.**

1. Montad los tres componentes y comprobad con el multímetro (modo voltaje) que en A1, A2 y A3 hay entre 0 y 5 V.
2. Completad `leerTemperatura()`. El TMP36 da 0,5 V a 0 °C y sube 10 mV por grado:
   - voltios = crudo × 5,0 / 1023
   - grados = (voltios − 0,5) × 100
3. Completad `leerHumedad()` para que el potenciómetro dé de 0 a 100 %.
4. Completad `leerPorcentaje()` de la luz.
5. Fijaos en que `loop()` solo usa `clima`, que es una referencia a la interfaz `SensorClima`. No sabe qué sensor hay detrás: esa es la gracia.

**Código base.**

```cpp
/**
 * P2 · Clima: temperatura, humedad del aire simulada y luz.
 */
const uint8_t PIN_LDR = A1;
const uint8_t PIN_TMP36 = A2;
const uint8_t PIN_POT_HR = A3;

/**
 * Interfaz común para cualquier sensor de clima.
 * En la P11 la implementará un DHT22 sin tocar el resto del programa.
 */
class SensorClima {
public:
  virtual ~SensorClima() {}
  /** @return Temperatura del aire en °C. */
  virtual float leerTemperatura() = 0;
  /** @return Humedad relativa del aire en %. */
  virtual float leerHumedad() = 0;
};

/**
 * Clima simulado: TMP36 para la temperatura y potenciómetro como higrómetro.
 */
class SensorClimaSimulado : public SensorClima {
public:
  SensorClimaSimulado(uint8_t pinTmp36, uint8_t pinPot) : pinTmp36(pinTmp36), pinPot(pinPot) {}

  float leerTemperatura() override {
    // TODO: crudo -> voltios -> grados (ver fórmula en el enunciado)
    return 0;
  }

  float leerHumedad() override {
    // TODO: 0-1023 del potenciómetro -> 0-100 %
    return 0;
  }

private:
  uint8_t pinTmp36;
  uint8_t pinPot;
};

/**
 * Fotorresistencia en un divisor de tensión.
 */
class SensorLuz {
public:
  explicit SensorLuz(uint8_t pin) : pin(pin) {}

  /** @return Luz relativa entre 0 y 100 %. */
  int leerPorcentaje() {
    // TODO
    return 0;
  }

private:
  uint8_t pin;
};

SensorClimaSimulado sensorSimulado(PIN_TMP36, PIN_POT_HR);
SensorClima& clima = sensorSimulado;
SensorLuz luz(PIN_LDR);

void setup() {
  Serial.begin(9600);
}

void loop() {
  Serial.print(F("T: "));
  Serial.print(clima.leerTemperatura(), 1);
  Serial.print(F(" C  HR: "));
  Serial.print(clima.leerHumedad(), 0);
  Serial.print(F(" %  Luz: "));
  Serial.print(luz.leerPorcentaje());
  Serial.println(F(" %"));
  delay(1000);
}
```

**Comprobación.**

| Caso | Esperado |
| --- | --- |
| TMP36 a 25 °C en su control | Entre 24 y 26 °C |
| TMP36 a −10 °C | Valor negativo, cerca de −10 |
| Potenciómetro en un extremo y en el otro | 0 % y 100 % |
| Fotorresistencia con la luz al máximo | Porcentaje alto; al bajarla, baja |

**Reto.** Con el multímetro, medid la tensión en A1 con la luz al máximo y al mínimo. Calculad con la fórmula del divisor qué resistencia tiene la fotorresistencia en cada caso.

**Al terminar.** La tabla de comprobación, rellena, en el diario.

### P3 · Multitarea sin delay() y primeras clases

**Objetivo.** Que cada tarea se ejecute a su ritmo sin bloquear a las demás, y reunir el código de P0–P2 en clases.

**Sesiones.** 2. En la primera, el problema y el `Temporizador`; en la segunda, la reorganización en clases.

**Componentes.** Los de la P1 y la P2. Es la primera integración: se crea el diseño principal (P03 Principal) a partir del de la P2 y se le añade el sensor de suelo de la P1.

**El problema.** Juntad el latido de la P0 con la lectura de la P2. Mientras `delay(1000)` espera, el Arduino no hace nada más: ni lee sensores, ni atiende botones, ni mueve la bomba. En un invernadero con seis tareas, eso no sirve.

**La solución.** `millis()` devuelve los milisegundos desde el arranque. En cada vuelta de `loop()`, cada tarea mira si ya le toca y, si no, sigue de largo. `loop()` da miles de vueltas por segundo y nunca se para.

**Pasos.**

1. Copiad la clase `Temporizador`, que ya está completa, y entended su método `vencido()`.
2. Convertid el código de la P1 en la clase `SensorHumedadSuelo` (abajo, con su método por completar).
3. Traed `SensorClima`, `SensorClimaSimulado` y `SensorLuz` de la P2 tal cual.
4. Cread cuatro temporizadores y programad estas tareas:

| Tarea | Periodo |
| --- | --- |
| Latido del LED de estado (cambia de encendido a apagado) | 500 ms |
| Leer suelo, clima y luz, y guardarlo en `lecturas` | 1 s |
| Imprimir `lecturas` por el monitor serie | 2 s |
| Imprimir `millis()` para comprobar los tiempos | 5 s |

**Código base.** Solo lo nuevo; el resto viene de la P2.

```cpp
/**
 * Temporizador periódico no bloqueante basado en millis().
 */
class Temporizador {
public:
  explicit Temporizador(unsigned long periodoMs) : periodoMs(periodoMs), ultimo(0) {}

  /**
   * @return true una vez por periodo; false el resto del tiempo.
   */
  bool vencido() {
    unsigned long ahora = millis();
    if (ahora - ultimo >= periodoMs) {
      ultimo = ahora;
      return true;
    }
    return false;
  }

private:
  unsigned long periodoMs;
  unsigned long ultimo;
};

/**
 * Sensor de humedad del suelo calibrado.
 */
class SensorHumedadSuelo {
public:
  /**
   * @param pin     Entrada analógica.
   * @param seco    Lectura cruda con el sensor seco.
   * @param mojado  Lectura cruda con el sensor en agua.
   */
  SensorHumedadSuelo(uint8_t pin, int seco, int mojado)
    : pin(pin), seco(seco), mojado(mojado) {}

  /** @return Humedad entre 0 y 100 %, media de 10 lecturas. */
  int leerPorcentaje() {
    // TODO: lo que hacían leerMedia() y crudoAPorcentaje() en la P1
    return 0;
  }

private:
  uint8_t pin;
  int seco;
  int mojado;
};

/** Últimas lecturas de todos los sensores. */
struct Lecturas {
  int suelo;
  float temperatura;
  float humedadAire;
  int luz;
};

const uint8_t PIN_LED_ESTADO = 13;

SensorHumedadSuelo suelo(A0, 0, 1023);  // TODO: vuestra calibración de la P1
Temporizador tLatido(500);
Temporizador tSensores(1000);
Temporizador tInforme(2000);
Temporizador tReloj(5000);
Lecturas lecturas = {};
bool ledEncendido = false;

void loop() {
  if (tLatido.vencido()) {
    ledEncendido = !ledEncendido;
    digitalWrite(PIN_LED_ESTADO, ledEncendido ? HIGH : LOW);
  }
  if (tSensores.vencido()) {
    // TODO: rellenar lecturas con suelo, clima y luz
  }
  if (tInforme.vencido()) {
    // TODO: imprimir lecturas en una línea
  }
  if (tReloj.vencido()) {
    // TODO: imprimir millis()
  }
}
```

En `setup()` van `Serial.begin(9600)` y `pinMode(PIN_LED_ESTADO, OUTPUT)`, como en la P0.

**Comprobación.**

- [ ] No queda ningún `delay()` en el programa.
- [ ] El LED sigue latiendo a ritmo constante mientras se imprimen las lecturas.
- [ ] Las marcas de `millis()` avanzan de 5000 en 5000, con un margen de pocos milisegundos.
- [ ] Al mover un sensor en la simulación, el cambio aparece en el siguiente informe.

**Reto.** `millis()` vuelve a cero a los 49,7 días. Pensad por qué `ahora - ultimo >= periodoMs` sigue funcionando entonces y `ahora >= ultimo + periodoMs` no. Pista: son enteros sin signo.

**Al terminar.** Si habéis hecho el reto, apuntad la respuesta en el diario.

### P4 · Pantalla LCD por I2C

**Objetivo.** Mostrar las lecturas en una pantalla de 16 × 2 caracteres conectada por el bus I2C, sin parpadeos ni restos de texto.

**Sesiones.** 1.

**Componentes.** LCD 16 × 2 (I2C). Buscad en Tinkercad la versión **I2C**, no la normal de 16 patas.

**Montaje.**

| Pata del LCD | Pin del Arduino |
| --- | --- |
| GND | GND |
| VCC | 5V |
| SDA | A4 |
| SCL | A5 |

Con I2C, la pantalla usa dos cables de datos en lugar de seis, y otros dispositivos pueden compartir esos mismos dos cables, cada uno con su dirección.

**Pasos.**

1. Añadid el LCD y conectadlo.
2. Añadid el código base al programa de la P3 y un temporizador nuevo de 3 s para la pantalla.
3. Completad `imprimirAncho()`, que escribe un número ocupando siempre el mismo número de caracteres.
4. Probad a bajar la humedad del suelo de 100 % a 5 %. Sin `imprimirAncho()` veríais «5%%» o «50%»: son restos del número anterior.

**Código base.**

```cpp
#include <Adafruit_LiquidCrystal.h>

/** En Tinkercad el LCD I2C tiene la dirección 0x20, que esta librería indica con un 0. */
Adafruit_LiquidCrystal lcd(0);
Temporizador tPantalla(3000);

/**
 * Escribe un número alineado a la derecha en un ancho fijo.
 * @param valor  Número a escribir.
 * @param ancho  Caracteres que debe ocupar, rellenando con espacios a la izquierda.
 */
void imprimirAncho(long valor, uint8_t ancho) {
  // TODO: convierte valor a texto con ltoa(), cuenta su longitud con strlen()
  //       y escribe los espacios que falten antes del número
}

/** Pinta las lecturas: "T24.5C HR 60%" arriba y "Suelo 45%Luz 80%" abajo (16 caracteres justos). */
void mostrarLecturas() {
  lcd.setCursor(0, 0);
  lcd.print(F("T"));
  lcd.print(lecturas.temperatura, 1);
  lcd.print(F("C HR"));
  imprimirAncho((long)lecturas.humedadAire, 3);
  lcd.print(F("%  "));
  lcd.setCursor(0, 1);
  // TODO: segunda línea con suelo y luz
}

void setup() {
  // …lo de la P3…
  lcd.begin(16, 2);
  lcd.setBacklight(1);
}
```

En `loop()`, cuando venza `tPantalla`, llamad a `mostrarLecturas()`. No uséis `lcd.clear()` en cada actualización: borra toda la pantalla y la hace parpadear.

**Comprobación.**

- [ ] Las dos líneas se ven completas y no se salen de los 16 caracteres.
- [ ] Al pasar de 100 % a 5 % no queda ningún carácter de más.
- [ ] La pantalla no parpadea.
- [ ] El LED de latido sigue a su ritmo.

**Reto.** Dibujad un carácter propio con forma de gota (`lcd.createChar`) y ponedlo delante de la humedad del suelo.

**Al terminar.** Una captura de la pantalla funcionando en el diario.

Con el LCD real, la librería habitual es `LiquidCrystal_I2C` y la dirección suele ser 0x27 o 0x3F. En Wokwi, en la P11, usaremos esa.

## Fase 2 · Actuadores y control en Tinkercad

En esta fase el invernadero pasa de medir a actuar: riega, ventila, ilumina y avisa cuando algo va mal.

### P5 · La bomba: relé, transistor y diodo

**Objetivo.** Encender una carga de potencia (la bomba) desde un pin del Arduino de forma segura, y encapsularlo en una clase `Actuador`.

**Sesiones.** 1.

**Componentes.** Relé SPDT, transistor NPN, diodo, resistencia de 1 kΩ, motor de CC (hace de bomba), fuente de alimentación y pulsador.

**Por qué no conectar la bomba directamente al pin.** Un pin del UNO da como mucho 20 mA de forma continua (40 mA es el límite absoluto). Una bomba pequeña pide cientos de miliamperios. El transistor amplifica la señal del pin para mover la bobina del relé, y el relé conmuta el circuito de la bomba, que tiene su propia fuente.

**El cálculo de la base.** Entre la base y el emisor del transistor caen unos 0,7 V, así que por la resistencia de 1 kΩ pasa:

```latex
I_B = \frac{5 - 0{,}7}{1\,000} \approx 4{,}3\ \text{mA}
```

El pin da poco más de 4 mA, muy lejos de su límite. El transistor amplifica esa corriente unas 100 veces, así que puede dejar pasar más de 400 mA por el colector: de sobra para la bobina de un relé pequeño, que necesita unos 70 mA.

**Montaje.**

| Parte | Conexión |
| --- | --- |
| Control | D4 → resistencia de 1 kΩ → base del NPN; emisor del NPN → GND |
| Bobina del relé | 5V → bobina → colector del NPN |
| Diodo | En paralelo con la bobina, con la banda (cátodo) hacia 5V |
| Circuito de la bomba | Fuente (+) → COM del relé; NO del relé → motor; motor → fuente (−) |
| Fuente | Ajustadla a 5 V |
| Pulsador | Una pata a D3, la opuesta a GND |

El diodo protege al transistor: al cortar la corriente de la bobina, esta genera un pico de tensión que, sin diodo, puede romperlo. El circuito de la bomba no comparte GND con el Arduino: el relé aísla los dos circuitos.

**Pasos.**

1. Montad el circuito y, antes de programar nada, probadlo con un `digitalWrite(4, HIGH)` en `setup()`: el motor debe girar.
2. Con el multímetro, medid la corriente de base (entre la resistencia y la base) y la corriente de la bobina. Anotadlas.
3. Completad la clase `Actuador`.
4. Programad el riego manual: al pulsar el botón de D3, la bomba riega 3 segundos y se apaga sola, sin `delay()`.
5. Añadid una seguridad: la bomba nunca puede estar encendida más de 10 segundos seguidos.

**Código base.**

```cpp
const uint8_t PIN_PULSADOR = 3;
const uint8_t PIN_BOMBA = 4;

/**
 * Salida digital que enciende o apaga una carga (relé, LED, zumbador).
 */
class Actuador {
public:
  /**
   * @param pin          Pin digital de control.
   * @param activoEnBajo true si la carga se enciende con LOW.
   */
  Actuador(uint8_t pin, bool activoEnBajo = false)
    : pin(pin), activoEnBajo(activoEnBajo), encendido(false), msInicio(0) {}

  /** Deja la salida apagada antes de configurarla como OUTPUT. */
  void iniciar() {
    digitalWrite(pin, activoEnBajo ? HIGH : LOW);
    pinMode(pin, OUTPUT);
  }

  /** Enciende la carga y apunta cuándo se encendió. */
  void encender() {
    // TODO: guarda millis() en msInicio solo si estaba apagada
  }

  /** Apaga la carga. */
  void apagar() {
    // TODO
  }

  bool estaEncendido() const { return encendido; }

  /** @return Milisegundos que lleva encendido (0 si está apagado). */
  unsigned long msEncendido() const {
    // TODO
    return 0;
  }

private:
  uint8_t pin;
  bool activoEnBajo;
  bool encendido;
  unsigned long msInicio;
};

Actuador bomba(PIN_BOMBA);

void setup() {
  // …lo de la P4…
  pinMode(PIN_PULSADOR, INPUT_PULLUP);
  bomba.iniciar();
}
```

`INPUT_PULLUP` activa una resistencia interna hacia 5 V: el pin lee `HIGH` en reposo y `LOW` al pulsar. Por eso el pulsador va a GND y no necesita resistencia.

**Comprobación.**

| Caso | Esperado |
| --- | --- |
| Arranque | La bomba está parada |
| Pulsación corta | La bomba gira 3 s y para |
| Mantener pulsado 15 s | La bomba para a los 10 s como mucho |
| Durante el riego | El LCD y el latido siguen actualizándose |

**Reto.** Con el multímetro, medid la corriente de base y la de la bobina y comparadlas con el apartado «El cálculo de la base». ¿Cuántas veces es mayor una que otra?

**Al terminar.** Las corrientes medidas, en el diario.

Los módulos de relés reales que compraremos ya llevan transistor, diodo y optoacoplador, y suelen activarse con `LOW`. Para ellos bastará con crear el actuador como `Actuador bomba(PIN_BOMBA, true);`.

### P6 · Ventilación con histéresis: ventilador PWM y trampilla con servo

**Objetivo.** Ventilar cuando hace calor o hay demasiada humedad, regular la velocidad del ventilador con PWM y evitar que se encienda y apague sin parar cerca del umbral.

**Sesiones.** 1.

**Componentes.** Segundo motor de CC (ventilador), transistor nMOS (MOSFET), diodo, resistencias de 220 Ω y 10 kΩ, y micro servo posicional.

**Montaje.**

| Parte | Conexión |
| --- | --- |
| Puerta del MOSFET | D5 → 220 Ω → puerta; 10 kΩ entre la puerta y GND |
| Ventilador | Fuente (+) → motor → drenador del MOSFET; surtidor → GND |
| Diodo | En paralelo con el motor, con la banda hacia la fuente (+) |
| GND común | Fuente (−) unida al GND del Arduino |
| Servo | Alimentación a 5V, tierra a GND, señal a D9 |

Aquí el GND común es obligatorio, al contrario que en la P5: el MOSFET compara la tensión de la puerta con la de su surtidor, así que ambos circuitos necesitan la misma referencia.

**La histéresis.** Si el ventilador se encendiera a 28 °C y se apagara al bajar de 28 °C, con la temperatura rondando ese valor arrancaría y pararía cada segundo. Con dos umbrales se enciende a 28 °C y no se apaga hasta bajar a 25 °C.

**Pasos.**

1. Montad el ventilador y probadlo con `analogWrite(5, 128)`: debe girar a media velocidad.
2. Completad `Histeresis::actualizar()`.
3. Cread dos histéresis: temperatura (encender a 28 °C, apagar a 25 °C) y humedad del aire (encender a 80 %, apagar a 70 %). Se ventila si cualquiera de las dos lo pide.
4. Montad el servo: con la ventilación activa, la trampilla se abre (90°); sin ella, se cierra (0°).
5. Velocidad del ventilador: 150 a 28 °C, subiendo hasta 255 a 35 °C o más. Usad `map()` y `constrain()`.

**Código base.**

```cpp
#include <Servo.h>

const uint8_t PIN_VENTILADOR = 5;
const uint8_t PIN_SERVO = 9;

/**
 * Control todo/nada con dos umbrales para evitar oscilaciones.
 */
class Histeresis {
public:
  /**
   * @param umbralEncender Valor a partir del cual se activa.
   * @param umbralApagar   Valor por debajo del cual se desactiva.
   */
  Histeresis(float umbralEncender, float umbralApagar)
    : umbralEncender(umbralEncender), umbralApagar(umbralApagar), activo(false) {}

  /** @return true si la salida debe estar activa tras la nueva medida. */
  bool actualizar(float valor) {
    // TODO: si no está activo y valor >= umbralEncender, se activa;
    //       si está activo y valor <= umbralApagar, se desactiva
    return activo;
  }

private:
  float umbralEncender;
  float umbralApagar;
  bool activo;
};

Histeresis ventTemp(28, 25);
Histeresis ventHum(80, 70);
Servo trampilla;
bool ventilando = false;

/** Ventilador y trampilla según temperatura y humedad. Se llama tras leer los sensores. */
void controlarVentilacion() {
  // TODO
}

void setup() {
  // …lo de la P5…
  pinMode(PIN_VENTILADOR, OUTPUT);
  trampilla.attach(PIN_SERVO);
  trampilla.write(0);
}
```

La librería `Servo` del UNO usa el temporizador interno que genera el PWM de los pines 9 y 10, así que en esos pines `analogWrite()` deja de funcionar. Por eso el ventilador va en el pin 5.

**Comprobación.** Con el potenciómetro de humedad por debajo del 70 %:

| Paso | Temperatura | Ventilador | Trampilla |
| --- | --- | --- | --- |
| 1 | 20 °C | Parado | Cerrada |
| 2 | Subir a 27 °C | Parado | Cerrada |
| 3 | Subir a 28 °C | Gira despacio | Abierta |
| 4 | Subir a 35 °C | Gira al máximo | Abierta |
| 5 | Bajar a 26 °C | Sigue girando | Abierta |
| 6 | Bajar a 25 °C | Parado | Cerrada |

Repetid la tabla con la temperatura a 20 °C y moviendo la humedad entre 60 % y 85 %.

**Reto.** Que la trampilla se abra poco a poco, un grado cada 15 ms, sin bloquear el programa.

**Al terminar.** Las dos tablas de comprobación, en el diario.

### P7 · Riego automático: máquina de estados y boya

**Objetivo.** Regar solo cuando hace falta, por pulsos, dejando que el agua empape antes de volver a medir, y no hacer funcionar nunca la bomba sin agua.

**Sesiones.** 2. Primera: diagrama de estados, espera, riego y absorción. Segunda: depósito vacío, alarma y pruebas.

**Componentes.** Interruptor deslizante (hace de boya del depósito) y piezo (zumbador).

**Montaje.**

| Componente | Conexión |
| --- | --- |
| Interruptor deslizante | Pata central a D2, una pata lateral a GND |
| Piezo | (+) a D8, (−) a GND |

Con `INPUT_PULLUP`, el interruptor en la posición que une D2 con GND da `LOW`: lo tomamos como «hay agua». La boya real funciona igual.

**Por qué por pulsos.** El sensor tarda en notar el agua. Si regáis «hasta que el sensor diga húmedo», cuando por fin lo dice la maceta ya está encharcada. Por eso se riega un poco, se espera a que el agua llegue al sensor y se vuelve a medir.

**Los estados.**

| Estado | Qué hace | Pasa a | Cuándo |
| --- | --- | --- | --- |
| ESPERA | Bomba parada, vigila el suelo | REGANDO | Suelo por debajo del 35 % |
| REGANDO | Bomba encendida | ABSORCION | Pasan 4 s |
| ABSORCION | Bomba parada, el agua empapa | ESPERA | Pasan 20 s |
| SIN\_AGUA | Bomba parada, zumbador sonando | ESPERA | Vuelve a haber agua |
| Cualquiera | — | SIN\_AGUA | La boya indica depósito vacío |

En un invernadero real, la absorción duraría minutos. Aquí usamos 20 s para poder probarlo en clase.

**Pasos.**

1. **Antes de programar**, dibujad el diagrama de estados (círculos y flechas con su condición) y guardad una foto en el diario.
2. Completad el `switch` de `actualizar()`.
3. Completad `cambiarA()`: es el único sitio donde se enciende o apaga la bomba y el zumbador.
4. En `loop()`, llamad a `riego.actualizar(lecturas.suelo, hayAgua)` en cada vuelta y mostrad `riego.nombreEstado()` en el LCD.
5. El riego manual de la P5 sigue funcionando, pero solo si hay agua.

**Código base.**

```cpp
const uint8_t PIN_BOYA = 2;
const uint8_t PIN_ZUMBADOR = 8;

/**
 * Zumbador piezoeléctrico pasivo: necesita tone() para sonar.
 */
class Zumbador {
public:
  Zumbador(uint8_t pin, unsigned int frecuencia) : pin(pin), frecuencia(frecuencia) {}
  void encender() { tone(pin, frecuencia); }
  void apagar() { noTone(pin); }

private:
  uint8_t pin;
  unsigned int frecuencia;
};

/** Estados del riego automático. */
enum class EstadoRiego : uint8_t { ESPERA, REGANDO, ABSORCION, SIN_AGUA };

/**
 * Máquina de estados del riego por pulsos.
 */
class ControladorRiego {
public:
  ControladorRiego(Actuador& bomba, Zumbador& alarma)
    : bomba(bomba), alarma(alarma), estado(EstadoRiego::ESPERA), msEntrada(0),
      umbralSeco(35), msPulso(4000), msAbsorcion(20000) {}

  /**
   * Avanza la máquina de estados. Se llama en cada vuelta de loop().
   * @param sueloPct  Humedad del suelo en %.
   * @param hayAgua   true si la boya detecta agua en el depósito.
   */
  void actualizar(int sueloPct, bool hayAgua) {
    if (!hayAgua && estado != EstadoRiego::SIN_AGUA) {
      cambiarA(EstadoRiego::SIN_AGUA);
      return;
    }
    switch (estado) {
      case EstadoRiego::ESPERA:
        // TODO
        break;
      case EstadoRiego::REGANDO:
        // TODO: usa tiempoEnEstado()
        break;
      case EstadoRiego::ABSORCION:
        // TODO
        break;
      case EstadoRiego::SIN_AGUA:
        // TODO
        break;
    }
  }

  /** @return Nombre del estado para el LCD y el monitor serie. */
  const char* nombreEstado() const {
    // TODO: un switch que devuelva "ESPERA", "REGANDO"...
    return "?";
  }

private:
  /** Cambia de estado y ejecuta las acciones de entrada del nuevo estado. */
  void cambiarA(EstadoRiego nuevo) {
    estado = nuevo;
    msEntrada = millis();
    // TODO: bomba encendida solo en REGANDO; zumbador solo en SIN_AGUA
  }

  unsigned long tiempoEnEstado() const { return millis() - msEntrada; }

  Actuador& bomba;
  Zumbador& alarma;
  EstadoRiego estado;
  unsigned long msEntrada;
  int umbralSeco;
  unsigned long msPulso;
  unsigned long msAbsorcion;
};

Zumbador alarma(PIN_ZUMBADOR, 1000);
ControladorRiego riego(bomba, alarma);
```

`ControladorRiego` no crea la bomba: la recibe por referencia. Así el controlador no sabe si detrás hay un relé de Tinkercad o un módulo real activo en `LOW`.

**Comprobación.**

| Caso | Esperado |
| --- | --- |
| Suelo al 60 %, hay agua | ESPERA, bomba parada |
| Bajar el suelo al 20 % | REGANDO 4 s, luego ABSORCION 20 s, luego ESPERA |
| Dejar el suelo al 20 % | Se repite el ciclo de pulsos |
| Subir el suelo al 60 % durante ABSORCION | Al acabar la absorción vuelve a ESPERA y no riega más |
| Quitar el agua durante REGANDO | SIN\_AGUA al instante, bomba parada, suena el zumbador |
| Devolver el agua | ESPERA, deja de sonar |
| Pulsar riego manual sin agua | La bomba no arranca |

**Reto.** Añadid un estado `AVERIA`: si después de 5 pulsos seguidos el suelo sigue por debajo del umbral, algo falla (sensor fuera de la maceta, tubo suelto). Se para todo y suena el zumbador con otro tono.

**Al terminar.** Una foto del diagrama de estados en el diario: volveréis a él en el montaje real.

### P8 · Reloj y ciclo de luz

**Objetivo.** Dar a las plantas 14 horas de luz al día, de 08:00 a 22:00, encendiendo el LED de cultivo solo cuando falta luz natural.

**Sesiones.** 1.

**Componentes.** LED blanco y resistencia de 220 Ω (hacen de tira LED de cultivo).

**Montaje.** D6 → 220 Ω → ánodo del LED; cátodo → GND. La tira real de 12 V iría con un MOSFET, igual que el ventilador de la P6.

**El problema de la hora.** El UNO no sabe qué hora es: solo cuenta milisegundos desde que arranca. En la realidad se añade un módulo de reloj (RTC), pero Tinkercad no lo tiene. Haremos un reloj simulado que parte de una hora fija y avanza acelerado: con una aceleración de 1, cada segundo real es un minuto, y un día completo dura 24 minutos.

Igual que con el clima, el reloj va detrás de una interfaz. En la P12, el ESP32 tomará la hora de internet con otra clase que implementa la misma interfaz.

**Pasos.**

1. Completad `RelojSimulado::minutosDelDia()`.
2. Mostrad la hora en formato `HH:MM` en el LCD. Podéis añadir una segunda pantalla que alterne con la de lecturas cada 3 s.
3. Completad `controlarLuz()`: LED encendido si la hora está entre `luzDesde` y `luzHasta` **y** la luz natural es menor del 40 %.

**Código base.**

```cpp
const uint8_t PIN_LED_CULTIVO = 6;

/**
 * Fuente de hora del sistema.
 */
class Reloj {
public:
  virtual ~Reloj() {}
  /** @return Minutos transcurridos desde medianoche (0–1439). */
  virtual uint16_t minutosDelDia() = 0;
};

/**
 * Reloj sin RTC: parte de una hora inicial y avanza con millis(), acelerado.
 */
class RelojSimulado : public Reloj {
public:
  /**
   * @param hora        Hora inicial (0–23).
   * @param minuto      Minuto inicial (0–59).
   * @param aceleracion Minutos simulados por cada segundo real.
   */
  RelojSimulado(uint8_t hora, uint8_t minuto, uint16_t aceleracion)
    : minutoInicio(hora * 60 + minuto), aceleracion(aceleracion), msInicio(0) {}

  /** Pone el reloj en hora a partir de este momento. */
  void ajustar(uint8_t hora, uint8_t minuto) {
    minutoInicio = hora * 60 + minuto;
    msInicio = millis();
  }

  uint16_t minutosDelDia() override {
    // TODO: segundos reales desde msInicio × aceleracion = minutos simulados;
    //       súmalos a minutoInicio y quédate con el resto de dividir entre 1440
    return 0;
  }

private:
  uint16_t minutoInicio;
  uint16_t aceleracion;
  unsigned long msInicio;
};

RelojSimulado relojSimulado(7, 55, 1);
Reloj& reloj = relojSimulado;
uint16_t luzDesde = 8 * 60;
uint16_t luzHasta = 22 * 60;

/** LED de cultivo dentro del horario y solo si falta luz natural. */
void controlarLuz(uint16_t minutos, int luzNatural) {
  // TODO
}
```

**Comprobación.** Arrancad la simulación, que empieza a las 07:55, con la fotorresistencia a oscuras.

| Momento | Esperado |
| --- | --- |
| 07:55 | LED apagado |
| 08:00 (5 s después) | LED encendido |
| Subir la luz natural al máximo | LED apagado |
| Volver a oscuras | LED encendido |
| 22:00 (14 min después) | LED apagado |
| 23:59 → 00:00 | La hora vuelve a 00:00, no a 24:00 |

**Reto.** Que el horario pueda cruzar la medianoche, por ejemplo de 20:00 a 06:00. Y que el LED amanezca: que suba su brillo con PWM durante los primeros 30 minutos simulados.

**Al terminar.** Apuntad en el diario el horario de luz elegido.

## Fase 3 · Integración en Tinkercad

En esta fase el invernadero aprende a hablar con el exterior y se prueba entero. Lo que defináis aquí es el contrato que usará la app.

### P9 · Protocolo serie: estado en JSON y comandos

**Objetivo.** Que el invernadero envíe su estado en JSON y obedezca comandos de texto. Es la misma interfaz que en la P12 viajará por MQTT hasta la app.

**Sesiones.** 1.

**Componentes.** Ninguno nuevo. Se trabaja con el monitor serie: lo que escribáis abajo y enviéis le llega al Arduino.

**El contrato.** Cada 2 s, el invernadero envía una línea como esta:

```json
{"t":24.5,"hr":60,"suelo":42,"luz":80,"agua":1,"bomba":0,"vent":1,"led":0,"riego":"ESPERA","modo":"AUTO","min":845}
```

Y acepta estos comandos, uno por línea:

| Comando | Efecto | Respuesta |
| --- | --- | --- |
| `GET` | Envía el estado al momento | La línea JSON de estado |
| `SET suelo_min 40` | Cambia el umbral de riego | `{"ok":true}` |
| `SET t_on 30` / `SET t_off 26` | Cambia los umbrales del ventilador | `{"ok":true}` |
| `MODO AUTO` / `MODO MANUAL` | En manual se desactiva el riego automático | `{"ok":true}` |
| `BOMBA ON` / `BOMBA OFF` | Solo en manual y si hay agua | `{"ok":true}` |
| `VENT ON` / `VENT OFF` | Solo en manual | `{"ok":true}` |
| Cualquier otra cosa | Nada | `{"ok":false,"error":"comando no valido"}` |

El campo `min` son los minutos desde medianoche (845 son las 14:05). Un número es más fácil de procesar que un texto `"14:05"`.

**Pasos.**

1. Completad `enviarEstado()` con todos los campos del contrato y llamadla cada 2 s.
2. Copiad `LectorLineas`, que ya está completa, y entended por qué cierra la línea también tras 50 ms de silencio.
3. Completad `ejecutarComando()` con los comandos que faltan. Para `SET t_on` y `SET t_off`, añadid a `Histeresis` un método `configurar()`.
4. Probad cada comando de la tabla desde el monitor serie.

**Código base.**

```cpp
#include <string.h>
#include <stdlib.h>

/**
 * Lee líneas de un Stream sin bloquear. Una línea termina con \n, \r
 * o tras 50 ms sin recibir caracteres (Tinkercad no siempre envía \n).
 */
class LectorLineas {
public:
  explicit LectorLineas(Stream& entrada) : entrada(entrada), longitud(0), msUltimo(0) {}

  /** @return Línea completa o nullptr si aún no hay ninguna. */
  char* leer() {
    while (entrada.available()) {
      char c = entrada.read();
      msUltimo = millis();
      if (c == '\n' || c == '\r') {
        if (longitud > 0) return cerrar();
      } else if (longitud < sizeof(buffer) - 1) {
        buffer[longitud++] = c;
      }
    }
    if (longitud > 0 && millis() - msUltimo > 50) return cerrar();
    return nullptr;
  }

private:
  char* cerrar() {
    buffer[longitud] = '\0';
    longitud = 0;
    return buffer;
  }

  Stream& entrada;
  char buffer[48];
  uint8_t longitud;
  unsigned long msUltimo;
};

/** Escribe el estado completo como una línea JSON. */
void enviarEstado(Print& salida) {
  salida.print(F("{\"t\":"));
  salida.print(lecturas.temperatura, 1);
  salida.print(F(",\"hr\":"));
  salida.print(lecturas.humedadAire, 0);
  // TODO: el resto de campos del contrato
  salida.println('}');
}

/**
 * Ejecuta un comando de texto y responde en JSON.
 * @param linea   Comando recibido; strtok() lo modifica.
 * @param salida  Dónde escribir la respuesta.
 */
void ejecutarComando(char* linea, Print& salida) {
  char* orden = strtok(linea, " ");
  char* arg1 = strtok(nullptr, " ");
  char* arg2 = strtok(nullptr, " ");
  if (orden == nullptr) return;

  if (strcmp(orden, "GET") == 0) {
    enviarEstado(salida);
    return;
  }
  if (strcmp(orden, "SET") == 0 && arg1 && arg2) {
    if (strcmp(arg1, "suelo_min") == 0) {
      riego.setUmbralSeco(atoi(arg2));
      salida.println(F("{\"ok\":true}"));
      return;
    }
    // TODO: t_on y t_off (atof convierte texto en float)
  }
  // TODO: MODO, BOMBA y VENT
  salida.println(F("{\"ok\":false,\"error\":\"comando no valido\"}"));
}

LectorLineas lector(Serial);

/* En loop():
   char* linea = lector.leer();
   if (linea) ejecutarComando(linea, Serial);
*/
```

`ControladorRiego` necesita dos métodos nuevos, `setUmbralSeco(int)` y `getUmbralSeco()`. Añadidlos vosotros.

Fíjaos en el parámetro `Print& salida`. `Serial` es un `Print`, pero no el único: en la P12 la respuesta saldrá por MQTT y `ejecutarComando()` no cambiará ni una línea.

**Comprobación.**

- [ ] Cada línea de estado es JSON válido: pegad una en [jsonlint.com](https://jsonlint.com) y no debe dar error.
- [ ] Cada comando de la tabla da la respuesta indicada.
- [ ] `BOMBA ON` en modo AUTO responde `{"ok":false,...}` y la bomba no arranca.
- [ ] Un comando de 100 caracteres no cuelga el programa.
- [ ] `SET suelo_min 50` cambia de verdad el comportamiento del riego.

**Reto.** Añadid `SET hora 14:30` para poner en hora el reloj simulado.

**Al terminar.** Copiad al diario la tabla de comandos y el formato del estado: es el contrato que usarán la P12 y la app.

### P10 · Sistema completo y batería de pruebas

**Objetivo.** Dejar cerrada la versión de Tinkercad: todo integrado, ordenado y probado de principio a fin.

**Sesiones.** 1.

**Componentes.** Todos los anteriores. Es el momento de ordenar los cables: un color por función (rojo 5V, negro GND, amarillo señales analógicas, azul señales digitales).

**Pasos.**

1. Revisad el programa con esta lista:
   - [ ] Ningún `delay()`.
   - [ ] Pines y umbrales en constantes al principio.
   - [ ] Cada clase con su comentario de documentación.
   - [ ] `loop()` cabe en una pantalla: solo llama a temporizadores y métodos.
   - [ ] La bomba solo se enciende en `cambiarA()` o en modo manual, y siempre con agua.
2. Pasad la batería de pruebas completa. Uno dirige y anota el resultado mientras el otro ejecuta, y a mitad de la tabla os intercambiáis.
3. Grabad un vídeo corto o una secuencia de capturas del sistema funcionando.
4. Guardad una copia del código completo, copiándolo desde el panel de código de Tinkercad: es la versión de Tinkercad terminada y el punto de partida de la P11.

**Batería de pruebas.**

| N.º | Prueba | Esperado | Resultado |
| --- | --- | --- | --- |
| 1 | Arranque | Todo parado, trampilla cerrada, LCD con datos, LED latiendo |  |
| 2 | Suelo seco con agua | Ciclo de pulsos REGANDO → ABSORCION → ESPERA |  |
| 3 | Depósito vacío durante el riego | SIN\_AGUA, bomba parada, alarma |  |
| 4 | Temperatura de 20 a 30 y vuelta a 24 °C | Ventilador y trampilla con histéresis 28/25 |  |
| 5 | Humedad del aire de 60 a 85 y vuelta a 65 % | Ventilación con histéresis 80/70 |  |
| 6 | De 07:55 a 08:05 a oscuras | LED de cultivo se enciende a las 08:00 |  |
| 7 | `MODO MANUAL` y `BOMBA ON` | La bomba arranca; para sola a los 10 s |  |
| 8 | `BOMBA ON` en modo AUTO | Respuesta de error, la bomba no arranca |  |
| 9 | `SET suelo_min 50` con el suelo al 45 % | Empieza a regar |  |
| 10 | Comando inventado | Respuesta de error, el programa sigue |  |
| 11 | Pulsador de riego manual sin agua | La bomba no arranca |  |
| 12 | Diez minutos funcionando | Ningún bloqueo, el LCD sigue actualizándose |  |

**Al terminar.** La tabla de pruebas con los resultados y un vídeo corto o unas capturas del sistema funcionando, en el diario.

## Fase 4 · ESP32 y conectividad en Wokwi

Tinkercad solo simula el UNO, sin WiFi ni Bluetooth. Wokwi simula el ESP32, tiene el DHT22 real, deja repartir el código en varios archivos y da salida a internet. Aquí se ve si vuestro diseño era bueno: si lo era, solo cambian las clases que tocan el hardware.

### P11 · Migración a ESP32 en Wokwi, un archivo por clase

**Objetivo.** Llevar el invernadero a un ESP32 con un archivo `.h` y uno `.cpp` por clase, y sustituir el clima simulado por un DHT22 sin tocar la lógica.

**Sesiones.** 2. En la primera, el circuito y la estructura de archivos; en la segunda, el DHT22, la pantalla y la batería de pruebas.

**Componentes en Wokwi.** ESP32 DevKit, DHT22, potenciómetro (Wokwi no tiene sensor de humedad del suelo), módulo fotorresistencia, LCD 1602 en modo I2C, módulo de relé, tres LED (ventilador, luz de cultivo y LED de bomba en el relé), servo, zumbador, interruptor deslizante y pulsador.

**Mapa de pines del ESP32.**

| GPIO | Conectado a | Nota |
| --- | --- | --- |
| 34 | Potenciómetro = humedad del suelo | Solo entrada, ADC1 |
| 35 | Módulo fotorresistencia, salida AO | Solo entrada, ADC1 |
| 4 | DHT22, pata de datos |  |
| 21 / 22 | SDA / SCL del LCD | Pines I2C por defecto |
| 27 | Interruptor de la boya | `INPUT_PULLUP` |
| 26 | Pulsador de riego manual | `INPUT_PULLUP` |
| 25 | Entrada IN del módulo de relé (bomba) |  |
| 18 | LED del ventilador | PWM |
| 19 | LED de cultivo | PWM |
| 23 | Zumbador |  |
| 13 | Servo de la trampilla |  |
| 2 | LED de estado | LED integrado de la placa |

**Lo que cambia respecto al UNO.**

- El ESP32 funciona a **3,3 V**, no a 5 V. Los sensores van a 3V3.
- El conversor analógico es de **12 bits**: lee de 0 a 4095, no de 0 a 1023. Hay que recalibrar el suelo y la luz, pero no cambiar la clase.
- Las lecturas analógicas van en los GPIO 32–39 (ADC1). Los del ADC2 dejan de funcionar con el WiFi encendido.
- La librería del servo es `ESP32Servo` y la del LCD, `LiquidCrystal_I2C` (dirección 0x27).

**La nueva estructura.**

```text
sketch.ino              crea el invernadero y llama a iniciar() y actualizar()
Config.h                pines, umbrales y tiempos
Temporizador.h / .cpp
SensorClima.h           interfaz (solo .h)
SensorClimaDHT22.h / .cpp
SensorHumedadSuelo.h / .cpp
SensorLuz.h / .cpp
Actuador.h / .cpp
Zumbador.h / .cpp
Histeresis.h / .cpp
ControladorRiego.h / .cpp
Reloj.h                 interfaz (solo .h)
RelojSimulado.h / .cpp
Pantalla.h / .cpp       envuelve el LCD
Invernadero.h / .cpp    reúne todo: lecturas, control, estado JSON y comandos
libraries.txt
diagram.json
```

En Tinkercad, `enviarEstado()` y `ejecutarComando()` usaban variables globales. Aquí pasan a ser métodos de la clase `Invernadero`, que contiene los sensores, los actuadores y los controladores. `sketch.ino` queda en unas pocas líneas.

**Pasos.**

1. Entrad en [wokwi.com](https://wokwi.com) con vuestra cuenta, cread un proyecto **ESP32** y guardadlo con el nombre `invernadero-esp32`.
2. Añadid los componentes con el botón **+** y conectadlos según el mapa. En el LCD, cambiad el atributo `pins` a `i2c`.
3. Cread `libraries.txt` con las librerías de abajo.
4. Pasad las clases a archivos, empezando por `Histeresis`, que os damos como modelo. Para añadir un archivo, usad la flecha junto a las pestañas y **New file**.
5. Escribid `SensorClimaDHT22` y `Pantalla`. Son las dos clases nuevas de verdad.
6. Pasad la batería de pruebas de la P10 (salvo lo que dependa del motor, que aquí son LED).

**libraries.txt**

```text
DHT sensor library for ESPx
LiquidCrystal I2C
ESP32Servo
```

**Modelo: una clase en dos archivos.**

```cpp
// Histeresis.h
#pragma once

/**
 * Control todo/nada con dos umbrales para evitar oscilaciones.
 */
class Histeresis {
public:
  /**
   * @param umbralEncender Valor a partir del cual se activa.
   * @param umbralApagar   Valor por debajo del cual se desactiva.
   */
  Histeresis(float umbralEncender, float umbralApagar);

  /** @return true si la salida debe estar activa tras la nueva medida. */
  bool actualizar(float valor);

  /** Cambia los dos umbrales. */
  void configurar(float umbralEncender, float umbralApagar);

private:
  float umbralEncender;
  float umbralApagar;
  bool activo;
};
```

```cpp
// Histeresis.cpp
#include "Histeresis.h"

Histeresis::Histeresis(float umbralEncender, float umbralApagar)
  : umbralEncender(umbralEncender), umbralApagar(umbralApagar), activo(false) {}

bool Histeresis::actualizar(float valor) {
  if (!activo && valor >= umbralEncender) {
    activo = true;
  } else if (activo && valor <= umbralApagar) {
    activo = false;
  }
  return activo;
}

void Histeresis::configurar(float encender, float apagar) {
  umbralEncender = encender;
  umbralApagar = apagar;
}
```

**El sensor real.**

```cpp
// SensorClimaDHT22.h
#pragma once
#include <DHTesp.h>
#include "SensorClima.h"

/**
 * Clima real con un DHT22. Implementa la misma interfaz que el sensor simulado.
 */
class SensorClimaDHT22 : public SensorClima {
public:
  explicit SensorClimaDHT22(uint8_t pin);

  /** Configura el sensor. Llamar en setup(). */
  void iniciar();

  float leerTemperatura() override;
  float leerHumedad() override;

private:
  uint8_t pin;
  DHTesp dht;
};
```

En el `.cpp`, `iniciar()` llama a `dht.setup(pin, DHTesp::DHT22)` y los otros dos métodos devuelven `dht.getTemperature()` y `dht.getHumidity()`. Si la lectura falla, el DHT22 devuelve `NaN`: comprobadlo con `isnan()` y conservad el último valor bueno.

**Comprobación.**

- [ ] Los archivos de `ControladorRiego`, `Histeresis`, `Actuador` y `Temporizador` tienen la misma lógica que en Tinkercad. Comprobadlo comparándolos con el código de la P10.
- [ ] El código que usa el clima sigue trabajando con `SensorClima`, sin saber que ahora hay un DHT22 detrás.
- [ ] La batería de pruebas de la P10 pasa en Wokwi.
- [ ] Al poner el DHT22 a 30 °C en su control, se enciende el LED del ventilador.

**Reto.** El UNO solo tenía cuatro entradas analógicas libres. Con el ESP32, añadid un segundo sensor de suelo (otro potenciómetro en el GPIO 32) y regad si cualquiera de las dos macetas está seca.

**Al terminar.** El enlace al proyecto de Wokwi en el diario.

### P12 · WiFi, hora por NTP y publicación MQTT

**Objetivo.** Conectar el invernadero a internet, tomar la hora real y publicar su estado en un servidor MQTT del que cualquier app pueda leer, y recibir por el mismo camino los comandos de la P9.

**Sesiones.** 2. En la primera, WiFi y hora; en la segunda, MQTT.

**Cómo funciona MQTT.** El invernadero no habla directamente con la app. Los dos se conectan a un intermediario (el **broker**). El invernadero **publica** su estado en un tema, una ruta de texto como `cfp-invernadero/equipo1/estado`, y la app está **suscrita** a ese tema. Para mandar órdenes se hace al revés. Así la app puede ser web, Android o un panel de Node-RED sin que el ESP32 cambie.

**Los temas.** Cambiad `equipo1` por un nombre vuestro: el broker es público y lo comparte gente de todo el mundo.

| Tema | Quién publica | Contenido |
| --- | --- | --- |
| `cfp-invernadero/equipo1/estado` | Invernadero, cada 10 s, retenido | El JSON de estado de la P9 |
| `cfp-invernadero/equipo1/cmd` | App | Un comando de la P9, como `GET` o `MODO MANUAL` |
| `cfp-invernadero/equipo1/resp` | Invernadero | La respuesta a cada comando |
| `cfp-invernadero/equipo1/online` | Invernadero (`1`) y broker (`0`), retenido | Si el invernadero está conectado |

**Retenido** quiere decir que el broker guarda el último mensaje y se lo da a quien se suscriba después. El `0` de `online` lo publica el propio broker si el invernadero desaparece sin despedirse: es el **testamento** (*last will*).

**Pasos.**

1. Añadid a `libraries.txt` la línea `PubSubClient`.
2. **WiFi.** Conectad a la red simulada de Wokwi con `WiFi.begin("Wokwi-GUEST", "", 6);`. No esperéis en un bucle a que conecte: comprobad `WiFi.status()` cada segundo con un temporizador. El invernadero tiene que seguir regando aunque no haya red.
3. **Hora.** Cread `RelojNTP`, que implementa `Reloj`. En `iniciar()` llamad a `configTzTime("CET-1CEST,M3.5.0,M10.5.0/3", "pool.ntp.org");` y en `minutosDelDia()` usad `getLocalTime()`. Esa cadena es la zona horaria de España peninsular, con el cambio de hora incluido.
4. **MQTT.** Cread la clase `ConexionMqtt` con el código de abajo y completad lo que falta.
5. Para ver los mensajes, abrid el [cliente web de HiveMQ](https://www.hivemq.com/demos/websocket-client/), conectad con los valores por defecto y suscribios a `cfp-invernadero/equipo1/#`. El `#` recoge todos los temas que cuelgan de esa ruta.

**Código base.**

```cpp
// BufferPrint.h
#pragma once
#include <Arduino.h>

/**
 * Print que escribe en memoria. Permite reutilizar enviarEstado() y
 * ejecutarComando() de la P9 para generar mensajes MQTT.
 */
class BufferPrint : public Print {
public:
  size_t write(uint8_t c) override {
    if (longitud < sizeof(texto) - 1) {
      texto[longitud++] = c;
      texto[longitud] = '\0';
      return 1;
    }
    return 0;
  }
  const char* c_str() const { return texto; }
  void vaciar() { longitud = 0; texto[0] = '\0'; }

private:
  char texto[256] = "";
  size_t longitud = 0;
};
```

```cpp
// ConexionMqtt.cpp (extracto)
#include <WiFi.h>
#include <PubSubClient.h>
#include "ConexionMqtt.h"

WiFiClient clienteWifi;
PubSubClient mqtt(clienteWifi);

void ConexionMqtt::iniciar() {
  mqtt.setServer("broker.hivemq.com", 1883);
  mqtt.setBufferSize(512);
  mqtt.setCallback(alRecibir);   // función estática de la clase
}

/** Se llama en cada vuelta de loop(). Nunca bloquea más de un intento. */
void ConexionMqtt::atender() {
  if (WiFi.status() != WL_CONNECTED) return;
  if (!mqtt.connected() && tReconectar.vencido()) {
    String id = "invernadero-" + String((uint32_t)ESP.getEfuseMac(), HEX);
    if (mqtt.connect(id.c_str(), TEMA_ONLINE, 1, true, "0")) {
      mqtt.publish(TEMA_ONLINE, "1", true);
      mqtt.subscribe(TEMA_CMD);
    }
  }
  mqtt.loop();
  if (mqtt.connected() && tPublicar.vencido()) {
    BufferPrint mensaje;
    invernadero.enviarEstado(mensaje);
    // TODO: publicar mensaje.c_str() en TEMA_ESTADO, retenido
  }
}

/** Llega un mensaje a un tema suscrito. */
void ConexionMqtt::alRecibir(char* tema, byte* datos, unsigned int longitud) {
  char linea[64];
  // TODO: copiar como mucho 63 bytes de datos en linea y terminar con '\0'
  BufferPrint respuesta;
  // TODO: ejecutar el comando con invernadero.ejecutarComando()
  //       y publicar la respuesta en TEMA_RESP
}
```

Los datos que entrega `PubSubClient` no terminan en `'\0'`: por eso hay que copiarlos y cerrarlos antes de tratarlos como texto.

**Comprobación.**

- [ ] En el monitor serie se ve la IP y la hora real.
- [ ] El LED de cultivo obedece al horario con la hora real.
- [ ] En el cliente web llega el estado cada 10 s.
- [ ] Al publicar `GET` en `.../cmd` llega el estado en `.../resp`.
- [ ] `MODO MANUAL` y `BOMBA ON` desde el cliente web activan el relé.
- [ ] Al parar la simulación, `online` pasa a `0` al cabo de unos segundos.
- [ ] Con el WiFi cortado (cambiad el nombre de la red), el riego y la ventilación siguen funcionando.

**Reto.** Publicad también en `.../evento` cada vez que el riego cambie de estado, con un JSON como `{"riego":"REGANDO","min":845}`.

**Al terminar.** La tabla de temas MQTT en el diario, junto al contrato de la P9, y una captura del cliente web recibiendo mensajes.

Un broker público no tiene seguridad: cualquiera que adivine vuestro tema puede leer y mandar comandos. Para clase es suficiente; en un invernadero real se usa un broker propio con usuario, contraseña y cifrado TLS.

### P13 · Ampliación: control remoto y contrato para la app

**Objetivo.** Dejar documentado el contrato entre el invernadero y la app, y hacer un primer cliente que lo use. Es opcional: la puede hacer quien vaya por delante, en paralelo con la fase 5, o todo el equipo si sobra tiempo en junio.

**Sesiones.** 2.

**Pasos.**

1. **El contrato.** Escribid en el diario todo lo que una app necesita saber para hablar con el invernadero sin leer su código:
   - La lista de temas y quién publica en cada uno.
   - Cada campo del JSON de estado, con su tipo, sus unidades y su rango.
   - Cada comando, sus argumentos válidos y sus respuestas posibles.
   - Un ejemplo completo de conversación: la app pide `GET`, el invernadero responde.
2. **Comandos con identificador.** Si la app manda dos comandos seguidos, ¿cómo sabe qué respuesta es de cuál? Añadid un identificador opcional al principio, como `#17 BOMBA ON`, y devolvedlo en la respuesta: `{"id":17,"ok":true}`.
3. **Validación.** Rechazad valores fuera de rango: `SET suelo_min 150` o `SET t_off 40` con `t_on` en 28 deben responder con un error que explique el motivo.
4. **Primer cliente.** Elegid con el profesor una de estas opciones y haced una pantalla que muestre el estado en vivo y tenga dos botones: regar y cambiar de modo.

| Opción | Qué se usa | Para quién encaja |
| --- | --- | --- |
| Web | Página HTML con la librería MQTT.js, conectada al broker por WebSockets | Quien quiera practicar JavaScript y desarrollo web |
| Android | App con un cliente MQTT para Kotlin o Java | Quien quiera practicar desarrollo móvil |
| Node-RED | Flujo con nodos MQTT y panel de control, sin programar casi nada | Quien quiera ver resultados rápido y centrarse en el diseño del panel |

**Comprobación.**

- [ ] Otra persona, solo con ese contrato, sabe qué mandar para activar el modo manual y regar.
- [ ] Cada respuesta lleva el identificador del comando que la provocó.
- [ ] Los valores fuera de rango se rechazan con un mensaje claro.
- [ ] El cliente muestra el estado y sus botones funcionan con el invernadero de Wokwi en marcha.

**Al terminar.** El contrato completo en el diario y el enlace o el código del cliente.

## Fase 5 · Montaje físico

El invernadero real lleva un ESP32 con el programa de la P12. Si el diseño de clases es bueno, pasar a los componentes reales obliga a cambiar muy poco código: calibraciones, una pantalla distinta y que el ventilador y la luz pasen a ser actuadores todo o nada. Primero se prueba cada parte por separado en la mesa (M1 y M2) y solo después se monta en el invernadero (M3 y M4).

### Qué cambia respecto a la simulación

| En Wokwi | En el invernadero real | Qué hay que tocar |
| --- | --- | --- |
| Potenciómetro como sensor de suelo | Dos sensores capacitivos | Recalibrar: la lectura **baja** con la humedad. Segundo sensor en el GPIO 32 |
| DHT22 | DHT22 | Nada |
| Módulo fotorresistencia | Módulo fotorresistencia | Recalibrar con luz real |
| Interruptor deslizante | Boya de nivel | Comprobar en qué posición cierra el contacto |
| LED en el relé | Bomba sumergible a través del módulo de relés | `Actuador bomba(PIN_BOMBA, true);`: el módulo se activa en bajo |
| LED del ventilador con PWM | Ventilador de 12 V en otro canal de relé | Pasa a ser un `Actuador`: todo o nada, sin velocidad |
| LED de cultivo con PWM | Tira LED de 12 V en otro canal de relé | Pasa a ser un `Actuador`: todo o nada, sin amanecer |
| LCD 1602 | Pantalla OLED de 0,96" (SSD1306) | Nueva implementación de `Pantalla`; quien la usa no cambia |
| Hora por NTP | Hora por NTP con la WiFi del centro | Cambiar nombre y contraseña de la red en `Config.h` |

Para regular la velocidad del ventilador o el brillo de la tira haría falta un módulo MOSFET, que no está en la lista de material. Con relés el sistema funciona igual, solo que sin regulación.

### Mapa de pines del montaje real

Es el de la P11 con tres cambios: un segundo sensor de suelo, la pantalla OLED en lugar del LCD y relés donde antes había LED.

| GPIO | Conectado a |
| --- | --- |
| 34 | Sensor de suelo 1, salida AOUT |
| 32 | Sensor de suelo 2, salida AOUT |
| 35 | Módulo fotorresistencia, salida AO |
| 4 | DHT22, datos |
| 21 / 22 | SDA / SCL de la pantalla OLED |
| 27 | Boya del depósito |
| 26 | Pulsador de riego manual |
| 25 | Relé 1: bomba |
| 18 | Relé 2: ventilador |
| 19 | Relé 3: tira LED |
| 13 | Servo de la trampilla |
| 23 | Zumbador (opcional) |

### Normas de seguridad

Todo el montaje funciona a 12 V y 5 V, sin peligro eléctrico para las personas. Los riesgos reales son quemar componentes y mezclar agua con electrónica.

1. **Nada a 230 V.** El único aparato que va al enchufe es la fuente de 12 V, y la enchufa el profesor.
2. **Sin alimentación mientras se cablea.** Cualquier cambio de cables se hace con la fuente desenchufada y el USB quitado.
3. **El reductor se ajusta antes de conectar nada.** El LM2596 sale de fábrica a una tensión cualquiera: se ajusta a 5,0 V con el multímetro y sin nada conectado a su salida.
4. **Polaridad, dos veces.** Antes de dar corriente, una persona distinta de quien cableó revisa positivos y negativos.
5. **El agua, abajo; la electrónica, arriba.** La caja estanca va por encima del depósito y de las macetas, y los cables entran por debajo de la caja.
6. **La bomba nunca en seco.** Se prueba siempre dentro de un vaso con agua.

### M1 · Banco de pruebas: alimentación y sensores reales

**Objetivo.** Tener el ESP32 programado desde vuestro ordenador, la alimentación preparada y cada sensor real calibrado, todo encima de la mesa y fuera del invernadero.

**Sesiones.** 2. En la primera, entorno de programación y alimentación; en la segunda, sensores y calibración.

**Material.** ESP32 DevKit y su placa de expansión, fuente de 12 V, adaptador jack con bornas, reductor LM2596, multímetro, DHT22, dos sensores capacitivos de suelo, módulo fotorresistencia, boya, cables dupont, un vaso con agua y una maceta con tierra seca.

**Pasos.**

1. **Entorno.** Instalad Arduino IDE 2 y, en el gestor de placas, el paquete **esp32** de Espressif. Elegid la placa **ESP32 Dev Module**. Instalad las librerías que ya usabais en Wokwi y añadid **Adafruit SSD1306** y **Adafruit GFX** para la pantalla. Si el ordenador no ve la placa, falta el controlador USB (CP210x o CH340, según el chip que lleve la placa).
2. **Primer programa.** Subid un parpadeo del LED integrado (GPIO 2). Si la subida se queda en «Connecting…», mantened pulsado el botón BOOT de la placa hasta que empiece a escribir.
3. **Alimentación.** Conectad la fuente al adaptador jack y este a la entrada del LM2596. **Sin nada conectado a la salida**, girad el tornillo del potenciómetro hasta que el multímetro marque 5,0 V. Esa salida será la línea de 5 V del montaje.
4. **Sensores.** Alimentad todos los sensores a **3,3 V** desde la placa: así su salida nunca supera lo que admite el ESP32. Conectadlos según el mapa de pines y escribid un programa corto que imprima cada segundo las lecturas crudas.
5. **Calibración.** Rellenad la tabla de abajo. Los sensores capacitivos se meten en el agua solo hasta la línea marcada en la placa: la parte de arriba tiene la electrónica al aire.
6. **Boya.** Comprobad qué lectura da con la boya arriba y con la boya abajo. Si sale al revés de lo que espera el programa, se le da la vuelta a la boya en su eje, sin tocar el código.

**Tabla de calibración** (copiadla en el diario)

| Sensor | Seco u oscuro | Mojado o con luz | Observaciones |
| --- | --- | --- | --- |
| Suelo 1, al aire |  |  |  |
| Suelo 1, tierra seca |  |  |  |
| Suelo 1, tierra recién regada |  |  |  |
| Suelo 1, en agua |  |  |  |
| Suelo 2 (mismos cuatro casos) |  |  |  |
| Fotorresistencia, tapada y bajo una lámpara |  |  |  |
| DHT22, comparado con un termómetro |  |  |  |

Los dos sensores de suelo no dan los mismos valores aunque sean del mismo modelo: cada uno lleva su propia calibración. Para el programa, «seco» es la tierra seca y «mojado» la tierra recién regada, no el aire ni el vaso de agua.

**Comprobación.**

- [ ] El ESP32 se programa desde el ordenador y el LED integrado parpadea.
- [ ] La salida del LM2596 marca entre 4,9 y 5,1 V.
- [ ] Cada sensor responde: al mojar, tapar, soplar o mover la boya, la lectura cambia.
- [ ] La tabla de calibración está completa.

**Al terminar.** Pasad las calibraciones a `Config.h` y guardad en el diario la tabla y una foto del banco de pruebas.

### M2 · Banco de pruebas: actuadores reales

**Objetivo.** Mover la bomba, el ventilador, la tira LED y el servo desde el ESP32 con el programa de la P12 adaptado, y medir el caudal de la bomba para decidir cuánto dura un pulso de riego.

**Sesiones.** 2. En la primera, el módulo de relés y las cargas; en la segunda, la pantalla OLED, los cambios de código y el caudal.

**Material.** Lo de M1, más el módulo de 4 relés, la bomba con su tubo, el ventilador, la tira LED, el servo, la pantalla OLED, dos vasos (uno con agua) y una jarra medidora.

**El módulo de relés con un ESP32.** El módulo está pensado para 5 V y el ESP32 da 3,3 V. Si el módulo tiene el puente **JD-VCC**, quitadlo: así las bobinas se alimentan a 5 V por JD-VCC y la parte que ve el ESP32 funciona a 3,3 V por VCC. Sin ese puente, alimentad VCC a 5 V y comprobad que cada relé se suelta de verdad cuando el pin está en `HIGH`; si alguno se queda pegado, avisad al profesor.

**Montaje.**

| Parte | Conexión |
| --- | --- |
| Módulo de relés | JD-VCC a 5 V del LM2596, VCC a 3V3 del ESP32, GND al GND común, IN1/IN2/IN3 a GPIO 25/18/19 |
| Bomba | 5 V del LM2596 → COM del relé 1; NO → bomba (+); bomba (−) → GND |
| Ventilador | 12 V → COM del relé 2; NO → cable rojo; cable negro → GND de 12 V |
| Tira LED | 12 V → COM del relé 3; NO → tira (+); tira (−) → GND de 12 V |
| Servo | Marrón a GND, rojo a 5 V del LM2596, naranja a GPIO 13 |
| Pantalla OLED | GND, VCC a 3V3, SDA a GPIO 21, SCL a GPIO 22 |
| ESP32 | VIN al 5 V del LM2596 solo en el montaje final; mientras se programa por USB, ese cable va suelto |

El servo y la bomba se alimentan de la línea de 5 V del reductor, nunca de los pines de la placa: sus picos de corriente reiniciarían el ESP32.

**¿Llega la fuente?** Sumad lo que consume cada parte, mejor con la etiqueta de vuestros componentes delante. Con valores típicos, la línea de 5 V pide como mucho 1 A (ESP32, tres relés, bomba y servo). Por la potencia, eso equivale a medio amperio en la entrada de 12 V del reductor:

```latex
P = V \cdot I = 5 \cdot 1 = 5\ \text{W} \qquad I_{12\,V} \approx \frac{5\ \text{W}}{12\ \text{V} \cdot 0{,}85} \approx 0{,}5\ \text{A}
```

El 0,85 es el rendimiento aproximado del reductor. A eso se suman el ventilador (unos 0,2 A) y la tira LED (hasta 1,5 A según el modelo). Si el total pasa de 2 A, la fuente se queda corta.

**Cambios en el código de la P12.**

1. Bomba, ventilador y tira LED son `Actuador` activos en bajo (en el ESP32, dentro de iniciar() va primero pinMode() y después digitalWrite(), porque al revés el núcleo puede ignorar la escritura): `Actuador bomba(PIN_BOMBA, true);`.
2. `controlarVentilacion()` y `controlarLuz()` dejan de usar `analogWrite()` y llaman a `encender()` y `apagar()`.
3. Calibraciones de M1 en `Config.h`, y el segundo sensor de suelo: se riega si cualquiera de las dos macetas está seca.
4. Nueva implementación de `Pantalla` para la OLED, con los mismos métodos públicos que la del LCD.

```cpp
// Pantalla.h (versión OLED)
#pragma once
#include <Adafruit_SSD1306.h>

/**
 * Pantalla OLED de 128 × 64 píxeles por I2C (dirección 0x3C).
 * Dibuja en memoria y vuelca la imagen entera de una vez, así que no parpadea.
 */
class Pantalla {
public:
  /** @return false si la pantalla no responde en el bus I2C. */
  bool iniciar();

  /** Dibuja las lecturas y el estado del riego. Adaptad los parámetros a vuestra clase Estado. */
  void mostrar(float temperatura, float humedadAire, int suelo1, int suelo2, const char* estadoRiego);

private:
  Adafruit_SSD1306 oled{128, 64, &Wire, -1};
};
```

```cpp
// Pantalla.cpp (extracto)
bool Pantalla::iniciar() {
  if (!oled.begin(SSD1306_SWITCHCAPVCC, 0x3C)) return false;
  oled.setTextColor(SSD1306_WHITE);
  oled.setTextSize(1);
  return true;
}

void Pantalla::mostrar(float temperatura, float humedadAire, int suelo1, int suelo2, const char* estadoRiego) {
  oled.clearDisplay();
  oled.setCursor(0, 0);
  oled.printf("T %.1f C   HR %.0f %%\n", temperatura, humedadAire);
  // TODO: suelo de las dos macetas, estado del riego y hora
  oled.display();
}
```

En el ESP32, a diferencia del UNO, `printf` con `%f` sí funciona.

**El caudal de la bomba.** Con la bomba en un vaso con agua y el tubo en la jarra medidora, mandad `MODO MANUAL`, `BOMBA ON` y, a los 10 s, `BOMBA OFF`. Los mililitros recogidos, divididos entre 10, son el caudal en ml/s. Decidid con el profesor cuánta agua lleva cada pulso para el tamaño de vuestras macetas y calculad `msPulso` a partir del caudal.

**Comprobación.**

- [ ] Cada relé hace clic y enciende su carga al activarlo, y la suelta al desactivarlo.
- [ ] Al arrancar el ESP32, ningún relé se activa ni un instante.
- [ ] La bomba pasa agua de un vaso a otro y para sola a los 10 s en modo manual.
- [ ] El servo abre y cierra la trampilla.
- [ ] La pantalla OLED muestra las lecturas.
- [ ] El ESP32 no se reinicia cuando arrancan la bomba o el ventilador.
- [ ] El estado sigue llegando por MQTT con la WiFi del centro.

**Al terminar.** Anotad en el diario el caudal y el `msPulso` elegido, y guardad una copia del código adaptado.

### M3 · Montaje en el invernadero

**Objetivo.** Pasar del banco de pruebas al invernadero: electrónica en la caja estanca, cada sensor y actuador en su sitio y los cables ordenados y protegidos del agua.

**Sesiones.** 2. En la primera, la caja estanca y el recorrido de los cables; en la segunda, colocar sensores y actuadores y conectar.

**Material.** Todo lo de M1 y M2, la caja estanca, la protoboard o la placa de expansión, bridas, cinta aislante, velcro, el depósito, las macetas con tierra y semillas, y una taladradora con brocas para hacer los pasos de cables (la usa el profesor).

**Dónde va cada cosa.**

| Elemento | Dónde | Por qué |
| --- | --- | --- |
| Caja estanca | Fuera del invernadero, o dentro y en lo más alto | La condensación y las salpicaduras son el mayor enemigo de la electrónica |
| Sensores de suelo | Uno por maceta, clavados en vertical hasta la línea marcada, a medio camino entre la planta y el borde | Junto a la pared de la maceta la tierra se seca antes y el sensor miente |
| DHT22 | En el centro, a la altura de las plantas, a la sombra | Al sol directo marca varios grados de más |
| Fotorresistencia | Arriba, mirando al cielo, lejos de la tira LED | Si la tira la ilumina, el invernadero cree que es de día y la apaga |
| Tira LED | Encima de las plantas, a 20–30 cm | Más lejos, apenas llega luz útil |
| Ventilador | En la parte alta, sacando aire hacia fuera | El aire caliente y húmedo se acumula arriba |
| Trampilla con servo | En el lado opuesto al ventilador | El aire entra por un lado y sale por el otro |
| Depósito y bomba | En el suelo, por debajo de las macetas | Si la bomba se para, el agua no sigue cayendo por gravedad |
| Tubo de riego | Una salida por maceta, con el extremo sujeto con una brida | Un tubo suelto riega el suelo, no la planta |
| Boya | Dentro del depósito, a un tercio de altura | Avisa antes de que la bomba aspire aire |

**Pasos.**

1. Dibujad en papel la planta del invernadero con la posición de cada elemento y el recorrido de los cables. Haced una foto para el diario.
2. Pasad la electrónica del banco a la caja estanca: placa de expansión, módulo de relés, LM2596 y adaptador jack, sujetos con velcro o tornillos.
3. Etiquetad cada cable en sus dos extremos con cinta y rotulador (`SUELO1`, `BOMBA`, `12V`…). Cuando algo falle, os ahorrará media sesión.
4. Los cables entran en la caja **por abajo** y hacen una curva hacia abajo antes de entrar (bucle de goteo): así el agua que resbale por el cable cae al suelo y no entra en la caja.
5. Colocad sensores y actuadores según la tabla y sujetad los cables a la estructura con bridas.
6. Con todo desenchufado, una persona que no haya cableado revisa cada conexión contra el mapa de pines.

**Comprobación.**

- [ ] Ningún cable cuelga ni pasa por donde cae agua.
- [ ] Los cables están etiquetados en los dos extremos.
- [ ] La tapa de la caja cierra y los cables entran por abajo con su bucle de goteo.
- [ ] Al dar corriente, el monitor serie muestra lecturas razonables de todos los sensores.

**Al terminar.** Fotos del montaje y del plano en el diario.

### M4 · Puesta en marcha y ajuste con plantas

**Objetivo.** Dejar el invernadero funcionando solo, con umbrales y tiempos ajustados a las plantas reales, y comprobar durante unas semanas que se comporta como se espera.

**Sesiones.** 1, y unos minutos de revisión en las sesiones siguientes.

**Pasos.**

1. **Tiempos reales.** En Tinkercad la absorción duraba 20 s para poder probarla en clase. Con tierra de verdad, el agua tarda minutos en llegar al sensor: empezad con 10 minutos y con el `msPulso` que calculasteis en M2.
2. **Umbral de riego.** Regad a mano hasta que la tierra esté bien húmeda y anotad el porcentaje que marca. Al cabo de unos días, cuando la tierra esté seca al tacto en la superficie, anotadlo de nuevo. El umbral `suelo_min` va algo por encima de ese segundo valor. Ajustadlo por MQTT con `SET suelo_min`, sin reprogramar.
3. **Batería de pruebas real.** Pasad la tabla de abajo con el invernadero completo.
4. **Registro.** Durante las semanas siguientes, al empezar cada sesión, mirad el último estado por MQTT y la planta, y apuntad en el diario la fecha, la humedad de las dos macetas, si ha regado y cómo están las plantas.

**Batería de pruebas real.**

| Prueba | Cómo provocarla | Esperado |
| --- | --- | --- |
| Arranque | Enchufar la fuente | Ningún relé se activa, la pantalla muestra datos, llega `online` = 1 por MQTT |
| Riego automático | `SET suelo_min` por encima de la humedad actual | Un pulso de riego, absorción y nueva medida |
| Depósito vacío | Levantar la boya con la mano durante un riego | La bomba para al momento y se avisa por pantalla y MQTT |
| Calor | Acercar una lámpara al DHT22 o calentarlo con la mano | Ventilador encendido y trampilla abierta; al enfriar, se apagan con histéresis |
| Luz de cultivo | Tapar la fotorresistencia dentro del horario | La tira LED se enciende |
| Sin WiFi | Apagar el punto de acceso o cambiar la contraseña | El riego y la ventilación siguen funcionando; al volver la red, vuelve MQTT |
| Corte de luz | Desenchufar la fuente y volver a enchufar | Arranca solo y retoma el control |

**Mantenimiento.**

- Rellenar el depósito antes de que la boya lo pida, y lavarlo cada pocas semanas para que no crezcan algas.
- Comprobar que los tubos siguen sujetos y apuntando a cada maceta.
- Limpiar con un trapo seco la tierra que se acumula en los sensores capacitivos por encima de la línea.
- Revisar si hay condensación dentro de la caja estanca.

**Comprobación.**

- [ ] La batería de pruebas real pasa entera.
- [ ] El invernadero ha regado solo al menos una vez sin que nadie lo provoque.
- [ ] Las plantas siguen vivas al cabo de dos semanas.

**Al terminar.** Guardad una copia del código final y, si os apetece, grabad un vídeo corto del invernadero regando solo para enseñárselo al resto del club.

## Recursos

Clase de Tinkercad del club: [tinkercad.com/joinclass/UFHDMVQSP](https://www.tinkercad.com/joinclass/UFHDMVQSP), código `UFHDMVQSP`.

- [Tinkercad](https://www.tinkercad.com): simulador de circuitos con Arduino UNO (fases 1 a 3).
- [Wokwi](https://wokwi.com): simulador de ESP32 (fase 4). Guía de [WiFi en Wokwi](https://docs.wokwi.com/guides/esp32-wifi).
- [Referencia del lenguaje Arduino](https://www.arduino.cc/reference/en/): `millis()`, `analogRead()`, `map()`, `Serial` y el resto de funciones.
- [Adafruit\_LiquidCrystal](https://github.com/adafruit/Adafruit_LiquidCrystal): la librería del LCD I2C en Tinkercad.
- [DHTesp](https://github.com/beegee-tokyo/DHTesp): la librería del DHT22 en Wokwi («DHT sensor library for ESPx»).
- [ESP32Servo](https://github.com/madhephaestus/ESP32Servo): servo en el ESP32.
- [PubSubClient](https://github.com/knolleary/pubsubclient): cliente MQTT para Arduino y ESP32.
- [Cliente web MQTT de HiveMQ](https://www.hivemq.com/demos/websocket-client/): para ver y mandar mensajes desde el navegador.
- [JSONLint](https://jsonlint.com): para validar el JSON de estado.
