<div align="center">
  
# UNIDAD 1
# Análisis de lógica combinacional con diseño clásico
</div>
  
# CONTENIDOS:
  
## Semana 1: Sistemas numéricos, códigos y compuertas lógicas
### Sistemas numéricos
Un sistema numérico es un conjunto de símbolos y reglas que se utilizan para representar cantidades. En los sistemas digitales y computación, se trabaja principalmente con cuatro bases numéricas:

- Decimal (Base 10): El sistema que usamos cotidianamente (dígitos del 0 al 9).

- Binario (Base 2): El lenguaje fundamental de las computadoras, compuesto únicamente por dos estados o dígitos: 0 y 1 (apagado y encendido).

- Octal (Base 8): Utiliza dígitos del 0 al 7; agrupa bits de tres en tres para simplificar la lectura de código binario.

- Hexadecimal (Base 16): Utiliza 16 símbolos (del 0 al 9 y las letras de la A a la F para los valores del 10 al 15); agrupa bits de cuatro en cuatro y es muy usado en programación de sistemas y arquitectura de computadoras.

### Códigos
Los códigos son combinaciones de bits (ceros y unos) diseñadas para representar información no numérica (como letras, símbolos) o para facilitar operaciones matemáticas y la detección/corrección de errores en la transmisión de datos. Los más comunes son:

- Código BCD (Decimal Codificado en Binario): Representa cada dígito decimal del 0 al 9 utilizando exactamente 4 bits.

- Código ASCII: Asigna un número binario único a cada carácter del teclado (letras mayúsculas, minúsculas, números, signos de puntuación).

- Código Gray: Un código binario donde dos valores sucesivos difieren en un solo bit, lo que evita errores en sistemas mecánicos o de lectura rápida (como sensores).

### Compuertas lógicas
Son circuitos electrónicos elementales construidos con transistores que realizan operaciones lógicas booleanas (AND, OR, NOT, NAND, NOR, XOR, XNOR). Toman una o más entradas binarias (0 o 1) y producen una única salida basada en una regla lógica. Son los bloques fundamentales de construcción de cualquier procesador o circuito digital.

## Semana 2: Álgebra de Boole y formas canónicas
### 1. Formas Canónicas (SOP y POS)
Una función lógica se puede expresar de forma única utilizando minitérminos o maxitérminos a partir de su tabla de verdad:

**SOP (Suma de Productos - Minitérminos):** Es una suma (OR lógico) de términos producto (AND lógico) donde cada término incluye todas las variables de entrada en su forma directa o negada para las filas donde la salida es 1.

**POS (Producto de Sumas - Maxitérminos):** Es un producto (AND lógico) de términos suma (OR lógico) donde se evalúan las filas donde la salida es 0.

### 2. Simplificación Algebraica mediante Álgebra de Boole

Consiste en aplicar los postulados, teoremas y leyes del álgebra de Boole (como la ley de absorción, idempotencia y adyacencia) para reducir una expresión canónica compleja a su mínima expresión en compuertas, disminuyendo el número de variables y literales sin alterar la tabla de verdad del circuito.

