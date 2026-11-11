<div align="center">

# UNIDAD 1
### Análisis de lógica combinacional con diseño clásico
</div>

---

## 📌 CONTENIDOS

## Semana 1: Sistemas numéricos, códigos y compuertas lógicas

### 1. Sistemas numéricos
Un sistema numérico es un conjunto de símbolos y reglas que se utilizan para representar cantidades. En los sistemas digitales y computación, las bases principales son:

*   **Decimal (Base 10):** El sistema cotidiano (dígitos del `0` al `9`).
*   **Binario (Base 2):** Lenguaje base de los circuitos digitales, compuesto por dos estados: `0` (apagado/falso) y `1` (encendido/verdadero).
*   **Octal (Base 8):** Utiliza dígitos del `0` al `7`. Agrupa los bits binarios de 3 en 3.
*   **Hexadecimal (Base 16):** Utiliza 16 símbolos (`0-9` y letras `A-F` para los valores del 10 al 15). Agrupa bits de 4 en 4.

> **💡 Ejemplo de equivalencia:**
> El número decimal **`13`** se representa en las diferentes bases de la siguiente manera:
> *   **Binario:** `1101₂` ($1\cdot 8 + 1\cdot 4 + 0\cdot 2 + 1\cdot 1 = 13$)
> *   **Octal:** `15₈` ($1\cdot 8 + 5 = 13$)
> *   **Hexadecimal:** `D₁₆` ($13 = \text{D}$)

---

### 2. Códigos
Combinaciones de bits diseñadas para representar información no numérica o facilitar operaciones y detección de errores.

*   **BCD (Decimal Codificado en Binario):** Representa cada dígito decimal individualmente usando exactamente 4 bits.
*   **ASCII:** Asigna un código binario estándar a cada carácter del teclado (letras, números, símbolos).
*   **Código Gray:** Código binario donde dos valores sucesivos difieren en **un solo bit**, evitando errores mecánicos o en sensores.

> **💡 Ejemplo (BCD vs. Binario Puro):**
> Para representar el número decimal **`45`**:
> *   **Binario Puro:** `101101₂`
> *   **BCD:** Se codifica cada dígito por separado con 4 bits $\rightarrow$ `0100` (4) y `0101` (5) $\rightarrow$ `01000101_{BCD}`.

---

### 3. Compuertas lógicas
Circuitos electrónicos elementales basados en transistores que realizan operaciones booleanas (`AND`, `OR`, `NOT`, `NAND`, `NOR`, `XOR`, `XNOR`).

> **💡 Ejemplo práctico:**
> *   **Compuerta AND:** Su salida es `1` **únicamente si todas** sus entradas son `1`. (Ej: $A = 1, B = 1 \rightarrow \text{Salida} = 1$).
> *   **Compuerta OR:** Su salida es `1` si **al menos una** de sus entradas es `1`. (Ej: $A = 0, B = 1 \rightarrow \text{Salida} = 1$).

---
<img width="1024" height="559" alt="image" src="https://github.com/user-attachments/assets/782ae211-5ba7-46a0-980a-5e4c1d29ace4" />


## Semana 2: Álgebra de Boole y formas canónicas

### 1. Formas Canónicas (SOP y POS)
Una función lógica se puede expresar de forma única mediante tablas de verdad:

*   **SOP (Suma de Productos / Minitérminos):** Suma (`OR`) de términos productos (`AND`) donde cada término incluye todas las variables (directas o negadas) para las filas donde la salida es **`1`**.
*   **POS (Producto de Sumas / Maxitérminos):** Producto (`AND`) de términos sumas (`OR`) evaluados en las filas donde la salida es **`0`**.

> **💡 Ejemplo rápido (SOP):**
> Dada una tabla de verdad para $F(A,B)$ donde la salida es `1` en las combinaciones $(A=0, B=1)$ y $(A=1, B=1)$:
> *   Para $0, 1 \rightarrow \bar{A}B$
> *   Para $1, 1 \rightarrow AB$
> *   **Forma SOP:** $F = \bar{A}B + AB$

---

### 2. Simplificación Algebraica
Consiste en aplicar leyes booleanas (absorción, idempotencia, De Morgan, etc.) para reducir expresiones complejas y optimizar los recursos de hardware en compuertas.

> **💡 Ejemplo de simplificación:**
> *   Expresión original: $F = A + AB$
> *   Aplicando Ley de Absorción ($A + AB = A$):
> *   **Expresión simplificada:** $F = A$ *(¡Pasamos de usar compuertas OR y AND a una simple conexión directa!)*

---
<img width="1024" height="559" alt="image" src="https://github.com/user-attachments/assets/78ffce75-b14e-439e-87e1-9e75b391f795" />


## Semana 3: Mapas de Karnaugh - Indiferentes y NAND/NOR

### 1. Mapas de Karnaugh (K-Maps)
Método gráfico para simplificar expresiones booleanas de forma intuitiva basado en el principio de adyacencia lógica (código Gray), agrupando celdas contiguas en potencias de 2 ($1, 2, 4, 8$).

> **💡 Ejemplo de agrupación:**
> Si en un K-map de 4 variables agrupamos un bloque de 4 celdas con `1`s, eliminamos automáticamente **dos variables** de la expresión final. Si agrupamos 8 celdas, eliminamos tres variables, dejando un término mucho más simple.

---

