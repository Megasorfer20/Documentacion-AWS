# Laboratorio de Introducción a IAM

## Información general sobre el laboratorio

En este laboratorio, explorará los usuarios, grupos y políticas en el servicio AWS Identity and Access Management (IAM).

### Objetivos

Después de completar este laboratorio, sabrá cómo realizar lo siguiente:

- analizar los usuarios y grupos de IAM creados previamente
- inspeccionar las políticas de IAM según se apliquen a los grupos creados previamente
- realizar un seguimiento de una situación real y agregar usuarios a los grupos con capacidades específicas habilitadas
- ubicar y utilizar la URL de inicio de sesión de IAM
- experimentar con los efectos de las políticas en el acceso a los servicios

## Desarrollo del Laboratorio

### Tarea 1: analizar los usuarios y grupos

En esta tarea, analizará los usuarios y grupos que ya se crearon para usted en IAM.

1- Primero, anote la región en la que se encuentra; por ejemplo, Norte de Virginia. La región aparece en la esquina superior derecha de la página de la consola.

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/8ce6997a-2009-4dcd-a026-8f3e0e54f2f2)


Es posible que necesite esta información más adelante en el laboratorio.

2- Elija el menú Services (Servicios), busque los servicios de Security, Identity, & Compliance (Seguridad, Identidad y Conformidad) y elija IAM.

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/3ae48995-ed8f-4002-9e38-16dcf74af45d)


3- En el panel de navegación de la izquierda, elija Users (Usuarios).

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/beed6068-9722-474d-9efa-857ddbae14c1)


Ya se crearon los siguientes usuarios de IAM para usted:

- usuario-1
- usuario-2
- usuario-3

4- Seleccione el nombre del usuario-1.

<img width="683" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/9d27c8a5-a34b-4984-968f-d7cd42909b6f">

- Esto lo llevará a una página de resumen para el usuario-1. Se mostrará la pestaña Permissions (Permisos).
- Observe que el usuario-1 no tiene permisos.

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/d1b165ef-1ad8-418b-9b43-72264afa8d5b)

5- Elija la pestaña Groups (Grupos).

<img width="670" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/b55e4176-84a9-4129-8f25-1ec757fbbf6a">


Observe que el usuario-1 tampoco es miembro de ningún grupo.

6- Elija la pestaña Security credentials (Credenciales de seguridad).

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/c36f7f25-aaa5-4253-9f4f-e495e7bb42b1)


Observe que al usuario-1 se le asignó una Console password (Contraseña de la consola). Esto permite al usuario acceder a AWS Management Console.

7- En el panel de navegación de la izquierda, elija User groups (Grupos de usuarios).

<img width="194" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/03417ce9-1efc-41e2-90ed-c177acb57c6f">


Los siguientes grupos ya están creados:

- EC2-Admin
- EC2-Support
- S3-Support

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/066ed7c5-00c3-4212-b507-b5980095b28b)


8- Elija el nombre del grupo EC2-Support.

<img width="674" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/4b7cc1df-bdc3-4f60-81ba-1fe4bb0842ff">


Esto le muestra la página de resumen del grupo EC2-Support.

9- Seleccione la pestaña Permissions (Permisos).

<img width="664" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/cca0c01e-b64f-4e5f-b48e-855ab228a78e">


Este grupo está asociado a una política administrada que se llama AmazonEC2ReadOnlyAccess. Las políticas administradas son políticas prediseñadas (que crearon AWS o sus administradores) que se pueden adjuntar a grupos o usuarios de IAM. Cuando la política se actualiza, los cambios se implementan inmediatamente en los usuarios y grupos adjuntos a ella.

10- En Policy Name (Nombre de la política), elija el enlace de la política AmazonEC2ReadOnlyAccess.

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/17c1ae80-13f6-4c0d-baee-bf8ec5509850)


11- Elija la pestaña {} JSON.

<img width="673" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/359105d2-871d-4436-bd9f-82194241ebbd">


- Una política define qué acciones se permiten o niegan para determinados recursos de AWS. Esta política concede permiso para Listar y Describir (ver) información sobre Amazon Elastic Compute Cloud (Amazon EC2), Elastic Load Balancing, Amazon CloudWatch y Amazon EC2 Auto Scaling. Esta capacidad que permite ver recursos, pero no modificarlos, es ideal como rol de soporte.
- La estructura básica de las statements de una política de IAM es la siguiente:
    - En Effect (Efecto), se encuentran las opciones Allow (Permitir) o Deny (Denegar) permisos.
    - Action (Acción) especifica las llamadas a la API que se pueden realizar desde un servicio de AWS (por ejemplo, cloudwatch:ListMetrics).
    - Resource (Recurso) define el alcance de las entidades cubiertas por la regla de la política (por ejemplo, un bucket de [Amazon S3] o una instancia de Amazon EC2 específicos; un [*] significa cualquier recurso).

