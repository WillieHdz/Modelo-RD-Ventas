# Incrustar el mapa interactivo en Power BI

El modelo estrella ya quedó construido y validado en **Modelo RD**. Esta guía explica cómo meter el mapa Leaflet (el demo que construimos) dentro de un informe de Power BI.

## Estado del modelo (ya hecho)

- **Esquema estrella limpio:** 8 relaciones activas, sin tablas de fecha automáticas basura.
  - Hechos: `Ventas`, `DetalleVentas`, `Metas`
  - Dimensiones: `Sucursales`, `Clientes`, `Productos`, `Calendario`, `Zonas`
- **15 medidas DAX** validadas (Venta Total RD$153.874.083,53, Cumplimiento 96,9%, Margen 35,2%).
- **Columnas geográficas** categorizadas (Latitud, Longitud, Provincia, Municipio).

## El reto del mapa HTML

El visual nativo no renderiza HTML arbitrario. El mapa pesa ~491 KB (Leaflet + datos embebidos), que excede el límite de datos de los visuales de texto. Hay 3 vías, de mejor a más simple:

---

### Opción A — Visual "HTML Content" + archivo alojado (recomendada)

1. **Instala el visual:** en Power BI Desktop → Visualizaciones → **⋯ → Obtener más objetos visuales** → busca **"HTML Content"** (de Daniel Marsh-Patrick) → Agregar.

2. **Aloja el HTML** en un lugar accesible por URL (cualquiera sirve):
   - GitHub Pages (gratis): sube `Mapa_Ventas_RD_paraPowerBI.html` a un repo y actívale Pages.
   - SharePoint / OneDrive de tu empresa (enlace público o de organización).
   - Un servidor web interno.

3. **Usa la medida `Mapa HTML`** (ya creada en `_Medidas`, carpeta "5 Visual"): edita su URL reemplazando `https://TU-URL/...` por la URL real donde alojaste el archivo. En Power BI: clic en la medida → en la barra de fórmulas cambia la URL → Enter.

4. Arrastra un visual **HTML Content** al lienzo y ponle la medida `Mapa HTML` en el campo de valores. El mapa aparece embebido en un iframe a pantalla completa del visual.

---

### Opción B — Visual "Deneb" o "Mapbox Viz" (mapa nativo dentro de PBI)

Si prefieres un mapa que reaccione a los filtros del informe (cross-filtering real), conviene reconstruir el mapa con un visual de mapas nativo:

- **Azure Maps** (ya viene en Power BI): arrastra `Sucursales[Latitud]` y `Sucursales[Longitud]` a Latitud/Longitud, `[Venta Total]` a Tamaño de burbuja, `Zonas[Zona]` a Leyenda. Activa el drill-down con la jerarquía `Zona > Provincia > Sucursal`.
- Esto pierde el look exacto del demo Leaflet, pero gana interactividad total con los slicers.

---

### Opción C — Imagen estática

Si solo necesitas mostrar el mapa como referencia visual, exporta un PNG desde el demo (botón Exportar) y mételo como imagen de fondo en la página.

---

## Recomendación

Para máxima fidelidad al demo: **Opción A** (HTML Content + GitHub Pages).
Para máxima interactividad con el modelo: **Opción B** (Azure Maps + drill-down).

Muchos equipos hacen las dos: una página con el mapa Leaflet incrustado (vista bonita) y otra con Azure Maps nativo (vista analítica que cruza con los slicers de mes, categoría, etc.).

## Archivos

- `Mapa_Ventas_RD_paraPowerBI.html` — el mapa autónomo listo para alojar/incrustar.
- La medida `Mapa HTML` en `_Medidas` — el iframe que lo carga (ajusta la URL).
