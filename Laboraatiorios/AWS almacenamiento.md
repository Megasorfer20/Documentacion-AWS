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

7- Haz click en `Open Console` o `Abrir la Consola` que te redireccionará a una página con la simulación de una consola de AWS para realizar el laboratorio

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/0649fdac-d42b-4a25-9b38-875d3f400790)


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

### Tarea 1: Creando un Bucket en Amazon S3

1- En la Consola de administración de AWS, en el menú Services (Servicios), elija S3

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/23184292-e965-459d-92a2-825ca3089e9f)

2- Elija Create bucket (Crear bucket). Para este laboratorio, utilizará un nombre de bucket que incluya un número aleatorio, como website-123

  El nombre de un bucket de S3 es único a nivel global, y todas las cuentas de AWS comparten el espacio de nombres. 
  Luego de haber creado un bucket, ninguna otra cuenta en ninguna de las regiones de AWS puede utilizar el nombre de ese bucket a menos que lo elimine.

  ![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/caa82289-40cb-4534-b356-f8ac84911203)

3- En Bucket name (Nombre del bucket), escriba ``website-<123>`` y reemplace ``<123>`` por un número aleatorio

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/1823bb3f-fd7e-4fc4-a010-afe7aee6ea5c)


4- En Object Ownership (Propiedad del objeto), elija ACLs enabled (ACL habilitadas)

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/5780f291-3c21-4de9-b9a9-efe7e1abb187)


5- Elija Bucket owner preferred (Propietario preferido del bucket)

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/db197442-ee77-48a0-a893-91a2049695c0)


6- En Block Public Access settings for this bucket (Configuración de bloqueo del acceso público para este bucket), desmarque la casilla Block all public access (Bloquear todo el acceso público) y, luego, seleccione la casilla que indica I acknowledge that the current settings might result in this bucket and the objects within becoming public. (Reconozco que la configuración actual puede dar lugar a que este bucket y los objetos dentro de él se vuelvan públicos)

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/4be0446d-961d-435f-9718-fcc7e8977a8c)


7- En Bucket Versioning (Control de versiones en buckets), seleccione Enable (Habilitar)

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/64d670fb-8e04-4fa5-8661-27b5e37149bf)


8- En Tags (Etiquetas) seleccione Add tag (Agregar etiqueta) y escriba lo siguiente:

  - Key (Clave): ``Department``

  - Value (Valor): ``Marketing`` Puede utilizar etiquetas para agregar información adicional a un bucket, como un código de proyecto, un centro de costos o un propietario.

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/b39da004-de09-4973-9003-38568ffc79e0)


9- Elija Create bucket (Crear bucket)

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/41ff4d4c-a9a4-4e3b-9b91-5837c1bdb0f0)


10- En la sección Buckets elija el nombre de su nuevo bucket

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/3788daee-7873-48d9-83fc-a2752c286561)


11- Elija la pestaña Properties (Propiedades)

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/7d91ac7b-1321-4f1e-97ac-dfbdb74bbf53)


### Tarea 2: Configurando un sitio web estático en Amazon S3

1- Desplácese hasta el panel Static website hosting (Alojamiento de sitios web estáticos)

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/7fd84ee4-38aa-4c39-966a-2eb13fb35932)


2- Elija Edit (Editar)

<img width="668" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/92379439-c458-46cf-a82e-fa15badb74fe">


3- Configure los siguientes ajustes:

  - En Static web hosting: (Alojamiento de sitios web estáticos), seleccione Enable (Habilitar)

    ![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/30aa4963-729f-4820-86c3-c3ae3c3f5f3c)

  
  - En Hosting type: (Tipo de alojamiento), elija Host a static website (Alojar un sitio web estático)

    ![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/62e52a7c-5024-46ef-bd2a-3a00eca7c56e)

  
  - En Index document (Documento de índice), ingrese `` index.html ``

  - En Error document (Documento de error), ingrese `` error.html ``

    <img width="458" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/34551112-4f20-492c-a1e6-9bb2ae09764d">


4- Elija Save changes (Guardar cambios)

<img width="631" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/c5128418-c131-4b5a-a130-871b0bc8a762">


