# diseno-circuitos-digitales-semanas1-4

`build: passing` | `weeks: 1-4` | `license: MIT` | `unit: 1` | `status: complete`

> **Repositorio Didáctico de Aprendizaje**: Compendio teórico-práctico correspondiente a la **Unidad 1: Análisis de Lógica Combinacional con Diseño Clásico** (Semanas 1 a 4) de la asignatura *Diseño de Circuitos Digitales* de la Carrera de Computación (Universidad Nacional de Loja).

---

## Estratigrafía del Repositorio (`repository-tree`)

```text
.
├── README.md
├── LICENSE
├── docs/
│   ├── semana-01-sistemas-numericos-y-compuertas/
│   │   ├── README.md
│   │   ├── 01-sistemas-y-conversiones.md
│   │   ├── 02-aritmetica-y-codigos.md
│   │   ├── 03-compuertas-logicas-74ls.md
│   │   └── ape-01-entorno-y-compuertas.md
│   ├── semana-02-algebra-boole-y-formas-canonicas/
│   │   ├── README.md
│   │   ├── 01-postulados-y-teoremas.md
│   │   ├── 02-formas-canonicas-sop-pos.md
│   │   ├── 03-caso-estudio-alarma-3-sensores.md
│   │   └── ape-02-canonicas-y-simplificacion.md
│   ├── semana-03-mapas-karnaugh-y-universales/
│   │   ├── README.md
│   │   ├── 01-mapas-karnaugh-3-4-var.md
│   │   ├── 02-condiciones-indiferentes.md
│   │   ├── 03-universalidad-nand-nor.md
│   │   └── ape-03-optimizacion-hardware.md
│   └── semana-04-bloques-aritmeticos-combinacionales/
│       ├── README.md
│       ├── 01-semisumador-y-sumador-completo.md
│       ├── 02-sumador-paralelo-4bit-ripple-carry.md
│       ├── 03-restador-complemento-a-dos.md
│       ├── 04-comparador-magnitud-y-alu.md
│       └── ape-04-circuitos-sumadores.md
└── tests/
    └── autoevaluaciones-semanas-1-a-4.md
```

---

## 1. Semana 1: Sistemas Numéricos, Códigos y Compuertas Lógicas Fundamentales

### 1.1 Representación de la Información en Hardware Digital
En los sistemas de computación presenciales y de arquitectura moderna, la información se representa físicamente mediante dos estados eléctricos diferenciados (lógica positiva: nivel alto $V_{DD} / 5\text{V}$ como '1' y nivel bajo $GND / 0\text{V}$ como '0'). La necesidad de fundamentar la construcción de hardware parte de comprender que todo programa ejecutable se traduce en última instancia a señales eléctricas manipuladas por redes combinacionales.

### 1.2 Sistemas Numéricos y Conversión de Bases
Los sistemas de numeración posicionales binario (base 2), octal (base 8) y hexadecimal (base 16) constituyen el lenguaje formal de representación de datos en hardware.

#### Procedimientos de Conversión entre Bases
1. **Decimal a Binario / Octal / Hexadecimal**: División sucesiva por la base destino guardando los residuos.
2. **Binario a Hexadecimal / Octal**: Agrupación de bits de derecha a izquierda en bloques de 4 bits (hexadecimal) o 3 bits (octal).

| Sistema | Base | Símbolos Utilizados | Ejemplo de Representación |
| :--- | :--- | :--- | :--- |
| Binario | 2 | 0, 1 | $(1101.01)_2$ |
| Octal | 8 | 0, 1, 2, 3, 4, 5, 6, 7 | $(15.2)_8$ |
| Decimal | 10 | 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 | $(13.25)_{10}$ |
| Hexadecimal | 16 | 0-9, A, B, C, D, E, F | $(D.4)_{16}$ |

### 1.3 Aritmética Binaria, Complemento a Dos y Códigos

#### Representación en Complemento a Dos ($C_2$)
Para representar números enteros con signo en un ancho de palabra de $n$ bits:
- El bit más significativo (MSB) actúa como bit de signo ($0$ para positivo, $1$ para negativo).
- El valor negativo de un número $A$ se calcula mediante $C_2(A) = \bar{A} + 1$, donde $\bar{A}$ representa el complemento a uno (inversión bit a bit).

#### Códigos Digitales
- **BCD (Binary Coded Decimal)**: Codificación directa de cada dígito decimal mediante 4 bits binarios (de 0000 a 1001).
- **Código Gray**: Código no ponderado donde dos números consecutivos difieren en un único bit, minimizando errores de transición en sensores y codificadores.
- **ASCII**: Código de 7 u 8 bits para representación de caracteres alfanuméricos y de control.

