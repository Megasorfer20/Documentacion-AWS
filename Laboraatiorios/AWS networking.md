# INTRODUCCIÓN NETWORKING EN AWS

## Como Ingresar al Laboratorio

1- Ingresa a tu cuenta de AWS educate

2- Entra al siguiente curso 


![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/6170511b-89db-404a-9ca0-c911ac541122)


3- Entra al apartado de Contenidos


<img width="884" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/1f57bb04-5e68-48a7-91b7-24b4eabef87e">


4- Entra al apartado de "Get Started With Networking Lab"


<img width="682" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/affd1ff6-ddf3-475f-964b-395822d1cc4c">


5- Selecciona la opcion de Inicar el laboratorio


<img width="875" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/8aee9d65-a9dc-4531-add7-78b700a9be62">


6- Después de que se abra la nueva ventana se leerán las instrucciones y luego de eso le darás a iniciar laboratorio


<img width="957" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/8cdfed9c-136c-457e-b463-9378f22c9999">


7- Sabrás que hiciste todo correctamente si te sale esto, debes esperar unos minutos y proseguir


<img width="953" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/7a3a3443-be6a-460c-8f99-8eb656fb0ed0">



## Desarrollo del laboratorio

### Localizaciones y conceptos básicos

1- Selecciona la opción AWS que sale en la pantalla y te redireccionara a la siguiente página


<img width="362" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/92826d92-97e5-4d68-b8a2-c19c266d8ac2">
<img width="937" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/331f70f7-7894-4a50-a4c5-be1f6f0746b9">


2- En el buscador pon VPC y selecciona la opción resaltada


<img width="958" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/8a8502af-f47c-4a1e-b858-9c00f0d35ad1">


3- Dale click a "Selecciona tu VPC" y luego selecciona la VPC de ejemplo, luego da un click a "Sus VPC" para ver las especificaciones


<img width="942" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/0e955710-2ac9-4afe-b199-0c768275cf66">

<img width="170" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/b7492512-5f2c-4d9b-8f4b-7ae556ebc7ba">

<img width="170" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/ed0b11f5-d2b0-4397-8b49-c56de6810d87">


4- Revisa las especificaciones como la máscara de red que por defecto está configurada en `` 172.31.0.0/16 `` y la ID del VPC, en este caso es `` vpc-0c8afb78625ec5c8b ``


<img width="748" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/c6d3f52e-62ee-4e8f-9dcc-205edcfe61af">


5- En el panel de navegación escoge el "Subnet" o "Suberedes"


![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/f13661c7-8bf5-41b2-bd4c-e714d7530e3b)


6- Selecciona la opción `` Public Subnet 1 ``

<img width="740" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/e679d23c-b13d-4e90-b85f-353ec891d7f4">

7- Revisa si la auto asignación de IP pública está activada, en el caso que no, actívala. Esto será para poder asignar una IP a toda instancia que se ingrese en esa subred.

<img width="746" alt="image" src="https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/3aff6669-fd62-489f-84e9-e014e5afb805">

8- En el panel de navegacion selecciona `` Internet Gateways ``

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/b5301e1c-09cd-4d4f-88e6-eecc9980f29d)

9- Selecciona el gateway llamado `` Internet Gateway `` y verifica que su estado sea `` Attached `` y grabate el ID que se usará más adelante, en este caso es `` igw-0d9f6bb2b826a8204 ``

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/547b9d07-3bb6-40e1-b176-ae657d5331d5)


10- En el panel de navegacion selecciona `` Route Tables ``

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/861aca20-66ff-428d-b8ba-415c84d6d18e)

11- Selecciona la Tabla de enrutamiento llamada ``  `` y seleccionala. 

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/f757fc20-7707-4e39-bea8-6012976f99b5)

12- En la parte inferior selecciona la pestaña de Rutas
Aquí se podrán ver dos rutas, una pública la cual es `` 0.0.0.0/0 `` para el Gateway y una local que es `` 172.31.0.0/16 `` que perite a las VPC comunicarse entre si.

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/f166b057-b7a2-44bd-9557-ab1c9490c574)


13- Selecciona la pestaña de `` Subnet associations ``

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/ce4d408c-3977-4c7f-ac94-713bf4834e82)

14 - Revisa si la IPv4 CIDR `` 172.31.0.0/20 `` está incluida en la lista. La cual es la misma subred que se vizualizo anteriormente.

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/5e63da07-69e9-4119-8202-fe05cf285139)

15- Selecciona el panel de `` Segurity groups ``

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/62f555fa-2dc0-4905-82dc-c1a7c4e9b955)

16- Vas a seleccionar la fila que tenga el grupo de seguridad por defecto, allí tndrás que localizar el ID del VPC que se usó anteriormente.

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/19b41b98-3ad9-470f-b697-76df4d2e4ee2)