5- En el cuadro Static website hosting (Alojamiento de sitios web estáticos) debajo de Bucket website endpoint (Punto de enlace del sitio web del bucket), elija el enlace.

Recibirá un mensaje 403 Forbidden (403 Prohibido) debido a que aún no ha configurado los permisos del bucket. Mantenga esta pestaña abierta en su navegador web para que pueda regresar a ella más tarde.

Ha configurado el bucket para alojar un sitio web estático.

<img width="958" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/a4777851-6a71-41aa-ba70-c3c16737b619">



### Tarea 3: Subiendo contenido en tu Bucket

1- Haga clic con el botón secundario en cada uno de los siguientes enlaces y descargue los archivos en su equipo:

  - [index.html](https://us-west-2-tcprod.s3.us-west-2.amazonaws.com/courses/CUR-TF-100-EDSTOR/v1.0.2.prod-68c99051/01-lab-s3/instructions/assets/index.html)

  - [script.js](https://us-west-2-tcprod.s3.us-west-2.amazonaws.com/courses/CUR-TF-100-EDSTOR/v1.0.2.prod-68c99051/01-lab-s3/instructions/assets/script.js)

  - [style.css](https://us-west-2-tcprod.s3.us-west-2.amazonaws.com/courses/CUR-TF-100-EDSTOR/v1.0.2.prod-68c99051/01-lab-s3/instructions/assets/style.css)

    <img width="415" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/77e3be7a-49a8-4529-af68-76190838c4fa">


2- Vuelva a la consola de Amazon S3 y elija la pestaña Objects (Objetos)

<img width="687" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/e70e7a0a-725f-4847-b060-36b6420f3905">


3- Elija Upload (Cargar)

<img width="675" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/6b05caf2-ed52-4d6c-a365-44a905f1757f">


4- Elija Add files (Agregar archivos)

<img width="643" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/5cdea961-6afe-4d5b-88ae-ebfb65f1f60f">


5- Elija los tres archivos que descargó

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/ddc3ce32-4694-4f41-8cd9-4d8336c8eec7)


6- Elija Upload (Cargar)

<img width="653" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/6445fb2a-7330-4ec0-a919-036eb353576a">


7- Elija Close (Cerrar)

<img width="897" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/3a1f1963-2398-4a3b-87d8-742fba9e170e">


### Tarea 4: Activando el acceso público a los objetos

1- Vuelva a la pestaña del navegador que muestra el mensaje 403 Forbidden (403 Prohibido)

<img width="958" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/b1e9cfdb-8e3d-4966-9278-bbf99ad14b27">


2- Actualice la página web `crtl + r` . Si cerró accidentalmente esta pestaña, diríjase a la pestaña Properties (Propiedades) y, en el panel Static website hosting (Alojamiento de sitios web estáticos), vuelva a elegir el enlace Bucket website endpoint (Punto de enlace del sitio web del bucket).

Aún debería ver el mensaje 403 Forbidden (403 Prohibido). ¡Esta es la respuesta esperada! Este mensaje indica que Amazon S3 aloja su sitio web estático, pero que el contenido es privado.

Puede hacer públicos los objetos de Amazon S3 de dos maneras diferentes:

  - Para hacer público un bucket completo o un directorio específico dentro del bucket, utilice una política de bucket.

  - Puede utilizar una lista de control de acceso (ACL) para hacer públicos objetos individuales en un bucket. En general, es más seguro hacer públicos objetos individuales porque esto evita que otros objetos se hagan públicos por accidente. Sin embargo, si sabe que la totalidad del bucket no contiene información confidencial, puede utilizar una política de bucket.

Ahora configurará los objetos individuales para que sean accesibles públicamente.

3- Mantenga abierta la pestaña del sitio web y vuelva a la pestaña del navegador web con la consola de Amazon S3

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/1f83de45-9bcd-401b-8282-d5c510fe1ff6)


4- Seleccione los tres objetos


<img width="842" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/889bf620-15a1-413b-a748-1e705c3af43b">


5- En el menú Actions (Acciones), elija Make public using ACL (Hacer público a través de ACL)

<img width="848" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/7cad62b1-2968-4d42-8b07-ed25c9a29bfd">


6- Elija Make public (Hacer público)

<img width="628" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/42fa1116-f4b5-468d-9739-5d40be5ed367">


7- Elija Close (Cerrar)

<img width="882" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/57986830-a494-4fd3-9bed-1fc5ce9b971b">


8- Vuelva a la pestaña del navegador web que tiene el mensaje 403 Forbidden (403 Prohibido)

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/09d3f92f-21de-489f-aed8-1735851b1d96)


