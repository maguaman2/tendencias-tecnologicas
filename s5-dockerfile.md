<div align="center">
  <img width="10%" src="https://github.com/user-attachments/assets/f9bb3527-89b9-4de9-8b1e-1ce2d079a855">
</div>

# Dockerfile — Guía de atajos


**Herencia o Imagen Base:** El siguiente comando es el que nos ayuda a crear nuestra imagen, a partir de otra en particular.

```Dockerfile
FROM node:alpine3.2.10
```

**Inicialización o Script:** Podemos correr scripts antes al momento de construir nuestra imagen, en este caso se indican las dependencias y módulos de node que se deben descargar.
- npm
```Dockerfile
RUN npm install
```
- yarn
```Dockerfile
RUN yarn install
```
- pnpm
```Dockerfile
RUN pnpm install
```
- bun
```Dockerfile
RUN bun install
```
**Directorio de Trabajo (Working Directory):** El comando establece en que directorio estamos trabajando actualmente. Funciona similar al tipico comando de linux `cd [PATH]`.
```Dockerfile
WORKDIR /app
```

**Copiar archivos locales hacia una imagen:** Podemos copiar el archivo de nuestro proyecto y colocarlo dentro de nuestra imagen en nuestro directorio de trabajo.
```Dockerfile
COPY app.js package.json ./
```
> [!TIP]
> Si deseas copiar todos los archivos del directorio en el que te encuentras actualmente de manera local, usa esto.
> ```Dockerfile
> COPY . .
> ```

> [!WARNING]
> Si copias todos tus archivos y las guardas en tu imagen con el comando `COPY`. Esto puede llegar a ser contraproducente debido a que tu imagén podría llegar a pesar mucho.

**Comando:** Nos permite ejecutar comando al momento que el contenedor se inicie.
```Dockerfile
# Ejemplo 1
CMD ["node", "app"]

# Ejemplo 2
CMD ["npm", "start"]
```
