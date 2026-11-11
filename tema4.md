[← Volver al Índice Principal](./Unidad1.md)

# Tema 4 · Indiferentes y NAND/NOR

## Condiciones indiferentes (X)

- Son combinaciones que **nunca ocurren** (ej.: en BCD, 1010 a 1111), así que el circuito puede hacer lo que más convenga.
- **Como 1:** si agrandan un grupo, se incluyen (término más corto).
- **Como 0:** si no ayudan, se ignoran (ninguna X está obligada a cubrirse).
- **Nunca solas:** un grupo formado solo por X agrega un término inútil.
- Notación: `F = Σm(minitérminos) + d(indiferentes)`

**Ejemplo: dígito BCD ≥ 5** → `F = Σm(5,6,7,8,9) + d(10,11,12,13,14,15)`

| Caso | Expresión | Literales |
|---|---|---|
| Sin usar las X | `AB'C' + A'BD + A'BC` | 9 |
| Con las X | `A + BD + BC` | 5 |

## Universalidad de NAND y NOR

| Función | Solo NAND | Solo NOR |
|---|---|---|
| NOT | `(A·A)'` | `(A + A)'` |
| AND | `((AB)')'` | `(A' + B')'` |
| OR | `(A'·B')'` | `((A + B)')'` |

- Si NOT, AND y OR se construyen con NAND, **cualquier función** también (NOR es el caso dual).
- **SOP mínima → NAND-NAND** · **POS mínima → NOR-NOR**.

## De SOP a NAND-NAND

1. `F = A + BD + BC` (SOP mínima)
2. `F = ((A + BD + BC)')'` (doble negación)
3. `F = (A' · (BD)' · (BC)')'` (De Morgan sobre la negación interna)
4. `F = NAND( A', NAND(B,D), NAND(B,C) )`

- El literal que aparece solo (A) **entra complementado**: la NAND se usa como inversor.
- Son dos niveles: el retardo es igual al de AND-OR.
- Toda la red sale de chips **7400 y 7410**.

## Costo en circuitos integrados

| Opción | Chips | Total |
|---|---|---|
| Sin X | 7404 + 7411 + 7432 | 3 CI |
| Con X, AND-OR | 7408 + 7432 | 2 CI |
| Con X, solo NAND | 7400 + 7410 | 2 CI |

El ahorro vino de las **X**; la NAND no agrega chips y deja una sola familia en el inventario.

[Seguir al tema 5 →](./tema5.md)
<br>
<br>
[← Volver al Índice Principal](./Unidad1.md)