9- Actualice la página web `crtl + r` 

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/82426bae-4ef9-47c1-911c-966ecd8638c0)


### Tarea 5: Compartir un objeto de manera segura usando una URL prediseñada

1- Haga clic con el botón secundario en el siguiente enlace y descargue los archivos en su equipo: Asegúrese de que el archivo mantenga su nombre, incluida la extensión

  - [new-report.png](https://us-west-2-tcprod.s3.us-west-2.amazonaws.com/courses/CUR-TF-100-EDSTOR/v1.0.2.prod-68c99051/01-lab-s3/instructions/assets/new-report.png)

<img width="415" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/66d4f145-c487-48cc-9b09-590836078997">


2- Vuelva a la consola de Amazon S3 y elija la pestaña Objects (Objetos)

<img width="848" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/d580956e-026c-47ee-b3e9-514f917ef874">


3- Elija Upload (Cargar)

<img width="848" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/a4db2ef4-c779-4e3a-8304-25f376991887">


4- Elija Add files (Agregar archivos)

<img width="621" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/83e462da-c78a-4d11-82a7-827065edbb59">


5- Elija el archivo que descargó

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/5d9a34b4-8d60-49d1-9e10-ac99e7b87323)


6- Elija Upload (Cargar)

<img width="614" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/d76e7d40-357b-4aac-aa84-67bcade72101">


7- Elija Close (Cerrar)

<img width="884" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/1e5ab207-929b-4e7e-b2bc-2da5e931a3f1">


8- En la pestaña Objects (Objetos), elija new-report.png

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/ff4bbf99-5f70-4a16-b9d2-4d658b4f2108)


9- En el menú Actions (Acciones), seleccione Share with a presigned URL (Compartir mediante una URL prefirmada)

<img width="254" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/3dd22061-01a4-4bba-9548-83919310aad9">


10- En la ventana emergente, configure Time interval until the presigned URL expires (Intervalo de tiempo hasta el vencimiento de la URL prefirmada). En este caso selecciona **minutos**

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/3102c55f-9252-4b87-a6eb-28dd21b37a4e)


11- Elija Create presigned URL (Crear URL prefirmada)

<img width="446" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/7b767fa3-a307-4495-80a9-4df8c46d4afb">


12- En el anuncio de la parte superior de la página, seleccione Copy presigned URL (Copiar URL prefirmada)

<img width="887" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/60566886-8b6b-48bb-9e5f-ec91ebd56c83">