### 1.4 Compuertas Lógicas y Hojas de Datos (Familia 74LS)
Las compuertas lógicas son los bloques constitutivos fundamentales. A continuación se presenta la tabla de verdad unificada para las compuertas de dos entradas:

| Entrada $A$ | Entrada $B$ | AND ($A \cdot B$) | OR ($A + B$) | NAND ($\overline{A \cdot B}$) | NOR ($\overline{A + B}$) | XOR ($A \oplus B$) | XNOR ($A \odot B$) |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| 0 | 0 | 0 | 0 | 1 | 1 | 0 | 1 |
| 0 | 1 | 0 | 1 | 1 | 0 | 1 | 0 |
| 1 | 0 | 0 | 1 | 1 | 0 | 1 | 0 |
| 1 | 1 | 1 | 1 | 0 | 0 | 0 | 1 |

> **Nota de Lectura de Hojas de Datos (74LS)**: En circuitos integrados de la familia TTL 74LS (por ejemplo, 74LS08 para AND, 74LS02 para NOR, 74LS00 para NAND, 74LS86 para XOR), el pin de alimentación $V_{CC}$ corresponde típicamente al pin 14 y la masa $GND$ al pin 7.

### 1.5 Práctica Experimental APE N.º 01
- **Objetivo**: Reconocimiento del entorno de simulación lógica de código abierto y comprobación experimental de compuertas lógicas.
- **Procedimiento**: Emplazamiento de fuente de voltaje, interruptores de entrada, sondas lógicas de salida y circuitos integrados de la familia 74LS. Se verifica experimentalmente la tabla de verdad de cada compuerta y se elabora el informe técnico correspondiente.

---

## 2. Semana 2: Álgebra de Boole y Formas Canónicas

### 2.1 Tradución de Requerimientos a Especificación Lógica
El diseño clásico exige traducir enunciados en lenguaje natural sin ambigüedad hacia tablas de verdad precisas. Cada combinación de variables de entrada produce un valor de salida unívoco.

### 2.2 Postulados, Teoremas del Álgebra de Boole y Leyes de De Morgan

#### Teoremas Fundamentales
- **Identidad**: $A \cdot 1 = A$, $A + 0 = A$
- **Nulo**: $A \cdot 0 = 0$, $A + 1 = 1$
- **Idempotencia**: $A \cdot A = A$, $A + A = A$
- **Inverso / Complemento**: $A \cdot \bar{A} = 0$, $A + \bar{A} = 1$
- **Doble Inversión**: $\overline{\bar{A}} = A$
- **Conmutatividad**: $A \cdot B = B \cdot A$, $A + B = B + A$
- **Asociatividad**: $(A \cdot B) \cdot C = A \cdot (B \cdot C)$, $(A + B) + C = A + (B + C)$
- **Distributividad**: $A \cdot (B + C) = A \cdot B + A \cdot C$, $A + (B \cdot C) = (A + B) \cdot (A + C)$
- **Leyes de De Morgan**: 
  $$\overline{A \cdot B} = \bar{A} + \bar{B}$$
  $$\overline{A + B} = \bar{A} \cdot \bar{B}$$

### 2.3 Formas Canónicas: Suma de Productos (SOP) y Producto de Sumas (POS)

#### Minitérminos ($m_i$) y Maxitérminos ($M_i$)
- **Minitérmino ($m_i$)**: Producto de todas las variables en forma directa (si la variable vale 1) o complementada (si vale 0). La forma canónica SOP es la suma de los minitérminos donde la función es 1:
  $$F = \sum m(i_1, i_2, \dots)$$
- **Maxitérmino ($M_i$)**: Suma de todas las variables en forma directa (si la variable vale 0) o complementada (si vale 1). La forma canónica POS es el producto de los maxitérminos donde la función es 0:
  $$F = \prod M(j_1, j_2, \dots)$$

### 2.4 Caso de Estudio Resuelto: Sistema de Alarma de 3 Sensores
Se requiere activar una alarma ($F = 1$) cuando al menos dos de tres sensores ($A, B, C$) se activan ($1$).

#### Tabla de Verdad del Sistema de Alarma
| $A$ | $B$ | $C$ | $F$ | Minitérmino / Maxitérmino |
| :---: | :---: | :---: | :---: | :---: |
| 0 | 0 | 0 | 0 | $M_0 = A + B + C$ |
| 0 | 0 | 1 | 0 | $M_1 = A + B + \bar{C}$ |
| 0 | 1 | 0 | 0 | $M_2 = A + \bar{B} + C$ |
| 0 | 1 | 1 | 1 | $m_3 = \bar{A} \cdot B \cdot C$ |
| 1 | 0 | 0 | 0 | $M_4 = \bar{A} + B + C$ |
| 1 | 0 | 1 | 1 | $m_5 = A \cdot \bar{B} \cdot C$ |
| 1 | 1 | 0 | 1 | $m_6 = A \cdot B \cdot \bar{C}$ |
| 1 | 1 | 1 | 1 | $m_7 = A \cdot B \cdot C$ |

