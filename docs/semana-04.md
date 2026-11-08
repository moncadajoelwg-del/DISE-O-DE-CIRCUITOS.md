[🏠 Volver a la Portada](../README.md) | [◀ Semana Anterior](semana-03.md)

---

# Semana 4: Bloques Combinacionales Aritméticos

## 4.1 Semisumador (Half Adder) y sumador completo (Full Adder)

### Semisumador (HA)

El semisumador calcula la suma de dos bits $A$ y $B$, generando el bit de suma $S$ y el acarreo de salida $C_{out}$.

- $S = A \oplus B$
- $C_{out} = A \cdot B$

### Sumador completo (FA)

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

- **Ecuaciones mínimas del sumador completo**:

$$S = A \oplus B \oplus C_{in}$$

$$C_{out} = AB + C_{in}(A \oplus B)$$

## 4.2 Sumador paralelo de 4 bits con propagación de acarreo (Ripple Carry Adder)

Para sumar dos números binarios de 4 bits $A = A_3 A_2 A_1 A_0$ y $B = B_3 B_2 B_1 B_0$, se conectan en cascada 4 celdas de sumador completo (FA), donde el $C_{out}$ de la etapa $i$ se introduce como $C_{in}$ de la etapa $i+1$.

> **Retardo de propagación**: el tiempo crítico de estabilización del resultado depende del tiempo de propagación del acarreo a través de las 4 etapas ($t_{prop} = 4 \times t_{carry}$).

## 4.3 Resta binaria mediante complemento a dos

La operación de resta $A - B$ se realiza como una adición mediante el complemento a dos:

$$A - B = A + C_2(B) = A + \bar{B} + 1$$

En hardware, esto se implementa utilizando un sumador paralelo de 4 bits introduciendo $C_{in} = 1$ en la primera etapa y pasando las entradas de $B$ a través de compuertas XOR gobernadas por la señal de control de operación $\text{Sub}$.

## 4.4 Comparador de magnitud

Un comparador de magnitud de dos operandos de $n$ bits $A$ y $B$ genera tres salidas binarias: $A > B$, $A = B$ y $A < B$.

- La condición de igualdad $A = B$ en 4 bits se expresa mediante XNOR bit a bit:

$$(A = B) = (A_0 \odot B_0) \cdot (A_1 \odot B_1) \cdot (A_2 \odot B_2) \cdot (A_3 \odot B_3)$$

## 4.5 Relación con la Unidad Aritmético-Lógica (ALU)

Los bloques combinacionales de suma, resta y comparación forman el núcleo de la Unidad Aritmético-Lógica (ALU) de un procesador, conectándose directamente con los registros internos para ejecutar el camino de datos.

## 4.6 Práctica experimental APE N.º 04

- **Objetivo**: implementación de circuitos sumadores y verificación de resta por complemento a dos.
- **Desarrollo**: construcción simulada de un semisumador y un sumador completo. Interconexión en un sumador paralelo de 4 bits, comprobación de adición y verificación del modo de resta sobre indicadores lógicos LED.

---

## Cuestionario de autoevaluación resuelto (Semanas 1 a 4)

1. **¿Por qué el complemento a dos simplifica la arquitectura del hardware aritmético?**
   *Respuesta*: porque permite reutilizar la misma red de sumadores paralelos para efectuar tanto sumas como restas, convirtiendo la resta en una adición con el operando invertido y un acarreo inicial $C_{in} = 1$.

2. **¿Cuál es la diferencia principal entre un minitérmino y un maxitérmino?**
   *Respuesta*: un minitérmino es un producto lógico que toma el valor 1 para una única combinación de variables; un maxitérmino es una suma lógica que toma el valor 0 para una única combinación de variables.

3. **¿Cómo se trata una condición indiferente ("Don't Care") en un mapa de Karnaugh?**
   *Respuesta*: se evalúa como 1 o como 0, según convenga para formar un grupo adyacente más grande de unos y reducir el número de compuertas de la expresión final.

4. **¿Cuál es la causa del retardo de propagación en un sumador paralelo de tipo Ripple Carry?**
   *Respuesta*: la necesidad de que el acarreo de cada etapa ($C_{out}$) se estabilice antes de que la siguiente etapa determine su resultado definitivo de suma y acarreo.

---

[🏠 Volver a la Portada](../README.md) | [◀ Semana Anterior](semana-03.md)
