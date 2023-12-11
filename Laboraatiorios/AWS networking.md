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


