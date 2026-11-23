# Uso de las plantillas de CI

Las plantillas son puntos de partida. La validación genérica sirve para cualquier tecnología; las de Node y PHP indican los requisitos de cada entorno. Todas fallan deliberadamente hasta que se configure el proyecto. Su presencia no acredita que se hayan probado en una aplicación concreta.

## Adaptación

1. En la pestaña Actions del repositorio, elige la plantilla de la organización y pulsa Configure. Revisa la rama objetivo: la predeterminada puede no coincidir con la rama de integración acordada.
2. Identifica versiones soportadas, lockfile, comandos de instalación, pruebas y build, y dependencias externas. Para PHP comprueba también extensiones y compatibilidad del lockfile; para Node identifica el gestor de paquetes adecuado.
3. Sustituye el paso que falla por checkout, configuración del runtime, instalación desde el lockfile y checks reales obligatorios. Revisa las acciones de terceros y fija sus versiones o SHA conforme a la política del proyecto. No conviertas pruebas obligatorias en pasos opcionales.
4. Abre una PR y comprueba los resultados de CI en el commit correspondiente. Documenta los pasos no ejecutados y las dependencias necesarias.

## Publicación y despliegue

Estas plantillas no publican imágenes ni despliegan. Para publicar un artefacto o desplegar, acuerda con el equipo de plataforma el contrato específico, permisos, evidencia y recuperación. El patrón OIDC permite usar credenciales temporales para AWS cuando la plataforma ha configurado un rol y las condiciones adecuadas. No copies claves de acceso estáticas ni añadas permisos de AWS al job de una PR por defecto.

Un ejemplo de ECS puede enseñar cómo construir y publicar una imagen, pero sus definiciones de tarea y despliegue son específicas de ECS. Las acciones que crean EKS o RDS pueden modificar infraestructura y deben evaluarse por sus responsables antes de su uso.
