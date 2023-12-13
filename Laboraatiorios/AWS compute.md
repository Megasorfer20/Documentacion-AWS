# Laboratorio: Introducción a Amazon EC2

## Descripción general y objetivos del laboratorio

Esta práctica de laboratorio le proporciona una descripción general básica del lanzamiento, cambio de tamaño, administración y monitoreo de una instancia de Amazon Elastic Compute Cloud (Amazon EC2).

Amazon EC2 es un servicio web que proporciona capacidad informática redimensionable en la nube. Está diseñado para hacer que la computación en la nube a escala web sea intuitiva y sencilla de usar. Amazon EC2 le brinda acceso rápido a nuevas instancias de servidor y puede ampliar o reducir rápidamente la capacidad a medida que cambian sus requisitos informáticos.

#### Objetivos

Después de completar esta práctica de laboratorio, sabrá cómo hacer lo siguiente:

- Inicie una instancia EC2 con la protección contra terminación activada.
- Supervise su instancia EC2.
- Modifique el grupo de seguridad que utiliza su servidor web para permitir el acceso HTTP.
- Conéctese a su instancia EC2 utilizando AWS Systems Manager Fleet Manager.
- Gestionar el estado de una instancia EC2.
- Cambie su tipo de instancia EC2.
- Protección de terminación de prueba.
- Explore los límites de Amazon EC2.

  
## Desarrollo del laboratorio

### Tarea 1: Lanzar su instancia EC2

En esta tarea, lanza una instancia EC2 con protección de terminación. La protección de terminación evita que usted finalice accidentalmente una instancia EC2. También implementa su instancia con un script de datos de usuario para implementar un servidor web simple.

1- En la Consola de administración de AWS, en el menú Servicios, ingrese EC2. De los resultados de la búsqueda, elija EC2.

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/25e2d38e-e140-4fc3-99af-f3fbd4fcce7a)


2- En el panel de navegación izquierdo, elija `EC2 Dashboard` para asegurarse de estar en la página del panel.

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/d0a102de-d402-4c80-b174-1f7b26cd436c)


3- En la sección `Launch instance`, elija el botón `Launch instance`.

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/1919a1bc-9e3e-4be6-a717-4a5cb74a07b0)


#### Paso 1: NOMBRE A SU INSTANCIA EC2

Al utilizar etiquetas, puede categorizar sus recursos de AWS de diferentes maneras (por ejemplo, por propósito, propietario o entorno). Esta categorización es útil cuando tienes muchos recursos del mismo tipo. Puede identificar rápidamente un recurso específico según las etiquetas que le haya asignado. Cada etiqueta consta de una clave y un valor, los cuales usted define.

Cuando le asigna un nombre a su instancia, AWS crea un par ``key-value``. La `key` para este par es Nombre y el `value` es el nombre que ingresa para su instancia EC2.

4- En el panel Nombre y etiquetas, en el cuadro de texto Nombre, ingrese `web-server`

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/77ed0f11-d454-4264-824b-8dd35f6709aa)


5- Elija el enlace Agregar etiquetas adicionales.

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/6a459fef-25a4-4651-a733-1d5aa6606719)


6- En la lista desplegable Tipos de recursos, seleccione Instancias y volúmenes.

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/eb2e5911-2713-48a9-b6eb-f53b5514b666)



#### Paso 2: ELIJA UN AMI

Una `Amazon Machine Image` (AMI) proporciona la información necesaria para lanzar una instancia, que es un servidor virtual en la nube. Un AMI incluye lo siguiente:

- Una plantilla para el volumen raíz de la instancia (por ejemplo, un sistema operativo o un servidor de aplicaciones con aplicaciones)
- Permisos de lanzamiento que controlan qué cuentas de AWS pueden usar la AMI para lanzar instancias
- Una asignación de dispositivo de bloque que especifica los volúmenes que se adjuntarán a la instancia cuando se lance

