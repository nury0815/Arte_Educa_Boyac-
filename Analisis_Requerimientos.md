# Análisis de Requerimientos Técnicos — CreaDigital Boyacá
**Autora:** Nury Montañez  
**Institución:** Universidad Nacional Abierta y a Distancia (UNAD)  
**Materia:** Proyecto de grado
**Versión:** 1.0 — Paquete TRL5  
**Fecha:** 2025-11-13

---
## 1. Alcance del sistema
CreaDigital Boyacá es una plataforma digital inclusiva dirigida a niños, jóvenes, mujeres y adultos del departamento de Boyacá. El sistema permite la entrega de contenidos educativos, la exposición de obras artísticas, la gestión de convocatorias y la administración de usuarios. Este documento describe los requerimientos funcionales y no funcionales, la arquitectura técnica propuesta, el plan de desarrollo (Scrum) y la evidencia mínima para acreditar TRL5.

## 2. Actores y perfiles
- **Usuario final (Estudiante/Artista):** consume cursos, sube obras, participa en foros y ve convocatorias.  
- **Docente / Facilitador:** crea y modera contenidos educativos, evalúa actividades.  
- **Administrador:** gestiona usuarios, contenidos y reportes del sistema.  
- **Sistema (Servicios en la nube):** autentica usuarios, almacena recursos multimedia y ofrece API para el frontend.

## 3. Requerimientos funcionales (priorizados)
1. RF-01 — Registro y autenticación de usuarios con roles (estudiante, artista, docente, admin).  
2. RF-02 — Módulo de cursos: creación, visualización, seguimiento de progreso.  
3. RF-03 — Galería artística: subir imagen/video, metadatos (título, autor, descripción), visualización pública.  
4. RF-04 — Panel administrativo: CRUD de usuarios, contenidos y métricas de uso.  
5. RF-05 — Sección de noticias y convocatorias con filtros por fecha y categoría.  
6. RF-06 — Sistema de retroalimentación y comentarios en obras y cursos.  
7. RF-07 — Descarga limitada de certificados o constancias (PDF).

## 4. Requerimientos no funcionales
- RNF-01 — **Disponibilidad:** uptime objetivo >= 99% para el servicio en producción.  
- RNF-02 — **Escalabilidad:** arquitectura con escalado horizontal en capas críticas (servicio de archivos y API).  
- RNF-03 — **Seguridad:** comunicaciones por HTTPS, almacenamiento seguro de credenciales, uso de JWT o Firebase Auth.  
- RNF-04 — **Accesibilidad:** cumplir WCAG 2.1 AA en elementos clave (navegación, contraste, etiquetas alt).  
- RNF-05 — **Rendimiento:** tiempo de respuesta medio < 800 ms para peticiones API básicas bajo carga moderada.  
- RNF-06 — **Tolerancia a fallos:** respaldo automático de base de datos y restauración en no más de 24 h.  
- RNF-07 — **Compatibilidad:** soportar navegadores modernos y dispositivos móviles con 3G/4G.

## 5. Casos de uso principales (resumen)
- CU-01: Usuario se registra → confirma correo → inicia sesión → completa perfil.  
- CU-02: Docente crea curso → sube contenidos multimedia → publica módulo.  
- CU-03: Artista sube obra → la obra se publica en galería → recibe comentarios.  
- CU-04: Administrador revisa métricas → exporta reporte CSV/PDF.

## 6. Requisitos de datos y privacidad
- Datos personales mínimos: nombre, correo, rol, edad (opcional).  
- Cumplimiento con la normativa de protección de datos: se recomienda anonimizar respuestas en investigación y solicitar consentimiento para publicación de obras.  
- Políticas de retención: backups semanales y retención de logs por 6 meses.

## 7. Arquitectura técnica propuesta (resumen)
- **Frontend:** React (SPA) o Angular como opción, HTML5/CSS3 para contenidos estáticos.  
- **Backend / API:** Node.js + Express o Firebase Functions para lógica de negocio.  
- **Base de datos:** Firestore (NoSQL) o MySQL si se opta por arquitectura tradicional.  
- **Almacenamiento multimedia:** Firebase Storage o AWS S3.  
- **Autenticación:** Firebase Auth / OAuth2 / JWT.  
- **Despliegue:** Firebase Hosting, Google Cloud Run o AWS Elastic Beanstalk.  
- **Observabilidad:** logs en Stackdriver/CloudWatch, alertas por uptime y errores críticos.

## 8. Integraciones externas
- Servicios de correo para verificación (SendGrid/SES).  
- Servicios de pagos (opcional) para gestión de inscripciones con pasarela local.  
- API para certificados (generación de PDF desde plantillas).

## 9. Plan de desarrollo ágil (Scrum)
- **Duración total estimada:** 4 a 6 meses (para MVP robusto).  
- **Sprints:** 2 semanas.  
- **Roles:** Product Owner (PO), Scrum Master (SM), Equipo de desarrollo (3–5 personas recomendado).  
- **Ceremonias:** Sprint Planning, Daily Standup (15 min), Sprint Review, Sprint Retrospective.  
- **Artefactos:** Product Backlog, Sprint Backlog, Incremento.  
- **Criterio de aceptación por historia de usuario:** definición de done incluye tests unitarios básicos, documentación y despliegue en entorno de staging.

## 10. Estrategia de pruebas y validación (evidencia TRL5)
- **Pruebas unitarias:** cobertura mínima del 60% en módulos críticos.  
- **Pruebas de integración:** endpoints principales (auth, uploads, consultas de galería).  
- **Pruebas funcionales con usuarios piloto:** al menos N=8 pruebas con usuarios representativos (niños, jóvenes, adultos). Registrar feedback y métricas de usabilidad (SUS o encuestas adaptadas).  
- **Pruebas de rendimiento:** tests de carga simulando hasta 100 usuarios concurrentes en staging.  
- **Evidencia requerida para TRL5:** resultados de pruebas, grabación de demostración del prototipo en entorno controlado, plan de pruebas y logs.

## 11. Entregables y checklist TRL5
- Código fuente en GitHub con README técnico y .gitignore.  
- Scripts para poblar datos de prueba (scripts/seedFirestore.js).  
- Carpeta `docs/` con capturas y video de demo.  
- Reporte de pruebas y encuestas piloto.  
- Diagrama de arquitectura y plan de despliegue.

## 12. Recomendaciones operativas
- Usar variables de entorno para credenciales y no subir nunca archivos con claves.  
- Configurar protección de rama `main` y políticas de pull request.  
- Añadir licencia (MIT/Apache 2.0) si se comparte públicamente.
