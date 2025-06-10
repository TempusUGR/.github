# TempusUGR: Gestión de Horarios Universitarios

## Descripción

**TempusUGR** es una aplicación de gestión de horarios universitarios diseñada para la **Universidad de Granada (UGR)**. El proyecto nace de la necesidad de modernizar el acceso a la información académica, superando los desafíos de la dispersión de datos y la falta de integración con las herramientas digitales actuales.

El objetivo principal es ofrecer un **servicio de calendario automático y personalizado** para la comunidad universitaria. Permite a estudiantes y profesores, previa autenticación, generar calendarios personalizados seleccionando los grupos de teoría y prácticas correspondientes a su matrícula o docencia.

Una de las características fundamentales es la **interoperabilidad con servicios de calendario externos** como Google Calendar, permitiendo a los usuarios exportar y sincronizar sus horarios para tener acceso a la información en tiempo real y desde cualquier dispositivo. En definitiva, TempusUGR busca optimizar la gestión del tiempo y mejorar la experiencia de la comunidad universitaria, promoviendo una gestión académica más eficiente y centralizada.

---

## Tecnologías Utilizadas

El sistema se ha desarrollado con un stack tecnológico moderno y robusto, separando claramente el backend del frontend.

### **Backend**
* **Lenguaje:** Java (Versión 21) 
* **Framework:** Spring Boot (Versión 3.4.4) y Spring Cloud para una arquitectura de microservicios.
* **Bases de Datos:**
    * **MySQL:** Para el servicio de usuarios y el de horarios.
    * **MongoDB:** Para el servicio de suscripciones académicas, aprovechando su flexibilidad.
* **Comunicación Asíncrona:** RabbitMQ para el intercambio de mensajes entre servicios.
* **Seguridad:** Spring Security con autenticación basada en JWT.
* **Descubrimiento de servicios:** Eureka para permitir que los servicios se registren y descubran entre sí.
* **Web Scraping:** Jsoup para la extracción de datos de horarios desde el portal de la UGR.
* **Contenerización:** Docker para empaquetar los servicios.

### **Frontend**
* **Framework:** Angular (Versión 19.0.2) 
* **Lenguaje:** TypeScript, HTML y CSS.
* **Estilos:** Tailwind CSS.
* **Comunicación con Backend:** Se realizan peticiones HTTP a la API REST del backend utilizando `HttpClient` de Angular.

---

## Arquitectura del Backend

El backend sigue una **arquitectura de microservicios**, descomponiendo la aplicación en servicios independientes, cada uno con una responsabilidad clara y bien definida. Esta arquitectura aporta flexibilidad, escalabilidad y resiliencia.

La comunicación entre los servicios se realiza de forma **síncrona mediante una API REST** y de forma **asíncrona a través de un bus de mensajes con RabbitMQ**. Un **API Gateway** actúa como punto de entrada único para todas las peticiones, gestionando el enrutamiento y la seguridad.

![Arquitectura general del Backend]([https://drive.google.com/file/d/1Xc4zPkO5o3ZRrDZddOkhBNByo8Ul_7Sk/view?usp=drive_link])

---

## Repositorios del Proyecto

El código del proyecto está organizado en varios repositorios dentro de la organización de GitHub [TempusUGR](https://github.com/TempusUGR)[cite: 1602].

### **Frontend**
* [**frontend-repo**](https://github.com/TempusUGR/frontend-repo): Contiene el código fuente de la aplicación cliente desarrollada con Angular.

### **Documentación**
* [**documentation-repo**](https://github.com/TempusUGR/documentation-repo): Incluye la memoria del proyecto y otros documentos relevantes en formato LaTeX.

### **Despliegue**
* [**apache-docker**](https://github.com/TempusUGR/apache-docker): Configuración del servidor web Apache en un contenedor Docker. Funciona como reverse proxy, gestiona los certificados SSL para HTTPS y sirve la aplicación frontend.

### **Backend (Microservicios)**
* [**eureka-service**](https://github.com/TempusUGR/eureka-service): Servidor de descubrimiento de servicios que permite a los demás microservicios registrarse y encontrarse en la red.
* [**user-service**](https://github.com/TempusUGR/user-service): Gestiona toda la información relativa a los usuarios, como perfiles y roles.
* [**auth-service**](https://github.com/TempusUGR/auth-service): Responsable de la autenticación de usuarios y la generación de tokens JWT.
* [**api-gateway**](https://github.com/TempusUGR/api-gateway): Punto de entrada único para todas las peticiones del cliente. Enruta las solicitudes a los servicios correspondientes y gestiona la seguridad.
* [**mail-service**](https://github.com/TempusUGR/mail-service): Servicio encargado del envío de notificaciones por correo electrónico (confirmación de registro, eventos, etc.).
* [**schedule-consumer-service**](https://github.com/TempusUGR/schedule-consumer-service): Realiza el web scraping de los horarios desde la web de la UGR y los almacena.
* [**academic-subscription-service**](https://github.com/TempusUGR/academic-subscription-service): Gestiona las suscripciones de los usuarios a las asignaturas, la creación de eventos y la generación de calendarios personalizados.
* [**docker-compose**](https://github.com/TempusUGR/docker-compose): Contiene scripts en bash para la canstrucción de imágenes y los archivos ".jar", y para la subida de imágenes a docker hub. Además contiene el archivo "docker-compose.yaml" necesario para levantar el backend.