- **Expresión Canónica SOP**:
  $$F = \sum m(3, 5, 6, 7) = \bar{A}BC + A\bar{B}C + AB\bar{C} + ABC$$
- **Simplificación Algebraica**:
  $$F = AB(C + \bar{C}) + C(A\bar{B} + \bar{A}B) = AB + C(A \oplus B) = AB + AC + BC$$

### 2.5 Práctica Experimental APE N.º 02
- **Objetivo**: Formas canónicas y simplificación algebraica.
- **Actividad**: Montaje simulado del circuito canónico frente al simplificado. Se contrasta el número de compuertas e integrados requeridos, comprobando que ambas versiones satisfacen exactamente la misma tabla de verdad.

---

## 3. Semana 3: Optimización con Mapas de Karnaugh y Compuertas Universales

### 3.1 Mapas de Karnaugh (K-Maps) de 3 y 4 Variables
El mapa de Karnaugh es un método gráfico de representación donde las celdas adyacentes difieren en un solo bit (ordenamiento en código Gray).

#### Esquema de Mapa de Karnaugh de 4 Variables ($A, B$ en filas; $C, D$ en columnas)
| $AB \backslash CD$ | 00 | 01 | 11 | 10 |
| :---: | :---: | :---: | :---: | :---: |
| **00** | $m_0$ | $m_1$ | $m_3$ | $m_2$ |
| **01** | $m_4$ | $m_5$ | $m_7$ | $m_6$ |
| **11** | $m_{12}$ | $m_{13}$ | $m_{15}$ | $m_{14}$ |
| **10** | $m_8$ | $m_9$ | $m_{11}$ | $m_{10}$ |

#### Reglas Rigurosas de Agrupación
1. Los grupos deben contener un número de celdas potencia de 2 ($1, 2, 4, 8, 16$).
2. Las celdas agrupadas deben ser adyacentes (incluyendo bordes extremos por continuidad).
3. Cada grupo debe ser lo más grande posible para eliminar la mayor cantidad de variables.
4. Todos los 1s de la función deben estar contenidos en al menos un grupo.

### 3.2 Condiciones Indiferentes ("Don't Care" - $d$ o $X$)
Las condiciones indiferentes corresponden a combinaciones de entrada que nunca ocurren físicamente o cuyas salidas no importan. Se marcan como $X$ en el mapa y pueden ser agrupadas con los 1s cuando ayudan a formar grupos más grandes, o ignoradas cuando no aportan a la simplificación.

### 3.3 Universalidad de Compuertas NAND y NOR
Las compuertas NAND y NOR son **universales** porque cualquier función booleana puede implementarse utilizando exclusivamente una de estas dos familias.

#### Conversión de Esquemas a Compuertas NAND
1. Obtener la función lógica simplificada en Suma de Productos (SOP).
2. Aplicar doble complementación a toda la expresión: $F = \overline{\overline{\text{SOP}}}$.
3. Aplicar los Teoremas de De Morgan para convertir las operaciones de suma externa e inversores a compuertas NAND de múltiples entradas.

### 3.4 Práctica Experimental APE N.º 03
- **Objetivo**: Optimización de hardware mediante mapas de Karnaugh.
- **Desarrollo**: Simulación funcional comparativa antes y después de la minimización. Conversión del circuito resultante a la familia universal NAND, verificando la reducción en el conteo total de CI y el consumo de área.

---

## 4. Semana 4: Bloques Combinacionales Aritméticos

### 4.1 Semisumador (Half Adder) y Sumador Completo (Full Adder)

#### Semisumador (HA)
El semisumador calcula la suma de dos bits $A$ y $B$, generando el bit de suma $S$ y el acarreo de salida $C_{out}$.
- $S = A \oplus B$
- $C_{out} = A \cdot B$

#### Sumador Completo (FA)
El sumador completo incorpora un acarreo de entrada $C_{in}$, permitiendo encadenar etapas aritméticas.

