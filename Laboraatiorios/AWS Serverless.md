# Laboratorio: Introducción a AWS Lambda

## Descripción general y objetivos del laboratorio

En esta práctica de laboratorio, creará y configurará una función de AWS Lambda que se iniciará cuando se cargue una imagen en un depósito de Amazon Simple Storage Service (Amazon S3). Revisa los registros relacionados para determinar cómo se está desempeñando la función. Modifica la configuración de la función para optimizar el rendimiento.

### Objetivos

Después de completar esta práctica de laboratorio, sabrá cómo hacer lo siguiente:

- Cree una función Lambda.
- Configure un disparador S3 en una función Lambda.
- Observe los registros y las métricas de una función Lambda para determinar el rendimiento.
- Dimensione y configure una función Lambda para un rendimiento óptimo.


### Restricciones del servicio de AWS

En este entorno de laboratorio, el acceso a los servicios y acciones de servicio de AWS puede estar restringido solo a aquellos que necesita para completar las instrucciones del laboratorio. Es posible que encuentre errores si intenta acceder a otros servicios o realizar acciones distintas a las que describe esta práctica de laboratorio.

## Solución del laboratorio

### Tarea 1: crear una función Lambda

1- En la Consola de administración de AWS, en el menú Servicios, ingrese Lambda. En los resultados de la búsqueda, elija Lambda.

2- Elija Crear función.

3- Edite lo siguiente:

- **Nombre de la función:** ``resize_image``
- **Runtime:** Python3.9

4- Expanda la sección ``Cambiar función de ejecución predeterminada``. Elija ``Usar un rol existente``. En la lista desplegable de Función existente, elija ``ResizeImageLambdaRole``.

5- Elija Crear función.

6- Desplázate hasta la sección Capas.

7- Elija Agregar una capa.

8- Elija capas personalizadas.

9- En la lista desplegable Capas personalizadas, elija ``PillowPythonLambdaLayer``.

10- En la lista desplegable Versión, elija 1 o la opción con el número de versión más alto.

11- Elija Agregar.

12- Desplácese hasta la sección Código fuente de la página.

13- Copie el código siguiente y reemplace el código fuente predeterminado en el archivo ``lambda_function.py`` con él.

    import boto3
    import os
    import sys
    import uuid
    from urllib.parse import unquote_plus
    from PIL import Image
    import PIL.Image

    s3_client = boto3.client('s3')

    def resize_image(image_path, resized_path):
       with Image.open(image_path) as image:
          image.thumbnail(tuple(x / 2 for x in image.size))
          image.save(resized_path)

    def lambda_handler(event, context):
       print('Begin resizing image')
       for record in event['Records']:
          bucket = record['s3']['bucket']['name']
          key = unquote_plus(record['s3']['object']['key'])
          print(bucket)
          print(key)
          tmpkey = key.replace('/', '')
          download_path = '/tmp/{}{}'.format(uuid.uuid4(), tmpkey)
          upload_path = '/tmp/resized-{}'.format(tmpkey)
          s3_client.download_file(bucket, key, download_path)
          resize_image(download_path, upload_path)
          s3_client.upload_file(upload_path, os.environ['RESIZED_BUCKET'], key)
       print('Resizing image complete')

14- Para implementar su función Lambda, elija Implementar.

15- Elija la pestaña Configuración y luego elija Configuración general. Elija Editar.

16- En el campo Memoria, ingrese ``512 MB``. Luego, elija Guardar.

17- En la parte superior de estas instrucciones, elija ``Detalles``. Junto a AWS, elija ``Mostrar``. Copie el valor junto a ``ResizedBucketName``. Úselo como valor en el paso 21.

18- En la Consola de administración de AWS, elija Variables de entorno.

19- Elija Editar.

20- Elija Agregar variable de entorno.

21- Introduzca los siguientes valores:

   - **Clave:** ``RESIZED_BUCKET``
   - **Valor:** Ingrese el valor que recuperó en el paso 17.

22- Elija Guardar.

Has creado una función Lambda.

