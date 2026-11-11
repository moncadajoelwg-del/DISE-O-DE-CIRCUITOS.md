[🏠 Volver a la Portada](../README.md) | [◀ Semana Anterior](semana-01.md) | [Siguiente Semana ▶](semana-03.md)

---

# Semana 2: Álgebra de Boole y Formas Canónicas

## 2.1 Traducción de requerimientos a especificación lógica

El diseño clásico exige traducir enunciados en lenguaje natural sin ambigüedad hacia tablas de verdad precisas. Cada combinación de variables de entrada produce un valor de salida unívoco.

<img src="https://github.com/user-attachments/assets/7c1561d0-93b3-41f3-ab02-e9ce47312c4a" width="600" alt="Descripción del circuito">

## 2.2 Postulados, teoremas del álgebra de Boole y leyes de De Morgan

### Teoremas fundamentales

- **Identidad**: $A \cdot 1 = A$, $A + 0 = A$
- **Nulo**: $A \cdot 0 = 0$, $A + 1 = 1$
- **Idempotencia**: $A \cdot A = A$, $A + A = A$
- **Inverso / Complemento**: $A \cdot \bar{A} = 0$, $A + \bar{A} = 1$
- **Doble inversión**: $\overline{\bar{A}} = A$
- **Conmutatividad**: $A \cdot B = B \cdot A$, $A + B = B + A$
- **Asociatividad**: $(A \cdot B) \cdot C = A \cdot (B \cdot C)$, $(A + B) + C = A + (B + C)$
- **Distributividad**: $A \cdot (B + C) = A \cdot B + A \cdot C$, $A + (B \cdot C) = (A + B) \cdot (A + C)$
- **Leyes de De Morgan**:

$$\overline{A \cdot B} = \bar{A} + \bar{B}$$

$$\overline{A + B} = \bar{A} \cdot \bar{B}$$

<img src="https://github.com/user-attachments/assets/b491ea01-e670-46a5-9f7e-3a1ae6f0f11c" width="600" alt="Descripción del circuito">

## 2.3 Formas canónicas: suma de productos (SOP) y producto de sumas (POS)

### Minitérminos ($m_i$) y maxitérminos ($M_i$)

- **Minitérmino ($m_i$)**: producto de todas las variables en forma directa (si la variable vale 1) o complementada (si vale 0). La forma canónica SOP es la suma de los minitérminos donde la función es 1:

$$F = \sum m(i_1, i_2, \dots)$$

- **Maxitérmino ($M_i$)**: suma de todas las variables en forma directa (si la variable vale 0) o complementada (si vale 1). La forma canónica POS es el producto de los maxitérminos donde la función es 0:

$$F = \prod M(j_1, j_2, \dots)$$

<img src="https://github.com/user-attachments/assets/511863b0-3106-453d-a6b6-e392190654dd" width="600" alt="Descripción del circuito">

## 2.4 Caso de estudio resuelto: sistema de alarma de 3 sensores

Se requiere activar una alarma ($F = 1$) cuando al menos dos de tres sensores ($A, B, C$) se activan ($1$).

### Tabla de verdad del sistema de alarma

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

- **Expresión canónica SOP**:

$$F = \sum m(3, 5, 6, 7) = \bar{A}BC + A\bar{B}C + AB\bar{C} + ABC$$

- **Simplificación algebraica**:

$$F = AB(C + \bar{C}) + C(A\bar{B} + \bar{A}B) = AB + C(A \oplus B) = AB + AC + BC$$

<img src="https://github.com/user-attachments/assets/80083505-3088-4d2c-a84f-a176e9074127" width="600" alt="Descripción del circuito">

---

[🏠 Volver a la Portada](../README.md) | [◀ Semana Anterior](semana-01.md) | [Siguiente Semana ▶](semana-03.md)
