# BLUEPRINT OFICIAL: ESTÁNDAR TÉCNICO Y SEMÁNTICO PARA LANDING PAGES INMOBILIARIAS
## Optimización para Google (SEO Local) y Modelos de Inteligencia Artificial (LLMs)
**Desarrollado para:** Austral Drone & Red de Proyectos Inmobiliarios (Chile / Chiloé / Décima Región)

Este documento contiene la metodología exacta, prevención de errores y checklist técnico que debe aplicarse a cada nueva página web o proyecto inmobiliario (por ejemplo: Isla Lemuy, 4 propiedades, loteos, parcelas).

---

### 1. ARQUITECTURA DE ARCHIVOS OBLIGATORIA
Cada proyecto o repositorio web debe contener como mínimo:
1. `index.html` (o páginas por propiedad, ej: `parcela-1.html`, `parcela-2.html`).
2. `sitemap.xml` con URLs absolutas canónicas y fecha `lastmod` actualizada.
3. `robots.txt` con permisos explícitos para rastreadores de IA (`GPTBot`, `ChatGPT-User`, `Google-Extended`, `PerplexityBot`, `ClaudeBot`).
4. `llms.txt` estructurado con la ficha técnica de cada propiedad, valores en CLP/UF, características geográficas y enlace a WhatsApp.
5. `CNAME` (si usa dominio propio .cl en GitHub Pages / Cloudflare).

---

### 2. ETIQUETAS HEAD Y MARCADO ESTRUCTURADO (SCHEMA.ORG)

#### A. Metaetiquetas Geo-Localizadas (SEO de Proximidad):
Google posiciona propiedades por cercanía física. Siempre incluir:
- **Título:** `[Tipo de Propiedad] en [Localidad], [Isla / Comuna] | [Atributo Clave] - Venta Directa`
  *Ejemplo:* `4 Parcelas Exclusivas en Isla Lemuy, Chiloé | Orilla de Mar & Rol Propio - Dueño Directo`
- **Keywords Geográficas:** Incluir comuna (ej. Puqueldón), isla (Lemuy), archipiélago (Chiloé), provincia y región.

#### B. Schema.org JSON-LD para Propiedades (`RealEstateListing` o `Place`):
```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "RealEstateListing",
  "name": "Parcelas Puchilco - Isla Lemuy, Chiloé",
  "description": "Venta directa de 4 parcelas con rol propio, factibilidad de agua y luz, vistas al mar interior de Chiloé.",
  "url": "https://tudominio.cl/",
  "offers": {
    "@type": "AggregateOffer",
    "priceCurrency": "CLP",
    "lowPrice": "25000000",
    "highPrice": "45000000"
  },
  "address": {
    "@type": "PostalAddress",
    "addressLocality": "Isla Lemuy (Puqueldón)",
    "addressRegion": "Los Lagos / Chiloé",
    "addressCountry": "CL"
  }
}
</script>
```

---

### 3. PREVENCIÓN DE ERRORES FRECUENTES (CHECKLIST TÉCNICO)

| Error Detectado en Proyectos Anteriores | Solución Estándar Aplicada |
| :--- | :--- |
| **Video hero se congela en móviles** | Atributos obligatorios: `autoplay loop muted playsinline webkit-playsinline x5-playsinline preload="auto"`. Además tener fallback de imagen poster WebP y watchdog en JS si el navegador suspende la reproducción. |
| **Menú superior saturado / confuso** | Mantener navegación limpia tipo Dock o cápsula flotante con no más de 5 a 6 enlaces clave (`INICIO`, `PROPIEDADES`, `FOTOS DRON`, `UBICACIÓN`, `CONTACTO`). |
| **Imágenes pesadas que demoran la carga** | Usar compresión WebP, `loading="lazy"`, y alojar videos pesados en CDN o GitHub Releases para no saturar el repositorio. |
| **Interesados perdidos sin saber a qué lote consultan** | Los botones de WhatsApp deben llevar mensaje precargado específico por lote: *ej: "Hola, me interesa la Parcela #2 (Orilla de Mar) en Isla Lemuy"*. |
| **IAs no reconocen el precio o disponibilidad** | Sintetizar en `llms.txt` el listado de las 4 propiedades con número de lote, hectáreas, precio en CLP y rol propio SAG. |

---

### 4. PROTOCOLO DE CONEXIÓN CON IA Y CHATBOT
- Integración del widget de asistencia o botón flotante.
- Inyección de datos técnicos de la propiedad:
  * Número de Rol de Avalúo (SII) y subdivisión aprobada SAG.
  * Factibilidad de empalme eléctrico (Saesa / Coopeles) y agua (APR / pozo profundo).
  * Distancias: Minutos a rampa de transbordador (Chulchuy - Huicha), a Castro o Chonchi.
