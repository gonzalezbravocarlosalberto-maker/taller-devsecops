# Taller DevSecOps
🔐 DevSecOps

DevSecOps es un enfoque de desarrollo de software que integra la seguridad en todas las fases del ciclo de vida del desarrollo, desde la planificación hasta el despliegue y la operación.

A diferencia del modelo tradicional donde la seguridad se evalúa al final, DevSecOps la incorpora desde el inicio bajo el principio de:

"Shift Left Security" — mover la seguridad hacia las primeras etapas del desarrollo.

📌 Origen del término

El nombre DevSecOps proviene de la combinación de tres áreas fundamentales:

DEV – Development → Desarrollo

SEC – Security → Seguridad

OPS – Operations → Operaciones

🎯 Objetivo principal

Integrar prácticas de seguridad de forma continua y automatizada dentro del pipeline de CI/CD para:

Reducir vulnerabilidades

Detectar fallos tempranamente

Disminuir costos de corrección

Mejorar la cultura de seguridad

Aumentar la velocidad sin comprometer la protección

🔄 Ciclo de Vida en DevSecOps

Planificación

Desarrollo

Integración

Pruebas

Despliegue

Monitoreo

Retroalimentación continua

🛠 Ejemplos de prácticas en DevSecOps

Análisis estático de código (SAST)

Análisis dinámico (DAST)

Escaneo de dependencias

Escaneo de contenedores

Infraestructura como código segura

Monitoreo de seguridad en producción

Implementación de MFA y control de acceso.

Trazabilidad: ¿Por qué es un riesgo de seguridad dejar la configuración de user.name y user.email vacía o utilizar datos genéricos en un entorno empresarial?
RTA: En un entorno empresarial, dejar la configuración de user.name y user.email vacía o utilizar datos genéricos en Git representa un riesgo porque elimina la trazabilidad real de los cambios realizados en el código. Esto impide identificar con precisión quién realizó una modificación, afectando la auditoría, el principio de responsabilidad individual y el no repudio. Desde el punto de vista de estándares como ISO/IEC 27001 y el control A09 del OWASP Top 10 2021 (Security Logging and Monitoring Failures), la correcta identificación de los usuarios es fundamental para garantizar registros confiables, análisis forense y control interno. Sin esta atribución clara, se debilita la gobernanza de seguridad y aumenta el riesgo de suplantación o manipulación no detectada.
Cifrado Asimétrico: En el caso de usar SSH, ¿cuál es la diferencia funcional entre la llave privada y la pública? ¿Qué pasaría si un tercero obtiene acceso a tu llave privada?
RTA: En el uso de SSH, la clave pública y la clave privada cumplen funciones complementarias: la clave pública se comparte y se registra en los servidores o servicios para identificar al usuario, mientras que la clave privada permanece protegida y se utiliza para firmar criptográficamente la autenticación. El servidor valida esa firma usando la clave pública, sin que la clave privada se transmita en ningún momento. Si un tercero obtiene acceso a la clave privada, puede suplantar completamente la identidad del usuario, acceder a sistemas, repositorios o servidores y realizar acciones en su nombre. Esto compromete la confidencialidad, la integridad y el principio de no repudio, y representa una violación a las buenas prácticas de autenticación fuerte exigidas por estándares como ISO/IEC 27001 y lineamientos de OWASP.
Principio de Mínimo Privilegio: Si decides usar un Token de Acceso Personal (PAT), ¿qué riesgos conlleva asignarle permisos de "Administrador" (Full Control) en lugar de solo permisos de "Lectura/Escritura"?
RTA: Asignar permisos de “Administrador” (Full Control) a un Token de Acceso Personal incrementa significativamente el riesgo porque amplía el impacto en caso de filtración o compromiso. Un token con control total no solo permite leer o modificar código, sino también eliminar repositorios, cambiar configuraciones de seguridad, gestionar usuarios o alterar pipelines de despliegue. Esto rompe el principio de mínimo privilegio y la segregación de funciones, aumentando la superficie de ataque y el daño potencial. Desde la perspectiva de gobierno de acceso y estándares como ISO/IEC 27001, los permisos deben limitarse estrictamente a lo necesario para la función específica, reduciendo así la probabilidad y el impacto de accesos indebidos.
Higiene del Repositorio: ¿Para qué sirve el archivo. gitignore desde una perspectiva de seguridad? (Menciona al menos dos tipos de archivos que nunca deberían subirse al repositorio remoto).
RTA: El archivo .gitignore permite excluir del control de versiones archivos que no deben publicarse en el repositorio remoto, especialmente aquellos que pueden contener información sensible. Desde una perspectiva de seguridad, su función principal es prevenir la exposición accidental de credenciales, configuraciones internas o datos del entorno local. Nunca deberían subirse archivos como .env, que suelen contener claves y variables de entorno, ni llaves privadas como id_rsa o archivos .pem, ya que su filtración podría permitir accesos no autorizados. Implementar correctamente el .gitignore reduce el riesgo de fuga de secretos y fortalece la higiene del repositorio dentro de buenas prácticas de desarrollo seguro.
Exposición de Secretos: Si accidentalmente subes una llave de API o una contraseña al repositorio en GitHub, ¿es suficiente con borrarla y hacer un nuevo commit? Justifica tu respuesta.
RTA: No, no es suficiente con borrar el archivo y hacer un nuevo commit. En Git, el historial es inmutable, por lo que la llave o contraseña seguirá existiendo en commits anteriores y podrá ser recuperada. Además, si el repositorio es público, bots automatizados pueden detectar y explotar secretos expuestos en cuestión de minutos. La acción correcta es revocar o rotar inmediatamente la credencial comprometida y luego limpiar el historial del repositorio antes de continuar. Desde una perspectiva de seguridad, asumir que el secreto ya fue comprometido es la única postura responsable.
