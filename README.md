# CLASE 5 - PROYECTOS CON PYTHON: DEPLOYING DJANGO TO PRODUCTION
---

## Introduccion

Crearemos una aplicacion web local, para luego instalarlo en un servidor web publico para que el personal y miembros de la aplicacion web puedan acceder a él a través de internet. Este ejemplo proporciona una descripcion generaral de como se puede encontrar un host para implementar el sitio web y lo que se debe hacer para que el sitio esté listo para la producción
 
 ### Pre-requisito

 Tener implemento un aplicacion web con el framework Django.

 ### Objetivo

Aprender donde y como se puede desplegar una aplicacion de Django para producción.

### Pasos siguientes:

* Realizar algunos cambios en la configuracion del proyecto
* Elejir un entorno para alojar la aplicacion Django.
* Elejir un entorno para alojar cualquier archivo estático.
* Configurar una estructra de nivel de produccion para servir al sitio web.

### ¿Que es un entorno de produccion?
El entorno de produccion es el entorno proporcionado por la computadora servidor donde se
ejecutara el sitio web para consumo externo. El entorno incluye: 

* Hardware informático en el que se ejecuta el sitio web
* Sistema operativo (por ejemplo, Linux, Windows).
* Bibliotecas de marco y tiempo de ejecución del lenguaje de programación sobre las cuales está escrito su sitio web.
* Servidor web utilizado para servir páginas y otro contenido (por ejemplo, Nginx, Apache).
* Servidor de aplicaciones que pasa solicitudes "dinámicas" entre su sitio web Django y el servidor web.
* Bases de datos de las que depende su sitio web

#### Elegir un proveedor de alojamiento

Hay muchos proveedores de alojamiento que se sabe que respaldan activamente o trabajan bien con Django, incluidos: **Heroku, Digital Ocean, Railway, Python Anywhere, Amazon Web Services, Azure, Google Cloud, Hetzner y Vultr Cloud Compute**, por nombrar solo algunos. pocos. Estos proveedores ofrecen diferentes tipos de entornos (IaaS, PaaS) y diferentes niveles de recursos informáticos y de red a diferentes precios.
Algunas de las cosas a considerar al elegir un anfitrión:
* Qué tan ocupado es probable que esté su sitio y el costo de los datos y los recursos informáticos necesarios para satisfacer esa demanda.
* Nivel de soporte para escalar horizontalmente (agregar más máquinas) y verticalmente (actualizar a máquinas más potentes) y los costos de hacerlo. Donde el proveedor tiene centros de datos y, por tanto, donde es probable que el acceso sea más rápido.
* El rendimiento histórico del tiempo de actividad y del tiempo de inactividad del host.
* Herramientas proporcionadas para administrar el sitio: ¿son fáciles de usar y seguras (por ejemplo, SFTP frente a FTP)?
* Marcos incorporados para monitorear su servidor.
Limitaciones conocidas. Algunos servidores bloquearán deliberadamente ciertos servicios (por ejemplo, correo electrónico). Otros ofrecen solo una cierta cantidad de horas de "tiempo de vida" en algunos niveles de precios, o solo ofrecen una pequeña cantidad de almacenamiento.
* Beneficios adicionales. Algunos proveedores ofrecerán nombres de dominio gratuitos y soporte para certificados TLS que de otro modo tendría que pagar.
* Si el nivel "gratuito" en el que confía caduca con el tiempo y si el costo de migrar a un nivel más caro significa que habría sido mejor utilizar algún otro servicio en primer lugar.

La buena noticia cuando estás empezando es que hay bastantes sitios que ofrecen entornos informáticos "gratuitos" destinados a la evaluación y prueba. Por lo general, estos son entornos con recursos bastante restringidos/limitados, y debe tener en cuenta que pueden caducar después de un período introductorio o tener otras limitaciones. Sin embargo, son excelentes para probar sitios con poco tráfico en un entorno alojado y pueden proporcionar una migración fácil para pagar por más recursos cuando su sitio esté más ocupado. Las opciones populares en esta categoría incluyen Vultr Cloud Compute, Python Anywhere, Amazon Web Services, Microsoft Azure, etc.

### Preparando su sitio Web para Publicar.
El sitio web creado con las herramientas django admin y manage.py esta configurado para facilitar el desarrollo. Muchas de las configuracion del proyecto Django(especificadas en settings.py) deberian ser diferentes para la produccion, ya sea por razones de seguridad o de rendimiento.


Las configuraciones críticas que debes verificar son:
* DEBUG (Falso)
* SECRET_KEY

Los documentos de Django sugieren que es mejor cargar la información secreta desde una variable de entorno o leerla desde un archivo exclusivo del servidor. Cambiemos la aplicación LocalLibrary para que leamos nuestras variables SECRET_KEY y DEBUG de las variables de entorno si están definidas, recurriendo a los valores definidos en un archivo .env en la raíz y, por último, usando los valores predeterminados en el archivo de configuración. Esto es muy flexible ya que permite cualquier configuración soportada por el servidor de hosting.

Para leer los valores del entorno de un archivo usaremos python-dotenv. Esta es una biblioteca para leer pares clave-valor de un archivo y usarlos como variables de entorno, pero solo si la variable de entorno correspondiente no está definida