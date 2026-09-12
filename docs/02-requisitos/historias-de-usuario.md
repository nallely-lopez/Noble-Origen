# Especificación de Historias de Usuario - Noble Origen 🌿

Documento formal de requisitos ágiles para la plataforma **Noble Origen**. Las historias han sido refinadas tras el proceso de auditoría para mitigar riesgos de conectividad intermitente, brecha digital y validación comunitaria en el estado de Oaxaca.

---

## Módulo 1: Identidad y Onboarding (Artesano)

### [HU-01] Registro y alta del artesano vía WhatsApp (Auditada)
* **Como** artesana o artesano de una comunidad de Oaxaca,
* **quiero** darme de alta en el sistema enviando una palabra clave y respondiendo preguntas con opciones por WhatsApp,
* **para** tener una cuenta activa ligada a mi número que me permita registrar piezas y calcular precios sin usar formularios web ni contraseñas.

#### Criterios de Aceptación:
- [ ] **CA-01 (Trigger):** El flujo se activa únicamente con la palabra clave "INICIAR" o al hacer clic en el enlace oficial de bienvenida.
- [ ] **CA-02 (Identidad):** Captura el nombre público o del taller artesanal (máximo 60 caracteres) sin exigir datos fiscales en esta etapa.
- [ ] **CA-03 (Taxonomía):** La técnica artesanal se selecciona mediante botones fijos (1: Textil/Telar, 2: Barro, 3: Madera/Copal, 4: Fibras vegetales, 5: Otra).
- [ ] **CA-04 (Resiliencia):** La sesión del usuario persiste hasta por 48 horas ante caídas de conexión antes de reiniciar el formulario.
- [ ] **CA-05 (Seguridad):** El perfil inicia en estado `Activo no verificado`, permitiendo costeo pero requiriendo validación comunitaria antes de publicar piezas en el catálogo público.

---

## Módulo 2: Finanzas y Costeo Justo (Artesano)

### [HU-02] Calculadora conversacional de precio mínimo justo
* **Como** artesano sin conocimientos de contabilidad,
* **quiero** ingresar en el chat los gastos de insumos y el tiempo dedicado a una pieza,
* **para** obtener un precio mínimo de venta sugerido que cubra mis costos y me proteja contra el regateo.

#### Criterios de Aceptación:
- [ ] **CA-01:** El bot solicita mediante preguntas numéricas: gasto total en materiales e insumos (pesos mexicanos) y tiempo invertido (horas o jornadas estimadas).
- [ ] **CA-02:** Si el artesano no define una tarifa horaria deseada, el sistema sugiere automáticamente el tabulador base de salario digno regional.
- [ ] **CA-03:** El sistema calcula y desglosa: `Costo Materiales + (Horas × Tarifa) + Margen de Utilidad Mínimo (20%)`.
- [ ] **CA-04:** El bot permite al artesano aceptar la cifra sugerida o ingresar un precio de venta superior. Si el artesano ingresa un monto inferior al costo base, el sistema emite una advertencia de pérdida económica antes de confirmar.

---

## Módulo 3: Catálogo y Publicación (Artesano)

### [HU-03] Alta de pieza artesanal por mensajería multimedia
* **Como** artesano registrado,
* **quiero** enviar por WhatsApp las fotografías y detalles esenciales de mi pieza terminada,
* **para** que mi producto se registre en la base de datos sin interactuar con computadoras.

#### Criterios de Aceptación:
- [ ] **CA-01:** El bot admite de 1 a 3 fotografías comprimidas por WhatsApp y valida que al menos una imagen sea nítida antes de continuar.
- [ ] **CA-02:** El bot solicita datos estructurados mediante respuestas breves: nombre de la pieza, medidas aproximadas (alto x ancho en cm) y materiales clave.
- [ ] **CA-03:** Es requisito haber calculado o asignado el precio en HU-02 antes de completar el alta de la pieza.
- [ ] **CA-04:** Al terminar, el bot envía un mensaje de resumen con ficha técnica completa y solicita confirmación con el botón "Confirmar y Publicar".

### [HU-04] Gestión básica de disponibilidad de inventario
* **Como** artesano que elabora piezas únicas,
* **quiero** marcar por WhatsApp cuando una pieza ya se vendió en mi taller local,
* **para** que el catálogo web no ofrezca piezas que ya no tengo disponibles.

