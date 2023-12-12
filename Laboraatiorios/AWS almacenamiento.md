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

  - Key (Clave): ``Department``

  - Value (Valor): ``Marketing`` Puede utilizar etiquetas para agregar información adicional a un bucket, como un código de proyecto, un centro de costos o un propietario.

9- Elija Create bucket (Crear bucket)

10- En la sección Buckets elija el nombre de su nuevo bucket

11- Elija la pestaña Properties (Propiedades)

### Tarea 2: Configurando un sitio web estático en Amazon S3

1- Desplácese hasta el panel Static website hosting (Alojamiento de sitios web estáticos)

2- Elija Edit (Editar)

3- Configure los siguientes ajustes:

  - En Static web hosting: (Alojamiento de sitios web estáticos), seleccione Enable (Habilitar)
  
  - En Hosting type: (Tipo de alojamiento), elija Host a static website (Alojar un sitio web estático)
  
  - En Index document (Documento de índice), ingrese `` index.html ``

  - En Error document (Documento de error), ingrese `` error.html ``

4- Elija Save changes (Guardar cambios)

5- En el cuadro Static website hosting (Alojamiento de sitios web estáticos) debajo de Bucket website endpoint (Punto de enlace del sitio web del bucket), elija el enlace

### Tarea 3: Subiendo contenido en tu Bucket

