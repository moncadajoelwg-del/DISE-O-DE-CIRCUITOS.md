[🏠 Volver a la Portada](../README.md) | [◀ Semana Anterior](semana-02.md) | [Siguiente Semana ▶](semana-04.md)

---

# Semana 3: Optimización con Mapas de Karnaugh y Compuertas Universales

## 3.1 Mapas de Karnaugh (K-Maps) de 3 y 4 variables

El mapa de Karnaugh es un método gráfico de representación donde las celdas adyacentes difieren en un solo bit (ordenamiento en código Gray).

### Esquema de mapa de Karnaugh de 4 variables ($A, B$ en filas; $C, D$ en columnas)

| $AB \backslash CD$ | 00 | 01 | 11 | 10 |
| :---: | :---: | :---: | :---: | :---: |
| **00** | $m_0$ | $m_1$ | $m_3$ | $m_2$ |
| **01** | $m_4$ | $m_5$ | $m_7$ | $m_6$ |
| **11** | $m_{12}$ | $m_{13}$ | $m_{15}$ | $m_{14}$ |
| **10** | $m_8$ | $m_9$ | $m_{11}$ | $m_{10}$ |

### Reglas rigurosas de agrupación

1. Los grupos deben contener un número de celdas potencia de 2 ($1, 2, 4, 8, 16$).
2. Las celdas agrupadas deben ser adyacentes (incluyendo bordes extremos por continuidad).
3. Cada grupo debe ser lo más grande posible para eliminar la mayor cantidad de variables.
4. Todos los 1s de la función deben estar contenidos en al menos un grupo.

## 3.2 Condiciones indiferentes ("Don't Care": $d$ o $X$)

Las condiciones indiferentes corresponden a combinaciones de entrada que nunca ocurren físicamente o cuyas salidas no importan. Se marcan como $X$ en el mapa y pueden ser agrupadas con los 1s cuando ayudan a formar grupos más grandes, o ignoradas cuando no aportan a la simplificación.

## 3.3 Universalidad de compuertas NAND y NOR

Las compuertas NAND y NOR son **universales** porque cualquier función booleana puede implementarse utilizando exclusivamente una de estas dos familias.

### Conversión de esquemas a compuertas NAND

1. Obtener la función lógica simplificada en Suma de Productos (SOP).
2. Aplicar doble complementación a toda la expresión: $F = \overline{\overline{\text{SOP}}}$.
3. Aplicar los teoremas de De Morgan para convertir las operaciones de suma externa e inversores a compuertas NAND de múltiples entradas.

## 3.4 Práctica experimental APE N.º 03

- **Objetivo**: optimización de hardware mediante mapas de Karnaugh.
- **Desarrollo**: simulación funcional comparativa antes y después de la minimización. Conversión del circuito resultante a la familia universal NAND, verificando la reducción en el conteo total de CI y el consumo de área.

---

[🏠 Volver a la Portada](../README.md) | [◀ Semana Anterior](semana-02.md) | [Siguiente Semana ▶](semana-04.md)