17- Entra a la pestaña `` Outbound rules `` donde encontrarás todos los protocolos y todos los rangos para enviarle tráfico a cualquier dirección IP

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/d7fff375-2ea5-44e5-9e10-a27827c55167)

18- Entra a la pestaña `` Inbound rules `` donde encontrarás una sola regla para enviarle tráfico a todos los protocolos y todos los rangos de recursos que usen el grupo de seguridad.

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/f058bbb2-11d2-42d4-8088-d9364238aabb)

19- Localice la fila que contiene el grupo de seguridad Web-Server-SG para la VPC de ejemplo y selecciónela

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/d196e5f7-52d8-4c87-8704-8f80b8764c1d)

20- Entra a la pestaña `` Inbound rules ``

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/1e13c596-b898-47a0-a134-e9de76b74f19)

21- Ahora haz click en `` Editar reglas de Entrada ``

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/cfb07ecc-1a74-40b1-8fd0-3697c5ec0d96)

22- Se te redireccionará a una nueva pestaña, ahora hz click en `` Add Rule ``

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/aa50d593-7869-45cd-8eb1-eae2c0917463)

23- Configura de la siguiente manera la regla, y luego guarda los cambios 

  A- Para `` Type `` , selecciona `` HTTP `` 

  B- Para `` Source type `` , selecciona `` Anywhere IPv4 `` 
  
  C- Para `` Description `` , selecciona `` Allow web access `` 
  

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/602c7847-3846-4048-9d4d-877686ba62a7)

24- Ve a la ventana de servicios y luego selecciona EC2

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/8fd0e095-e5b9-4d65-8629-84f22947f77e)

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/edf41ba4-6747-4cb6-a516-84a0b81d5c31)


25- Selecciona el campo de `` Instances (Running) `` y luego selecciona `` Web Server ``, para que en su pestaña de datalles localices que se desplegó en ek VPC de ejemplo, viendo que tiene su ID. También tiene el valor de la Subred donde se desplegó.

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/e07aa49b-9278-4f64-8215-4a51c24c4f5e)

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/c16dac7e-7e78-4895-a49b-4a34293ba3a9)

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/d6dbe0ff-44c6-4ca0-9818-859a8b6691d6)


16- De la pestaña de detalles copia la dirección IPv4 pública, para abrirla en una nueva ventana del navegador, al darle enter verás que saldrá un mensaje de  `` Hello from your webserver! ``

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/eccbe827-ee30-48ce-9848-f700234e6877)

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/8e6abdc3-f1cb-4657-9057-ec20aec0be2f)

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/dae9d1bf-a313-4744-a7dc-5791f13ba7d8)


### Creando y Configurando mi VPC

1- Entra a el apartado de VPC y selecciona en Crear VPC

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/d016477f-6579-4b15-85a2-21ccf6536764)

2- Se va configurar la VPC de la siguiente manera, y luego le darás click a `` Crear VPC ``

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/c3323179-0ddd-44e0-961c-f19210af555f)

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/3a089708-32e6-4afb-8d5d-b8f9d3ae9408)

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/d2863892-a70b-434a-bfa1-af65154df6d6)

3- Te deberá salir una pestaña como esta, habrá un link al que le deberias dar click que te va a redireccionar a la página de la consola donde se creó tu VPC

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/567fb7f6-7670-40ea-8da2-71d1f4b8133e)

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/d8265c64-ea5e-4a62-945d-d617648d27bf)

**A partir de aqupi por funciones bloqueadas por AWS Educate no se pudo avanzar correctamente en el laboratorio, por lo que solo voy a traducir el paso a paso de las instrucciones restantes**

4- Localice la fila que contiene el grupo de seguridad Web-Server2-SG para la VPC de ejemplo y selecciónela

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/d196e5f7-52d8-4c87-8704-8f80b8764c1d)

5- Entra a la pestaña `` Inbound rules ``

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/1e13c596-b898-47a0-a134-e9de76b74f19)

6- Ahora haz click en `` Editar reglas de Entrada ``

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/cfb07ecc-1a74-40b1-8fd0-3697c5ec0d96)

7- Se te redireccionará a una nueva pestaña, ahora hz click en `` Add Rule ``

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/aa50d593-7869-45cd-8eb1-eae2c0917463)

8- Configura de la siguiente manera la regla, y luego guarda los cambios 

  A- Para `` Type `` , selecciona `` HTTP `` 

  B- Para `` Source type `` , selecciona `` Anywhere IPv4 `` 
  
  C- Para `` Description `` , selecciona `` Allow web access `` 
  

![image](https://github.com/Megasorfer20/Documentacion-AWS/assets/123566003/602c7847-3846-4048-9d4d-877686ba62a7)