11- En el panel de navegación de la izquierda, elija User groups (Grupos de usuarios).

<img width="194" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/03417ce9-1efc-41e2-90ed-c177acb57c6f">

12- Elija el nombre del grupo S3-Support.

<img width="693" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/dd0e9627-e26a-44a2-9966-090092707f4d">


13- Seleccione la pestaña Permissions (Permisos).

<img width="667" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/f31af5c3-82bc-466a-93fe-2b8e66951afe">


El grupo S3-Support está adjunto a la política AmazonS3ReadOnlyAccess.

14- En Nombre de la política, elija el enlace de la política AmazonS3ReadOnlyAccess.

<img width="665" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/a9877098-a719-49a3-af15-6b24ac3d04c3">


15- Elija la pestaña {} JSON.

<img width="663" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/97d619cb-95c4-4f87-8a28-d98e81c63dd4">


La política tiene permisos para Obtener recursos y hacer una Lista de todos ellos en Amazon S3.

16- En el panel de navegación de la izquierda, elija User groups (Grupos de usuarios).

<img width="194" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/03417ce9-1efc-41e2-90ed-c177acb57c6f">

17- Elija el nombre del grupo EC2-Admin.

<img width="693" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/a06244c2-35eb-4dd9-8aac-91de04c371fb">


18- Seleccione la pestaña Permissions (Permisos).

<img width="667" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/6b21daf8-22c1-442f-b3fd-a43634807cce">


Este grupo difiere de los otros dos. En lugar de una política administrada, tiene una política insertada, que es una política asignada a un único usuario o grupo. Por lo general, las políticas insertadas se utilizan para asignar permisos a situaciones específicas.

19- En Policy Name (Nombre de la política), elija el nombre de la política EC2-Admin-Policy.

<img width="659" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/9818459a-bfa6-453d-9520-613c15ed60ad">


20- Elija la pestaña JSON.

<img width="632" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/d6176d3d-c9b8-4524-8c92-729bbdf7687e">


La política concede permiso para Describir información acerca de las instancias de Amazon EC2 y también la capacidad de Iniciar o Detener instancias.

21- Para cerrar la política, vaya a la parte inferior de la pantalla y haga clic en Cancel (Cancelar).

<img width="218" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/bd6dac68-d3d2-4f18-bc88-ab418a6a330c">


#### Situación empresarial

Durante el resto del laboratorio, trabajará con estos usuarios y grupos para habilitar los permisos compatibles con la siguiente situación empresarial.

Su compañía aprovecha los servicios de AWS cada vez más y utiliza muchas instancias de Amazon EC2 y buckets de Amazon S3. Desea dar acceso al nuevo personal dependiendo de su función laboral, como se indica en la siguiente tabla:

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/49f07c2c-fd3f-4fed-9541-4cab9d783975)


### Tarea 2: agregar usuarios a los grupos

Recientemente, contrató al usuario-1 para que brinde soporte a Amazon S3. Lo agregará al grupo S3-Support para que pueda heredar los permisos necesarios mediante la política adjunta AmazonS3ReadOnlyAccess.

Ignore los errores “no autorizados” que aparezcan durante esta tarea. Se producen porque su cuenta de laboratorio tiene permisos limitados, pero esto no afectará su capacidad para completar el laboratorio.

#### Agregar al usuario-1 al grupo S3-Support.

1- En el panel de navegación de la izquierda, elija User groups (Grupos de usuarios).

<img width="194" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/03417ce9-1efc-41e2-90ed-c177acb57c6f">

2- Elija el nombre del grupo S3-Support.

<img width="693" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/dd0e9627-e26a-44a2-9966-090092707f4d">

3- En la pestaña Users (Usuarios), seleccione Add users (Agregar usuarios).

<img width="674" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/7a4d668b-f4d1-4fa5-8f8d-e8c69f65269f">


4- Seleccione  user-1 (usuario-1) y elija Add users (Agregar usuarios).

<img width="866" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/ee6cef00-66b9-4092-b53b-0e64c33c8d66">


En la pestaña Users (Usuarios), verá que se agregó el usuario-1 al grupo.

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/ff62d115-654f-40f2-96ac-31c0cf726a44)


#### Agregar al usuario-2 al grupo EC2-Support.