1- Haga clic con el botón secundario en cada uno de los siguientes enlaces y descargue los archivos en su equipo:

  - [index.html](https://us-west-2-tcprod.s3.us-west-2.amazonaws.com/courses/CUR-TF-100-EDSTOR/v1.0.2.prod-68c99051/01-lab-s3/instructions/assets/index.html)

  - [script.js](https://us-west-2-tcprod.s3.us-west-2.amazonaws.com/courses/CUR-TF-100-EDSTOR/v1.0.2.prod-68c99051/01-lab-s3/instructions/assets/script.js)

  - [style.css](https://us-west-2-tcprod.s3.us-west-2.amazonaws.com/courses/CUR-TF-100-EDSTOR/v1.0.2.prod-68c99051/01-lab-s3/instructions/assets/style.css)

2- Vuelva a la consola de Amazon S3 y elija la pestaña Objects (Objetos)

3- Elija Upload (Cargar)

4- Elija Add files (Agregar archivos)

5- Elija los tres archivos que descargó

6- Elija Upload (Cargar)

7- Elija Close (Cerrar)

### Tarea 4: Activando el acceso público a los objetos

1- Vuelva a la pestaña del navegador que muestra el mensaje 403 Forbidden (403 Prohibido)

2- Actualice la página web `crtl + r` . Si cerró accidentalmente esta pestaña, diríjase a la pestaña Properties (Propiedades) y, en el panel Static website hosting (Alojamiento de sitios web estáticos), vuelva a elegir el enlace Bucket website endpoint (Punto de enlace del sitio web del bucket).

Aún debería ver el mensaje 403 Forbidden (403 Prohibido). ¡Esta es la respuesta esperada! Este mensaje indica que Amazon S3 aloja su sitio web estático, pero que el contenido es privado.

Puede hacer públicos los objetos de Amazon S3 de dos maneras diferentes:

  - Para hacer público un bucket completo o un directorio específico dentro del bucket, utilice una política de bucket.

  - Puede utilizar una lista de control de acceso (ACL) para hacer públicos objetos individuales en un bucket. En general, es más seguro hacer públicos objetos individuales porque esto evita que otros objetos se hagan públicos por accidente. Sin embargo, si sabe que la totalidad del bucket no contiene información confidencial, puede utilizar una política de bucket.

Ahora configurará los objetos individuales para que sean accesibles públicamente.

3- Mantenga abierta la pestaña del sitio web y vuelva a la pestaña del navegador web con la consola de Amazon S3

4- Seleccione los tres objetos

5- En el menú Actions (Acciones), elija Make public using ACL (Hacer público a través de ACL)

6- Elija Make public (Hacer público)

7- Elija Close (Cerrar)

8- Vuelva a la pestaña del navegador web que tiene el mensaje 403 Forbidden (403 Prohibido)

9- Actualice la página web `crtl + r` 

### Tarea 5: Compartir un objeto de manera segura usando una URL prediseñada

1- Haga clic con el botón secundario en el siguiente enlace y descargue los archivos en su equipo: Asegúrese de que el archivo mantenga su nombre, incluida la extensión

  - [new-report.png](https://us-west-2-tcprod.s3.us-west-2.amazonaws.com/courses/CUR-TF-100-EDSTOR/v1.0.2.prod-68c99051/01-lab-s3/instructions/assets/new-report.png)

2- Vuelva a la consola de Amazon S3 y elija la pestaña Objects (Objetos)

3- Elija Upload (Cargar)

4- Elija Add files (Agregar archivos)

5- Elija el archivo que descargó

6- Elija Upload (Cargar)

7- Elija Close (Cerrar)

8- En la pestaña Objects (Objetos), elija new-report.png

9- En el menú Actions (Acciones), seleccione Share with a presigned URL (Compartir mediante una URL prefirmada)

10- En la ventana emergente, configure Time interval until the presigned URL expires (Intervalo de tiempo hasta el vencimiento de la URL prefirmada). En este caso selecciona **minutos**

11- Elija Create presigned URL (Crear URL prefirmada)

12- En el anuncio de la parte superior de la página, seleccione Copy presigned URL (Copiar URL prefirmada)

13- Abra una nueva pestaña del navegador y pegue la URL en la barra de direcciones. Si espera el tiempo que hayas predefinido y usa el enlace nuevamente, descubrirá que venció la URL y ya no funciona.


### Tarea 6: Usar una política de bucket para proteger el bucket

1- Vuelva a la consola de Amazon S3 y elija la pestaña Permissions (Permisos)

2- En Bucket policy (Política de bucket), seleccione Edit (Editar)

3- Copie el siguiente texto de la política. En el editor de texto Policy (Política), reemplace el texto de la política existente por este:

    {
	    "Version": "2012-10-17",
	    "Id": "MyBucketPolicy",
	    "Statement": [
		    {
			    "Sid": "BucketPutDelete",
			    "Effect": "Deny",
			    "Principal": "*",
			    "Action": "s3:DeleteObject",
			    "Resource": [
				    "arn:aws:s3:::<bucket-name>/index.html",
				    "arn:aws:s3:::<bucket-name>/script.js",
				    "arn:aws:s3:::<bucket-name>/style.css"
            ]
		    }
	    ]
    }

Esta política impide que cualquier persona elimine los tres archivos que hacen funcionar su sitio web.

4- Luego, actualice el texto en el editor de políticas. En las siguientes líneas de código en el editor de políticas, reemplace los <bucket-name> marcadores de posición por el nombre de su bucket.

    "arn:aws:s3:::<bucket-name>/index.html",
    "arn:aws:s3:::<bucket-name>/script.js",
    "arn:aws:s3:::<bucket-name>/style.css"

Su código actualizado debe verse parecido a lo siguiente:

    "arn:aws:s3:::website-1234/index.html",
    "arn:aws:s3:::website-1234/script.js",
    "arn:aws:s3:::website-1234/style.css"


5- Elija Save changes (Guardar cambios)

6- Vuelva a la pestaña Object (Objeto)

7- Elija **index.html**

8- Elija Delete (Eliminar)

9- En el panel Delete objects (Eliminar objetos), ingrese ``delete`` para confirmar que desea eliminar este archivo

10- Elija Delete objects (Eliminar objetos)

11- Observe que el archivo index.html aparece en el panel Failed to delete (Error al eliminar). Esto confirma que la política funciona y que impide la eliminación de los archivos del sitio web.

12- Elija Close (Cerrar) para volver a la pestaña Objects (Objetos)

### Tarea 7: Actualiza el sitio web

Aunque configuró una política para impedir la eliminación de archivos del sitio web, de todas maneras puede actualizar el sitio web editando el archivo HTML y cargándolo en el bucket de S3 nuevamente.

Amazon S3 es un servicio de almacenamiento de objetos, por lo que debe cargar el archivo completo. Esta acción reemplazará al objeto existente en el bucket. No es posible editar el contenido de un objeto, debe reemplazarlo por completo.

1- En su equipo, cargue el archivo index.html en un editor de texto (por ejemplo, Bloc de notas o TextEdit)

2- Busque el texto Served from Amazon S3 (Entregado desde Amazon S3) y sustitúyalo por ``Created by <YOUR-NAME>`` y reemplace por su nombre ``<YOUR-NAME>`` (por ejemplo, Creado por **Esteban** ).

3- Guarde el archivo

4- Vuelva a la consola de Amazon S3 y cargue el archivo index.html que acaba de editar

5- Elija index.html y el menú Actions (Acciones), elija otra vez la opción Make public using ACL (Hacer público a través de ACL)

6- Elija Make public (Hacer público)

7- Regrese a la pestaña del navegador web con el sitio web estático y actualice la página

### Tarea 8: Explora las versiones de los archivos

El control de versiones en buckets está desactivado de forma predeterminada. Cuando está desactivado el control de versiones, no se pueden deshacer los cambios a los objetos. Por ejemplo, si carga una nueva versión de un archivo, el archivo antiguo es reemplazado por el nuevo. Se pierde el archivo original. Si elimina un archivo, se elimina de forma permanente y no puede recuperarlo.

Sin embargo, cuando esté activado el control de versiones, se guardan las versiones modificadas y eliminadas de los archivos. No se presentan las versiones anteriores de los objetos de forma predeterminada, pero puede acceder a ellas mediante la consola o con programación. Ya que conserva versiones anteriores de los objetos, puede recuperarlos si lo necesita.

 Es importante recordar que una vez que activa el control de versiones, no puede desactivarlo. Sin embargo, puede suspenderlo. Para obtener más información sobre el control de versiones en buckets, consulte la [Guía del usuario de Amazon Simple Storage Service](https://docs.aws.amazon.com/AmazonS3/latest/userguide/Versioning.html) .

Recuerde que cuando creó el bucket, activó el control de versiones. En esta tarea, verá las versiones del objeto disponibles en su bucket.

1- Vuelva a la consola de Amazon S3 y elija la pestaña Objects (Objetos)

2- Elija **Show versions** (Mostrar versiones) para activar el control de versiones en buckets

3- Revise la lista de objetos en el bucket}

*Imagen de ejemplo de AWS*

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/bca816c2-def9-4531-81f4-e78483613b34)

*Imagen de mi procedimiento*


  - Observe que cada archivo tiene un ID de versión. Estos ID son generados automáticamente por Amazon S3 cuando se activa el control de versiones
   
  - También debe encontrar dos versiones del archivo index.html porque cargó una nueva versión del archivo. La versión actual es el archivo que cargó cuando actualizó su sitio web
