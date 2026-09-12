# Historias de Usuario - Noble Origen 🌿

Documento de especificación de requisitos bajo metodología ágil para la plataforma **Noble Origen**.

---

## Módulo 1: Identidad y Onboarding (Artesano)

### HU-01: Registro y alta del artesano vía WhatsApp (Auditada)
* **Como** artesana o artesano de una comunidad de Oaxaca,
* **quiero** darme de alta en el sistema enviando una palabra clave y respondiendo preguntas con opciones por WhatsApp,
* **para** tener una cuenta activa ligada a mi número que me permita registrar piezas y calcular precios sin usar formularios web ni contraseñas.

#### Criterios de Aceptación:
- [ ] **CA-01 (Trigger):** El flujo se activa únicamente con la palabra clave "INICIAR" o al hacer clic en el enlace oficial de bienvenida.
- [ ] **CA-02 (Identidad):** Captura el nombre público o del taller artesanal (máximo 60 caracteres) sin exigir identificación fiscal en esta etapa.
- [ ] **CA-03 (Taxonomía):** La técnica artesanal se selecciona mediante una lista de botones fijos (1: Textil/Telar, 2: Barro, 3: Madera/Copal, 4: Fibras vegetales, 5: Otra).
- [ ] **CA-04 (Resiliencia):** La sesión del usuario persiste hasta por 48 horas ante caídas de conexión antes de reiniciar el formulario.
- [ ] **CA-05 (Seguridad):** El perfil inicia en estado `Activo no verificado`, permitiendo costeo pero requiriendo confirmación comunitaria antes de publicar piezas.

---

## Módulo 2: Finanzas y Costeo Justo (Artesano)

### HU-02: Calculadora conversacional de precio mínimo justo
* **Como** artesano sin conocimientos de contabilidad,
* **quiero** ingresar en el chat los gastos de insumos y el tiempo dedicado a una pieza,
* **para** obtener un precio mínimo de venta sugerido que cubra mis costos y me proteja contra el regateo.

#### Criterios de Aceptación:
- [ ] **CA-01:** El bot solicita costo de materiales y horas/jornadas de trabajo.
- [ ] **CA-02:** Si el artesano no define tarifa por hora, el sistema sugiere el tabulador base regional.
- [ ] **CA-03:** El sistema desglosa: `Materiales + Mano de Obra + Margen Sugerido`.
- [ ] **CA-04:** El artesano puede aceptar la cifra o ingresar su precio final propio.

---

## Módulo 3: Propiedad Intelectual y Trazabilidad (Stellar / Sistema)

### HU-05: Emisión de certificado digital de autoría con marca de tiempo
* **Como** artesano creador de piezas originales,
* **quiero** que el sistema registre digitalmente la autoría de mi diseño al subirlo,
* **para** tener una prueba inmutable con fecha y autoría frente a plagios de marcas industriales.

#### Criterios de Aceptación:
- [ ] **CA-01:** El backend genera un hash SHA-256 de la imagen y metadatos de la pieza.
- [ ] **CA-02:** Se registra la transacción en la red Stellar de forma transparente sin exponer llaves privadas al artesano.
- [ ] **CA-03:** El proceso de registro tarda menos de 30 segundos en completarse.

---

## Módulo 4: Transparencia y Consulta Pública (Comprador)

### HU-07: Verificación pública de origen y desglose ético
* **Como** comprador o turista interesado en artesanía legítima,
* **quiero** escanear el código QR de la etiqueta física con mi teléfono,
* **para** verificar que la pieza no es una imitación industrial y confirmar cuánto dinero recibió directamente el artesano.

#### Criterios de Aceptación:
- [ ] **CA-01:** Abre una página web ligera sin requerir registro ni descarga de apps.
- [ ] **CA-02:** Carga en menos de 3 segundos en redes móviles estándar.
- [ ] **CA-03:** Muestra foto, artesano, técnica, comunidad y desglose del pago en origen.
