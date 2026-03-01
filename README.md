# Literalura - Challenge ONE Java

**Literalura** es un catálogo literario interactivo desarrollado en Java. El sistema permite consumir datos de la API **Gutendex**, procesarlos y almacenarlos en una base de datos relacional para realizar consultas avanzadas y generar estadísticas.

---

## Arquitectura del Proyecto
El proyecto sigue una estructura de **arquitectura por capas** para garantizar el desacoplamiento y la facilidad de mantenimiento:

1.  **Capa de Modelo (`model`):** Definición de entidades JPA (`Libro`, `Autor`) y uso de `Java Records` como DTOs para una transferencia de datos inmutable.
2.  **Capa de Repositorio (`repository`):** Interfaces que extienden de `JpaRepository` para la persistencia y consultas personalizadas en PostgreSQL.
3.  **Capa de Servicio (`service`):** Lógica técnica para el consumo de la API externa (HttpClient) y conversión de JSON a objetos Java (Jackson/Gson).
4.  **Capa Principal (`principal`):** Clase de interacción con el usuario que coordina el flujo de la aplicación.

---

## 🚀 Funcionalidades Principales

### 1. Gestión Bibliográfica Inteligente
* **Búsqueda y Registro:** Al buscar un libro por título, el sistema consulta la API Gutendex. Si el libro no existe localmente, lo guarda vinculándolo automáticamente con su autor.
* **Integridad Referencial:** Implementa lógica de "Autor Único"; si el autor ya existe en la base de datos, se vincula al nuevo libro evitando duplicidad.

### 2. Consultas y Filtros
* **Listado General:** Visualización de todos los libros y autores registrados con sus datos biográficos.
* **Filtro por Idioma:** Conteo y listado de obras por códigos internacionales (es, en, fr, pt).
* **Filtro Cronológico:** Identificación de autores vivos en un año específico mediante consultas optimizadas.

### 3. Análisis Estadístico
* **Top 10:** Ranking de los libros más descargados en la colección local.
* **Métricas con Java Streams:** Generación de estadísticas (media, máximo, mínimo y conteo) sobre el número de descargas de los libros registrados.

---

## 🛠️ Tecnologías Utilizadas

* **Java 17+**
* **Spring Boot 3+**
* **Spring Data JPA:** Para la gestión de la base de datos.
* **PostgreSQL:** Como motor de base de datos relacional.
* **Jackson / Gson:** Para el parseo de JSON a Objetos.
* **Gutendex API:** Fuente de datos externa.

---

## 📋 Configuración e Instalación

1.  **Base de Datos:** Configura tus credenciales de PostgreSQL en el archivo `application.properties`.
2.  **Dependencias:** Asegúrate de tener las dependencias de Spring Data JPA, Driver de PostgreSQL y Jackson en tu `pom.xml`.
3.  **Ejecución:** Corre la clase `LiteraluraApplication` y utiliza el menú interactivo en consola.

---
Desarrollado como parte del programa **Oracle Next Education (ONE)** en Alura Latam.
