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

<img src="https://github.com/user-attachments/assets/c2e69c08-0d28-4ac2-8e12-741d41f32b3d" width="600" alt="Diagrama de sumador">

## 4.2 Sumador paralelo de 4 bits con propagación de acarreo (Ripple Carry Adder)

Para sumar dos números binarios de 4 bits $A = A_3 A_2 A_1 A_0$ y $B = B_3 B_2 B_1 B_0$, se conectan en cascada 4 celdas de sumador completo (FA), donde el $C_{out}$ de la etapa $i$ se introduce como $C_{in}$ de la etapa $i+1$.

> **Retardo de propagación**: el tiempo crítico de estabilización del resultado depende del tiempo de propagación del acarreo a través de las 4 etapas ($t_{prop} = 4 \times t_{carry}$).

<img src="https://github.com/user-attachments/assets/acbbe020-8731-473e-afc1-913a9684e184" width="600" alt="Diagrama de sumador">

## 4.3 Resta binaria mediante complemento a dos

La operación de resta $A - B$ se realiza como una adición mediante el complemento a dos:

$$A - B = A + C_2(B) = A + \bar{B} + 1$$

En hardware, esto se implementa utilizando un sumador paralelo de 4 bits introduciendo $C_{in} = 1$ en la primera etapa y pasando las entradas de $B$ a través de compuertas XOR gobernadas por la señal de control de operación $\text{Sub}$.

<img src="https://github.com/user-attachments/assets/422d380e-c9aa-47bf-8192-d27d1f9b40a2" width="600" alt="Diagrama de sumador">

## 4.4 Comparador de magnitud

Un comparador de magnitud de dos operandos de $n$ bits $A$ y $B$ genera tres salidas binarias: $A > B$, $A = B$ y $A < B$.

- La condición de igualdad $A = B$ en 4 bits se expresa mediante XNOR bit a bit:

$$(A = B) = (A_0 \odot B_0) \cdot (A_1 \odot B_1) \cdot (A_2 \odot B_2) \cdot (A_3 \odot B_3)$$

<img src="https://github.com/user-attachments/assets/175257bc-68f9-4f04-a22a-c1c284e2e16d" width="600" alt="Diagrama de sumador">

## 4.5 Relación con la Unidad Aritmético-Lógica (ALU)

Los bloques combinacionales de suma, resta y comparación forman el núcleo de la Unidad Aritmético-Lógica (ALU) de un procesador, conectándose directamente con los registros internos para ejecutar el camino de datos.

<img src="https://github.com/user-attachments/assets/e0c1c5f4-1fc9-4ca3-9337-4f1a1ae41787" width="600" alt="Diagrama de sumador">

---

[🏠 Volver a la Portada](../README.md) | [◀ Semana Anterior](semana-03.md)
