# Bistro FDI 🍴

[English](#english) · [Español](#español)

## English

Bistro FDI is a restaurant management web application built by a four-person team for the Web Applications course at Complutense University of Madrid. It uses PHP, MySQL and JavaScript, with a layered architecture separating views and forms, services, data access objects and data transfer objects.

The documented features include user accounts and roles, product categories and listings, a shopping cart, and an order workflow for customers, waiters, kitchen staff and managers. Customers can choose dine-in or takeaway and simulate a payment. Kitchen staff track preparation by item, while waiters handle payment and delivery.

The repository contains coursework stages in `practica1` through `practica4`. The Spanish documentation below describes the architecture, functionality, database and team. The project deployment is linked below; its current availability has not been verified.

## Español

[Facultad de Informática — UCM](https://www.fdi.ucm.es/) · [Código de este repositorio](https://github.com/sevillaa/AW)

Proyecto desarrollado para la asignatura **Aplicaciones Web** en la Universidad Complutense de Madrid. Este sistema integral permite la gestión de usuarios, categorías, productos y el flujo completo de pedidos en un entorno de restauración.

## 🚀 Datos de Despliegue y Acceso

  * **Despliegue del proyecto:** [vm016.containers.fdi.ucm.es](https://vm016.containers.fdi.ucm.es/)
  * **Disponibilidad del despliegue y cuentas:** no verificada actualmente.
  * **Repositorio:** [sevillaa/AW](https://github.com/sevillaa/AW)
  * **Repositorio de referencia enlazado en la documentación:** [Raanmdornes1920/AW](https://github.com/Raanmdornes1920/AW)

### Cuentas de Prueba:

| Rol | Usuario | Contraseña |
| :--- | :--- | :--- |
| **Gerente** | `admin` | `admin` |
| **Cliente** | `cliente` | `cliente` |
| **Camarero** | `camarero` | `camarero` |
| **Cocinero** | `cocinero` | `cocinero` |

-----

## 🛠️ Arquitectura del Sistema

La aplicación sigue un modelo de arquitectura por capas para garantizar la escalabilidad y el mantenimiento:

### 1\. Capa de Vistas y Formularios

Utiliza una estructura de scripts PHP para generar la interfaz dinámica. Se apoya en una clase base `formularioBase.php` para la gestión estandarizada de formularios.

### 2\. Capa de Servicio (SA)

Actúa como intermediaria entre las vistas y el acceso a datos, aplicando las reglas de negocio.

  * `UsuarioSA`, `CategoriaSA`, `ProductoSA`, `PedidoSA`.

### 3\. Capa de Acceso a Datos (DAO)

Encargada de las consultas SQL y la persistencia en la base de datos.

  * **Transacciones:** El `PedidoDAO` utiliza transacciones de MySQL para asegurar que el pedido y sus líneas se guarden correctamente o no se guarde nada (atomicidad).

### 4\. Objetos de Transferencia (DTO)

Clases que representan las entidades del sistema (`Usuario`, `Producto`, `Categoria`, `Pedido`) facilitando el transporte de información entre capas.

-----

## 📋 Funcionalidades Principales

### 👤 Gestión de Usuarios (Funcionalidad 0)

  * **Autenticación:** Sistema de login y registro con validación de campos.
  * **Perfil:** Los usuarios pueden editar su avatar, email y contraseña mediante pop-ups gestionados con JavaScript.
  * **Panel de Administración:** El gerente puede listar, crear, editar y eliminar cualquier usuario.

### 📦 Gestión de Catálogo (Funcionalidad 1)

  * **Categorías:** Organización de productos. El gerente gestiona las categorías (CRUD) y los clientes pueden navegar por ellas.
  * **Productos:** Fichas detalladas con carrusel de imágenes, gestión de stock, cálculo automático de IVA mediante `producto.js` y borrado lógico.

### 🛒 Ciclo de Pedidos (Funcionalidad 2)

1.  **Cliente:** Añade productos al carrito, elige modalidad (Local/Llevar) y simula el pago.
2.  **Seguridad:** El sistema recalcula el total en el backend antes de guardar para evitar manipulaciones de precio en el frontend.
3.  **Cocina/Sala:** Los cocineros marcan productos listos individualmente y los camareros gestionan el cobro y entrega final.

-----

## 💾 Estructura de la Base de Datos

El sistema se apoya en una base de datos relacional con las siguientes tablas principales:

  * **Usuarios:** Almacena credenciales, roles y rutas de avatares.
  * **Categorías y Productos:** Relación 1:N que define la carta del restaurante.
  * **Imágenes de Producto:** Permite múltiples fotos por producto para visualización en carrusel.
  * **Pedidos y Líneas de Pedido:** Estructura N:M para registrar las compras, estados del pedido y precios históricos de los productos.

-----

## 👥 Equipo (Grupo C - Equipo Nº 2)

  * Héctor Manuel Díaz Bernal
  * Ángela Meirás Seisdedos
  * Ramón Andrés Salazar Gutiérrez
  * Miguel Sevilla Benito

-----

*Facultad de Informática - Universidad Complutense de Madrid*
