# Arriendo-deptos

Tablero de búsqueda de arriendo 1D en Santiago Centro y Ñuñoa.

## Uso

Abre `index.html` en cualquier navegador. Es un solo archivo, sin instalación ni servidor.

Leaflet va incrustado dentro del archivo, así que la página funciona **sin conexión**.
Lo único que necesita internet son las teselas del mapa (OpenStreetMap): sin red los
marcadores igual se dibujan y todo lo demás — tarjetas, tabla, filtros — sigue funcionando.

## Qué contiene

44 avisos recolectados a mano desde Portal Inmobiliario, MercadoLibre, Yapo.cl, Assetplan,
iCasas y TikTok, más 11 descartados o caídos que quedan registrados para no volver a abrirlos.

Para cada aviso: arriendo, gasto común, **total mensual**, **costo de entrada del día 1**,
superficie, $/m², renta exigida y si califica con el sueldo configurado.

- Mapa con marcadores por nivel A–D. Clic abre la ficha; doble clic va directo al aviso.
- Filtros por estado, sector, tipo, tope de total mensual, tope de entrada, bodega,
  mascotas, sin comisión y "solo donde califico".
- Tabla comparativa ordenable con los mismos filtros aplicados.

## Tu renta no vive en el repositorio

La renta líquida se escribe **en la página**, en el campo del panel de filtros, y queda
guardada únicamente en el navegador de quien la escribe (`localStorage`). No está en el
HTML ni se sube a ningún lado, así que el archivo se puede publicar o compartir sin
exponer el sueldo de nadie. El botón «Borrar» la elimina.

Sin renta ingresada el tablero funciona igual: solo se apagan el techo de arriendo, el
filtro «solo donde califico» y los visto bueno de la tabla, y ningún aviso queda
descartado por ese motivo.

## Ajustar los supuestos

Al comienzo del `<script>` principal, en `index.html`:

```js
const PRESUPUESTO  = 400000;   // techo de arriendo
const UF           = 40851;    // UF al 14-ago-2026
const NOTARIAL_STD = 25000;    // gasto notarial estimado
```

Los avisos viven en el arreglo `D`, uno por objeto. Para agregar uno nuevo basta copiar
un objeto existente y cambiarle los campos; el puntaje, el nivel, el mapa y la tabla se
recalculan solos.

La fórmula del costo de entrada y el detalle del puntaje están explicados dentro de la
propia página, en la sección "Cómo se calcula todo".
