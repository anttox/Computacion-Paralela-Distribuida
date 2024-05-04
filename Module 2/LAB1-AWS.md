# TASK1: Creamos una plantilla y una pila de CloudFormation en un deposito S3
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
