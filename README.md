# Sistema Hotelero
Este proyecto consiste en el desarrollo de una solución integral para la gestión de servicios hoteleros, permitiendo la administración eficiente de reservaciones, huéspedes y disponibilidad de habitaciones.

 Equipo de Desarrollo y Responsabilidades
A continuación se detalla la contribución y las tareas específicas que cada integrante ha realizado hasta el momento:

👥 Trabajo Grupal — Equipo Completo
HU-01. Estructura de carpetas de la base de datos
Integrantes participantes:
Karen Holguín
Valery Sinaí
José Amaya
Johan Acero
Descripción:

Como equipo, se organizó la estructura de carpetas de la base de datos con el objetivo de separar migraciones, semillas, consultas de prueba y documentación técnica, permitiendo que cualquier integrante pudiera ubicar y ejecutar los archivos SQL sin confusiones.

Actividades realizadas
Creación de las carpetas:
01_ddl/
02_dml/
05_rollbacks/
Organización de subcarpetas internas para migraciones y documentación.
Configuración de archivos 0000changelog.yaml en cada dominio.
Definición de convenciones de nombres para:
Migraciones SQL.
Rollbacks SQL.
Configuración de changelog-master.yaml.
Actualización del README.md con instrucciones de ejecución.
Configuración de docker-compose.yml y .env.example.
Validación grupal del levantamiento de la base de datos usando Docker Compose.

👩‍💻 José Amaya
HU-02. Subir dominio de seguridad
Descripción

Se encargó de subir y estructurar el script DDL correspondiente al dominio de seguridad del sistema, permitiendo versionar y ejecutar correctamente las tablas relacionadas con usuarios, roles, permisos y módulos mediante Liquibase en el ambiente compartido.

Actividades realizadas
Creación del archivo:
01_ddl/03_tables/001-create-domain-security.sql
Desarrollo de las tablas:
persona
rol_aplicacion
permiso
modulo
vista_aplicacion
usuario_aplicacion
usuario_rol
rol_permiso
modulo_vista
Configuración de identificadores UUID usando:
DEFAULT gen_random_uuid()
Implementación de campos de auditoría en cada tabla:
created_by
created_at
updated_by
updated_at
deleted_by
deleted_at
status
Registro de la migración en:
01_ddl/03_tables/0000changelog.yaml
Validación de ejecución correcta de la migración desde cero usando Liquibase.
Revisión y preparación del Pull Request para aprobación antes del merge.

👨‍💻 Johan Acero
HU-03. Subir dominio de parametrización
Descripción

Se encargó de desarrollar y subir el script DDL correspondiente al dominio de parametrización del sistema, permitiendo versionar y ejecutar las tablas relacionadas con clientes, empresas, empleados, métodos de pago y configuraciones generales dentro del ambiente compartido.

Actividades realizadas
Creación del archivo:
01_ddl/03_tables/002-create-domain-parameterization.sql
Desarrollo de las tablas:
cliente
empresa
tipo_dia
metodo_pago
informacion_legal
empleado
Configuración de relaciones entre tablas mediante claves foráneas (FK).
Implementación de relación entre:
empleado → persona
usando FK y restricción:
UNIQUE (person_id)
Configuración de restricciones únicas:
cliente
UNIQUE (document_type, document_number)
UNIQUE (email)
empresa
UNIQUE (tax_id)
Implementación de tipos de datos monetarios usando:
NUMERIC(12,2)
Registro de la migración en:
01_ddl/03_tables/0000changelog.yaml
Validación de ejecución correcta después del dominio de seguridad.
Preparación y revisión del Pull Request antes del merge a la rama principal.











👨‍💻 José Amaya
Rol: Desarrollo de Lógica de Negocio y Backend

Gestión de Habitaciones: Desarrolló la lógica para la asignación y cambio de estado (disponible/ocupada) de las habitaciones.

Seguridad: Implementó los módulos de autenticación y validación de usuarios.

Integración de API: Responsable de conectar los servicios del servidor con la interfaz de usuario.

👨‍💻 Johan Acero
Rol: Arquitectura de Datos y Control de Flujo

Diseño de Base de Datos: Creó el modelo entidad-relación para gestionar huéspedes, reservas y pagos.

Consultas y Optimización: Desarrolló los procedimientos para la búsqueda rápida de disponibilidad por fechas.

Reportes: Implementó la generación de informes básicos de ocupación hotelera.

👩‍💻 Karen Holguín
Rol: Gestión de Procesos y Calidad

Módulo de Reservas: Desarrolló el flujo completo desde la selección de habitación hasta la confirmación de la estancia.

Pruebas de Usuario: Encargada de identificar errores en los procesos de registro y asegurar la calidad del software.

Gestión de Trello: Mantiene la organización de las tarjetas y el seguimiento de los "Sprints" en el tablero del proyecto.

# Estado Actual del Proyecto
Actualmente, el equipo ha completado las siguientes fases:

Definición de Requerimientos: Documentación de todas las necesidades del hotel.

Arquitectura de Datos: Base de datos estructurada y funcional.

Módulos Base: Registro de usuarios y gestión de inventario de habitaciones terminados. 
