# LABORATORIO AWS ALMACENAMIENTO (AMAZON S3)

## Como entrar al Laboratorio

1- Ingresa a tu cuenta de AWS

2- Selecciona el siguiente curso `Gettin Started with Storage (Lab)`

![imagen](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/5547bb39-174a-453b-aac6-089bde45d5c2)


3- Haz click en el botón de contenidos

![imagen](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/13444fee-022b-4ce3-b41d-9846e9950a1e)


4- Haz click en `` Introducción al almacenamiento ``

![imagen](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/d11bbe34-a7df-4bb0-a942-609497201aa4)


5- Haz click en `` Cargar Introducción al almacenamiento en una ventana nueva ``

![imagen](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/7108216a-fa08-478b-ba0c-8b742fd29a9a)


6- Después de leer las instrucciones haz click en ` Start Lab ` o `Iniciar Laboratorio`

![imagen](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/ae25493e-866e-4249-bf13-3b25dda94386)

7- Haz click en `Open Console` o `Abrir Consola` que te redireccionará a una página con la simulación de una consola de AWS para realizar el laboratorio

## Objetivos de este Laboratorio

En este laboratorio, usará algunas de las funciones de Amazon Simple Storage Service (Amazon S3) que acaba de aprender para crear un sitio web estático.

Los sitios web estáticos pueden contener páginas HTML, imágenes, hojas de estilo y todos los archivos que se necesitan para renderizar un sitio web. Los sitios web estáticos no utilizan scripting del lado del servidor ni bases de datos. Sin embargo, pueden contener scripts del lado del cliente que se ejecutan en el navegador web de un usuario.

Puede alojar un sitio web estático en Amazon S3 cargando el contenido y haciéndolo legible para los usuarios. No se requieren servidores. Puede usar Amazon S3 para almacenar y recuperar cualquier cantidad de datos en cualquier momento, desde cualquier parte de la Web.

OBJETIVOS
Después de completar este laboratorio, sabrá cómo realizar lo siguiente:

  - Crear un bucket en Amazon S3.
  - Configurar un bucket para alojar un sitio web estático.
  - Cargar contenido en un bucket.
  - Activar el acceso público a objetos de bucket.
  - Compartir de forma segura un objeto de bucket mediante el uso de una URL prefirmada.
  - Proteger un bucket mediante el uso de una política de bucket.
  - Actualizar el sitio web.
  - Ver versiones de objetos en la consola de Amazon S3.

## Actividades del laboratorio

### Tarea 1: Creando un Bucket en Amazon S3 }

1- En la Consola de administración de AWS, en el menú Services (Servicios), elija S3

2- Elija Create bucket (Crear bucket). Para este laboratorio, utilizará un nombre de bucket que incluya un número aleatorio, como website-123

  El nombre de un bucket de S3 es único a nivel global, y todas las cuentas de AWS comparten el espacio de nombres. 
  Luego de haber creado un bucket, ninguna otra cuenta en ninguna de las regiones de AWS puede utilizar el nombre de ese bucket a menos que lo elimine.


3- En Bucket name (Nombre del bucket), escriba ``website-<123>`` y reemplace ``<123>`` por un número aleatorio

4- En Object Ownership (Propiedad del objeto), elija ACLs enabled (ACL habilitadas)

5- Elija Bucket owner preferred (Propietario preferido del bucket)

6- En Block Public Access settings for this bucket (Configuración de bloqueo del acceso público para este bucket), desmarque la casilla Block all public access (Bloquear todo el acceso público) y, luego, seleccione la casilla que indica I acknowledge that the current settings might result in this bucket and the objects within becoming public. (Reconozco que la configuración actual puede dar lugar a que este bucket y los objetos dentro de él se vuelvan públicos)

7- En Bucket Versioning (Control de versiones en buckets), seleccione Enable (Habilitar)

8- En Tags (Etiquetas) seleccione Add tag (Agregar etiqueta) y escriba lo siguiente:

  A- Key (Clave): ``Department``

  B- Value (Valor): ``Marketing`` Puede utilizar etiquetas para agregar información adicional a un bucket, como un código de proyecto, un centro de costos o un propietario.

9- Elija Create bucket (Crear bucket)

10- En la sección Buckets elija el nombre de su nuevo bucket

11- Elija la pestaña Properties (Propiedades)

### Tarea 2: Configurando un sitio web estático en Amazon S3



### Tarea 3: Subiendo contenido en tu Bucket



### Tarea 4: Activando el acceso público a los objetos



### Tarea 5: Compartir un objeto de manera segura usando una URL prediseñada



### Tarea 6: Usar una Poliza de Seguridad en tu Bucket



### Tarea 7: Actualiza el sitio web



### Tarea 8: Explora las versiones de los archivos


