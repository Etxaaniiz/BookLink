# 📚 BookLink - Proyecto Completo

Este repositorio contiene la aplicación **BookLink**, compuesta por un **backend basado en microservicios** y un **frontend en React + TypeScript**.  
Permite a los usuarios **buscar libros, agregarlos a favoritos y gestionar su cuenta**.

---

## **0) Software que se necesita instalar**
Antes de ejecutar la aplicación, asegúrate de tener instalado:

- **Docker** → [Descargar aquí](https://www.docker.com/get-started)
- **Docker Compose** → Se incluye con Docker Desktop.
- **Node.js** → [Descargar aquí](https://nodejs.org/)
- **npm** o **yarn** (ya vienen con Node.js)
- **Python 3.9+** (necesario para `user-service`) → [Descargar aquí](https://www.python.org/downloads/)

---

## **1) Servicios que hay que arrancar**
El backend está compuesto por varios microservicios y un frontend independiente.  
Asegúrate de que estos servicios estén disponibles:

| **Servicio**      | **Puerto** | **Descripción** |
|------------------|----------|----------------|
| **API Gateway**  | `4001`   | Enrutador principal que gestiona las peticiones |
| **User Service** | `5000`   | Gestión de usuarios, autenticación y favoritos |
| **Book Search**  | `4000`   | Conexión con Google Books API para buscar libros |
| **Frontend**     | `3000`   | Interfaz web para los usuarios |

Si aún no has arrancado el backend, sigue las instrucciones en la siguiente sección.

---

## **2) Dependencias que hay que instalar**
Si deseas ejecutar el proyecto **sin Docker**, instala las dependencias manualmente.

### **🔹 Backend (Node.js y Python)**
Para `api-gateway` y `book-search` (Node.js):
```bash
cd api-gateway
npm install
cd ../book-search
npm install
```

Para `user-service` (Flask/Python):
```bash
cd user-service

# (Opcional) Activar entorno virtual
# En Windows:
venv\Scripts\activate
# En macOS/Linux:
source venv/bin/activate

# Instalar dependencias de Flask
pip install -r requirements.txt
```

### **🔹 Frontend (React + TypeScript)**
```bash
cd booklink-frontend
npm install
```
o si usas Yarn:
```bash
yarn install
```

---

## **3) Cómo arrancar la parte servidora**

Dependiendo de si deseas ejecutar el backend con **Docker** o **sin Docker**, usa uno de los siguientes métodos:

### **🔹 Opción 1: Arrancar con Docker (recomendado)**
1️⃣ **Abrir una terminal en la carpeta raíz del proyecto** (`BookLink`).  
2️⃣ **Ejecutar el siguiente comando para construir y levantar los contenedores**:
```bash
docker-compose up --build
```
Esto hará lo siguiente:
- Construirá las imágenes de `api-gateway`, `user-service` y `book-search` si no existen.
- Iniciará los servicios en los puertos correspondientes.

Si ya lo has construido antes y solo quieres iniciar los servicios, usa:
```bash
docker-compose up
```

📌 **Para detener los servicios**, presiona `Ctrl + C` en la terminal o ejecuta:
```bash
docker-compose down
```

---

### **🔹 Opción 2: Arrancar sin Docker**
Si prefieres ejecutar los servicios **manualmente**, abre **tres terminales** y ejecuta cada servicio por separado.

#### **1️⃣ Iniciar `user-service` (Flask)**
```bash
cd user-service

# (Opcional) Activar entorno virtual en Python
# En Windows:
venv\Scripts\activate
# En macOS/Linux:
source venv/bin/activate

# Iniciar el servidor Flask
flask run --host=0.0.0.0 --port=5000
```
👉 **El `user-service` estará disponible en `http://localhost:5000`**  

---

#### **2️⃣ Iniciar `api-gateway` (Node.js)**
```bash
cd api-gateway

# Iniciar el servidor Node.js
npm start
```
👉 **El `api-gateway` estará disponible en `http://localhost:4001`**  

---

#### **3️⃣ Iniciar `book-search` (Node.js)**
```bash
cd book-search

# Iniciar el servidor Node.js
npm start
```
👉 **El `book-search` estará disponible en `http://localhost:4000`**  

---

#### **4️⃣ Iniciar el frontend**
```bash
cd booklink-frontend
npm start
```
👉 **El frontend estará disponible en `http://localhost:3000`**  

---

## **4) Cómo acceder a la parte cliente**
Una vez iniciada la aplicación, accede desde el navegador a:

```
http://localhost:3000
```

Desde aquí, puedes:
- **Iniciar sesión / Registrarte**
- **Buscar libros**
- **Añadir libros a favoritos**
- **Eliminar libros a favoritos**
- **Ver detalles de un libro**

El frontend se conecta al backend en `http://localhost:4001`, así que asegúrate de que el servidor esté en ejecución.

---

---

## **📌 Repositorio en GitHub**
Puedes descargar el código fuente desde el siguiente enlace:
🔗 **[Repositorio en GitHub](https://github.com/Etxaaniiz/BookLink)**

---