### 2. Condiciones Indiferentes (*Don't Care - X*)
Combinaciones de entrada que nunca ocurren o cuyos resultados no afectan al sistema. Se aprovechan estratégicamente en los K-Maps como `1` o `0` para lograr agrupaciones más grandes y expresiones más simples.

> **💡 Ejemplo de uso:**
> Si un circuito solo procesa números BCD (del `0` al `9`), las combinaciones binarias del `10` al `15` (`A` hasta `F`) nunca ocurrirán. En el mapa de Karnaugh, estas celdas se llenan con una `X`. Si necesitamos una `X` para formar un grupo de 4 con tres `1`s reales, la tratamos como `1`; de lo contrario, la tratamos como `0`.

---

### 3. Conversión a Lógica Universal (Compuertas NAND)
Cualquier circuito lógico puede construirse exclusivamente con compuertas **NAND** aplicando doble negación y leyes de De Morgan, transformando redes de dos niveles en una estructura universal homogénea.

> **💡 Ejemplo de conversión:**
> Si tenemos la expresión SOP: $F = A \cdot B + C \cdot D$
> Aplicamos doble negación $\overline{\overline{A \cdot B + C \cdot D}}$ y luego la ley de De Morgan para obtener un circuito compuesto exclusivamente por compuertas NAND en cascada.

---
<img width="1024" height="559" alt="image" src="https://github.com/user-attachments/assets/a94f9252-db22-45ac-8517-8970307e5571" />


## Semana 4: Circuitos aritméticos y comparadores

### 1. Semisumador (*Half Adder*)
Suma dos bits de entrada ($A$ y $B$). 
*   **Suma ($S$):** $A \oplus B$ (Compuerta XOR)
*   **Acarreo ($C_{out}$):** $A \cdot B$ (Compuertaアンド)

> **💡 Ejemplo numérico:**
> Si entran $A = 1$ y $B = 1$:
> *   $\text{Suma } (S) = 1 \oplus 1 = 0$
> *   $\text{Acarreo } (C_{out}) = 1 \cdot 1 = 1$
> *   Resultado binario: `10` (que en decimal es $2$).

---

### 2. Sumador Completo (*Full Adder*)
Suma tres bits: $A$, $B$ y un acarreo de entrada previo ($C_{in}$), generando una salida de Suma y un $C_{out}$ para encadenamiento en serie.

> **💡 Ejemplo numérico:**
> Si sumamos $A = 1$, $B = 1$ y un acarreo de entrada $C_{in} = 1$:
> *   Suma total de unos = $3$ (en binario `11`).
> *   Salida de Suma ($S$) = `1`.
> *   Salida de Acarreo ($C_{out}$) = `1`.

---

### 3. Sumador Paralelo de 4 Bits (*Ripple Carry Adder*)
Interconexión en cascada de cuatro sumadores completos para sumar palabras binarias de 4 bits ($A_3A_2A_1A_0 + B_3B_2B_1B_0$).

> **💡 Ejemplo de operación:**
> Sumar $5$ (`0101`) y $3$ (`0011`):
> *   `0101` + `0011` $\rightarrow$ Resultado: `1000` (que equivale a decimal `8`), propagando los acarreos de bit en bit de derecha a izquierda.

---

### 4. Resta Binaria y Complemento a Dos
La resta $A - B$ se implementa reutilizando el circuito sumador mediante la operación equivalente: 
$$A + (\bar{B} + 1)$$
Donde se invierten los bits de $B$ y se fuerza un acarreo inicial $C_0 = 1$.

> **💡 Ejemplo rápido:**
> Restar $5 - 3$ ($0101 - 0011$):
> 1. Se toma el sustraendo $B = 0011$ y se complementa (se invierte): $\bar{B} = 1100$.
> 2. Se le suma $1$: $1100 + 1 = 1101$ (este es el complemento a dos de $3$, es decir, $-3$).
> 3. Se suma $A$ con el complemento: $0101 + 1101 = (1) 0010$ (descartando el acarreo final, queda `0010`, que es $2$).

---

### 5. Detección de Desbordamiento (*Overflow*)
Ocurre cuando el resultado en aritmética con signo excede el rango representable. Se detecta evaluando el acarreo que entra y el que sale del bit de signo mediante una compuerta XOR:
$$\text{Overflow} = C_{in\_MSB} \oplus C_{out\_MSB}$$

> **💡 Ejemplo práctico:**
> En un sistema de 4 bits con signo, el rango máximo es de $-8$ hasta $+7$. Si intentamos sumar $5 + 4$, el resultado numérico sería $+9$, lo cual excede el límite y activa la bandera de **Overflow** indicando un error de rango.

---

### 6. Comparador de Magnitud
Circuito combinacional que evalúa dos palabras binarias ($A$ y $B$) generando tres salidas lógicas independientes: **$A > B$**, **$A = B$** y **$A < B$**.

> **💡 Ejemplo práctico:**
> Al comparar $A = 1010_2$ ($10$) y $B = 1100_2$ ($12$):
> *   Salida $A > B \rightarrow 0$ (Falso)
> *   Salida $A = B \rightarrow 0$ (Falso)
> *   Salida $A < B \rightarrow 1$ (Verdadero, ya que $10 < 12$)

<img width="1024" height="559" alt="image" src="https://github.com/user-attachments/assets/c60621ef-5e30-466b-8c42-8b9186c92624" />

