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

👨‍💻 Johan Acero
HU-04. Subir dominio de distribución
Descripción

Se encargó de desarrollar y subir el script DDL correspondiente al dominio de distribución del sistema, permitiendo versionar y ejecutar las tablas relacionadas con sedes, habitaciones, estados y tarifas dentro del ambiente compartido.

Actividades realizadas
Creación del archivo:
01_ddl/03_tables/003-create-domain-distribution.sql
Desarrollo de las tablas:
sede
tipo_habitacion
estado_habitacion
habitacion
tarifa
Configuración de relaciones mediante claves foráneas (FK).
Implementación de relación:
sede → empresa
Configuración de restricciones:
UNIQUE (company_id, name) en sede
UNIQUE (branch_id, room_number) en habitacion
Implementación de validaciones:
CHECK (capacity > 0) en habitacion
CHECK (amount > 0) en tarifa
Configuración de referencias en:
tarifa → tipo_habitacion
tarifa → tipo_dia
Registro de la migración en:
01_ddl/03_tables/0000changelog.yaml
Validación de ejecución correcta después del dominio de parametrización.
Preparación y revisión del Pull Request antes del merge a la rama principal.

👨‍💻 Karen Holguín
HU-05. Subir dominio de inventario
Descripción

Se encargó de desarrollar y subir el script DDL correspondiente al dominio de inventario del sistema, permitiendo versionar y ejecutar las tablas relacionadas con proveedores, productos, servicios y movimientos de inventario dentro del ambiente compartido.

Actividades realizadas
Creación del archivo:
01_ddl/03_tables/004-create-domain-inventory.sql
Desarrollo de las tablas:
proveedor
producto
servicio
movimiento_producto
disponibilidad_inventario
Configuración de relaciones mediante claves foráneas (FK) hacia dominios anteriores:
Parametrización
Distribución
Implementación de campos de auditoría en todas las tablas:
created_by
created_at
updated_by
updated_at
deleted_by
deleted_at
status
Validación de integridad y relaciones del modelo de inventario.
Registro de la migración en:
01_ddl/03_tables/0000changelog.yaml
Validación de ejecución correcta después del dominio de distribución.
Preparación y revisión del Pull Request antes del merge a la rama principal.

👨‍💻 Valery Sinaí
HU-06. Subir dominio de prestación de servicio
Descripción

Se encargó de desarrollar y subir el script DDL correspondiente al dominio de prestación de servicio del sistema, permitiendo versionar y ejecutar las tablas relacionadas con reservas, estadías, check-in/check-out y consumos dentro del ambiente compartido.

Actividades realizadas
Creación del archivo:
01_ddl/03_tables/005-create-domain-service.sql
Desarrollo de las tablas:
reserva_habitacion
cancelacion_habitacion
disponibilidad_habitacion
catalogo_habitacion
estadia
check_in
check_out
venta_producto
venta_servicio
Configuración de relaciones mediante claves foráneas (FK) hacia los dominios:
Distribución
Parametrización
Inventario
Implementación de campos de auditoría en todas las tablas:
created_by
created_at
updated_by
updated_at
deleted_by
deleted_at
status
Validación de integridad y relaciones del dominio de prestación de servicio.
Registro de la migración en:
01_ddl/03_tables/0000changelog.yaml
Validación de ejecución correcta después del dominio de inventario.
Preparación y revisión del Pull Request antes del merge a la rama principal.








# Estado Actual del Proyecto
Actualmente, el equipo ha completado las siguientes fases:

Definición de Requerimientos: Documentación de todas las necesidades del hotel.

Arquitectura de Datos: Base de datos estructurada y funcional.

Módulos Base: Registro de usuarios y gestión de inventario de habitaciones terminados. 
