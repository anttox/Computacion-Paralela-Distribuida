# Sobre la linea de comandos

Linux, siendo un sistema operativo tipo Unix, es ampliamente utilizado en servidores,
supercomputadoras y sistemas distribuidos. Conocer la línea de comandos de Linux permite
comprender y manipular el sistema operativo subyacente en el que se ejecutan sus
aplicaciones concurrentes y distribuidas, ofreciendo una comprensión profunda de su
entorno de ejecución.
La línea de comandos de Linux es una herramienta poderosa para la automatización de
tareas repetitivas y la gestión eficiente de recursos del sistema. Podemos aprender a
escribir scripts para automatizar la compilación y ejecución de sus programas, la gestión de
procesos, el monitoreo del uso de recursos y la implementación de sistemas. Esta habilidad
es invaluable en entornos de computación distribuida, donde la gestión manual de múltiples
nodos y servicios puede ser tediosa y propensa a errores.
Muchas herramientas esenciales para el desarrollo, la prueba y la depuración de software
en computación concurrente y distribuida son accesibles a través de la línea de comandos.
Esto incluye herramientas para control de versiones (como git), empaquetado y despliegue
de software (como make y docker), y monitoreo de rendimiento y recursos (como top,
vmstat, y netstat). Familiarizarse con estas herramientas es esencial para el desarrollo de
software eficiente.
El conocimiento de la línea de comandos es fundamental para interactuar con servicios en
la nube y sistemas distribuidos, muchos de los cuales ofrecen interfaces basadas en CLI
(Command Line Interface) para su gestión y configuración. Aprenderemos a desplegar,
configurar y monitorear aplicaciones distribuidas en entornos cloud, utilizando la línea de
comandos.
La línea de comandos promueve un entendimiento más profundo de cómo funcionan los
computadores y las redes, alentando a todos a pensar y resolver problemas de manera
algorítmica. Esta forma de pensamiento es transferible a muchos otros ámbitos de la
informática y la ingeniería de software.

## Contenido

- What is "the Shell"?
- Navigation
- Looking Around
- A Guided Tour
- Manipulation Files
- Working with Commands
- I/O Redirection
- Expansion
- Permissions
- Job Control

[What is "the Shell"?](https://private-user-images.githubusercontent.com/118635410/322629604-44b854db-acc6-4b96-b2ac-68f8212168d4.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3MTMyMTU3MzQsIm5iZiI6MTcxMzIxNTQzNCwicGF0aCI6Ii8xMTg2MzU0MTAvMzIyNjI5NjA0LTQ0Yjg1NGRiLWFjYzYtNGI5Ni1iMmFjLTY4ZjgyMTIxNjhkNC5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjQwNDE1JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI0MDQxNVQyMTEwMzRaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT0yZWQyZGNkYTM5MTcxOGY2OTcxNmViNTA2MzYwZDc2MzUyNTdmMWE5MTFiODhmZjZkNmFiYzc1NWZmMzFhN2Y1JlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCZhY3Rvcl9pZD0wJmtleV9pZD0wJnJlcG9faWQ9MCJ9.M-eCLPELY0DhYBV2eBoF-f-k7dt6Inwf3vm0_9ONEjo)

[Navigation1](https://private-user-images.githubusercontent.com/118635410/322632675-f817780a-7418-4945-8a58-3170a43cb85b.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3MTMyMTYzNTksIm5iZiI6MTcxMzIxNjA1OSwicGF0aCI6Ii8xMTg2MzU0MTAvMzIyNjMyNjc1LWY4MTc3ODBhLTc0MTgtNDk0NS04YTU4LTMxNzBhNDNjYjg1Yi5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjQwNDE1JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI0MDQxNVQyMTIwNTlaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT1mNmFlZTIxYmYzMThkZTRhMTkyZDkxMTkwNzdmNGVkMmQwYTg3ZDcxMDZmMDA4NzExYmE2ZTY5NjA5NWQyNWZkJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCZhY3Rvcl9pZD0wJmtleV9pZD0wJnJlcG9faWQ9MCJ9.i6fmn0b4jK_hoD1CTL0xM949hywEuUgolL_sv9RExuM)( 
