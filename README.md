Prueba el mapa interactivo aquí: https://raw.githack.com/WillieHdz/Modelo-RD-Ventas/main/Mapa_Ventas_RD_paraPowerBI.html

 Quise llevar el análisis de ventas un paso más allá del clásico gráfico de barras, así que construí un modelo de un mapa interactivo de República Dominicana desarrollado con inteligencia artificial que permite explorar las ventas por zona, provincia y sucursal con drill-down, mapa de calor y vista satelital.
 
 ¿Cómo funciona?
 
 Arrancas viendo el país dividido en las 3 zonas comerciales (Norte, Sur, Este), donde el color indica el volumen de ventas. Haces clic en una zona y haces zoom a sus provincias; entras a una provincia y aparecen sus sucursales como puntos en el mapa. Al pasar sobre cualquiera, ves su venta total, ticket promedio, producto más vendido y cumplimiento de meta.
 
 Lo que hay detrás:
 
 - Modelo de datos en esquema estrella en Power BI (tablas de hechos, 5 dimensiones, 16 medidas DAX)
 
 - +59.000 facturas y 175.000 líneas de detalle de venta
 
 - Mapa construido con Leaflet y datos geográficos oficiales de RD (GeoJSON)
 
 - Cumplimiento de metas, márgenes y tendencias mensuales por sucursal
 
 Lo más interesante no fue solo el mapa, sino conectar todo: la base de datos, el modelo dimensional y la visualización en una sola historia que cualquiera puede explorar haciendo clic.
 
 Es un proyecto de práctica con datos de ejemplo, pero el enfoque es 100% aplicable a cualquier negocio con presencia territorial: retail, farmacias, distribución, banca.

 
