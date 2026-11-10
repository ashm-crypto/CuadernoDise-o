[← Volver al Índice Principal](./README.md)

# Álgebra de Boole y formas canónicas

## Circuito = expresión

- Cable = variable · AND = producto `·` · OR = suma `+` · NOT = complemento `'`
- **Precedencia:** NOT → AND → OR.
- Ejemplo: `Y = A·B + C'`

## Postulados y dualidad

| Postulado | Forma OR | Forma AND (dual) |
|---|---|---|
| Identidad | X + 0 = X | X · 1 = X |
| Complemento | X + X' = 1 | X · X' = 0 |
| Conmutativa | X + Y = Y + X | XY = YX |
| Distributiva | X(Y + Z) = XY + XZ | X + YZ = (X + Y)(X + Z) |

**Dualidad:** intercambiar `+ ↔ ·` y `0 ↔ 1` mantiene válida la identidad.

## Teoremas clave

| Teorema | Forma OR | Forma AND |
|---|---|---|
| Elemento nulo | X + 1 = 1 | X · 0 = 0 |
| Idempotencia | X + X = X | X · X = X |
| Absorción | X + XY = X | X(X + Y) = X |
| Absorción del complemento | X + X'Y = X + Y | X(X' + Y) = XY |
| Adyacencia | XY + XY' = X | (X + Y)(X + Y') = X |
| Consenso | XY + X'Z + YZ = XY + X'Z | (X+Y)(X'+Z)(Y+Z) = (X+Y)(X'+Z) |

## De Morgan

- `(AB)' = A' + B'` · `(A + B)' = A'B'`
- **Rompe la barra, cambia el operador.** Se generaliza a n variables.

## Minitérminos y maxitérminos

- **Minitérmino mᵢ:** producto de todas las variables. Variable en 1 → sin complemento; en 0 → complementada. Vale 1 solo en su fila.
- **Maxitérmino Mᵢ:** suma de todas las variables. Variable en 0 → sin complemento; en 1 → complementada. Vale 0 solo en su fila.
- Relación: `Mᵢ = (mᵢ)'`.

## Formas canónicas

Ejemplo: alarma de 3 sensores, suena si **al menos dos** están activos → filas 3, 5, 6, 7.

- **SOP (mira los 1):** se toma el minitérmino de cada fila con F = 1 y se unen con OR.
  `F = Σm(3, 5, 6, 7) = A'BC + AB'C + ABC' + ABC`
- **POS (mira los 0):** se toma el maxitérmino de cada fila con F = 0 y se unen con AND.
  `F = ΠM(0, 1, 2, 4) = (A+B+C)(A+B+C')(A+B'+C)(A'+B+C)`
- Los índices de ΠM son los que faltan en Σm. La forma canónica siempre existe y es única.

**¿SOP o POS?**

- Pocos 1 → SOP · Pocos 0 → POS.
- Solo NAND → SOP (NAND-NAND, 7400) · Solo NOR → POS (NOR-NOR, 7402).
- El criterio final es el **costo**: compuertas, circuitos integrados y niveles lógicos.

## Simplificación algebraica

Procedimiento: pares adyacentes (`XY + XY' = X`) → duplicar términos si hace falta (`X = X + X`) → absorción → absorción del complemento → consenso.

- Alarma simplificada: `F = AB + AC + BC` (en POS: `(A+B)(A+C)(B+C)`).
- Costo: canónica **4 CI** (7404 + 2×7411 + 7432) vs. simplificada **2 CI** (7408 + 7432).
- Ejemplo: `A + A'B + AB'C = A + B`.
- El álgebra **no garantiza el mínimo**; por eso se usan los mapas de Karnaugh.

## Ideas para recordar

- Lo que simplificas en papel lo ahorras en hardware.
- Dos expresiones son equivalentes si y solo si tienen la misma tabla de verdad.

[← Volver al Índice Principal](./README.md)
