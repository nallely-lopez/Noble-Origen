# Acta de Constitución del Proyecto (Project Charter) 🌿

## 1. Información General
* **Nombre del Proyecto:** Noble Origen
* **Tipo de Proyecto:** Desarrollo de Software / Comercio Ético y Trazabilidad
* **Líder de Proyecto / Product Owner:** Nallely López
* **Fecha de Inicio:** Septiembre 2026

---

## 2. Justificación y Planteamiento del Problema
Los artesanos en el estado de Oaxaca enfrentan tres problemáticas críticas:
1. **Intermediación abusiva:** Pérdida de margen de ganancia frente a revendedores que adquieren piezas a mayoreo a precios bajos y las revenden a sobreprecio.
2. **Desconocimiento del costo real:** Dificultad para calcular el valor de las horas de trabajo manual invertidas, resultando en ventas por debajo del costo real debido al regateo.
3. **Apropiación cultural y plagio:** Vulnerabilidad de los diseños tradicionales ante la copia masiva no remunerada por parte de marcas industriales.
4. **Brecha digital:** Resistencia y dificultad en el uso de computadoras o aplicaciones de e-commerce complejas; WhatsApp es el único canal digital ampliamente dominado.

---

## 3. Objetivos del Proyecto (Criterios SMART)
* **Objetivo General:** Desarrollar una plataforma integral accesible vía WhatsApp y web para el cálculo de costos justos, comercialización directa y certificación digital de autoría de artesanías oaxaqueñas.
* **Objetivos Específicos:**
  * Implementar un asistente conversacional en WhatsApp para el registro de artesanos y costeo de piezas en menos de 5 minutos por producto.
  * Diseñar un mecanismo de certificación en la red Stellar que genere un hash SHA-256 inmutable por diseño registrado sin exponer fricción criptográfica al artesano.
  * Generar etiquetas físicas con códigos QR únicos para que compradores finales auditen el origen y el pago justo recibido por el creador.
  * Publicar un catálogo web B2C responsivo que cargue en menos de 3 segundos bajo conexiones móviles estándar.

---

## 4. Alcance del Sistema (Scope)

### Dentro del Alcance (MVP):
* Flujo conversacional guiado por WhatsApp para registro de artesano (HU-01).
* Calculadora de precio mínimo justo basada en insumos y horas trabajadas (HU-02).
* Registro multimedia de piezas artesanales mediante fotografías en chat (HU-03).
* Emisión automática de certificados de autoría con marca de tiempo en Stellar (HU-05).
* Generación de etiquetas con código QR en formato descargable/imprimible (HU-06).
* Vista pública responsiva para validación de autenticidad y desglose ético de precios (HU-07).

### Fuera del Alcance (Fase 1 / Futuras Versiones):
* Pasarelas de pago directo en criptomonedas (el MVP usa métodos tradicionales en MXN).
* Sistema propio de paquetería y logística física centralizada.
* Algoritmos complejos de visión artificial para reconocimiento automático de patrones textiles.

---

## 5. Supuestos y Restricciones
* **Supuestos:**
  * El artesano cuenta con un teléfono inteligente con WhatsApp y conectividad intermitente (red móvil o comunitaria).
  * El artesano está dispuesto a compartir los tiempos aproximados dedicados a la elaboración de sus piezas.
* **Restricciones:**
  * Intermitencia de red en comunidades rurales de Oaxaca (requiere tolerancia a fallos de sesión de 48 horas).
  * Presupuesto cero para comisiones de red por parte del artesano (abstracción total en backend).
  * Limitación temporal del semestre académico para el desarrollo y entrega de los paquetes de software.

---

## 6. Matriz Preliminar de Riesgos

| ID | Riesgo Identificado | Severidad | Mitigación Planificada |
| :--- | :--- | :--- | :--- |
| **R-01** | Abandono del flujo por intermitencia de red. | Alta | Persistencia de estado conversacional durante 48 horas. |
| **R-02** | Suplantación de identidad por intermediarios. | Crítica | Aprobación en dos fases: cuenta inicial `Activo no verificado` con filtro comunitario posterior. |
| **R-03** | Fricción técnica por uso de blockchain. | Alta | Abstracción total; el artesano solo recibe una imagen con código QR sin gestionar llaves privadas. |
| **R-04** | Fijación de precios por debajo de costo. | Media | Advertencia automática interactiva en el bot cuando el monto final sugerido genere pérdidas. |
