[← Volver al Índice Principal](./README.md)

# Sistemas numéricos, códigos y compuertas lógicas

## Representación binaria

- El computador usa 0 y 1 porque un transistor es un interruptor controlado por voltaje: con dos estados es fácil distinguirlos aunque haya ruido.
- Un «1» es un rango de voltaje, no un valor exacto. Entre 0,8 V y 2,0 V (familia 74LS) está la zona indefinida; una entrada sin conectar suele caer ahí.
- Margen de ruido: margen alto = 0,7 V · margen bajo = 0,3 V.

## Sistemas numéricos

- **Posicional:** cada posición vale una potencia de la base.
- **Bit** = dígito binario.
- **Byte** = 8 bits.
- Potencias de 2: `128 · 64 · 32 · 16 · 8 · 4 · 2 · 1`
- **Decimal → binario:** dividir entre 2 y leer los restos de abajo hacia arriba. `25 = 11001₂`
- **Hexadecimal:** grupos de 4 bits desde la derecha. `10011101₂ = 9D₁₆` (A=10 … F=15)
- **Octal:** grupos de 3 bits desde la derecha. `10011101₂ = 235₈`

## Suma binaria

`0+0=0 · 0+1=1 · 1+1=10 (escribo 0, llevo 1) · 1+1+1=11`

## Complemento a dos (números con signo)

- Bit izquierdo 0 = positivo, 1 = negativo.
- **Obtener el negativo:** invertir los bits y sumar 1. `3 = 0011 → 1100 → 1101 = −3`
- **Rango:** 4 bits: −8 a +7 · 8 bits: −128 a +127.
- **Restar** = sumar el negativo: `5 − 3 = 0101 + 1101 = 1 0010 → 0010 = 2` (el bit que sobra se descarta). No hace falta un circuito restador.
- **Desbordamiento:** el resultado no cabe en los bits. `0111 + 0001 = 1000 → −8` (dos positivos dan un negativo).

## Códigos

| Código | Idea clave | Uso |
|---|---|---|
| **BCD** | Cada dígito decimal en 4 bits (157 → `0001 0101 0111`). 1010 a 1111 no se usan | Displays, relojes, contadores |
| **Gray** | Entre vecinos cambia un solo bit (método del espejo) | Encoders, sensores, mapas de Karnaugh |
| **ASCII** | Tabla de caracteres a números, 7 bits = 128 caracteres. `A = 65` | Texto (ñ y tildes: UTF-8) |

## Compuertas lógicas

| Compuerta | Expresión | Sale 1 cuando… |
|---|---|---|
| NOT | `A'` | la entrada es 0 |
| AND | `A·B` | **todas** valen 1 |
| OR | `A+B` | **al menos una** vale 1 |
| NAND | `(A·B)'` | **no** todas valen 1 |
| NOR | `(A+B)'` | **ninguna** vale 1 |
| XOR | `A⊕B` | las entradas son **distintas** |
| XNOR | `(A⊕B)'` | las entradas son **iguales** |

- El círculo en la salida significa «negado».
- Con solo NAND (o solo NOR) se puede construir cualquier circuito.
- Norma de dibujo usada en el curso: **ANSI**.

## Circuitos integrados (74LS08)

- Chip con **4 compuertas AND** de 2 entradas, encapsulado **DIP-14**.
- Pines: **14 = +5 V** y **7 = GND**. Pin 1 arriba a la izquierda (muesca arriba), se cuenta en sentido antihorario.
- Código `SN 74 LS 08 N`: fabricante · rango comercial · familia (LS = TTL, HC = CMOS) · función · encapsulado.
- El 74HC08 es la versión CMOS: misma función y pines.

[← Volver al Índice Principal](./README.md)