La lista de inicio rápido contiene las AMI más utilizadas. También puede crear su propia AMI o seleccionar una AMI de AWS Marketplace, una tienda en línea donde puede vender o comprar software que se ejecuta en AWS.

7- Localice la sección `Application and OS Images` (Imagen de máquina de Amazon). Está justo debajo de la sección `Name and tags`

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/87e87634-a3f0-4b42-a504-99e3f9e1f4a9)


8- En el cuadro de búsqueda, ingrese ``Microsoft Windows Server 2019 Base`` y presione Entrar

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/d87ce807-fb50-45b3-b965-f520e6a0a4d7)


9- Junto a ``Microsoft Windows Server 2019 Base``, elija Seleccionar

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/911badd1-f9ea-4ae3-ad6a-d6a270736ec7)


10- Elija Confirmar cambios.

#### Paso 3: ELIJA UN TIPO DE INSTANCIA

Amazon EC2 ofrece una amplia selección de tipos de instancias optimizadas para adaptarse a diferentes casos de uso. Los tipos de instancias comprenden distintas combinaciones de CPU, memoria, almacenamiento y capacidad de red y le brindan la flexibilidad de elegir la combinación adecuada de recursos para sus aplicaciones. Cada tipo de instancia incluye uno o más tamaños de instancia para que pueda escalar sus recursos según los requisitos de su carga de trabajo de destino.

En este paso, elige una instancia ``t2.micro``. Este tipo de instancia tiene 1 CPU virtual y 1 GiB de memoria.

11- En la sección ``Tipo de instancia``, mantenga el tipo de instancia predeterminado, ``t2.micro``.

<img width="545" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/a4eaaeeb-dad0-4a2d-b1fd-b404bd0b724b">


#### Paso 4: CONFIGURAR UN `KEY` DE LLAVES

Amazon EC2 utiliza criptografía de clave pública para cifrar y descifrar la información de inicio de sesión. Para iniciar sesión en su instancia, debe crear un par de claves, especificar el nombre del par de claves cuando inicia la instancia y proporcionar la clave privada cuando se conecta a la instancia.

En esta práctica de laboratorio, no se conecta a su instancia mediante una clave SSH, por lo que no necesita configurar un `Key pair`.

12- En la sección `key pair` (iniciar sesión), en la lista desplegable `Key pair name - required`, elija `Proceed without a key pair` (no recomendado).

<img width="541" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/1b4239c8-d19b-44b7-aebd-7f008eb9f04d">


#### Paso 5: CONFIGURAR LOS AJUSTES DE RED

Utilice este panel para configurar los ajustes de red.

La nube privada virtual (VPC) indica en qué VPC desea iniciar la instancia. Puede tener varias VPC, incluidas diferentes para desarrollo, pruebas y producción.

13- En la sección `Network settings`, elija Editar

<img width="565" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/b7fd7306-15ff-427f-9317-ce0b691b136b">


14- En la lista desplegable VPC: requerida, elija ``Lab VPC``

<img width="410" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/f787f98d-3496-404e-9f20-85bc49f7a68c">


La VPC de laboratorio se creó utilizando una plantilla de ``AWS CloudFormation`` durante el proceso de configuración de su laboratorio. Esta VPC incluye dos subredes públicas en dos zonas de disponibilidad diferentes.

15- Para `Security group name - required`, elija `Select existing security group`.

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/b9f89814-cab3-4930-93c3-4ce10ea227bb)


16- En `Common security groups`, seleccione `Web Server security group`.

<img width="401" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/1f1a8789-32f8-40e5-a5f4-3d34b0d601a1">

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/d1f8088a-65e1-4e51-a89b-93b6f9ee8f62)


Un grupo de seguridad actúa como un firewall virtual que controla el tráfico de una o más instancias. Cuando lanza una instancia, asocia uno o más grupos de seguridad con la instancia. Agrega reglas a cada grupo de seguridad que permiten el tráfico hacia o desde sus instancias asociadas. Puedes modificar las reglas de un grupo de seguridad en cualquier momento; las nuevas reglas se aplican automáticamente a todas las instancias asociadas con el grupo de seguridad.

