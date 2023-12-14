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

Es posible que necesite esta información más adelante en el laboratorio.

2- Elija el menú Services (Servicios), busque los servicios de Security, Identity, & Compliance (Seguridad, Identidad y Conformidad) y elija IAM.

3- En el panel de navegación de la izquierda, elija Users (Usuarios).

Ya se crearon los siguientes usuarios de IAM para usted:

- usuario-1
- usuario-2
- usuario-3

4- Seleccione el nombre del usuario-1.

- Esto lo llevará a una página de resumen para el usuario-1. Se mostrará la pestaña Permissions (Permisos).
- Observe que el usuario-1 no tiene permisos.

5- Elija la pestaña Groups (Grupos).

Observe que el usuario-1 tampoco es miembro de ningún grupo.

6- Elija la pestaña Security credentials (Credenciales de seguridad).

Observe que al usuario-1 se le asignó una Console password (Contraseña de la consola). Esto permite al usuario acceder a AWS Management Console.

7- En el panel de navegación de la izquierda, elija User groups (Grupos de usuarios).

Los siguientes grupos ya están creados:

- EC2-Admin
- EC2-Support
- S3-Support

8- Elija el nombre del grupo EC2-Support.

Esto le muestra la página de resumen del grupo EC2-Support.

9- Seleccione la pestaña Permissions (Permisos).

Este grupo está asociado a una política administrada que se llama AmazonEC2ReadOnlyAccess. Las políticas administradas son políticas prediseñadas (que crearon AWS o sus administradores) que se pueden adjuntar a grupos o usuarios de IAM. Cuando la política se actualiza, los cambios se implementan inmediatamente en los usuarios y grupos adjuntos a ella.

10- En Policy Name (Nombre de la política), elija el enlace de la política AmazonEC2ReadOnlyAccess.

11- Elija la pestaña {} JSON.

- Una política define qué acciones se permiten o niegan para determinados recursos de AWS. Esta política concede permiso para Listar y Describir (ver) información sobre Amazon Elastic Compute Cloud (Amazon EC2), Elastic Load Balancing, Amazon CloudWatch y Amazon EC2 Auto Scaling. Esta capacidad que permite ver recursos, pero no modificarlos, es ideal como rol de soporte.
- La estructura básica de las statements de una política de IAM es la siguiente:
    - En Effect (Efecto), se encuentran las opciones Allow (Permitir) o Deny (Denegar) permisos.
    - Action (Acción) especifica las llamadas a la API que se pueden realizar desde un servicio de AWS (por ejemplo, cloudwatch:ListMetrics).
    - Resource (Recurso) define el alcance de las entidades cubiertas por la regla de la política (por ejemplo, un bucket de [Amazon S3] o una instancia de Amazon EC2 específicos; un [*] significa cualquier recurso).

11- En el panel de navegación de la izquierda, elija User groups (Grupos de usuarios).

12- Elija el nombre del grupo S3-Support.

13- Seleccione la pestaña Permissions (Permisos).

El grupo S3-Support está adjunto a la política AmazonS3ReadOnlyAccess.

14- En Nombre de la política, elija el enlace de la política AmazonS3ReadOnlyAccess.

15- Elija la pestaña {} JSON.

La política tiene permisos para Obtener recursos y hacer una Lista de todos ellos en Amazon S3.

16- En el panel de navegación de la izquierda, elija User groups (Grupos de usuarios).

17- Elija el nombre del grupo EC2-Admin.

18- Seleccione la pestaña Permissions (Permisos).

Este grupo difiere de los otros dos. En lugar de una política administrada, tiene una política insertada, que es una política asignada a un único usuario o grupo. Por lo general, las políticas insertadas se utilizan para asignar permisos a situaciones específicas.

19- En Policy Name (Nombre de la política), elija el nombre de la política EC2-Admin-Policy.

20- Elija la pestaña JSON.

La política concede permiso para Describir información acerca de las instancias de Amazon EC2 y también la capacidad de Iniciar o Detener instancias.

21- Para cerrar la política, vaya a la parte inferior de la pantalla y haga clic en Cancel (Cancelar).

