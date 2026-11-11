[🏠 Volver a la Portada](../README.md) | [Siguiente Semana ▶](semana-02.md)

---

# Semana 1: Sistemas Numéricos, Códigos y Compuertas Lógicas Fundamentales

## 1.1 Representación de la información en hardware digital

En los sistemas de computación presenciales y de arquitectura moderna, la información se representa físicamente mediante dos estados eléctricos diferenciados (lógica positiva: nivel alto $V_{DD} / 5\text{V}$ como '1' y nivel bajo $GND / 0\text{V}$ como '0'). La necesidad de fundamentar la construcción de hardware parte de comprender que todo programa ejecutable se traduce en última instancia a señales eléctricas manipuladas por redes combinacionales.

<img width="641" height="456" alt="image" src="https://github.com/user-attachments/assets/5c1a418b-9a84-41f1-873a-4a0bb35d90a2" />


## 1.2 Sistemas numéricos y conversión de bases

Los sistemas de numeración posicionales binario (base 2), octal (base 8) y hexadecimal (base 16) constituyen el lenguaje formal de representación de datos en hardware.

### Procedimientos de conversión entre bases

1. **Decimal a Binario / Octal / Hexadecimal**: división sucesiva por la base destino guardando los residuos.
2. **Binario a Hexadecimal / Octal**: agrupación de bits de derecha a izquierda en bloques de 4 bits (hexadecimal) o 3 bits (octal).

| Sistema | Base | Símbolos utilizados | Ejemplo de representación |
| :--- | :--- | :--- | :--- |
| Binario | 2 | 0, 1 | $(1101.01)_2$ |
| Octal | 8 | 0, 1, 2, 3, 4, 5, 6, 7 | $(15.2)_8$ |
| Decimal | 10 | 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 | $(13.25)_{10}$ |
| Hexadecimal | 16 | 0-9, A, B, C, D, E, F | $(D.4)_{16}$ |

<img src="https://github.com/user-attachments/assets/9935529b-ecde-4444-90c9-654c4d357ba0" width="600" alt="Descripción">

## 1.3 Aritmética binaria, complemento a dos y códigos

### Representación en complemento a dos ($C_2$)

Para representar números enteros con signo en un ancho de palabra de $n$ bits:

- El bit más significativo (MSB) actúa como bit de signo ($0$ para positivo, $1$ para negativo).
- El valor negativo de un número $A$ se calcula mediante $C_2(A) = \bar{A} + 1$, donde $\bar{A}$ representa el complemento a uno (inversión bit a bit).

### Códigos digitales

- **BCD (Binary Coded Decimal)**: codificación directa de cada dígito decimal mediante 4 bits binarios (de 0000 a 1001).
- **Código Gray**: código no ponderado donde dos números consecutivos difieren en un único bit, minimizando errores de transición en sensores y codificadores.
- **ASCII**: código de 7 u 8 bits para representación de caracteres alfanuméricos y de control.

<img src="https://github.com/user-attachments/assets/1fe25fd3-6590-4cd6-a2de-a5ee8db3b778" width="600" alt="Descripción">

## 1.4 Compuertas lógicas y hojas de datos (familia 74LS)

Las compuertas lógicas son los bloques constitutivos fundamentales. A continuación se presenta la tabla de verdad unificada para las compuertas de dos entradas:

| Entrada $A$ | Entrada $B$ | AND ($A \cdot B$) | OR ($A + B$) | NAND ($\overline{A \cdot B}$) | NOR ($\overline{A + B}$) | XOR ($A \oplus B$) | XNOR ($A \odot B$) |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| 0 | 0 | 0 | 0 | 1 | 1 | 0 | 1 |
| 0 | 1 | 0 | 1 | 1 | 0 | 1 | 0 |
| 1 | 0 | 0 | 1 | 1 | 0 | 1 | 0 |
| 1 | 1 | 1 | 1 | 0 | 0 | 0 | 1 |

> **Nota de lectura de hojas de datos (74LS)**: en circuitos integrados de la familia TTL 74LS (por ejemplo, 74LS08 para AND, 74LS02 para NOR, 74LS00 para NAND, 74LS86 para XOR), el pin de alimentación $V_{CC}$ corresponde típicamente al pin 14 y la masa $GND$ al pin 7.

<img src="https://github.com/user-attachments/assets/618123dd-c84d-435d-baed-ebf31d2dcc3b" width="600" alt="Descripción">

---

[🏠 Volver a la Portada](../README.md) | [Siguiente Semana ▶](semana-02.md)
