# La conquista de China sobre la automoción europea parte desde España

**Infografía interactiva** con las principales factorías de vehículos, baterías y componentes de España con capital chino —en operación y anunciadas para 2027–2030— frente a la industria tradicional, con la bandera del país propietario de cada empresa.

**Web:** https://europenguin.github.io/china-coches-espana/

Datos actualizados a **30 de septiembre de 2026**.

---

## Contenido

| Sección | Qué incluye |
|---|---|
| Portada + KPIs | Cuota de marcas chinas (16,65% en julio 2026), 16 proyectos con capital chino, ≈7.000 M€ anunciados, peso en la producción española (3% → 13%) |
| Mapa | 23 plantas sobre mapa SVG de provincias: 16 con capital chino + 7 de la industria tradicional. Filtros por tipo (vehículos / baterías / componentes), etiquetas y panel de detalle con datos, banderas y fuentes |
| Índice | Lista ordenada por fecha de arranque de los 16 proyectos chinos |
| Fichas | 16 tarjetas con inversión, empleo, capacidad, modelos y estado de cada proyecto |
| Gráficos | Evolución de cuota 2024–2026, marcas más vendidas y capacidad instalada (1,6% → 22%), cada uno con su bloque de análisis |
| Cronología | 2024–2031: de la alianza Chery–Nissan al 13% de la producción nacional |
| Fuentes y notas | Medio a medio, comunicados oficiales y metodología (qué cuenta como «capital chino», cómo se estima la capacidad) |
| Certificado | Sello circular «Certificado de calidad» en el pie, junto a la fecha de verificación de los datos |

## Estructura

Sin dependencias ni build:

```
index.html             HTML + CSS + JS (mapa, tarjetas, gráficos, filtros, estilos de impresión)
mapa-espana.js         window.SPAIN_GEO → límites provinciales (GeoJSON abierto),
                       proyección Mercator, viewBox 1000×821,7 y recuadro de Canarias
sello-europenguin.png  sello circular «Certificado de calidad» del pie
README.md
```

- **Sin framework ni npm**: se abre directamente en el navegador (`file://` funciona igual que en servidor).
- **El mapa es SVG generado a runtime**: cada provincia es un `<path>`, cada planta un marcador con forma por tipo (círculo = vehículo, rombo = batería, triángulo = componente) y color por capital.

## Ver en local

Abre `index.html` con doble clic, o sirve la carpeta:

```powershell
npx serve .
```

## Editar los datos

Todo vive en el array `SITES` de `index.html` (~línea 543):

```js
{id:'ebro', n:'Ebro Factory (ex-Nissan)', short:'Ebro · Chery',
 city:'Barcelona · Zona Franca', ccaa:'Cataluña',
 lat:41.34, lon:2.15,           // coordenadas del marcador en el mapa
 t:'vehiculo',                   // vehiculo | bateria | componente
 cn:1,                           // 1 = capital chino, ausente = industria tradicional
 st:'operativa',                 // operativa | construccion | anunciada
 stl:'En operación',             // etiqueta visible
 flags:['ES','CN'],              // banderas de la matriz propietaria
 desc:'…', f:[['Inversión','…']], src:'Fuente (fecha)',
 lp:[13,4,'r']}                  // etiqueta: desplazamiento x,y y lado (l/r)
```

Al añadir un proyecto, recuerda actualizar también los KPIs, el chip de la portada y la nota del panel (conteos de proyectos, tipos y CCAA).

## PDF / imprimir

Botón **«Guardar en PDF / imprimir»** en el mapa. Los estilos `@media print` fuerzan A4 con paginación de 8 páginas (portada · mapa · panel+índice · 2 páginas de fichas · gráficos · capacidad+cronología · fuentes). Si el contenido crece, revisa que siga saliendo en 8.

## Publicación

GitHub Pages despliega `main` automáticamente en cada push (~1 min):

```powershell
git add index.html
git commit -m "mensaje"
git push
```

Recarga con **Ctrl+F5** si el navegador muestra una versión anterior.

## Fuentes

Recopilación propia de fuentes públicas: El País, Expansión, Reuters, Europa Press, faro de Vigo, Economía Digital, elEconomista, medios locales (El Correo, Tribuna, Diario de Valladolid…), comunicados de Stellantis, CATL, Geely, Ford, MG/SAIC, Ebro Motors, Renault Group, Horse Powertrain y Aramco, más Anfac, Sernauto, ACEA y las administraciones autonómicas. El listado completo, con fechas, está en el pie de la infografía.

Las coordenadas son municipales o aproximadas y la capacidad instalada es una estimación propia: no existe dato oficial por planta.