#### Situación empresarial

Durante el resto del laboratorio, trabajará con estos usuarios y grupos para habilitar los permisos compatibles con la siguiente situación empresarial.

Su compañía aprovecha los servicios de AWS cada vez más y utiliza muchas instancias de Amazon EC2 y buckets de Amazon S3. Desea dar acceso al nuevo personal dependiendo de su función laboral, como se indica en la siguiente tabla:

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/49f07c2c-fd3f-4fed-9541-4cab9d783975)


### Tarea 2: agregar usuarios a los grupos

Recientemente, contrató al usuario-1 para que brinde soporte a Amazon S3. Lo agregará al grupo S3-Support para que pueda heredar los permisos necesarios mediante la política adjunta AmazonS3ReadOnlyAccess.

Ignore los errores “no autorizados” que aparezcan durante esta tarea. Se producen porque su cuenta de laboratorio tiene permisos limitados, pero esto no afectará su capacidad para completar el laboratorio.

#### Agregar al usuario-1 al grupo S3-Support.

1- En el panel de navegación de la izquierda, elija User groups (Grupos de usuarios).
2- Elija el nombre del grupo S3-Support.
3- En la pestaña Users (Usuarios), seleccione Add users (Agregar usuarios).
4- Seleccione  user-1 (usuario-1) y elija Add users (Agregar usuarios).

En la pestaña Users (Usuarios), verá que se agregó el usuario-1 al grupo.

#### Agregar al usuario-2 al grupo EC2-Support.

Contrató al usuario-2 para que brinde soporte a Amazon EC2. Lo agregará al grupo EC2-Support para que pueda heredar los permisos necesarios mediante la política adjunta AmazonEC2ReadOnlyAccess.

5- Con lo aprendido en los pasos anteriores, agregue al usuario-2 al grupo EC2-Support.

Ahora, el usuario-2 debería formar parte del grupo EC2-Support.

#### Agregar al usuario-3 al grupo EC2-Admin

Contrató al usuario-3 como administrador de Amazon EC2 para que administre sus instancias EC2. Lo agregará al grupo EC2-Admin para que pueda heredar los permisos necesarios mediante la política adjunta EC2-Admin-Policy.

6- Con lo aprendido en los pasos anteriores, agregue al usuario-3 al grupo EC2-Admin.

Ahora, el usuario-3 debería formar parte del grupo EC2-Admin.

7- En el panel de navegación de la izquierda, elija User groups (Grupos de usuarios).

Cada grupo debería tener un 1 en la columna Users (Usuarios). Esto indica la cantidad de usuarios en cada grupo.

Si no se muestra un 1 junto a cada grupo, revise las instrucciones anteriores para garantizar que cada usuario esté asignado a un grupo, como se muestra en la tabla de la sección Situación empresarial.

### Tarea 3: iniciar sesión y probar usuarios

En esta tarea, probará los permisos de cada usuario de IAM en la consola.

#### Obtener la URL de inicio de sesión de la consola

1- En el panel de navegación de la izquierda, elija Dashboard (Panel).

En la parte superior de la página observe la sección Sign-in URL for IAM users in this account (URL de inicio de sesión para los usuarios de IAM de esta cuenta). La URL de inicio de sesión es similar a la siguiente: ``https://123456789012.signin.aws.amazon.com/console``

El enlace se puede usar para iniciar sesión en la cuenta de AWS que está usando.

2- Copie el enlace de inicio de sesión en un editor de texto.

##### Probar los permisos del usuario-1

3- Abra una ventana privada o de incógnito en su navegador.

4- Pegue el enlace de inicio de sesión en el navegador privado y presione ENTER (Intro).

Ahora iniciará sesión como el usuario-1, a quien se contrató como personal de soporte para el almacenamiento de Amazon S3.

5- Inicie sesión con las siguientes credenciales:

- **IAM user name (Nombre de usuario de IAM):** ``user-1``
- **Password (Contraseña):** ``Lab-Password1``

6- Elija el menú Services (Servicios), elija S3.

7- Haga clic en el nombre de uno de los buckets y busque el contenido.