| $A$ | $B$ | $C_{in}$ | $S$ | $C_{out}$ |
| :---: | :---: | :---: | :---: | :---: |
| 0 | 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 1 | 0 |
| 0 | 1 | 0 | 1 | 0 |
| 0 | 1 | 1 | 0 | 1 |
| 1 | 0 | 0 | 1 | 0 |
| 1 | 0 | 1 | 0 | 1 |
| 1 | 1 | 0 | 0 | 1 |
| 1 | 1 | 1 | 1 | 1 |

- **Ecuaciones Mínimas del Sumador Completo**:
  $$S = A \oplus B \oplus C_{in}$$
  $$C_{out} = AB + C_{in}(A \oplus B)$$

### 4.2 Sumador Paralelo de 4 Bits con Propagación de Acarreo (Ripple Carry Adder)
Para sumar dos números binarios de 4 bits $A = A_3 A_2 A_1 A_0$ y $B = B_3 B_2 B_1 B_0$, se conectan en cascada 4 celdas de sumador completo (FA), donde el $C_{out}$ de la etapa $i$ se introduce como $C_{in}$ de la etapa $i+1$.

> **Retardo de Propagación**: El tiempo crítico de estabilización del resultado depende del tiempo de propagación del acarreo a través de las 4 etapas ($t_{prop} = 4 \times t_{carry}$).

### 4.3 Resta Binaria Mediante Complemento a Dos
La operación de resta $A - B$ se realiza como una adición mediante el complemento a dos:
$$A - B = A + C_2(B) = A + \bar{B} + 1$$
En hardware, esto se implementa utilizando un sumador paralelo de 4 bits introduciendo $C_{in} = 1$ en la primera etapa y pasando las entradas de $B$ a través de compuertas XOR gobernadas por la señal de control de operación $\text{Sub}$.

### 4.4 Comparador de Magnitud
Un comparador de magnitud de dos operandos de $n$ bits $A$ y $B$ genera tres salidas binarias: $A > B$, $A = B$ y $A < B$.
- La condición de igualdad $A = B$ en 4 bits se expresa mediante XNOR bit a bit:
  $$(A = B) = (A_0 \odot B_0) \cdot (A_1 \odot B_1) \cdot (A_2 \odot B_2) \cdot (A_3 \odot B_3)$$

### 4.5 Relación con la Unidad Aritmético-Lógica (ALU)
Los bloques combinacionales de suma, resta y comparación forman el núcleo de la Unidad Aritmético-Lógica (ALU) de un procesador, conectándose directamente con los registros internos para ejecutar el camino de datos.

### 4.6 Práctica Experimental APE N.º 04
- **Objetivo**: Implementación de circuitos sumadores y verificación de resta por complemento a dos.
- **Desarrollo**: Construcción simulada de un semisumador y un sumador completo. Interconexión en un sumador paralelo de 4 bits, comprobación de adición y verificación del modo de resta sobre indicadores lógicos LED.

---

## Cuestionarios de Autoevaluación y Banco de Pruebas

### Preguntas de Autoevaluación Resueltas

1. **¿Por qué el complemento a dos simplifica la arquitectura del hardware aritmético?**
   - *Respuesta*: Porque permite reutilizar la misma red de sumadores paralelos para efectuar tanto sumas como restas, convirtiendo la resta en una adición con el operando invertido y un acarreo inicial $C_{in} = 1$.

2. **¿Cuál es la diferencia principal entre un Minitérmino y un Maxitérmino?**
   - *Respuesta*: Un minitérmino es un producto lógico que toma el valor 1 para una única combinación de variables; un maxitérmino es una suma lógica que toma el valor 0 para una única combinación de variables.

3. **¿Cómo se trata una condición indiferente ("Don't Care") en un Mapa de Karnaugh?**
   - *Respuesta*: Se evalúa como 1 o como 0 conveniente según permita formar un grupo adyacente más grande de unos para reducir el número de compuertas de la expresión final.

4. **¿Cuál es la causa del retardo de propagación en un sumador paralelo de tipo Ripple Carry?**
   - *Respuesta*: La necesidad de que el acarreo de cada etapa ($C_{out}$) se estabilice antes de que la siguiente etapa determine su resultado definitivo de suma y acarreo.

---

## Especificaciones de Licencia y Referencias

### Licencia del Repositorio
Este compendio de código y documentación se distribuirá bajo la Licencia MIT.

### Referencias Bibliográficas (Fuentes del Sílabo)
- Carpinelli, J. D. (2023). *An Animated Introduction to Digital Logic Design*. New Jersey Institute of Technology.
- Bégin, G. (2023). *Circuits logiques combinatoires et séquentiels*.
- Pedroni, V. A. (2020). *Circuit Design with VHDL*. The MIT Press.
- Sílabo de la Asignatura *Diseño de Circuitos Digitales* (2026-2027), Universidad Nacional de Loja.
