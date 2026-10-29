#!!IMPORTANTE!!
##Para el funcionamiento del proyecto se debe considerar lo siguiente:

**Debido a conflictos entre Next y Jasmine se debe cambiar el nombre de babel.config.json a babel.config.json.bak para que la página funcione y cargue y para las pruebas se debe revertir el nombre del archivo a babel.config.json**

Esto fue extensivamente intentado de arreglar para que se pudieran ejecutar ambas la página y las pruebas al mismo tiempo pero no lo logré y por tiempo dejaré esta solución parche.

# Kiwi Ayuda

Plataforma web de apoyo a la adopción de mascotas, desarrollada con Next.js y React. El proyecto utiliza datos simulados en el navegador para gestionar mascotas, usuarios y solicitudes de adopción.

> **Estado del proyecto:** versión demostrativa. Actualmente no cuenta con backend funcional; la autenticación y la persistencia de datos se simulan en el frontend mediante localStorage.

## Tecnologías utilizadas

- **Next.js** y **React:** framework y biblioteca respectivamente para el desarrollo de la aplicación web.
- **JavaScript:** lógica de la aplicación.
- **Bootstrap 5:** estilos y diseño adaptable.
- **Bootstrap Icons:** iconografía de la interfaz.
- **Chart.js:** creación de gráficos para dashboard administrador.
- **Jasmine:** framework para las pruebas automatizadas.
- **Karma:** ejecución de pruebas en el navegador Firefox.
- **Babel y Webpack:** procesamiento de los archivos JSX utilizados en las pruebas.
- **ESLint:** herramienta para revisión de código.

## Funcionalidades

### 1. Gestión de mascotas

El módulo de datos de mascotas permite:

- Consultar las mascotas registradas.
- Agregar nuevas mascotas.
- Actualizar la información de una mascota.
- Eliminar mascotas.
- Guardar los cambios en localStorage para conservar la información en el navegador.

### 2. Usuarios y autenticación simulada

El sistema de usuarios y autenticación contempla:

- Registro de usuarios con nombres, apellidos, RUT, teléfono, correo electrónico y contraseña.
- Validación del formato y del dígito verificador del RUT chileno.
- Comprobación de correos electrónicos y RUT duplicados durante el registro.
- Inicio de sesión mediante correo electrónico y contraseña.
- Validación de coincidencia de contraseñas y una longitud mínima de seis caracteres durante el registro.
- Inicio de sesión automático después de registrar una cuenta.
- Gestión de sesiones mediante localStorage.
- Definición de roles para administrador, usuario e invitado.

### 3. Solicitudes de adopción

El módulo de solicitudes permite:

- Consultar las solicitudes registradas.
- Registrar nuevas solicitudes.
- Asignar un identificador, fecha y estado inicial Pendiente a cada nueva solicitud.
- Actualizar el estado de una solicitud.
- Eliminar solicitudes.
- Guardar los cambios en localStorage.

### 4. Panel de administración

El dashboard presenta un resumen de la actividad de Kiwi Ayuda mediante indicadores que muestran:

- Cantidad total de mascotas registradas.
- Cantidad de mascotas disponibles para adopción.
- Cantidad total de solicitudes.
- Cantidad de solicitudes pendientes de revisión.
- Cantidad de solicitudes aprobadas.

Además, incluye accesos a las secciones de mascotas, solicitudes, usuarios, reportes y a la página principal.

La disponibilidad de cada funcionalidad depende de la implementación de su respectiva sección.

### 5. Interfaz de usuario

La aplicación utiliza componentes React y clases de Bootstrap para construir su interfaz.

Entre las funcionalidades de interfaz identificadas se encuentran:

- Modal de inicio de sesión y registro.
- Alternancia entre el formulario de inicio de sesión y el de registro.
- Mensajes de error para informar problemas durante la autenticación o el registro.
- Formularios con campos controlados mediante el estado de React.
- Tarjetas de resumen y accesos directos en el panel administrativo.

El diseño adaptable depende de cada página. El panel administrativo está pensado para uso de escritorio.

## Estructura del proyecto

La siguiente estructura resume las carpetas principales del proyecto:

```text
kiwi-ayuda-next/
├── app/
│   ├── admin/
│   ├── blogs/
│   ├── contacto/
│   ├── mascotas/
│   ├── nosotros/
│   ├── solicitudes/
│   ├── globals.css
│   └── layout.jsx
├── components/
├── context/
│   └── AuthContext.jsx
├── data/
│   ├── mascotas.js
│   ├── usuarios.js
│   └── solicitudes.js
├── public/
│   └── img/
├── spec/
│   ├── karma/
│   └── support/
├── babel.config.json
├── karma.conf.cjs
└── package.json
```

