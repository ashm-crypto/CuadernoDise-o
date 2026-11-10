[← Volver al Índice Principal](./Unidad1.md)

# Tema 4.1 · Circuitos aritméticos

## Sumar un bit

- **S** = suma (el dígito que se escribe) · **C** = carry/acarreo (el que «me llevo»).
- `1 + 1 = 10₂` → S = 0, C = 1.
- Los acarreos se **encadenan**: un acarreo puede provocar otro.

## Dos tipos de columna

- **Semisumador** (columna 0): suma 2 bits, A y B. `S = A ⊕ B` · `C = A · B`. No recibe acarreo.
- **Sumador completo** (columnas 1, 2, 3…): suma A, B y el acarreo que llega (Cin).

## Sumador completo

**Truco:** contar los unos de la fila y escribir ese número en binario (Cout S).

| A | B | Cin | # de 1 | Cout | S |
|---|---|---|---|---|---|
| 0 | 0 | 0 | 0 | 0 | 0 |
| 0 | 0 | 1 | 1 | 0 | 1 |
| 0 | 1 | 0 | 1 | 0 | 1 |
| 0 | 1 | 1 | 2 | 1 | 0 |
| 1 | 0 | 0 | 1 | 0 | 1 |
| 1 | 0 | 1 | 2 | 1 | 0 |
| 1 | 1 | 0 | 2 | 1 | 0 |
| 1 | 1 | 1 | 3 | 1 | 1 |

- `S = 1` cuando hay un número **impar** de unos → `S = A ⊕ B ⊕ Cin` (en el K-map sale «tablero de ajedrez», no hay grupos).
- `Cout = 1` cuando hay **al menos dos** unos → `Cout = AB + A·Cin + B·Cin`.

## Sumador de 4 bits (ripple carry)

- 4 sumadores completos en cadena. **Regla:** el `Cout` de un sumador va al `Cin` del siguiente.
- El acarreo avanza como una ola: cada etapa espera a la anterior, y el resultado se completa de derecha a izquierda.
- **Retardo ≈ 2 · n · 10 ns** (≈ 2 compuertas por etapa, ≈ 10 ns cada una): 4 bits → 80 ns · 16 bits → 320 ns · 32 bits → 640 ns. Más bits → más lento.

## Restar con el mismo sumador

- `A − B = A + (−B)`, y `−B` = invertir los bits de B y sumar 1.
- Se usa una **XOR como inversor controlado** con la señal M: `B ⊕ M`.
  - **M = 0:** B pasa igual → **suma**.
  - **M = 1:** B se invierte → **resta**. M también entra al `Cin` del primer sumador y aporta el +1.
- Un solo circuito suma o resta según M.

## Overflow

- Ocurre cuando el resultado no cabe: `0101 (+5) + 0100 (+4) = 1001 → −7` ✗.
- 4 bits con signo: rango de −8 a +7.
- **Se detecta con `V = C3 ⊕ C4`** (acarreo que entra a la última etapa ≠ el que sale).
- `Cout = 1` **no** significa error.

## Comparador de magnitud

- **¿A = B?** XNOR en cada bit y AND de todas.
- **¿A > B?** Se compara desde el bit más a la izquierda: el primer bit en que difieren decide.
- Circuito integrado: **7485**.

## ALU

La ALU combina sumador/restador + comparador + AND/OR/XOR + multiplexor.

## Resumen

| Concepto | Idea clave |
|---|---|
| Semisumador | S = XOR · C = AND · solo columna 0 |
| Sumador completo | S = impar de unos · Cout = al menos dos |
| Ripple | El acarreo avanza etapa por etapa |
| Resta | M = 1: XOR invierte B y Cin = 1 |
| Overflow | V = C3 ⊕ C4, no Cout |

[← Volver al Índice Principal](./Unidad1.md)
