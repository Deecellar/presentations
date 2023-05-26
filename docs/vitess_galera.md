---

marp: true
class:
  + invert
size: 16:9
paginate: true

---

# Vitess, Galera, Bases de datos distribuidas

### Dan Ellis Echavarria 2023

---

# Introducción a Vitess
![image](https://github.com/Deecellar/presentations/assets/12878831/f1f68be0-37af-457f-84cd-236e48b2bbc7)

---

## ¿Qué es Vitess?

- Vitess es un sistema de escalado horizontal y fragmentación de bases de datos de código abierto.
- Diseñado originalmente por YouTube para manejar su escala masiva de datos.
- Ahora es mantenido y utilizado por la Cloud Native Computing Foundation (CNCF).

---

## Características principales

- Escalado horizontal: Vitess permite escalar una base de datos MySQL existente a través de múltiples servidores.
- Fragmentación: Divide los datos en fragmentos más pequeños, distribuyéndolos en diferentes servidores para mejorar la escalabilidad y el rendimiento.
- Transparencia de fragmentación: Las aplicaciones pueden seguir accediendo a la base de datos de manera transparente sin conocer la fragmentación subyacente.
- Shard Management: Vitess maneja automáticamente la asignación de consultas a los fragmentos correctos.
- Resiliencia: Ofrece tolerancia a fallos y recuperación automática en caso de errores o caídas de los servidores.

---

## Beneficios de Vitess

- Escalabilidad: Permite escalar la base de datos sin modificar la lógica de la aplicación.
- Rendimiento: Distribuye la carga de trabajo en múltiples servidores, lo que mejora el rendimiento y reduce la latencia.
- Alta disponibilidad: Proporciona mecanismos de redundancia y failover para garantizar la disponibilidad continua de los datos.
- Operaciones simplificadas: Vitess facilita la administración de bases de datos distribuidas, proporcionando herramientas para la gestión de fragmentos y configuración.

---

## Casos de uso

- Grandes volúmenes de datos: Vitess es ideal para aplicaciones con millones o incluso miles de millones de filas de datos.
- Aplicaciones web y móviles: Escala la base de datos detrás de aplicaciones populares que requieren un alto rendimiento y una disponibilidad constante.
- Microservicios: Vitess puede adaptarse bien a entornos de microservicios, donde cada servicio puede tener su propia base de datos fragmentada.

---

## Comunidad y adopción

- Vitess tiene una comunidad activa y creciente de desarrolladores y usuarios.
- Es parte de la CNCF, lo que garantiza su apoyo y desarrollo continuo.
- Empresas conocidas, como YouTube, Slack y Square, utilizan Vitess en producción.

---

## Recursos adicionales

- Sitio web oficial de Vitess: [Enlace al sitio web](https://vitess.io)
- Documentación: Amplia documentación disponible para ayudar con la instalación, configuración y uso de Vitess.
- Repositorio de GitHub: El código fuente de Vitess está disponible en GitHub para contribuciones y seguimiento de problemas.

---

## Conclusión

- Vitess es una solución poderosa para escalar y fragmentar bases de datos MySQL.
- Ofrece beneficios significativos en términos de escalabilidad, rendimiento y disponibilidad.
- Si tienes una aplicación que necesita escalar su base de datos, Vitess puede ser la solución adecuada.

--- 


<!-- Título de la presentación -->
# Introducción a Galera Cluster
## Una solución de clustering de bases de datos altamente disponible

![Galera Cluster](https://github.com/Deecellar/presentations/assets/12878831/ddcdeeab-00b4-4040-93a7-8f549c5ba057)
---

<!-- Slide: ¿Qué es Galera Cluster? -->
# ¿Qué es Galera Cluster?
- Galera Cluster es una solución de clustering de bases de datos multi-maestro síncrona para sistemas de gestión de bases de datos relacionales.
- Permite la replicación y la sincronización de datos en tiempo real entre varios nodos de base de datos.

---

<!-- Slide: Características principales de Galera Cluster -->
# Características principales de Galera Cluster
- Replicación multi-maestro: Todos los nodos pueden aceptar tanto lecturas como escrituras.
- Sincronización en tiempo real: Los datos se replican de manera síncrona entre los nodos para garantizar la consistencia.
- Tolerancia a fallos: Si un nodo falla, el clúster sigue funcionando sin interrupciones.
- Escalabilidad horizontal: Se pueden agregar nuevos nodos al clúster para aumentar la capacidad de almacenamiento y el rendimiento.

---

<!-- Slide: Arquitectura de Galera Cluster -->
# Arquitectura de Galera Cluster
![Arquitectura](https://github.com/Deecellar/presentations/assets/12878831/13489e3f-2801-4a7e-9650-d19c99fb7db5)

---

<!-- Slide: Requisitos de hardware y software -->
# Requisitos de hardware y software
- Galera Cluster es compatible con sistemas operativos basados en Linux, como Ubuntu, CentOS y Red Hat.
- Se requiere una red de baja latencia y alta velocidad para una replicación eficiente.
- Cada nodo debe tener suficiente memoria, capacidad de almacenamiento y potencia de procesamiento para manejar la carga de trabajo.

---

<!-- Slide: Casos de uso de Galera Cluster -->
# Casos de uso de Galera Cluster
- Alta disponibilidad: Garantiza que la base de datos esté siempre disponible incluso en caso de fallos en los nodos individuales.
- Escalabilidad: Permite agregar nuevos nodos para aumentar la capacidad de la base de datos a medida que crece la carga de trabajo.
- Balanceo de carga: Distribuye las solicitudes de lectura y escritura entre los nodos para un rendimiento óptimo.

---

<!-- Slide: Ventajas de Galera Cluster -->
# Ventajas de Galera Cluster
- Alta disponibilidad y tolerancia a fallos.
- Sincronización en tiempo real para garantizar la consistencia de los datos.
- Escalabilidad horizontal sin interrupciones del servicio.
- Fácil configuración y administración.

---

<!-- Slide: Conclusiones -->
# Conclusiones
- Galera Cluster es una solución de clustering de bases de datos altamente disponible y escalable.
- Proporciona replicación síncrona y en tiempo real para garantizar la consistencia de los datos.
- Es una opción ideal para aplicaciones que requieren alta disponibilidad, escalabilidad y rendimiento.

---

# Comparación entre Galera Cluster y Vitess

---

## Galera Cluster

- Solución de clustering de bases de datos multi-master sincrónica.
- Arquitectura de replicación peer-to-peer.
- Garantiza consistencia transaccional entre todos los nodos.
- Escalabilidad lineal al agregar nodos adicionales.
- Failover automático en caso de fallas.

---

## Vitess

- Sistema de fragmentación de bases de datos.
- Fragmentación horizontal de datos en shards.
- Escalabilidad elástica con la adición o eliminación dinámica de nodos y shards.
- Uso de Proxy SQL para enrutamiento y balanceo de carga.
- Réplicas y failover para alta disponibilidad.

---

## Comparación

|                  | Galera Cluster              | Vitess                |
|------------------|-----------------------------|-----------------------|
| Arquitectura     | Replicación de transacciones | Fragmentación de datos |
| Consistencia     | Sincrónica                   | No sincrónica         |
| Escalabilidad    | Lineal                       | Elástica              |
| Enrutamiento     | N/A                          | Proxy SQL             |
| Réplicas         | Sí                           | Sí                    |
| Failover         | Automático                   | Automático            |

---

## Conclusiones

- Galera Cluster se enfoca en replicación transaccional, alta disponibilidad y escalabilidad lineal.
- Vitess se centra en fragmentación de datos, escalabilidad elástica y balanceo de carga.
- Ambas son opciones adecuadas según los requisitos y características de la aplicación.


---



# ¡Gracias por tu atención!

¿Tienes alguna pregunta?