13- Abra una nueva pestaña del navegador y pegue la URL en la barra de direcciones. Si espera el tiempo que hayas predefinido y usa el enlace nuevamente, descubrirá que venció la URL y ya no funciona.

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/daef1f0e-e20b-4ec2-976b-d11cc82926eb)


		https://website-2011.s3.us-east-1.amazonaws.com/new-report.png?response-content-disposition=inline&X-Amz-Security-Token=IQoJb3JpZ2luX2VjELb%2F%2F%2F%2F%2F%2F%2F%2F%2F%2FwEaCXVzLWVhc3QtMSJIMEYCIQDw9gIsQxrFtUQp%2B%2Fw77FNWbTI9Qk6Ykvl4X%2BTlp7Q7gwIhANrtD6Mk3h1sqcNbBZ7bkaP2KNz7SsaVIoRpxzaARhwPKpcECC8QAxoMOTEwOTU0MTIxNzczIgyjNTwqq6l8u5hoWE4q9ANH81PmvaNZqrczixw5QQxIq65P93rZI48zusxvi4SUSRLSlsXfa%2Fgf3HH7XlYN2wRPlrmM%2FvAWCmbcRMi4UfdOMchs1Od2Vby56Kri6M1hSVJhOGTjXHEOViSVS2diC0aEY4OBhPXMCAkv7hMnUyIcX3i4f9ZNa1aH%2FFA4XrW9O4DNT2lW2f82RieloXJP3GVWVonIbnsrS0pd2pTWhbr%2B9Q2sKeNmqwJOFH34AUpNx95vI8v%2FjR1GSZQ8w0kceFAOzoOyq5BlpqLW1p9mBZDFBuRRtFBBipkh6PcBvrDsmT%2FJ53yQF8vcjx%2ByZttlkhbAW3%2B9b3JWGJOvY30gWooYw44vA6VTvchw0YqjODHKFOZEYbUaSguLNI%2FqxceugZMMkw%2BssOBUa00ZV80PV3DnhaBpusTWae721xdgCvQ9tEnE2EAvfnmTZFdYK%2FVpmigYdjQ6H5Z93p%2BWTz3eYrqvjlU5a7gn7RkGuF5On33wlneXSUuWCLEdm814PvnRaIah0vIE3sCqr%2BZ8m%2BEEgLAG4QPpRFlawxKF1KxqSldg00bscjWrViqIChh7EmMJfa%2B6vhJQuqYpVstvwUX9hGrMGACSz8bVmPCJPR5FVo1W0LhoEbBZbLb%2FknnUZcGu1aMi36VPU6vqGSmxFk7mc30s9mCiOTC1wOGrBjr4AdkQvvRtoWIrNYFUhldExQJElqA%2FgT%2F6%2F2MRXKDggDcQwCEchvWOKdA8PvHM2Ps6qfFo%2FOWdT5RcHNXgXxVU23HFZA2zYaVc%2B4S9Zq3Lfcnnm40nx1ctdNSyKz07rQc6FQ3D1WyavsFibcYqSLmpu4HWh417%2FGMOls0Pswpq9V2Rmujp5dwLHBPfQkF2k7620AlamiQv9CXkzLfc5nWfB12%2F6M4Vv88HfLrbuaZxKCcNnmoJCzD3fvXCP7iGOWSHGmz8o9QfB3dDOn%2BsCzmiN5XB2Uy0BlDsfK7gR3C4zW6%2BErNxHdp1OB%2F8NayQ7M4ejcD8eklHl28q&X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Date=20231212T140920Z&X-Amz-SignedHeaders=host&X-Amz-Expires=180&X-Amz-Credential=ASIA5IGIYZIW4SXHVMVI%2F20231212%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Signature=44c679e15727a8a354ba809c30787da2762ca8cd8dd6c10a7d4046b930f7fd19


### Tarea 6: Usar una política de bucket para proteger el bucket

1- Vuelva a la consola de Amazon S3 y elija la pestaña Permissions (Permisos)

<img width="877" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/98d3be86-5a4d-42e0-8f61-af52cb82250d">


2- En Bucket policy (Política de bucket), seleccione Edit (Editar)

<img width="829" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/04455fa7-f186-42dc-b988-7b93b9b885e3">


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

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/9d54545e-856d-4e5c-ae37-110675f08a10)


4- Luego, actualice el texto en el editor de políticas. En las siguientes líneas de código en el editor de políticas, reemplace los <bucket-name> marcadores de posición por el nombre de su bucket.

    "arn:aws:s3:::<bucket-name>/index.html",
    "arn:aws:s3:::<bucket-name>/script.js",
    "arn:aws:s3:::<bucket-name>/style.css"

Su código actualizado debe verse parecido a lo siguiente:

    "arn:aws:s3:::website-1234/index.html",
    "arn:aws:s3:::website-1234/script.js",
    "arn:aws:s3:::website-1234/style.css"

<img width="556" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/6c9588ae-9ef6-4a06-8f60-cb14ff063d4f">


5- Elija Save changes (Guardar cambios)

<img width="385" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/793f85bc-e14f-460a-a128-fcc0223eb622">


6- Vuelva a la pestaña Object (Objeto)

7- Elija **index.html**

8- Elija Delete (Eliminar)

<img width="849" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/24160fe6-c0da-4f1e-a9b4-5a97a781f6db">


9- En el panel Delete objects (Eliminar objetos), ingrese ``delete`` para confirmar que desea eliminar este archivo

