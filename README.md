# Luxury Motors Elite Corp. — MVP de e-commerce

Aplicación web SPA de demostración para catálogo, compra y alquiler de vehículos y motocicletas. Incluye carrito mixto, checkout simulado, cálculo de ITBIS, depósito reembolsable y generación de factura/contrato PDF.

## Ejecutar

1. Descomprime la carpeta del proyecto.
2. Abre una terminal dentro de `LuxuryMotorsElite`.
3. Ejecuta `python -m http.server 8000` (o usa Live Server en VS Code).
4. Visita `http://localhost:8000`.

Se recomienda servidor local porque los navegadores restringen `fetch()` sobre archivos `file://`. La aplicación incluye un pequeño catálogo embebido de respaldo, pero el inventario completo se carga desde `vehiculo.json`.

## Archivos

- `index.html`: estructura semántica, navbar, catálogo y modales.
- `styles.css`: estilos premium, contraste y responsive.
- `app.js`: carga JSON, filtros, alquileres, carrito, ITBIS y documentos PDF.
- `vehiculo.json`: catálogo original entregado como recurso.
- `pdf_thumbnails.js`: miniaturas JPEG en Base64 para el render PDF.
- `assets/`: fotografías y logotipos proporcionados.

## Funciones incluidas

- Alternar entre vehículos y motocicletas; búsqueda en tiempo real.
- Fichas con imagen, marca, código, características, stock y tarifas.
- Alquiler por día/hora, fecha de inicio, duración y fianza de USD 500.
- Compra, carrito mixto, cantidades, eliminación y vaciado.
- Cálculo de ITBIS (18%), subtotal, fianza y total.
- Checkout con datos demo precargados y botón de restauración.
- Factura PDF, contrato PDF o documento mixto con términos, firmas y miniaturas.

## Dependencias CDN

Bootstrap 5.3.3, Font Awesome 6.5.1, SweetAlert2 11 y html2pdf.js 0.10.1. Se requiere conexión a internet para cargar estas librerías.

## Consideraciones de demostración

- No existe una pasarela bancaria real ni se realizan cargos.
- El ITBIS se simula al 18% para el ejercicio.
- El depósito de USD 500 por unidad alquilada se suma al total y se muestra como reembolsable.
- El JSON de origen no contiene en todos los registros las propiedades `precio_alquiler_hora`, `precio_alquiler_dia` ni `oferta_alquiler`; el frontend genera tarifas demo y textos predeterminados cuando faltan.
- La información de cliente y tarjeta está precargada para pruebas. No debe utilizarse una tarjeta real.
- El sistema comprueba existencia al agregar, pero al ser un MVP estático no bloquea inventario en un servidor ni persiste pedidos.
- El PDF se compone desde una plantilla HTML en memoria y se convierte a un elemento DOM temporal antes de llamar a html2pdf, ya que html2pdf espera un elemento renderizable. El documento no se agrega a un contenedor oculto de la página.

## Compatibilidad

Navegadores modernos con JavaScript ES6+, `fetch`, `crypto.randomUUID` y acceso a CDN. Si se ejecuta sin servidor, puede activarse el catálogo de respaldo por restricciones de `file://`.