Esta es una representación resumida de la estructura compartida durante la documentación. El proyecto puede contener otros archivos y subcarpetas.

## Requisitos previos

Para ejecutar el proyecto se necesita:

- Node.js.
- npm.
- Mozilla Firefox para ejecutar las pruebas configuradas con Karma.

Las dependencias y sus versiones se encuentran declaradas en `package.json`.

## Instalación y ejecución

### 1. Clonar el repositorio

Reemplaza la URL de ejemplo por la dirección del repositorio de GitHub:

```bash
git clone <URL_DEL_REPOSITORIO>
```

### 2. Entrar a la carpeta del proyecto

```bash
cd kiwi-ayuda-next
```

### 3. Instalar las dependencias

```bash
npm.cmd install
```

### 4. Iniciar el servidor de desarrollo

```bash
npm.cmd run dev
```

### 5. Abrir la aplicación

Abre en el navegador la dirección local que indique Next.js en la terminal. Normalmente es:

```text
http://localhost:3000
```

## Comandos disponibles

| Comando | Descripción |
|---|---|
| `npm.cmd run dev` | Inicia el servidor de desarrollo de Next.js. |
| `npm.cmd run build` | Genera la compilación de producción. |
| `npm.cmd start` | Inicia la aplicación compilada, normalmente después de ejecutar `npm run build`. |
| `npm.cmd run lint` | Ejecuta ESLint para revisar el código. |
| `npm.cmd test` | Ejecuta el comando Jasmine definido en `package.json`. |
| `npm.cmd run test:karma` | Ejecuta Karma utilizando la configuración `karma.conf.cjs` y Firefox. |

## Pruebas automatizadas

###Dentro de este repositorio se puede encontrar el documento de Cobertura de Pruebas(CoberturaTesting_IvanGonzalez008D.docx)

El proyecto utiliza Jasmine para las pruebas y Karma como ejecutor en el navegador.

La configuración de Karma procesa los archivos de prueba JSX ubicados en `spec/karma/` que coincidan con el patrón `**/*.spec.jsx`.

Las herramientas configuradas son:

- **Jasmine:** framework de pruebas.
- **Karma:** ejecución de las pruebas.
- **Webpack:** procesamiento de los archivos de prueba.
- **Babel:** transformación de JavaScript y JSX mediante los presets configurados.
- **Firefox:** navegador utilizado para ejecutar las pruebas.
- **Ejecución única:** Karma está configurado con `singleRun: true`, por lo que ejecuta las pruebas y finaliza.

Entre las pruebas compartidas durante el desarrollo se incluyen verificaciones de:

- Renderizado e interacción de componentes React.
- Visualización de información de mascotas.
- Validación del RUT.
- Flujo del formulario de solicitud de adopción.
- Operaciones CRUD del módulo de mascotas.
- Elementos básicos de la interfaz.

Para ejecutar las pruebas mediante Karma:

```bash
npm.cmd run test:karma
```

Es necesario tener Firefox instalado. Se recomienda ejecutar los comandos en el entorno local para comprobar los resultados actuales de las pruebas.

## Persistencia y alcance de la simulación

Los módulos de datos utilizan localStorage para guardar información en el navegador. Esto permite conservar los registros entre recargas dentro del mismo navegador, pero no equivale a una base de datos compartida entre usuarios o dispositivos.

Como el proyecto no cuenta actualmente con backend:

- Las credenciales no se validan en un servidor.
- Los datos almacenados en el navegador pueden ser inspeccionados o modificados por quien lo utiliza.
- La autenticación y la persistencia forman parte de una simulación académica.
- La aplicación no debe considerarse una solución de producción para gestionar información sensible.

## Consideraciones antes de publicar en GitHub

Antes de publicar el repositorio, se recomienda:

- Verificar que no se incluyan archivos `.env`, tokens, contraseñas reales ni otros secretos.
- Revisar la cuenta administradora de prueba definida en el código del módulo de usuarios, ya que sus credenciales son visibles en el repositorio.
- Evitar el uso de información personal real durante las pruebas.
- Comprobar que el archivo `.gitignore` excluya los archivos generados y la información local que no corresponda publicar.

## Posibles mejoras futuras

Las siguientes son ideas para una evolución posterior y no se presentan como funcionalidades actualmente implementadas:

- Incorporar un backend y una base de datos.
- Implementar autenticación y autorización del lado del servidor.
- Almacenar contraseñas de forma segura en el backend.
- Ampliar la documentación de las pruebas automatizadas.
- Registrar los resultados de ejecución y la cobertura de las pruebas.

## Autoría

Proyecto académico desarrollado en el contexto de estudios en DUOC UC.

---

**Kiwi Ayuda** — proyecto demostrativo para apoyar la gestión de adopciones de mascotas.
