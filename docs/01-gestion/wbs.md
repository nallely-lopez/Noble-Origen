# Estructura de Desglose del Trabajo (EDT / WBS) 🌿
## Proyecto: Noble Origen

Documento jerárquico de descomposición del alcance en paquetes de trabajo entregables (regla del 100%).

---

## 1. Diagrama Jerárquico de la EDT

```text
1.0 Proyecto Noble Origen
│
├── 1.1 Gestión del Proyecto
│   ├── 1.1.1 Acta de Constitución (Project Charter)
│   ├── 1.1.2 Plan de Gestión de Requisitos e Historias de Usuario
│   ├── 1.1.3 Matriz de Riesgos y Mitigación
│   └── 1.1.4 Cierre y Evaluación de Entregas
│
├── 1.2 Análisis y Diseño
│   ├── 1.2.1 Especificación de Requisitos de Software (SRS)
│   ├── 1.2.2 Flujos Conversacionales UX/UI (Chatbot WhatsApp)
│   ├── 1.2.3 Arquitectura Backend y Modelo Relacional
│   └── 1.2.4 Diseño de Interfaces Web (Catálogo y Visor QR)
│
├── 1.3 Asistente Conversacional (WhatsApp Bot)
│   ├── 1.3.1 Integración con API de Mensajería
│   ├── 1.3.2 Módulo de Registro y Alta de Artesano (HU-01)
│   ├── 1.3.3 Calculadora Conversacional de Costeo Justo (HU-02)
│   └── 1.3.4 Módulo de Captura Multimedia de Piezas (HU-03)
│
├── 1.4 Backend y Trazabilidad en Stellar
│   ├── 1.4.1 API REST / Servicios de Negocio
│   ├── 1.4.2 Servicio de Generación de Hash SHA-256
│   ├── 1.4.3 Conexión y Emisión de Transacciones en Stellar (HU-05)
│   └── 1.4.4 Generador de Etiquetas con Código QR (HU-06)
│
├── 1.5 Plataforma Web Marketplace
│   ├── 1.5.1 Catálogo Web Responsivo B2C (HU-08)
│   ├── 1.5.2 Visor Público de Verificación Ética y de Origen (HU-07)
│   └── 1.5.3 Integración de Pasarela de Pagos Tradicional
│
└── 1.6 Calidad y Despliegue
    ├── 1.6.1 Pruebas de Resiliencia ante Cortes de Conexión
    ├── 1.6.2 Pruebas de Usabilidad con Artesanos (Validación de Campo)
    └── 1.6.3 Despliegue en Ambiente de Pruebas / Producción
## 2. Diccionario de la EDT (Paquetes Críticos)

### Paquete 1.3.3: Calculadora Conversacional de Costeo Justo
* **Descripción:** Implementación del flujo de preguntas por WhatsApp que solicita gastos de materiales e insumos, jornadas/horas de elaboración y tarifa horaria esperada, devolviendo un precio sugerido transparente.
* **Entregable:** Árbol conversacional conectado a la base de datos con motor de cálculo financiero.
* **Criterios de Aceptación:**
  * Si el artesano no define tarifa por hora, el sistema asigna el tabulador base de salario digno regional.
  * El cálculo aplica la fórmula: `Costo Materiales + (Horas × Tarifa) + Margen Mínimo (20%)`.
  * Genera una advertencia interactiva si el usuario intenta fijar un precio inferior al costo calculado.

### Paquete 1.4.3: Conexión y Emisión de Transacciones en Stellar
* **Descripción:** Módulo backend que acuña la autoría de la pieza con marca de tiempo en la red Stellar sin exponer claves criptográficas ni cobros directos al artesano.
* **Entregable:** Microservicio de emisión de certificados en la red de pruebas (testnet) o red principal.
* **Criterios de Aceptación:**
  * Confirmación de transacción en menos de 30 segundos.
  * Manejo automático de reintentos (hasta 3 intentos) ante fallos temporales de red.
  * Registro del identificador de transacción y hash en la base de datos.

### Paquete 1.5.2: Visor Público de Verificación Ética y de Origen
* **Descripción:** Página web ligera optimizada para dispositivos móviles que se abre al escanear la etiqueta física con código QR.
* **Entregable:** Interfaz web pública responsiva.
* **Criterios de Aceptación:**
  * Tiempo de carga menor a 3 segundos en redes móviles estándar.
  * Desglose visual del artesano, técnica, comunidad, fecha y distribución ética del pago.
  * Enlace al explorador de Stellar con la prueba inmutable del registro.
