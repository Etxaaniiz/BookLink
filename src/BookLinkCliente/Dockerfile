# Usa una imagen oficial de Node.js como base para construir la aplicación
FROM node:18 AS build

# Establecer el directorio de trabajo dentro del contenedor
WORKDIR /app

# Copiar archivos esenciales
COPY package.json package-lock.json ./

# Instalar dependencias
RUN npm install

# Configurar OpenSSL para compatibilidad con versiones antiguas
ENV NODE_OPTIONS=--openssl-legacy-provider

# Copiar el código fuente necesario
COPY public/ ./public/
COPY src/ ./src/
COPY tailwind.config.js ./
COPY postcss.config.js ./
COPY tsconfig.json ./

# Construir la aplicación
RUN npm run build

# ---- Segunda etapa: Servir el frontend con Nginx ----
FROM nginx:latest

# Copiar los archivos construidos desde la etapa anterior
COPY --from=build /app/build /usr/share/nginx/html

# Copiar configuración de Nginx
COPY nginx/default.conf /etc/nginx/conf.d/default.conf

# Exponer el puerto 3000
EXPOSE 3000

# Mantener Nginx en ejecución
CMD ["nginx", "-g", "daemon off;"]
