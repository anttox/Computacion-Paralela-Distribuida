# AWS LAB1
## TASK1: Creamos una plantilla y una pila de CloudFormation en un deposito S3
La plantilla de Cloudformation es un modelo
La pila de CloudFormation crea un deposito S3 -> ade-s3lab-bucket Y una politifa de IAM -> Policy-For-Data-Scientists
La pila de CloudFormation (Instancia real)  crea y gestiona el estado y dependencias de los recursos de la plantilla
IAM:servicio web para controlar de forma segura el acceso a los recursos de AWS
aws s3 list-buckets: comando para interactuar con un deposito S3
Wget: recupera el conjunto de datos orginales
aws s3 cp: comando para copiar el conjunto de datos en un deposito S3 -> ade-s3lab-bucket
Cifrar el archivo S3 mediante claves administradas -> SSE-S3
Cloud9: sirve para crear una platilla de CloudFormation y la plantilla nos sirve para crear la pila de CloudFormation
Comando para validar plantilla de CloudFormation: aws cloudformation validate-template --template-body file://create_bucket.yml
Comando pa crear pila de CloudFormation: aws cloudformation create-stack --stack-name ade-my-bucket  --template-body file://create_bucket.yml
Este comando incluye un ARN (Nombre de recurso de Amazon)
Comando para verificar los recursos creados de la pila: aws s3api list-buckets
Eliminar pila -> se elimina todos los recursos que contiene el deposito -> tambien se elimina el deposito creado
Comando para eliminar pila: aws cloudformation delete-stack --stack-name ade-my-bucket
Comando para confirmar si la pila ha sido eliminada: aws cloudformation list-stacks
Comando para verificar si el deposito se elimino: aws s3api list-buckets

