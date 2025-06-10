# TempusUGR: Gestión de Horarios Universitarios

## Descripción

[cite_start]**TempusUGR** es una aplicación de gestión de horarios universitarios diseñada para la **Universidad de Granada (UGR)**. [cite_start]El proyecto nace de la necesidad de modernizar el acceso a la información académica, superando los desafíos de la dispersión de datos y la falta de integración con las herramientas digitales actuales.

[cite_start]El objetivo principal es ofrecer un **servicio de calendario automático y personalizado** para la comunidad universitaria. [cite_start]Permite a estudiantes y profesores, previa autenticación, generar calendarios personalizados seleccionando los grupos de teoría y prácticas correspondientes a su matrícula o docencia.

[cite_start]Una de las características fundamentales es la **interoperabilidad con servicios de calendario externos** como Google Calendar, permitiendo a los usuarios exportar y sincronizar sus horarios para tener acceso a la información en tiempo real y desde cualquier dispositivo. [cite_start]En definitiva, TempusUGR busca optimizar la gestión del tiempo y mejorar la experiencia de la comunidad universitaria, promoviendo una gestión académica más eficiente y centralizada.

---

## Tecnologías Utilizadas

[cite_start]El sistema se ha desarrollado con un stack tecnológico moderno y robusto, separando claramente el backend del frontend.

### **Backend**
* [cite_start]**Lenguaje:** Java (Versión 21) 
* [cite_start]**Framework:** Spring Boot (Versión 3.4.4) y Spring Cloud para una arquitectura de microservicios.
* **Bases de Datos:**
    * [cite_start]**MySQL:** Para el servicio de usuarios y el de horarios.
    * [cite_start]**MongoDB:** Para el servicio de suscripciones académicas, aprovechando su flexibilidad.
* [cite_start]**Comunicación Asíncrona:** RabbitMQ para el intercambio de mensajes entre servicios.
* [cite_start]**Seguridad:** Spring Security con autenticación basada en JWT.
* [cite_start]**Descubrimiento de servicios:** Eureka para permitir que los servicios se registren y descubran entre sí.
* [cite_start]**Web Scraping:** Jsoup para la extracción de datos de horarios desde el portal de la UGR.
* [cite_start]**Contenerización:** Docker para empaquetar los servicios.

### **Frontend**
* [cite_start]**Framework:** Angular (Versión 19.0.2) 
* [cite_start]**Lenguaje:** TypeScript, HTML y CSS.
* [cite_start]**Estilos:** Tailwind CSS.
* [cite_start]**Comunicación con Backend:** Se realizan peticiones HTTP a la API REST del backend utilizando `HttpClient` de Angular.

---

## Arquitectura del Backend

[cite_start]El backend sigue una **arquitectura de microservicios**, descomponiendo la aplicación en servicios independientes, cada uno con una responsabilidad clara y bien definida. [cite_start]Esta arquitectura aporta flexibilidad, escalabilidad y resiliencia.

[cite_start]La comunicación entre los servicios se realiza de forma **síncrona mediante una API REST** y de forma **asíncrona a través de un bus de mensajes con RabbitMQ**. [cite_start]Un **API Gateway** actúa como punto de entrada único para todas las peticiones, gestionando el enrutamiento y la seguridad.

![Arquitectura general del Backend](https://i.imgur.com/G4nS23N.png)

---

## Repositorios del Proyecto

[cite_start]El código del proyecto está organizado en varios repositorios dentro de la organización de GitHub [TempusUGR](https://github.com/TempusUGR)[cite: 1602].

### **Frontend**
* [**frontend-repo**](https://github.com/TempusUGR/frontend-repo): Contiene el código fuente de la aplicación cliente desarrollada con Angular.

### **Documentación**
* [**documentation-repo**](https://github.com/TempusUGR/documentation-repo): Incluye la memoria del proyecto y otros documentos relevantes en formato LaTeX.

### **Despliegue**
* [cite_start][**apache-docker**](https://github.com/TempusUGR/apache-docker): Configuración del servidor web Apache en un contenedor Docker. [cite_start]Funciona como reverse proxy, gestiona los certificados SSL para HTTPS y sirve la aplicación frontend.

### **Backend (Microservicios)**
* [cite_start][**eureka-service**](https://github.com/TempusUGR/eureka-service): Servidor de descubrimiento de servicios que permite a los demás microservicios registrarse y encontrarse en la red.
* [cite_start][**user-service**](https://github.com/TempusUGR/user-service): Gestiona toda la información relativa a los usuarios, como perfiles y roles.
* [cite_start][**auth-service**](https://github.com/TempusUGR/auth-service): Responsable de la autenticación de usuarios y la generación de tokens JWT.
* [cite_start][**api-gateway**](https://github.com/TempusUGR/api-gateway): Punto de entrada único para todas las peticiones del cliente. [cite_start]Enruta las solicitudes a los servicios correspondientes y gestiona la seguridad.
* [cite_start][**mail-service**](https://github.com/TempusUGR/mail-service): Servicio encargado del envío de notificaciones por correo electrónico (confirmación de registro, eventos, etc.).
* [cite_start][**schedule-consumer-service**](https://github.com/TempusUGR/schedule-consumer-service): Realiza el web scraping de los horarios desde la web de la UGR y los almacena.
* [cite_start][**academic-subscription-service**](https://github.com/TempusUGR/academic-subscription-service): Gestiona las suscripciones de los usuarios a las asignaturas, la creación de eventos y la generación de calendarios personalizados.