#### Paso 6: AÑADIR ALMACENAMIENTO

Amazon EC2 almacena datos en un disco virtual conectado a la red llamado ``Amazon Elastic Block Store`` (Amazon EBS)

La instancia EC2 se inicia utilizando un volumen de disco predeterminado de 30 GiB. Este es su volumen raíz (también conocido como volumen de arranque)

17- En la sección Configurar almacenamiento, mantenga la configuración de almacenamiento predeterminada

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/9a2c7ebf-e700-48ad-b74c-14feb7678e6c)


#### Paso 7: CONFIGURAR DETALLES AVANZADOS

18- Expanda la sección Detalles avanzados.

<img width="568" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/fdf7c797-4828-4619-8e73-1a3c1f0a5e42">

<img width="565" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/d717f588-ff36-4f8a-919c-18cacd97fc3c">


19- Para el perfil de instancia de IAM, elija la función que tenga ``LabInstanceProfile`` en el nombre.

<img width="402" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/3e1321ba-c7ee-4707-83da-2ee9b82133ed">


Cuando ya no necesite una instancia EC2, puede finalizarla, lo que significa que la instancia se detiene y Amazon EC2 libera los recursos de la instancia. No puede reiniciar una instancia terminada. Si desea evitar que sus usuarios finalicen accidentalmente la instancia, puede activar (habilitar) la protección de terminación para la instancia, lo que evita que los usuarios finalicen instancias.

20- En la lista desplegable `Termination protection`, elija Habilitar.

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/00e66b46-354a-42c0-aa5f-f67cd0f6b900)


Cuando lanza una instancia en Amazon EC2, tiene la opción de pasar datos de usuario a la instancia. Estos comandos se pueden utilizar para realizar tareas comunes de configuración automatizada e incluso ejecutar scripts después de que se inicie la instancia.

21- Copie los siguientes comandos y péguelos en el cuadro de texto Datos del usuario.

      <powershell>
      # Installing web server
      Install-WindowsFeature -name Web-Server -IncludeManagementTools
      # Getting website code
      wget https://us-east-1-tcprod.s3.amazonaws.com/courses/CUR-TF-100-EDCOMP/v1.0.4.prod-ef70397c/01-lab-ec2/scripts/code.zip -outfile "C:\Users\Administrator\Downloads\code.zip"
      # Unzipping website code
      Add-Type -AssemblyName System.IO.Compression.FileSystem
      function Unzip
      {
          param([string]$zipfile, [string]$outpath)
          [System.IO.Compression.ZipFile]::ExtractToDirectory($zipfile, $outpath)
      }
      Unzip "C:\Users\Administrator\Downloads\code.zip" "C:\inetpub\"
      # Setting Administrator password
      $Secure_String_Pwd = ConvertTo-SecureString "P@ssW0rD!" -AsPlainText -Force
      $UserAccount = Get-LocalUser -Name "Administrator"
      $UserAccount | Set-LocalUser -Password $Secure_String_Pwd
      </powershell>

<img width="467" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/79c364be-e723-4a9f-a530-1629e7d9faf6">


El guión hace lo siguiente:

- Instala un servidor web de Microsoft Internet Information Services (IIS)
- Crea un sitio web sencillo.
- Establece la contraseña para el usuario Administrador


#### Paso 8: LANZAR UNA INSTANCIA EC2

Ahora que ha configurado los ajustes de su instancia EC2, es hora de iniciar su instancia.

22- En la sección `Summary `, elija `Launch instance`.

<img width="278" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/c3f7273a-5680-4c65-816c-7fd3520b9e89">


Un mensaje indica que ha iniciado exitosamente el lanzamiento de su instancia.

<img width="881" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/49a6e9d7-ff23-4101-85ae-ff26c7558cb6">


23- Elija Ver todas las instancias

<img width="866" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/543a1ede-c648-47d5-8a93-4848798fd690">


