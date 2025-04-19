# Bash y Scripting para Data Engineering

## Tabla de Contenido

* [1. Introducción: Bash en el Ecosistema de Data Engineering](#1-introducción-bash-en-el-ecosistema-de-data-engineering)  
    * [1.1. ¿Qué es Bash y por qué es crucial para Data Engineers?](#11-qué-es-bash-y-por-qué-es-crucial-para-data-engineers)  
    * [1.2. La Terminal como Herramienta de Trabajo](#12-la-terminal-como-herramienta-de-trabajo)  

* [2. Fundamentos Esenciales de la CLI](#2-fundamentos-esenciales-de-la-cli)  
    * [2.1. Navegación y Gestión Básica del Sistema de Archivos](#21-navegación-y-gestión-básica-del-sistema-de-archivos)  
        * (`pwd`, `ls`, `cd`, `mkdir`, `rmdir`, `tree`)  
    * [2.2. Trabajo con Archivos y Directorios (Foco en Datos)](#22-trabajo-con-archivos-y-directorios-foco-en-datos)  
        * (`touch`, `cp`, `mv`, `rm`, `stat`, `du`, `df`)  
    * [2.3. Visualización de Archivos Grandes](#23-visualización-de-archivos-grandes)  
        * (`cat`, `less`, `more`, `head`, `tail -f`)  
    * [2.4. Permisos y Propiedad (Importante para Pipelines)](#24-permisos-y-propiedad-importante-para-pipelines)  
        * (`chmod`, `chown`, `ls -l`)  
    * [2.5. Obtener Ayuda (`man`, `--help`)](#25-obtener-ayuda-man---help)  
    * [2.6. Alias, Variables de Entorno y Personalización](#26-alias-variables-de-entorno-y-personalización)  
        * (`alias`, `unalias`, `.bashrc`, `.bash_profile`, `export`)  

* [3. Procesamiento de Datos en la Línea de Comandos](#3-procesamiento-de-datos-en-la-línea-de-comandos)  
    * [3.1. Búsqueda y Filtrado de Texto](#31-búsqueda-y-filtrado-de-texto)  
        * [`grep` (con regex básicas)](#grep-con-regex-básicas)  
    * [3.2. Manipulación y Transformación de Texto/Stream](#32-manipulación-y-transformación-de-textostream)  
        * [`sed`](#sed---editor-de-flujo-para-transformaciones)  
        * [`awk`](#awk---procesamiento-avanzado-por-columnas)  
        * [`cut`](#cut---seleccionar-columnas-o-campos)  
        * [`tr`](#tr---traducir-o-eliminar-caracteres)  
    * [3.3. Ordenación y Agregación Básica](#33-ordenación-y-agregación-básica)  
        * [`sort`](#sort---ordenar-líneas)  
        * [`uniq`](#uniq---eliminar-duplicados-y-contar)  
        * [`wc`](#wc---contar-líneas-palabras-bytes)  
    * [3.4. Trabajo con JSON](#34-trabajo-con-json)  
        * [`jq`](#jq---el-procesador-json-de-línea-de-comandos)  
    * [3.5. Redirección de I/O (`>`, `>>`, `<`, `2>`)](#35-redirección-de-io---2)  
    * [3.6. Combinando Herramientas con Tuberías (Pipes `|`)](#36-combinando-herramientas-con-tuberías-pipes-)  

* [4. Conectividad y Transferencia de Datos](#4-conectividad-y-transferencia-de-datos)  
    * [4.1. Conexión Remota](#41-conexión-remota)  
        * [`ssh`](#ssh---conexión-segura-a-servidores-remotos)  
    * [4.2. Transferencia Segura de Archivos](#42-transferencia-segura-de-archivos)  
        * [`scp`](#scp---copia-segura-simple)  
        * [`rsync`](#rsync---sincronización-eficiente-de-archivos)  
    * [4.3. Descarga de Datos desde la Web/APIs](#43-descarga-de-datos-desde-la-webapis)  
        * [`curl`](#curl---transferencia-de-datos-con-urls-interacción-con-apis)  
        * [`wget`](#wget---descarga-no-interactiva-de-archivos)  

* [5. Scripting Bash para Automatización de Tareas](#5-scripting-bash-para-automatización-de-tareas)  
    * [5.1. Creación y Ejecución de Scripts (`#!/bin/bash`, `chmod +x`)](#51-creación-y-ejecución-de-scripts-binbash-chmod-x)  
    * [5.2. Variables, Comillas y Sustitución de Comandos](#52-variables-comillas-y-sustitución-de-comandos)  
    * [5.3. Entrada y Argumentos en Scripts](#53-entrada-y-argumentos-en-scripts)  
        * [5.3.1. Argumentos de Script (`$0`, `$1`, `$@`, `$#`)](#531-argumentos-de-script-0-1-)  
        * [5.3.2. Entrada del Usuario (`read`)](#532-entrada-del-usuario-read) 
    * [5.4. Estructuras Condicionales (`if`, `case`)](#54-estructuras-condicionales-if-case)  
    * [5.5. Bucles (`for`, `while`)](#55-bucles-for-while)  
    * [5.6. Funciones para Reutilizar Código](#56-funciones-para-reutilizar-código)  
    * [5.7. Gestión de Errores y Estado de Salida (`exit`, `$?`, `set -e`, `set -o pipefail`)](#57-gestión-de-errores-y-estado-de-salida-exit--set--e-set--o-pipefail)  
        * [Importancia para orquestadores (Airflow, Cron, etc.)](#importancia-para-orquestadores-airflow-cron-etc)  
    * [5.8. Pruebas y Validaciones en Scripts](#58-pruebas-y-validaciones-en-scripts)  

* [6. Interacción con Herramientas de Data Engineering](#6-interacción-con-herramientas-de-data-engineering)  
    * [6.1. CLIs de Bases de Datos (Ejemplos)](#61-clis-de-bases-de-datos-ejemplos)  
        * (`psql`, `mysql`, `sqlcmd`, etc.)  
    * [6.2. CLIs de Cloud Providers (Ejemplos)](#62-clis-de-cloud-providers-ejemplos)  
        * (`aws cli`, `gcloud`, `az cli`)  
    * [6.3. Interacción con Contenedores (Docker/Kubernetes)](#63-interacción-con-contenedores-dockerkubernetes)  
        * (`docker exec`, `kubectl cp`, `kubectl logs`)  
    * [6.4. Control de Versiones con Git](#64-control-de-versiones-con-git)  
        * (Comandos básicos de `git` desde la CLI)  
    * [6.5. Lanzar Scripts de Python desde Bash](#65-lanzar-scripts-de-python-desde-bash)  
        * (`python script.py`, `venv`, logs, errores)  

* [7. Tópicos Adicionales y Buenas Prácticas](#7-tópicos-adicionales-y-buenas-prácticas)  
    * [7.1. Gestión de Variables de Entorno y Secretos](#71-gestión-de-variables-de-entorno-y-secretos)  
    * [7.2. Compresión y Archivado (`tar`, `gzip`, `zip`)](#72-compresión-y-archivado-tar-gzip-zip)  
    * [7.3. Programación de Tareas con `cron`](#73-programación-de-tareas-con-cron)  
    * [7.4. Debugging de Scripts (`set -x`, `echo`)](#74-debugging-de-scripts-set--x-echo)  
    * [7.5. Estilo y Legibilidad en Scripts](#75-estilo-y-legibilidad-en-scripts)  
    * [7.6. Herramientas CLI útiles para Data Engineers](#76-herramientas-cli-útiles-para-data-engineers)  
        * (`htop`, `watch`, `pv`, `parallel`, `fd`, `ripgrep`)  

* [8. Ejemplos de Scripts para Data Engineering](#8-ejemplos-de-scripts-para-data-engineering)  
    * [8.1. Script para Descargar y Preprocesar Logs](#81-script-para-descargar-y-preprocesar-logs)  
    * [8.2. Script para Mover Datos Procesados a Almacenamiento Cloud](#82-script-para-mover-datos-procesados-a-almacenamiento-cloud)  
    * [8.3. Script Wrapper para Ejecutar un Proceso SQL/Python](#83-script-wrapper-para-ejecutar-un-proceso-sqlpython)  

* [9. Recursos](#9-recursos)

# 1. Introducción: Bash en el Ecosistema de Data Engineering

Bash (Bourne Again SHell) es uno de los intérpretes de línea de comandos más utilizados en sistemas Unix y Linux. En el contexto del Data Engineering, Bash no solo es una herramienta útil, sino muchas veces esencial. Permite automatizar tareas, procesar archivos, interactuar con sistemas remotos y coordinar flujos de trabajo entre diferentes herramientas.



---

## 1.1. ¿Qué es Bash y por qué es crucial para Data Engineers?

Bash es una shell de comandos que permite al usuario comunicarse con el sistema operativo mediante texto. Si bien Bash se puede usar de forma interactiva, su verdadero poder está en los **scripts**: pequeños programas escritos en Bash que automatizan tareas repetitivas o complejas.

### Razones por las que Bash es fundamental en Data Engineering:

- 🔁 **Automatización de tareas rutinarias** como mover archivos, lanzar scripts Python o descargar datos.
- 📂 **Manipulación eficiente de archivos y directorios**, algo frecuente al trabajar con datos crudos, logs o archivos CSV.
- 📡 **Conexión remota y transferencia de archivos** a través de `ssh`, `scp` o `rsync`.
- 🧩 **Integración con otras herramientas** como `cron`, Docker, gestores de bases de datos o cloud CLIs (`aws`, `gcloud`, etc.).
- 🧪 **Validación y preprocesamiento de datos** directamente desde la línea de comandos.

Incluso si el núcleo del procesamiento de datos está en Python, Spark o SQL, Bash actúa como el **pegamento que conecta todo el pipeline**.

---

## 1.2. La Terminal como Herramienta de Trabajo

La **terminal** (o consola) es la interfaz a través de la cual interactuamos con Bash. Usar eficientemente la terminal te permite:

- Navegar rápidamente por carpetas y archivos.
- Ejecutar comandos del sistema.
- Visualizar logs en tiempo real.
- Componer comandos poderosos con tuberías (`|`) y redirecciones (`>`).

Como Data Engineer, dominar la terminal es una ventaja porque:

- Puedes trabajar en servidores remotos donde no hay interfaces gráficas.
- Permite usar herramientas CLI como `jq`, `awk`, `curl`, `psql`, etc.
- Es indispensable para el debugging de scripts, servicios o ETL jobs.

---

# 2. Fundamentos Esenciales de la CLI

Antes de automatizar tareas o procesar datos desde la terminal, necesitas dominar lo básico: navegar por el sistema de archivos, gestionar archivos y carpetas, consultar información útil y personalizar tu entorno de trabajo.

---

## 2.1. Navegación y Gestión Básica del Sistema de Archivos

En Bash, puedes moverte entre carpetas y explorar tu sistema de archivos rápidamente con unos pocos comandos:

| Comando      | Descripción |
|--------------|-------------|
| `pwd`        | Muestra la ruta del directorio actual (*print working directory*). |
| `ls`         | Lista el contenido de un directorio. Usa `ls -l` para una vista detallada y `ls -a` para incluir archivos ocultos. |
| `cd`         | Cambia de directorio. Ejemplo: `cd /var/log` o `cd ..` para subir un nivel. |
| `mkdir`      | Crea una carpeta. Ejemplo: `mkdir datos` |
| `rmdir`      | Elimina un directorio vacío. Para carpetas con contenido, usa `rm -r`. |
| `tree`       | Muestra la estructura de carpetas en forma de árbol (puede requerir instalación previa). |
---

## 2.2. Trabajo con Archivos y Directorios

Manipular archivos es una tarea central en pipelines de datos. Estos comandos te permiten crearlos, copiarlos, moverlos, renombrarlos y analizarlos:

| Comando      | Descripción |
|--------------|-------------|
| `touch`      | Crea un archivo vacío. También actualiza la fecha de modificación si ya existe. |
| `cp`         | Copia archivos o carpetas. Usa `cp -r` para copiar directorios recursivamente. |
| `mv`         | Mueve o renombra archivos. Ejemplo: `mv archivo.csv backup/archivo_2025.csv` |
| `rm`         | Elimina archivos. Usa con cuidado. `rm -r` para eliminar directorios con contenido. |
| `stat`       | Muestra metadatos del archivo: tamaño, permisos, fechas, etc. |
| `du -sh`     | Muestra el tamaño de una carpeta o archivo. Muy útil para logs o dumps de datos. |
| `df -h`      | Muestra el uso del sistema de archivos (espacio libre/disco ocupado). |
---

## 2.3. Visualización de Archivos Grandes

Muchos archivos de datos (CSV, logs, JSON) pueden ser grandes. Estos comandos permiten inspeccionarlos sin sobrecargar la terminal:

| Comando      | Descripción |
|--------------|-------------|
| `cat`        | Muestra todo el contenido del archivo (solo recomendable para archivos pequeños). |
| `less`       | Navega por el archivo página a página. Usa `q` para salir. |
| `more`       | Similar a `less`, pero menos flexible. |
| `head`       | Muestra las primeras líneas. Ejemplo: `head -n 20 archivo.log` |
| `tail`       | Muestra las últimas líneas. |
| `tail -f`    | Sigue el crecimiento de un archivo en tiempo real (útil para ver logs en ejecución). |

---

## 2.4. Permisos y Propiedad (Importante para Pipelines)

Cuando trabajas con scripts o pipelines, es clave entender los permisos de los archivos y carpetas:

| Comando      | Descripción |
|--------------|-------------|
| `ls -l`      | Lista archivos con detalles de permisos, propietario y grupo. |
| `chmod`      | Cambia los permisos. Ejemplo: `chmod +x script.sh` para hacerlo ejecutable. |
| `chown`      | Cambia el propietario de un archivo. Útil al mover archivos entre usuarios o contenedores. |
---

## 2.5. Obtener Ayuda (`man`, `--help`)

Bash tiene ayuda integrada. Puedes consultar la documentación oficial de cualquier comando:

| Comando      | Descripción |
|--------------|-------------|
| `man nombre_comando` | Abre el manual del comando. Ejemplo: `man grep` |
| `nombre_comando --help` | Muestra ayuda rápida. Ejemplo: `ls --help` |
---

## 2.6. Alias, Variables de Entorno y Personalización

Una de las ventajas de Bash es que puedes personalizarlo para que se adapte a tu flujo de trabajo. Esto incluye crear alias para comandos que usas frecuentemente, definir variables de entorno, y modificar archivos de configuración como `.bashrc` o `.bash_profile`.

---

### 🔁 Alias

Un **alias** es una forma de acortar o modificar un comando para hacerlo más rápido de escribir o más funcional por defecto.


#### 👉 Ver todos los alias definidos:

```bash
alias
```
#### 📌 Ejemplos comunes:

```bash
alias ll='ls -lh --color=auto'
alias gs='git status'
alias py='python3'
alias cls='clear'
```
#### 🔨 Para crear un alias:

```bash
alias nombre='comando'
```

#### ❌ Eliminar un alias temporalmente:

```bash
unalias ll
```

#### ✅ Hacer que un alias sea permanente:

Agrega el alias en tu archivo `~/.bashrc` o `~/.bash_profile`:

Una vez guardado, tenemos que recargar con source

```bash
echo "alias ll='ls -lh --color=auto'" >> ~/.bashrc
source ~/.bashrc
```
#### 💻 Ejecutar un comando sin alias

```bash
\ls
command ls
/bin/ls
```

#### 💻 Notas

Un alias no estará disponible en otra ventana de la terminal, a no ser, que se haya guardado en bashrc y recargado con source.

Si creamos un alias con comillas dobles, si cambiamos una variable, no le afectará al alias

```bash
nombre="Juan"
alias saludo="echo Hola $nombre"
nomber="Ana"
saludo # La salida seguirá siendo Hola Juan
```
Si creamos un alias con comillas simples, si cambiamos una variable, esta afectará al alias

```bash
nombre="Juan"
alias saludo='echo Hola $nombre'
nomber="Ana"
saludo # La salida será ahora Hola Ana
```

---

### 🌍 Variables de Entorno

Las **variables de entorno** almacenan información usada por Bash y otros programas. Son especialmente útiles para rutas de datos, tokens, claves, o configuraciones que necesitas reutilizar.

#### 📌 Ejemplo:

```bash
export DATA_PATH="/home/usuario/data"
echo $DATA_PATH
```

Puedes usar `$DATA_PATH` en scripts, comandos y otros scripts como si fuera una constante.

#### ✅ Hacerlas permanentes:

Agrega la línea al final de tu `~/.bashrc` o `~/.bash_profile`:

```bash
export API_KEY="tu_token_secreto"
```

#### 🔎 Ver todas las variables de entorno activas:

```bash
printenv
```

---

### 🛠 Archivos de configuración: `.bashrc` y `.bash_profile`

| Archivo           | Propósito principal |
|-------------------|---------------------|
| `~/.bashrc`       | Se ejecuta en cada sesión interactiva (cuando abres una terminal). Aquí van la mayoría de tus alias y funciones. |
| `~/.bash_profile` | Se ejecuta una vez al inicio de la sesión de login. A menudo carga `~/.bashrc`. |
---
# 3. Procesamiento de Datos en la Línea de Comandos

Uno de los superpoderes de Bash es la capacidad de procesar datos directamente desde la terminal, sin necesidad de scripts complejos ni lenguajes externos. Con las herramientas adecuadas, puedes filtrar, transformar, ordenar, combinar y preparar datos desde archivos de texto, logs o salidas de comandos.

---

## 3.1. Búsqueda y Filtrado de Texto

### `grep` (con regex básicas)

`grep` permite buscar patrones de texto dentro de archivos o flujos. Muy útil para filtrar logs, buscar errores o localizar líneas específicas en grandes volúmenes de texto.

#### 📌 Ejemplos:

```bash
grep "ERROR" logs.txt
grep -i "usuario" usuarios.csv        # Ignora mayúsculas/minúsculas
grep -v "DEBUG" logs.txt              # Excluye líneas con DEBUG
grep "^2025" fechas.txt               # Líneas que comienzan con 2025
grep -r "pipeline" ./proyectos        # Búsqueda recursiva
```

#### 🧠 Útil para:
- Extraer líneas relevantes de logs
- Filtrar grandes volúmenes de datos
- Preprocesar archivos antes de analizarlos con Python

---

## 3.2. Manipulación y Transformación de Texto/Stream

Las herramientas de esta sección te permiten editar, modificar o seleccionar partes específicas de un flujo de texto o archivo.

### `sed` – Editor de flujo para transformaciones

`sed` es un editor de texto no interactivo. Sirve para reemplazos, inserciones, borrado de líneas, entre otros.

#### 📌 Ejemplos:

```bash
sed 's/foo/bar/g' archivo.txt              # Reemplaza todas las apariciones de "foo" por "bar"
sed -n '10,20p' archivo.txt                # Muestra líneas 10 a 20
sed '/^#/d' archivo.conf                   # Elimina líneas que comienzan con #
```

### `awk` – Procesamiento avanzado por columnas

`awk` permite operar sobre archivos columna por columna, como si fueran tablas.

#### 📌 Ejemplos:

```bash
awk -F',' '{print $1, $3}' datos.csv       # Imprime columna 1 y 3 (separadas por coma)
awk '{suma += $2} END {print suma}' file   # Suma los valores de la segunda columna
awk '$3 > 100 {print $1, $3}' archivo.txt  # Filtra filas donde la columna 3 es mayor a 100
```

### `cut` – Seleccionar columnas o campos

Extrae por posición o delimitador.

#### 📌 Ejemplos:

```bash
cut -d',' -f1,3 usuarios.csv               # Extrae columnas 1 y 3 separadas por coma
cut -c1-10 archivo.txt                     # Extrae los primeros 10 caracteres de cada línea
```

### `tr` – Traducir o eliminar caracteres

`tr` se usa para reemplazar o eliminar caracteres.

#### 📌 Ejemplos:

```bash
tr '[:lower:]' '[:upper:]' < archivo.txt  # Convierte a mayúsculas
tr -d '\r' < win.txt > unix.txt           # Elimina retornos de carro (convertir formato Windows a Unix)
```

---

## 3.3. Ordenación y Agregación Básica

### `sort` – Ordenar líneas

#### 📌 Ejemplos:

```bash
sort archivo.txt                          # Orden alfabético
sort -n valores.txt                       # Orden numérico
sort -r archivo.txt                       # Orden inverso
```

### `uniq` – Eliminar duplicados y contar ocurrencias

Debe combinarse con `sort` para funcionar correctamente (espera líneas duplicadas consecutivas).

#### 📌 Ejemplos:

```bash
sort archivo.txt | uniq                   # Elimina duplicados
sort archivo.txt | uniq -c                # Cuenta repeticiones
```

### `wc` – Contar líneas, palabras o bytes

#### 📌 Ejemplos:

```bash
wc -l archivo.txt                         # Cantidad de líneas
wc -w archivo.txt                         # Cantidad de palabras
wc -c archivo.txt                         # Cantidad de bytes
```

---

## 3.4. Trabajo con JSON

### `jq` – El procesador JSON de línea de comandos

`jq` permite leer, formatear, filtrar y transformar datos JSON desde la terminal.

#### 📌 Ejemplos:

```bash
jq '.' datos.json                         # Formatear y mostrar
jq '.usuarios[].nombre' datos.json        # Obtener nombres dentro de un array
jq 'map(select(.activo == true))' usuarios.json
```

#### 🧠 Muy útil para:
- Inspeccionar respuestas de APIs
- Filtrar logs en formato JSON
- Automatizar procesamiento de estructuras complejas

---

## 3.5. Redirección de I/O (`>`, `>>`, `<`, `2>`)

En Bash, puedes redirigir entradas y salidas fácilmente:

| Símbolo | Significado |
|--------|-------------|
| `>`    | Redirige la salida (sobrescribe archivo) |
| `>>`   | Redirige la salida (agrega al archivo) |
| `<`    | Usa un archivo como entrada |
| `2>`   | Redirige errores (stderr) |

#### 📌 Ejemplos:

```bash
echo "Hola mundo" > mensaje.txt            # Crea o sobrescribe
echo "Otra línea" >> mensaje.txt           # Agrega al final
sort archivo.txt > salida.txt              # Guarda salida ordenada
comando < entrada.txt                      # Usa archivo como entrada
comando 2> errores.log                     # Guarda errores en archivo
```

---

## 3.6. Combinando Herramientas con Tuberías (Pipes `|`)

El operador `|` permite encadenar comandos: la salida de uno se convierte en la entrada del siguiente.

#### 📌 Ejemplo clásico:

```bash
cat logs.txt | grep "ERROR" | cut -d' ' -f1 | sort | uniq -c | sort -nr
```

Este comando:
1. Filtra líneas con "ERROR".
2. Extrae el primer campo (por ejemplo, una fecha).
3. Cuenta cuántas veces ocurre cada fecha.
4. Ordena los resultados de mayor a menor.

#### 🧠 Composición de herramientas:

Combinar `grep`, `awk`, `cut`, `jq`, `sort`, `uniq`, `head`, `tail` permite procesar datos complejos sin salir de Bash. Esto es ideal para validaciones rápidas, exploración de datos o preprocesamiento en pipelines.

---

# 4. Conectividad y Transferencia de Datos

En Data Engineering, muchas veces necesitas conectarte a servidores remotos, mover archivos entre máquinas, descargar datasets desde APIs o páginas web, y sincronizar contenido entre entornos. Bash ofrece herramientas muy potentes y seguras para todas estas tareas, que puedes usar directamente desde la terminal.

---

## 4.1. Conexión Remota

### `ssh` – Conexión segura a servidores remotos

`ssh` (Secure Shell) permite conectarse de forma segura a otro equipo o servidor a través de la red. Es una herramienta esencial para trabajar con servidores Linux, entornos cloud y clusters de procesamiento de datos.

#### 📌 Ejemplos básicos:

```bash
ssh usuario@192.168.1.100
ssh usuario@mi-servidor.com
```

#### 🔐 Conexión con clave privada:

```bash
ssh -i ~/.ssh/id_rsa usuario@mi-servidor.com
```

#### ⚙️ Opciones útiles:

| Opción | Descripción |
|--------|-------------|
| `-p 2222` | Especificar un puerto diferente (por defecto es el 22) |
| `-T` | No asigna una pseudo-terminal (ideal para automatización) |
| `-L` | Redireccionamiento de puertos (túneles SSH) |

#### 🧠 Casos de uso:

- Ejecutar scripts en servidores remotos
- Acceder a logs o bases de datos
- Configurar y controlar servicios ETL desplegados en producción

---

## 4.2. Transferencia Segura de Archivos

### `scp` – Copia segura simple

`scp` (Secure Copy) permite copiar archivos entre máquinas a través de SSH. Es simple, rápido y ampliamente soportado.

#### 📌 Ejemplos:

```bash
scp archivo.csv usuario@servidor:/home/usuario/datos/
scp usuario@servidor:/var/log/app.log ./logs/
```

#### ⚙️ Opciones útiles:

| Opción | Descripción |
|--------|-------------|
| `-r` | Copia directorios recursivamente |
| `-P` | Especifica el puerto (ej. `-P 2222`) |
| `-i` | Usa una clave privada específica |

---

### `rsync` – Sincronización eficiente de archivos

`rsync` es ideal para sincronizar archivos o carpetas entre sistemas. Solo transfiere los cambios, por lo que es más eficiente que `scp`.

#### 📌 Ejemplos:

```bash
rsync -avh datos/ usuario@servidor:/home/usuario/datos/
rsync -azP ./proyecto usuario@servidor:/deploy
```

#### ⚙️ Opciones recomendadas:

| Opción | Descripción |
|--------|-------------|
| `-a` | Modo archivo (mantiene permisos, fechas, etc.) |
| `-v` | Muestra salida detallada (verbose) |
| `-z` | Comprime durante la transferencia |
| `-P` | Muestra progreso y permite continuar descargas interrumpidas |

#### 🧠 Casos de uso:

- Mover backups de datos entre servidores
- Sincronizar directorios locales con entornos cloud
- Automatizar cargas de datos entre equipos de trabajo

---

## 4.3. Descarga de Datos desde la Web/APIs

### `curl` – Transferencia de datos con URLs e interacción con APIs

`curl` es una herramienta versátil que permite realizar peticiones HTTP, descargar archivos, enviar datos a APIs, autenticarse y más.

#### 📌 Ejemplos básicos:

```bash
curl -O https://datos.gob.es/archivo.csv       # Descarga archivo
curl https://api.datos.com/info                # Muestra respuesta en pantalla
```

#### 🛠 Autenticación y Headers:

```bash
curl -H "Authorization: Bearer $TOKEN" https://api.datos.com/data
curl -X POST -d '{"nombre":"Juan"}' -H "Content-Type: application/json" https://api.app.com/crear
```

#### ⚙️ Opciones comunes:

| Opción | Descripción |
|--------|-------------|
| `-O` | Guarda el archivo con el mismo nombre |
| `-o archivo.ext` | Guarda con nombre específico |
| `-H` | Agrega un encabezado HTTP |
| `-d` | Envía datos en el cuerpo del request |
| `-X` | Especifica método HTTP (`GET`, `POST`, etc.) |

---

### `wget` – Descarga no interactiva de archivos

`wget` es ideal para descargar archivos de forma automática o en segundo plano. Funciona muy bien con enlaces directos.

#### 📌 Ejemplos:

```bash
wget https://example.com/dataset.zip
wget -c https://example.com/bigfile.zip       # Continúa descarga interrumpida
wget -r -np -nH --cut-dirs=1 -R index.html https://example.com/data/
```

#### ⚙️ Opciones recomendadas:

| Opción | Descripción |
|--------|-------------|
| `-c` | Reanuda descargas |
| `-r` | Descarga recursiva |
| `-np` | No seguir enlaces a carpetas superiores |
| `--limit-rate=200k` | Limita la velocidad de descarga |

---

# 5. Scripting Bash para Automatización de Tareas

Los scripts en Bash son la forma más común y eficiente de automatizar tareas repetitivas en sistemas Unix/Linux. Desde mover archivos hasta ejecutar pipelines de datos, Bash permite crear flujos lógicos robustos y reutilizables con muy poco código.

---

## 5.1. Creación y Ejecución de Scripts (`#!/bin/bash`, `chmod +x`)

Un script Bash es simplemente un archivo de texto que contiene comandos que se ejecutarían normalmente en la terminal.

### 📌 Ejemplo básico:

```bash
#!/bin/bash
echo "Hola, mundo"
```

### ✅ Pasos para ejecutarlo:

1. Crear el archivo, por ejemplo `script.sh`
2. Darle permisos de ejecución:

```bash
chmod +x script.sh
```

3. Ejecutarlo:

```bash
./script.sh
```

> La línea `#!/bin/bash` se conoce como *shebang* y le dice al sistema que debe ejecutar el script usando Bash.

---

## 5.2. Variables, Comillas y Sustitución de Comandos

### 📌 Declaración de variables:

```bash
nombre="Juan"
echo "Hola $nombre"
```

### 📌 Uso de comillas:

- Comillas dobles (`"`): permiten evaluar variables.
- Comillas simples (`'`): muestran el contenido literal.

```bash
echo "Hola $nombre"   # Hola Juan
echo 'Hola $nombre'   # Hola $nombre
```

### 📌 Sustitución de comandos:

```bash
fecha=$(date)
echo "Hoy es $fecha"
```

---

### 5.3. Entrada y Argumentos en Scripts

En Bash, los scripts pueden recibir **argumentos desde la línea de comandos** y también **solicitar entrada del usuario de forma interactiva**. Ambas formas son fundamentales para crear scripts dinámicos, reutilizables y más flexibles.

---

#### 5.3.1. Argumentos de Script (`$0`, `$1`, `$@`, `$#`)

Cuando ejecutas un script y le pasas parámetros, Bash los asigna a **parámetros posicionales** automáticamente:

```bash
#!/bin/bash

echo "Nombre del script: $0"
echo "Primer argumento: $1"
echo "Segundo argumento: $2"
echo "Todos: $@"
echo "Cantidad de argumentos: $#"
```

##### 🔍 Ejemplo de ejecución:

```bash
./script.sh archivo.csv 2025
```

**Resultado:**

```
Nombre del script: ./script.sh
Primer argumento: archivo.csv
Segundo argumento: 2025
Todos: archivo.csv 2025
Cantidad de argumentos: 2
```

##### 🧠 Descripción rápida:

| Variable | Significado |
|----------|-------------|
| `$0`     | Nombre del script |
| `$1`     | Primer argumento |
| `$2`     | Segundo argumento |
| `$@`     | Todos los argumentos, separados correctamente |
| `$*`     | Todos los argumentos como una sola cadena |
| `$#`     | Número total de argumentos |

##### 📌 Diferencia entre `$@` y `$*`:

```bash
for arg in "$@"; do
  echo "arg: $arg"
done
```

Este ejemplo **respeta los espacios** en los argumentos.

```bash
for arg in "$*"; do
  echo "arg: $arg"
done
```

Este los trata como una sola cadena, lo que puede generar errores si hay espacios.

---

#### 5.3.2. Entrada del Usuario (`read`)

Bash también permite **solicitar valores directamente al usuario** con el comando `read`.

##### 📌 Ejemplo básico:

El flag -p en el comando read sirve para mostrar un mensaje o prompt antes de leer la entrada del usuario.

```bash
#!/bin/bash

read -p "¿Cómo te llamas? " nombre
echo "Hola, $nombre"
```

Cuando se ejecuta:

```
¿Como te llamas? Ana
Hola, Ana
```

##### ✅ Variantes útiles:

El flag -s en read es súper útil para ocultar la entrada del usuario (como cuando se escribe una contraseña).

```bash
read -s -p "Introduce tu contraseña: " pass   # Entrada oculta
read -n 1 -p "¿Deseas continuar? [s/n] " opt   # Solo una tecla
```

> Usa `read` para configuraciones interactivas, confirmaciones, o cuando no quieras pasar parámetros al iniciar el script.

---

🔁 Combinando ambos (argumentos + read) puedes crear scripts muy flexibles. Por ejemplo:

```bash
#!/bin/bash

if [ -z "$1" ]; then
    read -p "Introduce tu nombre: " nombre
else
    nombre=$1
fi

echo "Bienvenido, $nombre"
```
### 📘 Flags del comando `read` en Bash

| Flag     | Descripción                                                                 | Ejemplo                                              |
|----------|-----------------------------------------------------------------------------|------------------------------------------------------|
| `-p`     | Muestra un **mensaje (prompt)** antes de leer                              | `read -p "Tu nombre: " nombre`                      |
| `-s`     | **Oculta** la entrada (ideal para contraseñas)                             | `read -s -p "Contraseña: " pass`                    |
| `-n N`   | Lee **solo N caracteres**, sin esperar Enter                               | `read -n 1 -p "¿Continuar? [s/n] " opcion`          |
| `-t N`   | **Espera N segundos** antes de cancelar el `read`                          | `read -t 5 -p "Ingresa valor: " valor`              |
| `-e`     | Habilita **edición de línea e historial** (como la terminal)               | `read -e -p "Ruta del archivo: " ruta`              |
| `-r`     | No interpreta **caracteres de escape** (`\\`, `\\n`, etc.)                 | `read -r linea`                                     |
| `-a`     | Guarda la entrada como un **array**, separando por espacios                | `read -a palabras`                                  |
| `-d X`   | Lee hasta el **carácter delimitador X** (en vez de Enter)                  | `read -d ':' variable`                              |

> 💡 Puedes combinar varios flags:  
> Ejemplo: `read -s -n 1 -p "Presiona una tecla..." tecla`


---

## 5.4. Estructuras Condicionales (`if`, `case`)

### `if` básico:

```bash
if [ -f archivo.txt ]; then
  echo "El archivo existe"
else
  echo "No existe"
fi
```

### `case` para múltiples opciones:

```bash
case $1 in
  start)
    echo "Iniciando..."
    ;;
  stop)
    echo "Deteniendo..."
    ;;
  *)
    echo "Uso: $0 {start|stop}"
    ;;
esac
```

---

## 5.5. Bucles (`for`, `while`)

### `for`:

```bash
for archivo in *.csv; do
  echo "Procesando $archivo"
done
```

### `while`:

```bash
contador=1
while [ $contador -le 5 ]; do
  echo "Iteración $contador"
  ((contador++))
done
```

---

## 5.6. Funciones para Reutilizar Código

Definir funciones permite reutilizar bloques de código y estructurar mejor los scripts.

```bash
saludar() {
  echo "Hola $1"
}

saludar "Ana"
```

Puedes pasar parámetros, retornar códigos de estado y usar funciones como cualquier otro comando.

---

## 5.7. Gestión de Errores y Estado de Salida (`exit`, `$?`, `set -e`, `set -o pipefail`)

### 📌 Salida y códigos de error:

```bash
exit 0  # Éxito
exit 1  # Error
```

Ver el estado de salida del último comando:

```bash
echo $?
```

### 📌 Fallar al primer error:

```bash
set -e
```

### 📌 Asegurar propagación de errores en pipes:

```bash
set -o pipefail
```

> Muy importante en entornos de producción y cuando se integran con orquestadores como **Airflow**, **Luigi**, **Cron**, etc. Evita que errores pasen desapercibidos.

---

## 5.8. Pruebas y Validaciones en Scripts

Validar condiciones antes de ejecutar operaciones es fundamental.

### 📌 Validaciones comunes:

```bash
# Verificar que un archivo existe
if [ ! -f datos.csv ]; then
  echo "El archivo datos.csv no existe"
  exit 1
fi

# Verificar que una variable no esté vacía
if [ -z "$API_KEY" ]; then
  echo "Falta la API_KEY"
  exit 1
fi
```

### 📌 Uso de `test`:

```bash
test -d carpeta && echo "La carpeta existe"
```

---

# 6. Interacción con Herramientas de Data Engineering

El trabajo de un Data Engineer implica usar una gran variedad de herramientas, muchas de las cuales ofrecen interfaces de línea de comandos (CLI). Integrarlas con Bash permite automatizar flujos complejos, gestionar recursos y lanzar procesos de datos de forma eficiente.

---

## 6.1. CLIs de Bases de Datos (Ejemplos)

### `psql` – PostgreSQL

```bash
psql -U usuario -d basedatos -c "SELECT COUNT(*) FROM usuarios;"
```

Autenticación por variables:

```bash
PGPASSWORD=clave psql -U usuario -h host -d basedatos -c "SELECT version();"
```

### `mysql` – MySQL/MariaDB

```bash
mysql -u root -p
mysql -u usuario -p basedatos < consulta.sql
```

### `sqlcmd` – SQL Server

```bash
sqlcmd -S servidor -U usuario -P contraseña -Q "SELECT * FROM tabla"
```

#### 🧠 Casos de uso:
- Ejecutar consultas automatizadas desde scripts
- Validar integridad de datos en pipelines
- Exportar resultados con redirección de salida (`> salida.txt`)

---

## 6.2. CLIs de Cloud Providers (Ejemplos)

### `aws cli`

```bash
aws s3 ls
aws s3 cp archivo.csv s3://mi-bucket/
aws ec2 describe-instances
```

### `gcloud`

```bash
gcloud auth login
gcloud storage cp archivo.csv gs://mi-bucket/
gcloud compute instances list
```

### `az cli` (Azure)

```bash
az login
az storage blob upload --container-name datos --file archivo.csv --name archivo.csv
az vm list --output table
```

#### 🧠 Casos de uso:
- Automatizar cargas y descargas de datos
- Gestionar recursos cloud desde scripts
- Integración con Airflow, Jenkins, CI/CD

---

## 6.3. Interacción con Contenedores (Docker/Kubernetes)

### `docker`

```bash
docker ps
docker exec -it contenedor bash
docker cp archivo.txt contenedor:/ruta
```

### `kubectl`

```bash
kubectl get pods
kubectl logs nombre-pod
kubectl exec -it nombre-pod -- bash
kubectl cp archivo.txt pod:/ruta
```

#### 🧠 Casos de uso:
- Acceder a contenedores en ejecución
- Inspeccionar logs de ETL jobs o APIs
- Subir scripts o descargar resultados dentro del contenedor

---

## 6.4. Control de Versiones con Git

La línea de comandos es el entorno más rápido para interactuar con Git, especialmente para automatizar pushes, crear ramas o integrarlo con CI/CD.

```bash
git clone https://github.com/usuario/repositorio.git
cd repositorio
git checkout -b nueva-rama
git add archivo.py
git commit -m "Agrega script de validación"
git push origin nueva-rama
```

#### 🧠 Recomendaciones:
- Usar `git status` frecuentemente
- Integrar `git` en scripts para versionar backups o configuraciones

---

## 6.5. Lanzar Scripts de Python desde Bash

Python es el lenguaje preferido para procesamiento de datos. Bash puede lanzarlos, pasarles parámetros, capturar su salida, o integrarlos en pipelines más amplios.

### 📌 Ejecutar scripts directamente:

```bash
python script.py
```

### 📌 Activar entorno virtual:

```bash
source venv/bin/activate
python procesar_datos.py
deactivate
```

### 📌 Ejecutar con logging y control de errores:

```bash
if python script.py > log.txt 2>&1; then
  echo "Ejecutado correctamente"
else
  echo "Error en ejecución"
fi
```

### 📌 Pasar parámetros:

```bash
python etl.py --fecha 2025-04-19 --origen s3
```

---

# 7. Tópicos Adicionales y Buenas Prácticas

Además de los comandos y técnicas clásicas de Bash, existen herramientas complementarias y buenas prácticas que marcan una gran diferencia en la productividad, robustez y mantenibilidad de scripts en Data Engineering.

---

## 7.1. Gestión de Variables de Entorno y Secretos

Las variables de entorno son fundamentales para mantener configuraciones desacopladas del código. También se usan para manejar claves, rutas o parámetros en entornos de ejecución.

### 📌 Definición en Bash:

```bash
export DATA_PATH="/home/usuario/datos"
export API_KEY="mi_token_secreto"
```

### 📌 Acceso en scripts:

```bash
echo "Ruta de datos: $DATA_PATH"
```

### 📌 Uso de `.env` y `source`:

Guarda tus variables en un archivo `.env`:

```bash
# .env
API_KEY="mi_api_key"
```

Y cárgalas con:

```bash
source .env
```

> ⚠️ Nunca subas `.env` con secretos a Git. Usa `.gitignore`.

---

## 7.2. Compresión y Archivado (`tar`, `gzip`, `zip`)

Estas herramientas permiten reducir el tamaño de archivos, comprimir backups o preparar envíos de datos.

### `tar` – Agrupar y archivar

```bash
tar -czvf backup.tar.gz carpeta/
tar -xvzf backup.tar.gz
```

### `gzip` – Comprimir un solo archivo

```bash
gzip archivo.csv        # Genera archivo.csv.gz
gunzip archivo.csv.gz
```

### `zip` y `unzip` – Compresión multiplataforma

```bash
zip -r archivos.zip carpeta/
unzip archivos.zip
```

> 🧠 Ideal para ahorrar espacio y acelerar transferencias en pipelines.

---

## 7.3. Programación de Tareas con `cron`

`cron` permite ejecutar scripts automáticamente en intervalos definidos (cada hora, día, semana, etc.)

### 📌 Ver y editar cronjobs:

```bash
crontab -e
```

### 📌 Ejemplo de tarea diaria a las 2:00 AM:

```
0 2 * * * /home/usuario/scripts/etl.sh >> /home/usuario/logs/etl.log 2>&1
```

| Campo   | Significado         |
|---------|---------------------|
| `0`     | Minuto              |
| `2`     | Hora                |
| `*`     | Día del mes         |
| `*`     | Mes                 |
| `*`     | Día de la semana    |

### 📌 Ver tareas programadas:

```bash
crontab -l
```

> 🧠 Perfecto para automatizar tareas ETL o backups.

---

## 7.4. Debugging de Scripts (`set -x`, `echo`)

### `set -x` – Modo verbose

Muestra cada comando antes de ejecutarlo:

```bash
set -x
echo "Esto se verá con su comando"
set +x
```

### `echo` para rastrear valores

```bash
echo "Procesando archivo: $archivo"
```

> ✅ Útil para entender errores, flujos lógicos y valores intermedios.

---

## 7.5. Estilo y Legibilidad en Scripts

Un script bien escrito no solo funciona, también es fácil de mantener y entender por otros.

### 🧠 Buenas prácticas:

- Usa nombres descriptivos (`procesar_datos.sh` en lugar de `pd.sh`)
- Añade comentarios explicativos (`# Este bloque valida la conexión`)
- Organiza en bloques lógicos (secciones de variables, funciones, ejecución)
- Usa `set -e` para evitar errores silenciosos
- Documenta al inicio el propósito y los argumentos del script

---

## 7.6. Herramientas CLI útiles para Data Engineers

Más allá de Bash puro, existen herramientas modernas que mejoran la experiencia y velocidad de trabajo:

| Herramienta | Descripción |
|-------------|-------------|
| `htop`      | Monitor de sistema interactivo (CPU, RAM, procesos) |
| `watch`     | Repite un comando cada X segundos (`watch -n 5 df -h`) |
| `pv`        | Muestra progreso de datos por pipes (`cat archivo | pv | gzip > archivo.gz`) |
| `parallel`  | Ejecuta comandos en paralelo (`cat urls.txt | parallel wget`) |
| `fd`        | Alternativa moderna a `find` (más rápida y fácil de usar) |
| `ripgrep`   | Búsqueda rápida de texto (mejor que `grep` para grandes proyectos) |

### 📌 Instalación en Ubuntu:

```bash
sudo apt install htop pv moreutils fd-find ripgrep
```

---

# 8. Ejemplos de Scripts para Data Engineering

En esta sección te presento tres ejemplos prácticos y reales de cómo usar Bash para automatizar tareas comunes en el flujo de trabajo de un Data Engineer. Todos los scripts están diseñados para ser simples, reutilizables y fáciles de adaptar.

---

## 8.1. Script para Descargar y Preprocesar Logs

Este script descarga un archivo de logs desde una URL, lo descomprime si es necesario, y filtra los errores más relevantes.

### 📁 `descargar_y_filtrar_logs.sh`

```bash
#!/bin/bash

set -e

# Variables
URL_LOG="https://example.com/logs/app.log"
ARCHIVO="app.log"
SALIDA="errores_filtrados.log"

# Descargar
echo "Descargando logs desde $URL_LOG..."
curl -O "$URL_LOG"

# Validar descarga
if [ ! -f "$ARCHIVO" ]; then
    echo "Error: No se descargó el archivo."
    exit 1
fi

# Filtrar errores
echo "Filtrando errores..."
grep -i "ERROR" "$ARCHIVO" | grep -v "DEBUG" > "$SALIDA"

echo "Errores guardados en $SALIDA"
```

---

## 8.2. Script para Mover Datos Procesados a Almacenamiento Cloud

Este script toma un conjunto de archivos procesados y los sube a un bucket de AWS S3. También permite loguear el proceso.

### 📁 `subir_a_s3.sh`

```bash
#!/bin/bash

set -e
set -o pipefail

# Variables
CARPETA="datos_procesados"
BUCKET="s3://mi-bucket-etl/procesados/"
LOG="upload.log"

# Verificar AWS CLI
if ! command -v aws &> /dev/null; then
    echo "Error: aws cli no está instalado."
    exit 1
fi

# Subir archivos
echo "Subiendo datos desde $CARPETA a $BUCKET"
aws s3 cp "$CARPETA" "$BUCKET" --recursive | tee -a "$LOG"

echo "Subida completada. Revisa el log en $LOG"
```

---

## 8.3. Script Wrapper para Ejecutar un Proceso SQL/Python

Este script sirve como envoltorio (*wrapper*) que lanza primero una consulta SQL (ej. limpieza de staging) y luego un script de procesamiento en Python.

### 📁 `ejecutar_pipeline.sh`

```bash
#!/bin/bash

set -e
set -o pipefail

# Variables
SQL_FILE="preparar_datos.sql"
PY_SCRIPT="procesar_datos.py"
LOG="pipeline.log"

# Ejecutar SQL
echo "[INFO] Ejecutando SQL..."
psql -U usuario -d basedatos -f "$SQL_FILE" >> "$LOG" 2>&1

# Validar salida SQL
if [ $? -ne 0 ]; then
    echo "[ERROR] Falló la consulta SQL"
    exit 1
fi

# Ejecutar Python
echo "[INFO] Ejecutando procesamiento Python..."
python "$PY_SCRIPT" >> "$LOG" 2>&1

if [ $? -eq 0 ]; then
    echo "[OK] Pipeline ejecutado correctamente"
else
    echo "[ERROR] Falló el script Python"
    exit 1
fi
```

---