10- Elija Delete objects (Eliminar objetos)

<img width="626" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/8b2af27c-ae5a-458e-9180-281138b60095">

11- Observe que el archivo index.html aparece en el panel Failed to delete (Error al eliminar). Esto confirma que la política funciona y que impide la eliminación de los archivos del sitio web.

12- Elija Close (Cerrar) para volver a la pestaña Objects (Objetos)

### Tarea 7: Actualiza el sitio web

Aunque configuró una política para impedir la eliminación de archivos del sitio web, de todas maneras puede actualizar el sitio web editando el archivo HTML y cargándolo en el bucket de S3 nuevamente.

Amazon S3 es un servicio de almacenamiento de objetos, por lo que debe cargar el archivo completo. Esta acción reemplazará al objeto existente en el bucket. No es posible editar el contenido de un objeto, debe reemplazarlo por completo.

1- En su equipo, cargue el archivo index.html en un editor de texto (por ejemplo, Bloc de notas o TextEdit)

2- Busque el texto Served from Amazon S3 (Entregado desde Amazon S3) y sustitúyalo por ``Created by <YOUR-NAME>`` y reemplace por su nombre ``<YOUR-NAME>`` (por ejemplo, Creado por **Esteban** ).

3- Guarde el archivo

4- Vuelva a la consola de Amazon S3 y cargue el archivo index.html que acaba de editar

<img width="612" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/779be8f9-2032-4d4b-b0bd-7b2fc5688b80">


5- Elija index.html y el menú Actions (Acciones), elija otra vez la opción Make public using ACL (Hacer público a través de ACL)

<img width="848" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/1dde69d2-8f09-4044-a7e0-7171ddf380f7">


6- Elija Make public (Hacer público)

<img width="652" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/90336d24-f7ca-4fb2-988b-e5f311090528">


7- Regrese a la pestaña del navegador web con el sitio web estático y actualice la página

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/80d4dbc4-6a97-4274-995c-74dbeef9d2f4)


### Tarea 8: Explora las versiones de los archivos

El control de versiones en buckets está desactivado de forma predeterminada. Cuando está desactivado el control de versiones, no se pueden deshacer los cambios a los objetos. Por ejemplo, si carga una nueva versión de un archivo, el archivo antiguo es reemplazado por el nuevo. Se pierde el archivo original. Si elimina un archivo, se elimina de forma permanente y no puede recuperarlo.

Sin embargo, cuando esté activado el control de versiones, se guardan las versiones modificadas y eliminadas de los archivos. No se presentan las versiones anteriores de los objetos de forma predeterminada, pero puede acceder a ellas mediante la consola o con programación. Ya que conserva versiones anteriores de los objetos, puede recuperarlos si lo necesita.

 Es importante recordar que una vez que activa el control de versiones, no puede desactivarlo. Sin embargo, puede suspenderlo. Para obtener más información sobre el control de versiones en buckets, consulte la [Guía del usuario de Amazon Simple Storage Service](https://docs.aws.amazon.com/AmazonS3/latest/userguide/Versioning.html) .

Recuerde que cuando creó el bucket, activó el control de versiones. En esta tarea, verá las versiones del objeto disponibles en su bucket.

1- Vuelva a la consola de Amazon S3 y elija la pestaña Objects (Objetos)

<img width="872" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/e40aa2b6-4451-47f6-9620-a5e181ceb36b">


2- Elija **Show versions** (Mostrar versiones) para activar el control de versiones en buckets

<img width="827" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/1c2f4670-cdce-4ff5-ae51-fd0fce768fb4">


3- Revise la lista de objetos en el bucket

*Imagen de ejemplo de AWS*

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/bca816c2-def9-4531-81f4-e78483613b34)

*Imagen de mi procedimiento*

<img width="881" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/c4684dd3-b767-40da-b9e5-6a7d7a57b9b7">

  - Observe que cada archivo tiene un ID de versión. Estos ID son generados automáticamente por Amazon S3 cuando se activa el control de versiones
   
  - También debe encontrar dos versiones del archivo index.html porque cargó una nueva versión del archivo. La versión actual es el archivo que cargó cuando actualizó su sitio web
