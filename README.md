# FerroForma — Autocotizador de Rejas

Sitio premium para captar proyectos de rejas metálicas: configurador visual SVG en vivo, estimación por rango, formulario de proyecto, cobro de reserva técnica y agenda desbloqueada después del pago.

## Qué funciona
- Ancho y altura en vivo.
- Material: 20x20, 30x30, 40x20, pletina.
- Estilos: vertical, horizontal, geométrico, diagonal, semi-privado, industrial.
- Densidad, remate superior, acceso, terminación y color.
- Vista SVG que cambia con la selección.
- Motor de precio preliminar configurable.
- Reserva técnica de $9.990 CLP (configurable).
- Mercado Pago Checkout Pro en producción; modo demo sin credenciales.
- Desbloqueo de agenda después de pago.
- Embed de Cal.com mediante `APP.calBookingUrl`.
- JSON-LD LocalBusiness + Service, canonical, sitemap, robots y meta tags.

## Producción
1. Cambiar nombre/marca, comuna y dominio en `index.html`.
2. Reemplazar `TU-DOMINIO.CL` en HTML, `robots.txt` y `sitemap.xml`.
3. Ajustar `APP.baseM2`, multiplicadores y `APP.visitFee` con costos reales del soldador.
4. Desplegar en Vercel.
5. Configurar `MERCADOPAGO_ACCESS_TOKEN`; opcional `MERCADOPAGO_WEBHOOK_URL`.
6. Crear evento “Visita técnica” en Cal.com y pegar su URL pública en `APP.calBookingUrl`.

## Lógica de cotización
La cifra nunca se presenta como presupuesto definitivo. Se calcula a partir de superficie × precio base × multiplicadores de perfil, estilo, densidad y terminación + accesos. Se muestra una banda aproximada de -10% / +12%. Ajustar con datos reales de materiales, mano de obra, merma y traslado.

## Conversión recomendada
La reserva técnica se cobra después de que el usuario ya diseñó y vio una banda de inversión. Conviene comunicar que el fee se descuenta del trabajo final si el presupuesto es aprobado. Eso filtra consultas poco serias sin esconder el precio detrás de un paywall.

## SEO recomendado para fase 2
Crear URLs independientes por intención y zona, solo donde realmente se preste servicio: `/rejas-metalicas-osorno`, `/portones-metalicos-osorno`, `/cierres-perimetrales-osorno`, `/estructuras-metalicas-osorno`. Añadir fotos reales antes/después, ficha de Google Business Profile, testimonios verificables con permiso, casos de obra, tiempos típicos y FAQs reales de clientes.

## Boleta electrónica
El pago está separado del documento tributario. Conectar webhook de pago aprobado a OpenFactura/SII cuando estén definidos RUT emisor, giro, sucursal, tipo DTE (39/41 u otro aplicable), tratamiento IVA e idempotencia. No hardcodear estos datos hasta validarlos con contador/a.