Debido a que el usuario forma parte del grupo S3-Support en IAM, tiene permiso para ver una lista de buckets de Amazon S3 y su contenido.

Ahora, pruebe si puede obtener acceso a Amazon EC2.

8- Elija el menú Services (Servicios), elija EC2.

9- En el panel de navegación izquierdo, elija Instances (Instancias).

No puede ver ninguna instancia. En su lugar, verá un mensaje de error con el texto You are not authorized to perform this operation (No está autorizado para realizar esta operación). Este usuario no tiene ningún permiso para utilizar Amazon EC2.

Ahora, iniciará sesión como el usuario-2, a quien se contrató como personal de soporte para Amazon EC2.

10- En primer lugar, cierre la sesión del usuario-1 desde la consola:

- Elija el usuario-1 en la esquina superior derecha de la página.
- Elija Sign Out (Cerrar sesión).

##### Probar los permisos del usuario-2

11- Vuelva a pegar el enlace de inicio de sesión en el navegador privado y presione ENTER (Intro).

12- Inicie sesión con las siguientes credenciales:

- **IAM user name (Nombre de usuario de IAM):** ``user-2``
- **Password (Contraseña):** ``Lab-Password2``
- 
13- Elija el menú Services (Servicios), elija EC2.

14- En el panel de navegación de la izquierda, elija Instances (Instancias).

- Ahora puede ver una instancia EC2. Sin embargo, ya que solo tiene permisos de lectura, no puede realizar ningún cambio en los recursos de Amazon EC2.
- Si la instancia EC2 no es visible, es posible que la región sea incorrecta. En la esquina superior derecha de la página, elija el nombre de la región y, a continuación, elija la región en la que se encontraba al principio del laboratorio (por ejemplo, Norte de Virginia).

15- Seleccione la instancia EC2.

16- Seleccione el menú de Instance state (Estado de la instancia) y, a continuación, elija Stop instance (Detener instancia).

17- Para confirmar que desea detener la instancia, seleccione Stop (Detener).

Aparece un mensaje de error que dice: *You are not authorized to perform this operation* (No está autorizado para realizar esta operación). Esto demuestra que la política solo le permite ver la información, pero no realizar cambios.

Luego, verifique si el usuario-2 puede acceder a Amazon S3.

18- Elija el menú Services (Servicios), elija S3.

Un mensaje de error dice: You don't have permissions to list buckets (No tiene permisos para listar buckets) porque el usuario-2 no tiene permisos para usar Amazon S3.

Ahora, iniciará sesión como el usuario-3, a quien se contrató como administrador de Amazon EC2.

19- En primer lugar, cierre la sesión del usuario-2 desde la consola:

- Elija el usuario-2 en la esquina superior derecha de la página.
- Elija Sign Out (Cerrar sesión).

##### Probar los permisos del usuario-3

20- Vuelva a pegar el enlace de inicio de sesión en el navegador privado y presione ENTER (Intro).

21- Inicie sesión con las siguientes credenciales:

- **IAM user name (Nombre de usuario de IAM):** ``user-3``
- **Password (Contraseña):** ``Lab-Password3``

22- Elija el menú Services (Servicios), elija EC2.

23- En el panel de navegación de la izquierda, elija Instances (Instancias).

- Aparece una instancia EC2. Como administrador de Amazon EC2, ahora debería tener permisos para Detener la instancia de EC2.
- Si la instancia EC2 no es visible, es posible que la región sea incorrecta. En la esquina superior derecha de la página, elija el nombre de la región y, a continuación, elija la región en la que se encontraba al principio del laboratorio (por ejemplo, Norte de Virginia).

24- Seleccione la instancia EC2.

25- Seleccione el menú de Instance state (Estado de la instancia) y, a continuación, elija Stop instance (Detener instancia).

26- Para confirmar que desea detener la instancia, seleccione Stop (Detener).

En esta ocasión, la acción tiene éxito porque el usuario-3 tiene permisos para detener las instancias EC2. El Instance state (Estado de la instancia) cambia a Stopping (Deteniendo) y comienza a apagarse.

27- Cierre la ventana privada del navegador.