## Semana 3: Mapas de Karnaugh - Indiferentes y NAND/NOR
### 1. Mapas de Karnaugh (K-Maps)
Un Mapa de Karnaugh es un método gráfico de reorganización de tablas de verdad en una cuadrícula bidimensional, utilizada para simplificar expresiones booleanas de forma intuitiva sin necesidad de desarrollar complejas demostraciones algebraicas. Se basa en el principio de adyacencia lógica (código Gray), donde las celdas contiguas solo difieren en un bit. Esto permite identificar y agrupar visualmente términos adyacentes en bloques de potencias de $2$ ($1, 2, 4, 8, 16$) para eliminar las variables que cambian de estado.
### 2. Condiciones Indiferentes (Don't Care)
Las condiciones indiferentes (representadas por una $X$ o la letra $d$) son combinaciones específicas de las variables de entrada que nunca ocurrirán en el funcionamiento real del sistema, o cuyas salidas no producen ningún impacto en la operación deseada. En la etapa de simplificación con Mapas de Karnaugh, el diseñador tiene la libertad de asumir el valor de cada $X$ estratégicamente como un $1$ (para formar grupos más grandes y obtener términos más sencillos) o como un $0$ (si no ayuda a agrandar ningún grupo).
### 3. Conversión a Lógica Universal (Sólo Compuertas NAND)
Las compuertas NAND (y NOR) se clasifican como compuertas universales porque cualquier circuito o función lógica (formada por AND, OR y NOT) puede implementarse exclusivamente con este tipo de compuerta. La conversión desde una expresión simplificada en Suma de Productos (SOP) se logra aplicando el teorema de doble negación y las leyes de De Morgan, lo que transforma un circuito de dos niveles AND-OR en una red estructuralmente idéntica compuesta únicamente por compuertas NAND.
## Semana 4: Circuitos aritméticos: semisumador, sumador completo, sumador de 4 bits, resta, overflow y comparador
### 1. Semisumador (Half Adder)
Es el circuito aritmético combinacional más elemental. Recibe dos bits de entrada ($A$ y $B$) y realiza la suma binaria básica, generando dos salidas: la Suma ($S$), calculada mediante una compuerta XOR ($S = A \oplus B$), y el Acarreo de salida ($C_{out}$), calculado mediante una compuerta AND ($C_{out} = A \cdot B$). Su limitación principal es que no posee una entrada para procesar acarreos provenientes de una posición o columna anterior.
### 2. Sumador Completo (Full Adder)
Es un circuito aritmético capaz de procesar tres entradas de un solo bit: los dos operandos ($A$ y $B$) y el Acarreo de entrada ($C_{in}$) generado por la etapa previa. Posee dos salidas ($S$ y $C_{out}$). Se construye internamente conectando dos semisumadores y una compuerta OR para el acarreo final, permitiendo la encadenación en serie de múltiples etapas para sumar números binarios de cualquier longitud.
### 3. Sumador Paralelo de 4 Bits (Ripple Carry Adder)
Es una red combinacional formada por la cascada o interconexión en serie de cuatro bloques sumadores completos. Permite sumar dos palabras binarias de 4 bits cada una ($A_3A_2A_1A_0$ y $B_3B_2B_1B_0$) más un acarreo inicial $C_0$. El acarreo de salida de cada bit ($C_{out}$) se propaga secuencialmente hacia la entrada de acarreo ($C_{in}$) del bit de la siguiente posición hacia la izquierda.
### 4. Circuitos de Resta Binaria y Complemento a Dos
En lugar de diseñar un circuito restador independiente, la resta binaria $A - B$ se ejecuta reutilizando el mismo circuito sumador mediante la operación equivalente en Complemento a Dos: $A + (\bar{B} + 1)$. Para lograr esto, las líneas de entrada de $B$ se pasan a través de inversores (o compuertas XOR bajo una señal de control) y se suma un $1$ forzando el acarreo inicial $C_0 = 1$.
### 5. Detección de Desbordamiento (Overflow)
El desbordamiento u overflow ocurre en aritmética binaria con signo (complemento a dos) cuando el resultado de una operación excede el rango numérico representable con el número de bits disponibles ($N$ bits, rango de $-2^{N-1}$ a $+2^{N-1}-1$). Se detecta mediante una compuerta XOR evaluando el acarreo que entra al bit del signo ($C_{in\_MSB}$) y el acarreo que sale de él ($C_{out\_MSB}$): $\text{Overflow} = C_{n-1} \oplus C_n$.
### 6. Comparador de Magnitud
Es un circuito combinacional especializado que toma dos palabras binarias ($A$ y $B$) y determina su relación cuantitativa de magnitud, generando tres salidas independientes indicadoras: $A > B$, $A = B$ y $A < B$. La igualdad ($A = B$) utiliza compuertas XNOR para verificar que cada par de bits sea idéntico, mientras que las desigualdades evalúan jerárquicamente desde el bit más significativo ($MSB$) hacia el menos significativo ($LSB$).
