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