Contrató al usuario-2 para que brinde soporte a Amazon EC2. Lo agregará al grupo EC2-Support para que pueda heredar los permisos necesarios mediante la política adjunta AmazonEC2ReadOnlyAccess.

5- Con lo aprendido en los pasos anteriores, agregue al usuario-2 al grupo EC2-Support.

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/18b05970-aa19-4dac-ac4e-5ec35317d335)


Ahora, el usuario-2 debería formar parte del grupo EC2-Support.

#### Agregar al usuario-3 al grupo EC2-Admin

Contrató al usuario-3 como administrador de Amazon EC2 para que administre sus instancias EC2. Lo agregará al grupo EC2-Admin para que pueda heredar los permisos necesarios mediante la política adjunta EC2-Admin-Policy.

6- Con lo aprendido en los pasos anteriores, agregue al usuario-3 al grupo EC2-Admin.

<img width="662" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/3187b6fc-68fa-4c17-8df3-b00f311b03b0">


Ahora, el usuario-3 debería formar parte del grupo EC2-Admin.

7- En el panel de navegación de la izquierda, elija User groups (Grupos de usuarios).

<img width="194" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/03417ce9-1efc-41e2-90ed-c177acb57c6f">

Cada grupo debería tener un 1 en la columna Users (Usuarios). Esto indica la cantidad de usuarios en cada grupo.

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/5c0e4fb5-6589-4370-82d8-57264a57a5f8)


Si no se muestra un 1 junto a cada grupo, revise las instrucciones anteriores para garantizar que cada usuario esté asignado a un grupo, como se muestra en la tabla de la sección Situación empresarial.

### Tarea 3: iniciar sesión y probar usuarios

En esta tarea, probará los permisos de cada usuario de IAM en la consola.

#### Obtener la URL de inicio de sesión de la consola

1- En el panel de navegación de la izquierda, elija Dashboard (Panel).

<img width="192" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/ac59d6a7-0e81-47a5-b2b6-6e951ef4f037">


En la parte superior de la página observe la sección Sign-in URL for IAM users in this account (URL de inicio de sesión para los usuarios de IAM de esta cuenta). La URL de inicio de sesión es similar a la siguiente: ``https://123456789012.signin.aws.amazon.com/console``

El enlace se puede usar para iniciar sesión en la cuenta de AWS que está usando.

2- Copie el enlace de inicio de sesión en un editor de texto.

``https://784954296964.signin.aws.amazon.com/console``

##### Probar los permisos del usuario-1

3- Abra una ventana privada o de incógnito en su navegador.

4- Pegue el enlace de inicio de sesión en el navegador privado y presione ENTER (Intro).

<img width="954" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/65a29f70-d372-4fcf-af17-751a18e52a64">


Ahora iniciará sesión como el usuario-1, a quien se contrató como personal de soporte para el almacenamiento de Amazon S3.

5- Inicie sesión con las siguientes credenciales:

- **IAM user name (Nombre de usuario de IAM):** ``user-1``
- **Password (Contraseña):** ``Lab-Password1``

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/1025de32-0bc7-43e5-91be-9bff2c121393)


6- Elija el menú Services (Servicios), elija S3.

<img width="774" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/fcbf952c-46c3-4f9b-8c17-f4d6f8ed5e1f">


7- Haga clic en el nombre de uno de los buckets y busque el contenido.

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/2feb957c-dcab-4d3c-b0c6-bc22c1fc1e30)


Debido a que el usuario forma parte del grupo S3-Support en IAM, tiene permiso para ver una lista de buckets de Amazon S3 y su contenido.

Ahora, pruebe si puede obtener acceso a Amazon EC2.

8- Elija el menú Services (Servicios), elija EC2.

<img width="776" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/dcfbf4a7-cf8e-428e-8d2a-7623019c2a68">


9- En el panel de navegación izquierdo, elija Instances (Instancias).

<img width="167" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/1f55e0a1-8ee8-421e-b162-5f6c7d72b791">


No puede ver ninguna instancia. En su lugar, verá un mensaje de error con el texto You are not authorized to perform this operation (No está autorizado para realizar esta operación). Este usuario no tiene ningún permiso para utilizar Amazon EC2.

<img width="770" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/6aa9645e-7ff2-4b2d-bfa5-01120e8d5fa0">


Ahora, iniciará sesión como el usuario-2, a quien se contrató como personal de soporte para Amazon EC2.

10- En primer lugar, cierre la sesión del usuario-1 desde la consola:

- Elija el usuario-1 en la esquina superior derecha de la página.
- Elija Sign Out (Cerrar sesión).

<img width="236" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/85ec4b9b-5fd7-4a2f-8fb9-18c97cbe31f8">