![TASK1](https://cdn.discordapp.com/attachments/1030129034593579012/1233957449221013634/image.png?ex=6636e4ed&is=6635936d&hm=b5afa3b6bb589dc94508acde7fbad0172b49fb783bf0ba5e044d0e8baab67a67&)

## TASK2: Cargar un conjunto de datos en un deposito S3 (Descargamos y descomprimimos un conjunto de datos de muestra)
Comando para descargar archivo .csv en un archivo ZIP: wget https://aws-tc-largeobjects.s3.us-west-2.amazonaws.com/CUR-TF-200-ACDSCI-1-DEV/lab-01-s3/code.zip -P /home/ec2-user/environment
Comando para descomprimir archivo ZIP: unzip code.zip
Comando para recuperar el nombre del deposito S3: aws s3api list-buckets
Comando para copiar el archivo .csv en el eposito S3: aws s3 cp lab1.csv s3://<LAB-BUCKET-NAME>
Comando para verificar la operacion: aws s3 ls s3://<LAB-BUCKET-NAME>

![TASK2](https://cdn.discordapp.com/attachments/1030129034593579012/1233967238319443968/image.png?ex=6636454b&is=6634f3cb&hm=6350df6359f953bfaee3e99bf4d20b4707446afdadf79ee2ee9ecb544ba225ed&)

## TASK3: Configurar infraestructura de un deposito S3 mediante un proceso repetible en CloudFormation, usaremos S3 Select para consultar el conjunto de datos
Pasos: Search -> S3 -> Buckets -> choose lab1.csv -> choose Object Actions -> Query (consulta) with S3 Select
Para ver los datos en forma tabular elegir la pestaña: FORMATTED
Amazon Select S3 solo funciona para objetos comprimidos con GZIP o BZIP2

![TASK3.1](https://cdn.discordapp.com/attachments/1030129034593579012/1233971846584598578/image.png?ex=66364996&is=6634f816&hm=8b475ed07c73a3ba1d7d8cf3b33490a30f9715f114e8cdf5cbebc233a422df85&)

![TASK3.2](https://cdn.discordapp.com/attachments/1030129034593579012/1233972063719653437/image.png?ex=663649ca&is=6634f84a&hm=e824d8c312420823a92e5ccfa28e177b6daf5887cd4263e78c191469d757b7b6&)

## TASK4: Cifrar datos con Amazon S3 -> usar cifrado del lado del servidor, modificar clase alamacenamiento
CLI: configurar el cifrado en reposo y el tipo de clase de almacenamiento
Las claves que admiten son: SSE-S3 y AWS Key Management Servise (AWS KMS) o conocidas como SSE-KMS
Cifrado del lado del servidor (permite mejorar la seguridad de mis datos almacenados en Amazon S3 cuando esta en reposo -> cada obejto tiene una clave unica, si usamos claves de AWS KMS, los objetos se cifraran con claves unicas pero nosotros aministriraremos las claves
Estandar de cifrado de 256 bits (AES-256): se aplica automáticamente a todos los depósitos nuevos y a cualquier depósito S3 existente que aún no tenga configurado el cifrado predeterminado
Pasos para modficar la clase de almacenamiento: Search -> S3 -> Buckets -> choose lab1.csv -> choose Object Actions -> Edit storage class -> choose Intelligent-Tiering
Clase de almacenamiento Intelligent-Tiering: Se asegura que los costos se optimicen par todos los datos almacenados en el objeto S3

![TASK4](https://cdn.discordapp.com/attachments/1030129034593579012/1233977259711266877/image.png?ex=66364ea0&is=6634fd20&hm=56e01b8c823098d0c0a3ce3cb984488fa42a741055d1d190103aae872d50a581&)

## TASK5: Usaremos el formato GZIP para comprimir el archivo de datos y compararemos el tamaño con el archivo comprimido con ZIP
Cargaremos el archivo GZIP en el deposito S3 y luego confirmaremos si se puede usar S3 Select para consultar el archivo comprimido
Comando para comprimir el archivo en formato ZIP: zip lab lab1.csv
Comando para comprimir el archivo lab.csv en formato GZIP: gzip -v lab1.csv
Comando para enumerar objetos del directorio: ls -la
Comando para cargar el conjunto de datos (DATASET) en el deposito (bucket) S3: aws s3 cp lab1.csv.gz s3://<LAB-BUCKET-NAME> --cache-control max-age=60
--cache-control: especificia el comportamiento de almacenamiento en cache del obejto a lo largo de la cadena solicitud/respuesta
Pasos par verificar si podemos usar S3 Select: S3 -> buckets -> choose lab1.csv.gz -> Acciones de objetos -> Consultar con S3 Select

![TASK5.1](https://cdn.discordapp.com/attachments/1030129034593579012/1233994773526876170/image.png?ex=66365ef0&is=66350d70&hm=c8dc98adefa5861e4d1290753d919ba414cd80851ded14f728062e62fc7957da&)

![TASK5.2](https://cdn.discordapp.com/attachments/1030129034593579012/1233994773900300378/image.png?ex=66365ef0&is=66350d70&hm=41007a200b6c7f7236d55e7ca7699dfa3b629d3fe1baec8dbb4dbcc7ecb55258&)

## TASK6: Revisar grupo IAM del equipo de ciencia de datos y la politica de IAM asociada
Tomar acciones para determinar si el grupo y la politica tienen permisos para acceder al conjunto de datos Amazon S3.
Pasos: IAM -> Grupo de usuarios -> permisos
La plantilla de CloudFormation que creó los recursos en su entorno de laboratorio genera la clave de acceso y la clave de acceso secreta para el usuario
Comando para crear una variable para la clave de acceso: AK=<ACCESS-KEY>
Comando para crear una variable papra la clave de acceso secreta: SAK=<SECRET-ACCESS-KEY>
Comando para probar si el usuario puede ejecutar un comando AWS CLI para el servicio Amazon Elastic Compute Cloud (Amazon EC2): AWS_ACCESS_KEY_ID=$AK AWS_SECRET_ACCESS_KEY=$SAK aws ec2 describe-instances --region us-east-1
Comando para probar si el usuario puede ejecutar comandos de AWS CLI en un objeto S3: AWS_ACCESS_KEY_ID=$AK AWS_SECRET_ACCESS_KEY=$SAK aws s3api get-object --bucket <LAB-BUCKET-NAME> --key lab1.csv --region us-east-1 pulled_lab.csv
Dato Task6: Comprender cómo IAM autentica y autoriza a los usuarios es importante cuando se utilizan canalizaciones de datos para sus datos en AWS. Quiere asegurarse de que solo las personas que tienen una necesidad crítica puedan acceder y modificar los datos

![TASK6.1](https://cdn.discordapp.com/attachments/1030129034593579012/1234007037940338688/image.png?ex=66366a5c&is=663518dc&hm=fb14bf0a776a37826c417265d2c81ab47d6b8a06ec60467fbda65829a001b074&)

![TASK6.2](https://cdn.discordapp.com/attachments/1030129034593579012/1234007038347055124/image.png?ex=66366a5c&is=663518dc&hm=f24b8194be2283dcd96135b3778d6532b8f43dbfe5aad861b2b65c9fbe96be56&)