La instancia aparece en estado Pendiente, lo que significa que se está lanzando. Luego cambia a En ejecución, lo que indica que la instancia ha comenzado a iniciarse. Pasará un breve periodo de tiempo antes de que puedas acceder a la instancia.

La instancia recibe un nombre público de Sistema de nombres de dominio (DNS) que puede utilizar para comunicarse con la instancia desde Internet.

24- Al lado de su `Web-Server`, seleccione la casilla de verificación. La pestaña Detalles muestra información detallada sobre su instancia.

<img width="755" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/44d633b8-eecd-4452-913b-fe88ca7366b4">


Para ver más información en la pestaña Detalles, arrastre el divisor de la ventana hacia arriba.

Revise la información que se muestra en las pestañas Detalles, Seguridad y Redes.

25- Espere a que su instancia muestre lo siguiente:

_**Nota:** actualice si es necesario._

- **Estado de instancia:** en ejecución
- **Comprobaciones de estado:** 2/2 comprobaciones aprobadas

<img width="754" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/75e5c2cc-23bc-450a-b728-188f378ba632">


### Tarea 2: Monitorear su instancia

El monitoreo es una parte importante para mantener la confiabilidad, la disponibilidad y el rendimiento de sus instancias EC2 y sus soluciones de AWS.

1- Elija la pestaña Verificaciones de estado.

<img width="755" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/2b94d303-60e3-433d-a011-db5f4ca58b4a">


Con la supervisión del estado de las instancias, puede determinar rápidamente si Amazon EC2 ha detectado algún problema que pueda impedir que sus instancias ejecuten aplicaciones. Amazon EC2 realiza comprobaciones automatizadas en cada instancia EC2 en ejecución para identificar problemas de hardware y software.

Observe que se han superado las comprobaciones de `System reachability` y de ` Instance reachability`.

2- Elija la pestaña Monitoreo.

<img width="741" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/f9761dbd-4663-45f8-950a-7d4772fedfd5">


Esta pestaña muestra las métricas de Amazon CloudWatch para su instancia. Actualmente, no hay muchas métricas para mostrar porque la instancia se lanzó recientemente.

Puede elegir un gráfico para ver una vista ampliada.

Amazon EC2 envía métricas a Amazon CloudWatch para sus instancias EC2. La monitorización básica (5 minutos) está activada de forma predeterminada y es gratuita. Puede activar el seguimiento detallado (1 minuto). Con un seguimiento detallado, se le cobrará por la métrica que envíe a CloudWatch.

3- En la parte superior de la página, elija el menú desplegable Acciones. Seleccione `Monitor and troubleshoot > Get system log`.

<img width="653" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/29e8e12f-2d42-44ae-99ad-b707a90c8f72">

El registro del sistema muestra la salida de la consola de la instancia, que es una herramienta valiosa para el diagnóstico de problemas. Es especialmente útil para solucionar problemas de configuración del servicio que podrían provocar que una instancia finalice o se vuelva inaccesible. Si no ve un registro del sistema, espere unos minutos y vuelva a intentarlo.

4- Desplácese por el registro y revise los mensajes en el resultado

<img width="691" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/3ae9748c-2229-4bca-b712-452805b7b040">

5- Para regresar al panel de Amazon EC2, elija Cancelar

<img width="735" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/b323e844-4c60-45f0-911c-c2c3d707348d">


6- Con su `Web-Server` seleccionado, elija el menú desplegable Acciones y seleccione `Monitor and troubleshoot > Get instance screenshot`

<img width="490" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/4162afbc-0327-4a83-8102-acc17db85d9c">


Esta opción le muestra cómo se vería la consola de su instancia EC2 si se le conectara una pantalla. Debido a que se trata de una instancia de Windows, la captura de pantalla muestra una pantalla de inicio de sesión bloqueada.

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/4e202ad4-b012-49fa-97c3-dd63a53b9081)

Si no puede acceder a su instancia a través de SSH o RDP, puede capturar una captura de pantalla de su instancia y verla como una imagen. Esta opción proporciona visibilidad sobre el estado de la instancia para una resolución de problemas más rápida

