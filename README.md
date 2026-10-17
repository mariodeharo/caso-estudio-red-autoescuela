# Caso de Estudio: Modernización de Infraestructura IT y Red (Entorno Multi-sede)

## 1. Contexto del Proyecto
Infraestructura compuesta por **2 sedes físicas** y aproximadamente **50 puestos de usuario** (aulas informatizadas de alumnos y puestos de administración). El entorno presentaba cortes de conectividad WiFi por saturación del router del ISP, fallos recurrentes en los sistemas operativos de las aulas y dependencia crítica de un software de gestión obsoleto (PONS) incompatible con entornos modernos.

## 2. Soluciones Implementadas

### A. Virtualización transparente de Software Legacy (PONS)
* **Problema:** El software administrativo requería rutas estáticas antiguas, versiones obsoletas de Adobe y obligaba al personal a retrasar manualmente la fecha del sistema operativo a 2010, generando fallos de seguridad y bloqueos constantes al intentar migrar de equipo.
* **Solución:** Creación de una Máquina Virtual aislada (Windows 7/8 Pro) replicando la estructura exacta de directorios requerida.
* **Automatización:** Configuración de script/servicio de autoarranque en pantalla completa al iniciar el PC anfitrión. Para el usuario final, la experiencia es encender el equipo y trabajar directamente sin pasos intermedios.

### B. Estandarización de 40+ Equipos mediante Imágenes Maestras (Golden Images)
* **Problema:** Corrupción del sistema operativo, disparidad de drivers y lentitud generalizada en los ~40 ordenadores de las dos sedes.
* **Solución:** Auditoría del hardware (2 modelos base, uno por sede) y creación de 2 imágenes maestras limpias, optimizadas y preconfiguradas.
* **Resolución de incidencias (Post-despliegue):** Detección y corrección de un conflicto gráfico provocado por la aceleración por hardware en Firefox en una de las sedes.
* **Resultado:** >97% de estabilidad durante más de 3 meses continuados en producción (solo 1 equipo de ~40 requirió reinstalación de imagen).

### C. Rediseño WiFi Empresarial y Cableado Estructurado
* **Problema:** Saturación del router de la operadora y baja cobertura en el aula de exámenes/alumnos y zona de administración.
* **Solución:** 
  * Desactivación del WiFi integrado en el router del ISP (Movistar).
  * Tendido de cableado estructurado por falso techo e instalación de punto de acceso **Ubiquiti UniFi U6+ (PoE)** ubicado estratégicamente en el aula.
  * Segmentación inalámbrica en dos redes independientes: `Red Alumnos` y `Red Administración`.
  * Enlace directo por cableado estructurado hacia el área de administración con conmutación dedicada (Switch 5 puertos) para garantizar caudal estable en los equipos de gestión e impresora en red.
