[← Volver al Índice Principal](./README.md)

# Tema 3 · Mapas de Karnaugh

## Idea clave: teorema de adyacencia

`X·Y + X·Y' = X`: si dos minitérminos difieren en **una sola variable**, esa variable desaparece.

## Por qué el orden 00, 01, 11, 10

Es **código Gray**: entre celdas vecinas cambia un solo bit (y la última es vecina de la primera), así las adyacencias se ven en el mapa.

## Mapas

```
3 variables               4 variables
A \ BC | 00 01 11 10      AB \ CD | 00 01 11 10
  0    |  0  1  3  2        00    |  0  1  3  2
  1    |  4  5  7  6        01    |  4  5  7  6
                            11    | 12 13 15 14
                            10    |  8  9 11 10
```

Ojo: m3 va antes que m2.

## Reglas para agrupar

1. Tamaño **2ᵏ** (1, 2, 4, 8, 16); un grupo de 2ᵏ elimina k variables.
2. **Rectangular**, sin formas en L ni diagonales.
3. **Lo más grande posible** (grupos grandes → términos más cortos).
4. **El mapa se enrolla:** bordes opuestos y las 4 esquinas son vecinos.

**Leer un grupo:** variable constante en 1 → `A` · constante en 0 → `A'` · si cambia → desaparece.

## Implicantes

- **Implicante:** cualquier grupo válido de 1 (o X).
- **Implicante primo:** grupo que ya no se puede agrandar.
- **Primo esencial:** el único primo que cubre algún 1; debe estar en la solución.
- **Solución mínima = primos esenciales + los primos mínimos necesarios para cubrir el resto.** No siempre es única.

## Procedimiento para la SOP mínima

1. Colocar 1, 0 y X en el mapa.
2. Agrupar los grupos más grandes.
3. Elegir los primos esenciales.
4. Cubrir los 1 restantes con pocos grupos.
5. Leer un término por grupo.

## Ejemplo: `F = Σm(0,1,2,5,8,9,10)`

- `B'C'` (m0, m1, m8, m9) · `B'D'` (las 4 esquinas) · `A'C'D` (m1, m5)
- **SOP:** `F = B'C' + B'D' + A'C'D` → 7 literales.

## POS: se agrupan los 0

- La lectura se **invierte**: `0 → A` · `1 → A'`.
- Misma función: `F = (A'+B')(B'+D)(C'+D')` → 6 literales.
- Se construyen ambas formas y se elige la de menor costo (literales, compuertas, CI).

## Ideas para recordar

- SOP agrupa los 1; POS agrupa los 0 y se lee invertido.
- Primos esenciales primero.

[Seguir al siguiente tema ->](./tema4.md)