<img width="670" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/349fa353-69d5-4c46-919a-dea0fd424e6f">


7- En la parte inferior de la página, elija Cancelar

<img width="620" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/ab99f26d-3213-4d45-a99f-fd629b947c70">


### Tarea 3: Actualizar su grupo de seguridad y acceder al servidor web

Cuando lanzó la instancia EC2, proporcionó un script que instaló un servidor web y creó una página web simple. En esta tarea, accede al contenido desde el servidor web.

1- Seleccione la casilla de verificación junto al `Web-Server` Amazon EC2 que creó y luego elija la pestaña Detalles.

<img width="754" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/cfb86872-6841-4421-abba-a80e3e581f19">


2- Copie la dirección IPv4 pública de su instancia a su portapapeles.

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/ff7cc1cc-5690-4b02-83a5-aea4ca1a4af7)


3- En su navegador web, abra una nueva pestaña, pegue la dirección IP que acaba de copiar y luego presione Entrar.

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/2fa0a78e-9f8c-4fc0-885f-3094e9ba06e4)

<img width="957" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/c4c08b8b-c55d-4c7d-8752-bf816841f2ec">


**Pregunta:** ¿Puede acceder a su servidor web? ¿Por qué no?

Actualmente no puede acceder a su servidor web porque el grupo de seguridad no permite el tráfico entrante en el puerto 80, que se utiliza para solicitudes web HTTP. Este paso es una demostración de cómo utilizar un grupo de seguridad como firewall para restringir el tráfico de red que se permite dentro y fuera de una instancia.

Para corregir este problema, ahora actualice el grupo de seguridad para permitir el tráfico web en el puerto 80.

4- Mantenga abierta la pestaña del navegador, pero regrese a la pestaña de la Consola de administración EC2

5- En el panel de navegación izquierdo, elija Grupos de seguridad

<img width="151" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/f560dbf1-57c0-43db-9a5c-91b82de94cbe">


6- Junto al grupo de seguridad del servidor web, seleccione la casilla de verificación.

<img width="733" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/2f26fedb-f19d-4d4f-b6e1-100c052989bd">


7- Elija la pestaña `Inbound rules`.

<img width="717" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/d85d84e1-1597-4d96-9bd4-c3d55b46f423">


El grupo de seguridad actualmente no tiene reglas

8- Elija `Edit inbound rules` y luego elija Agregar regla y configure las siguientes opciones:

**Type:** elija HTTP.
**Source:** Elija Anywhere-IPv4.

<img width="886" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/85102887-6e43-4df8-a637-a3e496fbdd58">


**Nota:** Observe que las “Reglas con fuente de 0.0.0.0/0 permiten que todas las direcciones IP accedan a su instancia. Recomendamos configurar reglas de grupo de seguridad para permitir el acceso únicamente desde direcciones IP conocidas”. Si bien esta es una práctica recomendada verdadera y común, esta práctica de laboratorio permite el acceso desde cualquier dirección IP (en cualquier lugar) para simplificar tanto la configuración del grupo de seguridad como las pruebas del sitio web que se ejecuta en su instancia EC2.

43- Elija Guardar reglas

<img width="398" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/e9d69c45-3107-4977-add1-dc3d966518a8">


44- Regrese a la pestaña del navegador del servidor web con la dirección IPv4 pública que abrió anteriormente y elija actualizar la página.

Ahora debería encontrar un sitio web con el mensaje `Welcome Students!`

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/0d86eb31-0f4e-4e58-b97f-515245a2c573)


**Nota:** Si el sitio web no se carga, verifique que la URL en la barra de direcciones comience con `http://` y no `https://`

### Tarea 4: Conectarse a su instancia utilizando ``AWS Systems Manager Fleet Manager``

Con la capacidad de Fleet Manager de AWS Systems Manager, puede administrar y configurar de forma remota sus nodos administrados. Un nodo administrado es cualquier máquina configurada para Systems Manager.

