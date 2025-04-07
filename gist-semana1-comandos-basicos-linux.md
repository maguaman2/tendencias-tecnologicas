# Uso Básico de la Terminal en Linux

## 1. Introducción a la Línea de Comandos
La terminal en Linux permite interactuar con el sistema operativo mediante comandos de texto. Es una herramienta poderosa para administrar archivos, ejecutar programas y configurar el sistema de manera precisa sin la necesidad de interfaz gráfica.

## 2. Navegación por el Sistema de Archivos
- `pwd` → Muestra el directorio actual.
- `ls` → Lista archivos y directorios en el directorio actual.
  - `ls -l` → Muestra detalles como permisos y tamaño.
  - `ls -a` → Muestra archivos ocultos.
- `cd <ruta>` → Cambia de directorio.
  - `cd ..` → Sube un nivel en la jerarquía.
  - `cd /` → Va a la raíz del sistema.
  - `cd ~` → Va al directorio personal del usuario. Si tienes configurada la variable de entorno `$HOME`, se abrirá automáticamente utilizando únicamente `cd`.
  - `cd -` → Vuelve al directorio anterior.
- (UPDATE) `whoami`  → Lista el usuario que ejecuta el comando
- (UPDATE) `who` → Lista los usuarios que actualmente tengan una sesión abierta en el servidor
- 

## 3. Manipulación de Archivos
- `touch archivo.txt` → Crea un archivo vacío.
- `mkdir carpeta` → Crea un directorio.
- `cp archivo.txt destino/` → Copia un archivo.
- `mv archivo.txt destino/` → Mueve o renombra un archivo.
- `rm archivo.txt` → Elimina un archivo.
- `rm -r carpeta/` → Elimina un directorio y su contenido.
- `rm -rf carpeta/` → Elimina un directorio y su contenido sin pedir confirmación.
- `find /ruta -name "archivo.txt"` → Busca un archivo en el sistema.
- `locate archivo.txt` → Busca un archivo rápidamente en una base de datos actualizada.
- `updatedb` → Actualiza la base de datos de `locate`.

## 4. Redireccionamiento y Tuberías
- `>` → Redirige la salida a un archivo (sobreescribe).
  ```bash
  echo "Hola" > saludo.txt
  ```
- `>>` → Redirige la salida a un archivo (añade sin sobrescribir).
  ```bash
  echo "Mundo" >> saludo.txt
  ```
- `<` → Usa un archivo como entrada de un comando.
  ```bash
  sort < nombres.txt
  ```
- `|` → Pasa la salida de un comando como entrada de otro.
  ```bash
  history | grep "flatpak"
  ```

## 5. Variables de Entorno
- `echo $HOME` → Muestra el directorio personal del usuario.
- `export MI_VARIABLE="Hola Mundo"` → Define una variable temporal.
- `env` → Lista todas las variables de entorno.
- `unset MI_VARIABLE` → Elimina una variable de entorno.

## 6. Elevación de Permisos (sudo)
Algunos comandos requieren permisos de administrador por motivos de seguridad e integridad del sistema:
- `sudo <comando>` → Ejecuta un comando como superusuario.
  ```bash
  sudo dnf update
  ```
- `sudo su` → Cambia al usuario root. (en algunos sistemas requiere el uso de `sudo -s`)

## 7. Consejos y Trucos
- **Autocompletar:** Usa `Tab` para completar comandos y nombres de archivos.
- **Historial de Comandos:** Usa `↑` y `↓` para navegar en los comandos usados.
- **Ejecutar el último comando:** Usa `!!` para repetir el último comando ejecutado.
- **Limpiar la pantalla:** Usa `clear` o `Ctrl + L`.
- **¿No sabes cómo utilizar un comando o qué argumentos acepta?:** Usa `man <comando>` para obtener ayuda detallada.

## 8. Conexión a un Servidor con SSH
- `ssh usuario@servidor` → Conectarse a un servidor remoto (Por defecto, se utiliza el puerto 22).
- `ssh -p 8022 usuario@servidor` → Conectarse en un puerto diferente.
- `ssh-keygen -t rsa -b 4096 -C "correo@example.com"` → Generar clave SSH con algoritmo RSA de 4096 bits.
- `ssh-copy-id -p 8022 usuario@servidor` → Copiar clave SSH al servidor.
- `scp -P 8022 archivo.txt usuario@servidor:/ruta/destino/` → Copiar un archivo al servidor.
- `scp -P 8022 -r carpeta/ usuario@servidor:/ruta/destino/` → Copiar un directorio.

## 9. Transferencia de Archivos con rsync
- `rsync -avz -e "ssh -p 8022" carpeta/ usuario@servidor:/ruta/destino/` → Sincronizar archivos con un servidor remoto con argumentos verbose, comprimir y cifrar.
- `rsync -avz --progress carpeta/ usuario@servidor:/ruta/destino/` → Mostrar progreso de la transferencia.

## Recursos utilizados:
- [Warp Terminal](https://www.warp.dev/), la terminal con IA integrada.
- [Fedora 41 KDE](https://fedoraproject.org/kde/) en caso de usar VM o instalación local.
- [WSL](https://docs.microsoft.com/en-us/windows/wsl/install) en caso de utilizar el subsistema en Windows.
- [Oh my Zsh](https://ohmyz.sh/) si desean usar ZSH en lugar de Bash.
- [Fish](https://fishshell.com/) para una terminal más amigable (reemplaza Bash).

# Tarea
Crear una estructura de carpetas para un proyecto basado en el framework de Angular mediante el uso de los comandos nativos de Linux (no usar Angular CLI), la estructura debe ser creada utilizando máximos 8 comandos, los archivos no necesitan poseer contenido.

En el entregable se debe incluir una captura de pantalla de la estructura de carpetas creada junto a los comandos utilizados.

La estructura de carpetas debe incluir las siguientes carpetas principales:
- `src`: Contiene el código fuente del proyecto.
- `dist`: Contiene la versión compilada del proyecto.
- `public`: Contiene los archivos estáticos del proyecto.

Dentro de la raíz del proyecto se deben incluir los siguientes archivos:
- `README.md`: Contiene información sobre el proyecto.
- `angular.json`: Contiene la configuración del proyecto.
- `package.json`: Contiene la información del proyecto y las dependencias.
- `tsconfig.json`: Contiene la configuración de TypeScript.

## Vista con tree
```
.
├── dist/
├── public/
├── src/
│   ├── app/
│   │   ├── components/
│   │   ├── app.component.ts
│   │   ├── app.component.html
│   │   ├── app.component.css
│   │   ├── app.module.ts
│   ├── assets/
│   │   ├── images/
│   │   ├── fonts/
│   │   └── styles/
│   ├── index.html
│   ├── main.ts
│   ├── styles.css
│   └── favicon.ico
├── angular.json
├── package.json
├── tsconfig.json
└── README.md
```

## IMPORTANTE:
Diviértete :)