#### Criterios de Aceptación:
- [ ] **CA-01:** El comando "MIS PIEZAS" despliega una lista numerada de las obras activas del artesano con su estatus actual.
- [ ] **CA-02:** El artesano puede responder con el número de pieza y la opción "VENDIDA" para darla de baja de la venta web.
- [ ] **CA-03:** El cambio de estado a `No disponible` se refleja en la base de datos en menos de 5 segundos para evitar compras concurrentes.

---

## Módulo 4: Propiedad Intelectual y Trazabilidad (Stellar / Backend)

### [HU-05] Emisión de certificado digital de autoría con marca de tiempo
* **Como** artesano creador de piezas originales,
* **quiero** que el sistema registre digitalmente la autoría de mi diseño al subirlo,
* **para** tener una prueba inmutable con fecha y autoría frente a plagios de marcas industriales.

#### Criterios de Aceptación:
- [ ] **CA-01:** El backend genera un hash criptográfico SHA-256 utilizando la imagen principal, el identificador del artesano, la comunidad y la marca de tiempo (timestamp).
- [ ] **CA-02:** Se registra la transacción en la red Stellar gestionada por la cuenta custodio del sistema, sin comisiones ni llaves criptográficas expuestas al artesano.
- [ ] **CA-03:** En caso de interrupción en la red Stellar, el sistema encola la transacción y realiza hasta 3 reintentos automáticos sin detener el flujo del usuario.
- [ ] **CA-04:** La confirmación de emisión en la red queda registrada en la base de datos en un tiempo menor a 30 segundos.

### [HU-06] Generación de etiqueta física con código QR único
* **Como** artesano que entrega su producto al comprador,
* **quiero** recibir en mi chat una imagen descargable con el código QR único de la pieza,
* **para** imprimirlo o adjuntarlo físicamente a la prenda como sello de autenticidad.

#### Criterios de Aceptación:
- [ ] **CA-01:** El bot genera y envía un archivo de imagen ligero (PNG optimizado para impresión) con el código QR y el folio alfanumérico visible.
- [ ] **CA-02:** El código QR contiene una URL única e irrepetible que apunta al visor público de la pieza (`nobleorigen.com/verificar/[folio]`).
- [ ] **CA-03:** La imagen incluye el nombre de la plataforma, el nombre del taller y espacio marcado para perforación de etiqueta física.

---

## Módulo 5: Transparencia y Compra Ética (Comprador / Turista)

### [HU-07] Verificación pública de origen y desglose ético
* **Como** comprador o turista interesado en artesanía legítima,
* **quiero** escanear el código QR de la etiqueta con la cámara de mi teléfono,
* **para** verificar que la pieza no es una imitación industrial y confirmar cuánto dinero recibió directamente el creador.

#### Criterios de Aceptación:
- [ ] **CA-01:** La URL del QR abre una página web responsiva sin solicitar inicio de sesión ni instalación de software adicional.
- [ ] **CA-02:** La vista web se renderiza en menos de 3 segundos bajo redes móviles 3G/4G estándar.
- [ ] **CA-03:** Muestra de forma pública: fotografía original, nombre del artesano/taller, comunidad de origen, técnica, fecha de certificación y desglose ético (monto directo recibido por el artesano vs. gastos operativos de plataforma).
- [ ] **CA-04:** Incluye un enlace al explorador de bloques de Stellar para auditar la transacción y su hash SHA-256.

### [HU-08] Exploración de catálogo y compra con precio justo
* **Como** comprador en línea,
* **quiero** filtrar artesanías por técnica tradicional y comunidad oaxaqueña,
* **para** adquirir piezas auténticas directamente de los talleres comunitarios.

#### Criterios de Aceptación:
- [ ] **CA-01:** El catálogo permite filtrar por técnica (Telar/Textil, Barro, Madera, Fibras) y por municipio de origen.
- [ ] **CA-02:** Cada ficha de producto muestra el perfil del taller artesanal y su estado de verificación.
- [ ] **CA-03:** El sistema procesa pagos en moneda nacional mediante pasarelas estándar (tarjeta / transferencia SPEI).
- [ ] **CA-04:** Al confirmarse un pago, el sistema envía una alerta inmediata por WhatsApp al artesano con los datos de entrega y bloquea la pieza para evitar compras simultáneas.