Cuando comenzó este laboratorio, su usuario de AWS recibió automáticamente permisos para usar Sistement Manager. Además, la política de Gestión de Identidad y Acceso de AWS (IAM) que seleccionó al configurar su instancia de EC2 encendió Systems Manager para su instancia de servidor web.

Una característica conveniente de Fleet Manager es la capacidad de conectarse a su instancia de EC2 usando un navegador. En esta tarea, se conecta a su escritorio de Windows con Fleet Manager.

1- En la consola de administración de AWS en el menú Servicios, busque y seleccione ``Systems Manager``.

<img width="700" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/305970d5-3d4b-4aab-b989-3b258ac0a2cb">


2- En el panel de nagivación izquierda, seleccione ``Fleet Manager``.

<img width="187" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/16742adf-e569-4d6f-b24f-8d22bf5d91d5">


3- En nodos administrados, seleccione su instancia de ``Web-Server`` EC2.

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/c48e97c1-5b2b-4ea1-9766-ade7b9067513)


4- Desde la lista desplegable de las acciones del nodo, elija conectarse con el escritorio remoto.

<img width="449" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/f52d3e5b-c04b-4a95-9a0c-71b7ea8cb187">


Se abre una nueva pestaña.

5- Ingrese los siguientes valores:

 - Nombre de usuario: ``Administrator``
 - Contraseña: ``P@ssw0rd!``

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/cbb69810-4675-444b-af27-16ef8695ff1f)


6- Elija ``Connect``.

<img width="442" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/27eb3f82-406c-46e0-93a2-eeaf7fd6962f">


Después de varios segundos, el panel muestra el escritorio de Windows. Puede navegar por este escritorio como lo haría en una computadora local. Como aprendió anteriormente, con Amazon EC2, puede acceder rápidamente a los recursos de cálculo. En lugar de comprar hardware físico y configurar un sistema operativo, todo lo que tiene que hacer es iniciar una instancia de EC2, y todo ese trabajo se realiza automáticamente en minutos.

<img width="460" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/31040bc4-2658-4a5a-abd4-6068c5db6a92">


7- Para desconectar en su instancia de `Web-Server`, elija Action y luego elija la `End session`.

<img width="445" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/00e7668d-0240-459b-b6b1-9dff0d61391f">


8- En la ventana emergente, elija la `End session` nuevamente.

<img width="513" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/63fd289a-f98d-42a0-9a7c-c72c271906b8">


### Tarea 5: Reescalar tu instancia

A medida que sus necesidades cambian, puede encontrar que su instancia está excesiva (demasiado pequeña) o subutilizada (demasiado grande). Si es así, puede cambiar el tipo de instancia. Por ejemplo, si una instancia T2.Micro es demasiado pequeña para su carga de trabajo, puede cambiarla a una instancia M5. Medium

#### Detén tu instancia

Antes de que pueda cambiar el tamaño de una instancia, debe detenerla

Cuando detiene una instancia, se apaga. No hay carga para una instancia de EC2 detenido, pero la carga de almacenamiento para los volúmenes EBS adjuntos permanece.

1- Desde la consola de administración de AWS en el menú de servicios, elija EC2

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/25e2d38e-e140-4fc3-99af-f3fbd4fcce7a)

2- En la consola de gestión de EC2, en el panel de navegación izquierda, elija instancias.

<img width="154" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/61eeb956-c4fb-4a63-bb79-6494d4e91007">


3- Seleccione la casilla de verificación junto a su instancia de servidor web. En la parte superior de la página, elija el menú desplegable de estado de instancia y elija Stop Instance.

<img width="513" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/6b2a6c11-95bb-4bce-b80e-e3c5e15314b3">


4- En el `Stop instance?` Ventana emergente, elija parar.

<img width="479" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/34257a8b-a801-41cc-96d5-58e5b9ae4acf">


Su instancia realiza un apagado normal y luego deja de funcionar.

