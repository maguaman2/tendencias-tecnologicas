# Volumes

## 1. Introducción a los Volúmenes de Docker

Los volúmenes son el mecanismo preferido para persistir datos generados y utilizados por contenedores Docker. A diferencia de los bind mounts y tmpfs mounts, los volúmenes ofrecen varias ventajas:

- Más fáciles de respaldar o migrar
- Pueden ser administrados mediante comandos de Docker
- Funcionan tanto en contenedores Linux como Windows
- Pueden ser compartidos de manera más segura entre múltiples contenedores

## 2. Tipos de Volúmenes

### 2.1 Volúmenes Nombrados (Named Volumes)

Los volúmenes nombrados son creados y administrados por Docker. Tienen un nombre específico que los identifica.

```bash
# Crear un volumen nombrado
docker volume create mi-volumen

# Listar volúmenes
docker volume ls

# Inspeccionar un volumen
docker volume inspect mi-volumen

```

### 2.2 Volúmenes Anónimos (Anonymous Volumes)

Se crean automáticamente por Docker cuando no se especifica un nombre explícito.

```bash
# Ejemplo de creación de volumen anónimo
docker run -v /data imagen-ejemplo

```

### 2.3 Bind Mounts

Permiten mapear un directorio del host directamente a un contenedor.

```bash
# Ejemplo de bind mount
docker run -v /ruta/en/host:/ruta/en/contenedor imagen

```

## 3. Comandos Principales de Volúmenes

### 3.1 Crear un Volumen

```bash
docker volume create nombre-volumen

```

### 3.2 Listar Volúmenes

```bash
docker volume ls

```

### 3.3 Inspeccionar un Volumen

```bash
docker volume inspect nombre-volumen

```

### 3.4 Eliminar un Volumen

```bash
# Eliminar un volumen específico
docker volume rm nombre-volumen

# Eliminar volúmenes no utilizados
docker volume prune

```

## 4. Solución de Problemas Comunes

### 4.1 Permisos de Volumen

```bash
# Cambiar permisos de un volumen
docker run -v nombre-volumen:/ruta -u $(id -u):$(id -g) imagen

```

### 4.2 Eliminar Volúmenes Huérfanos

```bash
# Eliminar volúmenes que no están siendo utilizados
docker volume prune

```

## 5. Comandos especificos de la clase

### 5.1 Levantar postgresql sin volumen

```jsx
docker run --name postgres-sin-volumen -e POSTGRES_PASSWORD=1234 -p 5432:5432 -d postgres
```

### 5.2 Levantar postgresql con volumen

```jsx
docker run --name postgres-con-volumen -e POSTGRES_PASSWORD=1234 -v postgres_data:/var/lib/postgresql/data -d postgres
```

## Conclusión

Los volúmenes son fundamentales para la gestión de datos persistentes en Docker. Comprender sus tipos, comandos y mejores prácticas te ayudará a crear infraestructuras de contenedores más robustas y eficientes.