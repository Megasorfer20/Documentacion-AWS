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

2- En el panel de navegación izquierdo, elija `EC2 Dashboard` para asegurarse de estar en la página del panel.

3- En la sección `Launch instance`, elija el botón `Launch instance`.

#### Paso 1: NOMBRE A SU INSTANCIA EC2

Al utilizar etiquetas, puede categorizar sus recursos de AWS de diferentes maneras (por ejemplo, por propósito, propietario o entorno). Esta categorización es útil cuando tienes muchos recursos del mismo tipo. Puede identificar rápidamente un recurso específico según las etiquetas que le haya asignado. Cada etiqueta consta de una clave y un valor, los cuales usted define.

Cuando le asigna un nombre a su instancia, AWS crea un par ``key-value``. La `key` para este par es Nombre y el `value` es el nombre que ingresa para su instancia EC2.

4- En el panel Nombre y etiquetas, en el cuadro de texto Nombre, ingrese `web-server`

5- Elija el enlace Agregar etiquetas adicionales.

6- En la lista desplegable Tipos de recursos, seleccione Instancias y volúmenes.


#### Paso 2: ELIJA UN AMI

Una `Amazon Machine Image` (AMI) proporciona la información necesaria para lanzar una instancia, que es un servidor virtual en la nube. Un AMI incluye lo siguiente:

- Una plantilla para el volumen raíz de la instancia (por ejemplo, un sistema operativo o un servidor de aplicaciones con aplicaciones)
- Permisos de lanzamiento que controlan qué cuentas de AWS pueden usar la AMI para lanzar instancias
- Una asignación de dispositivo de bloque que especifica los volúmenes que se adjuntarán a la instancia cuando se lance

La lista de inicio rápido contiene las AMI más utilizadas. También puede crear su propia AMI o seleccionar una AMI de AWS Marketplace, una tienda en línea donde puede vender o comprar software que se ejecuta en AWS.

7- Localice la sección `Application and OS Images` (Imagen de máquina de Amazon). Está justo debajo de la sección `Name and tags`

8- En el cuadro de búsqueda, ingrese ``Servidor Windows 2019 básico`` y presione Entrar

9- Junto a ``Microsoft Windows Server 2019 Base``, elija Seleccionar

10- Elija Confirmar cambios.

#### Paso 3: ELIJA UN TIPO DE INSTANCIA

Amazon EC2 ofrece una amplia selección de tipos de instancias optimizadas para adaptarse a diferentes casos de uso. Los tipos de instancias comprenden distintas combinaciones de CPU, memoria, almacenamiento y capacidad de red y le brindan la flexibilidad de elegir la combinación adecuada de recursos para sus aplicaciones. Cada tipo de instancia incluye uno o más tamaños de instancia para que pueda escalar sus recursos según los requisitos de su carga de trabajo de destino.

En este paso, elige una instancia ``t2.micro``. Este tipo de instancia tiene 1 CPU virtual y 1 GiB de memoria.

11- En la sección ``Tipo de instancia``, mantenga el tipo de instancia predeterminado, ``t2.micro``.

#### Paso 4: CONFIGURAR UN `KEY` DE LLAVES

Amazon EC2 utiliza criptografía de clave pública para cifrar y descifrar la información de inicio de sesión. Para iniciar sesión en su instancia, debe crear un par de claves, especificar el nombre del par de claves cuando inicia la instancia y proporcionar la clave privada cuando se conecta a la instancia.

En esta práctica de laboratorio, no se conecta a su instancia mediante una clave SSH, por lo que no necesita configurar un `Key pair`.

12- En la sección `key pair` (iniciar sesión), en la lista desplegable `Key pair name - required`, elija `Proceed without a key pair` (no recomendado).

#### Paso 5: CONFIGURAR LOS AJUSTES DE RED

Utilice este panel para configurar los ajustes de red.

La nube privada virtual (VPC) indica en qué VPC desea iniciar la instancia. Puede tener varias VPC, incluidas diferentes para desarrollo, pruebas y producción.

13- En la sección `Network settings`, elija Editar