##### Probar los permisos del usuario-2

11- Vuelva a pegar el enlace de inicio de sesión en el navegador privado y presione ENTER (Intro).

12- Inicie sesión con las siguientes credenciales:

- **IAM user name (Nombre de usuario de IAM):** ``user-2``
- **Password (Contraseña):** ``Lab-Password2``

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/a4e02b88-9ffe-4939-9250-d5162944779b)


13- Elija el menú Services (Servicios), elija EC2.

<img width="527" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/cd2c0185-3122-4ab0-b6cb-7ff9e00a32a3">


14- En el panel de navegación de la izquierda, elija Instances (Instancias).

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/533066e7-3292-4403-a811-8fc769b47ac7)


- Ahora puede ver una instancia EC2. Sin embargo, ya que solo tiene permisos de lectura, no puede realizar ningún cambio en los recursos de Amazon EC2.
- Si la instancia EC2 no es visible, es posible que la región sea incorrecta. En la esquina superior derecha de la página, elija el nombre de la región y, a continuación, elija la región en la que se encontraba al principio del laboratorio (por ejemplo, Norte de Virginia).

15- Seleccione la instancia EC2.

<img width="552" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/f866526f-e34a-45fb-aa02-6f07a54fb74e">


16- Seleccione el menú de Instance state (Estado de la instancia) y, a continuación, elija Stop instance (Detener instancia).

<img width="118" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/44236f5e-afc9-4a34-ba29-a30144879a5c">


17- Para confirmar que desea detener la instancia, seleccione Stop (Detener).

<img width="314" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/396f2dc4-d34e-40e2-9341-cd9644f1b5ee">


Aparece un mensaje de error que dice: *You are not authorized to perform this operation* (No está autorizado para realizar esta operación). Esto demuestra que la política solo le permite ver la información, pero no realizar cambios.

<img width="551" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/7ea90dd9-abca-4a6f-9f65-f226966b0c66">


Luego, verifique si el usuario-2 puede acceder a Amazon S3.

18- Elija el menú Services (Servicios), elija S3.

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/75713406-a7f5-431d-9b38-b7fdeca6ba87)


Un mensaje de error dice: You don't have permissions to list buckets (No tiene permisos para listar buckets) porque el usuario-2 no tiene permisos para usar Amazon S3.

Ahora, iniciará sesión como el usuario-3, a quien se contrató como administrador de Amazon EC2.

19- En primer lugar, cierre la sesión del usuario-2 desde la consola:

- Elija el usuario-2 en la esquina superior derecha de la página.
- Elija Sign Out (Cerrar sesión).

<img width="236" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/64d8345e-41e4-484a-94a6-d65782f94364">


##### Probar los permisos del usuario-3

20- Vuelva a pegar el enlace de inicio de sesión en el navegador privado y presione ENTER (Intro).

21- Inicie sesión con las siguientes credenciales:

- **IAM user name (Nombre de usuario de IAM):** ``user-3``
- **Password (Contraseña):** ``Lab-Password3``

<img width="210" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/f782f93c-3903-4358-8e6a-d1f75caba9c4">


22- Elija el menú Services (Servicios), elija EC2.

<img width="552" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/f866526f-e34a-45fb-aa02-6f07a54fb74e">

23- En el panel de navegación de la izquierda, elija Instances (Instancias).

<img width="109" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/c8bafb4d-2784-4a12-977a-524471915123">


- Aparece una instancia EC2. Como administrador de Amazon EC2, ahora debería tener permisos para Detener la instancia de EC2.
- Si la instancia EC2 no es visible, es posible que la región sea incorrecta. En la esquina superior derecha de la página, elija el nombre de la región y, a continuación, elija la región en la que se encontraba al principio del laboratorio (por ejemplo, Norte de Virginia).

24- Seleccione la instancia EC2.

<img width="552" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/f866526f-e34a-45fb-aa02-6f07a54fb74e">

25- Seleccione el menú de Instance state (Estado de la instancia) y, a continuación, elija Stop instance (Detener instancia).

<img width="118" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/44236f5e-afc9-4a34-ba29-a30144879a5c">

26- Para confirmar que desea detener la instancia, seleccione Stop (Detener).

<img width="314" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/396f2dc4-d34e-40e2-9341-cd9644f1b5ee">

En esta ocasión, la acción tiene éxito porque el usuario-3 tiene permisos para detener las instancias EC2. El Instance state (Estado de la instancia) cambia a Stopping (Deteniendo) y comienza a apagarse.

<img width="554" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/ed2b3c47-7acd-4c30-bd0d-cf6014aa296a">


27- Cierre la ventana privada del navegador.