5- Espere a que el estado de instancia se detenga.

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/82b58193-e475-4356-b12e-2f1e20969491)


#### Cambiar el tipo de instancia

6- Seleccione la casilla de verificación junto a su servidor web. En el menú desplegable Acciones, seleccione Configuración de instancia Cambiar el tipo de instancia y luego configure la siguiente opción:

- Tipo de instancia: seleccione T2.Nano.

<img width="731" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/11ba456e-e83c-434c-bf97-594db794ba94">

<img width="650" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/47509df4-c9a3-4975-9c08-516a2a478db8">



7- Elija aplicar

<img width="650" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/cd50854f-d587-404c-8ad0-235244593e2d">


_**Nota:** Está restringido de usar otros tipos de instancias en este laboratorio._

#### Iniciar la instancia redimensionada

Cuando la instancia se inicia nuevamente, es una instancia t2.nano. Ahora comienza la instancia nuevamente, que tiene menos memoria pero más espacio en disco.

8- En el panel de navegación izquierda, elija instancias. Junto a su ``Web-Server``, seleccione la casilla de verificación.

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/9a46dba1-1163-4a95-ab70-5e1e9c0f614a)


9- Desde el menú desplegable de estado de instancia, elija Iniciar instancia.

<img width="176" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/c553da87-3f7e-4f0d-8829-f71085e17635">


Una vez que se reinicia la instancia, el estado de instancia se muestra en ejecución.

### Tarea 6: Probar la protección de terminación

Puede eliminar su instancia cuando ya no la necesite. Esto se conoce como terminar su instancia. No puede conectarse ni reiniciar una instancia una vez finalizada.

En esta tarea, aprenderá a utilizar la protección contra terminación.

1- Seleccione la casilla de verificación junto a su instancia de `Web-Server`. En el menú desplegable `Instance state`, elija `Terminate instance`.

<img width="167" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/e63f7bcf-6c68-4984-a4e3-53e4b4cc383a">


2- Observe el mensaje junto a la opción Terminar instancia: La protección de terminación está habilitada para una o más de las instancias seleccionadas.

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/aa7648cf-0494-4e23-b58d-c4c3db33c408)


Esta es una salvaguardia para evitar la terminación accidental de una instancia. Si realmente desea finalizar la instancia, debe desactivar la protección de terminación.

Puede habilitar y deshabilitar fácilmente la protección contra terminación desde el menú desplegable Acciones.

3- En el menú desplegable Acciones, elija `Instance settings` y luego elija `Change termination protection`.

<img width="587" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/13151510-9d48-4377-97c0-6ecaeb07e561">


4- Elija Guardar.

<img width="449" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/ea16177e-549f-4486-b914-7b69d3f40d2c">


5- Ahora, intenta terminar la instancia nuevamente

<img width="167" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/e63f7bcf-6c68-4984-a4e3-53e4b4cc383a">

El estado de la instancia ahora finalizará exitosamente.

### Tarea 7: Explorando los límites de EC2

Amazon EC2 proporciona diferentes recursos que puede utilizar. Estos recursos incluyen imágenes, instancias, volúmenes e instantáneas. Cuando crea una cuenta de AWS, existen límites predeterminados para estos recursos por región.

1- En el panel de navegación izquierdo, elija `Limits`.

**Nota:** Existe un límite en la cantidad de instancias que puede iniciar en esta región. Al lanzar una instancia, la solicitud no debe hacer que su uso exceda el límite de instancia actual en esa región.

Puedes solicitar un aumento para muchos de estos límites

## Resumen

En esta práctica de laboratorio, creó una instancia EC2 y aprendió a administrar propiedades de la instancia, como el tipo de instancia. Modificó la configuración del grupo de seguridad para que el sitio web fuera accesible y aprendió a utilizar la protección contra terminación para evitar la eliminación de instancias. Aprendió cómo detener, iniciar y finalizar una instancia EC2. Finalmente, aprendió a encontrar los límites de EC2 para su cuenta de AWS.