14- En la lista desplegable VPC: requerida, elija ``Lab VPC``

La VPC de laboratorio se creó utilizando una plantilla de ``AWS CloudFormation`` durante el proceso de configuración de su laboratorio. Esta VPC incluye dos subredes públicas en dos zonas de disponibilidad diferentes.

15- Para `Security group name - required`, elija `Select existing security group`.

16- En `Common security groups`, seleccione `Web Server security group`.

Un grupo de seguridad actúa como un firewall virtual que controla el tráfico de una o más instancias. Cuando lanza una instancia, asocia uno o más grupos de seguridad con la instancia. Agrega reglas a cada grupo de seguridad que permiten el tráfico hacia o desde sus instancias asociadas. Puedes modificar las reglas de un grupo de seguridad en cualquier momento; las nuevas reglas se aplican automáticamente a todas las instancias asociadas con el grupo de seguridad.

#### Paso 6: AÑADIR ALMACENAMIENTO

Amazon EC2 almacena datos en un disco virtual conectado a la red llamado ``Amazon Elastic Block Store`` (Amazon EBS)

La instancia EC2 se inicia utilizando un volumen de disco predeterminado de 30 GiB. Este es su volumen raíz (también conocido como volumen de arranque)

17- En la sección Configurar almacenamiento, mantenga la configuración de almacenamiento predeterminada

#### Paso 7: CONFIGURAR DETALLES AVANZADOS

18- Expanda la sección Detalles avanzados.

19- Para el perfil de instancia de IAM, elija la función que tenga ``LabInstanceProfile`` en el nombre.

Cuando ya no necesite una instancia EC2, puede finalizarla, lo que significa que la instancia se detiene y Amazon EC2 libera los recursos de la instancia. No puede reiniciar una instancia terminada. Si desea evitar que sus usuarios finalicen accidentalmente la instancia, puede activar (habilitar) la protección de terminación para la instancia, lo que evita que los usuarios finalicen instancias.

20- En la lista desplegable `Termination protection`, elija Habilitar.

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

El guión hace lo siguiente:

- Instala un servidor web de Microsoft Internet Information Services (IIS)
- Crea un sitio web sencillo.
- Establece la contraseña para el usuario Administrador


#### Paso 8: LANZAR UNA INSTANCIA EC2

Ahora que ha configurado los ajustes de su instancia EC2, es hora de iniciar su instancia.

22- En la sección `Summary `, elija `Launch instance`.

Un mensaje indica que ha iniciado exitosamente el lanzamiento de su instancia.

23- Elija Ver todas las instancias

La instancia aparece en estado Pendiente, lo que significa que se está lanzando. Luego cambia a En ejecución, lo que indica que la instancia ha comenzado a iniciarse. Pasará un breve periodo de tiempo antes de que puedas acceder a la instancia.

La instancia recibe un nombre público de Sistema de nombres de dominio (DNS) que puede utilizar para comunicarse con la instancia desde Internet.

24- Al lado de su `Web-Server`, seleccione la casilla de verificación. La pestaña Detalles muestra información detallada sobre su instancia.

Para ver más información en la pestaña Detalles, arrastre el divisor de la ventana hacia arriba.

Revise la información que se muestra en las pestañas Detalles, Seguridad y Redes.

25- Espere a que su instancia muestre lo siguiente:

_**Nota:** actualice si es necesario._

- **Estado de instancia:** en ejecución
- **Comprobaciones de estado:** 2/2 comprobaciones aprobadas


### Tarea 2:

### Tarea 3:

### Tarea 4:

### Tarea 5:

### Tarea 6:

### Tarea 7:

## Resumen

En esta práctica de laboratorio, creó una instancia EC2 y aprendió a administrar propiedades de la instancia, como el tipo de instancia. Modificó la configuración del grupo de seguridad para que el sitio web fuera accesible y aprendió a utilizar la protección contra terminación para evitar la eliminación de instancias. Aprendió cómo detener, iniciar y finalizar una instancia EC2. Finalmente, aprendió a encontrar los límites de EC2 para su cuenta de AWS.
