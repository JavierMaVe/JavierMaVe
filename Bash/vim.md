# Guía práctica de Vim para principiantes

Vim es un editor de texto avanzado, rápido y poderoso que viene preinstalado en la mayoría de sistemas Unix/Linux. Aunque al principio puede parecer intimidante, conocer lo básico te da una ventaja enorme en edición de archivos desde la terminal.

---

## 📚 Tabla de Contenido

1. [¿Qué es Vim y por qué usarlo?](#1-qué-es-vim-y-por-qué-usarlo)
2. [Modos de operación](#2-modos-de-operación)
3. [Navegación básica](#3-navegación-básica)
4. [Edición de texto](#4-edición-de-texto)
5. [Guardar, salir y combinaciones importantes](#5-guardar-salir-y-combinaciones-importantes)
6. [Buscar y reemplazar](#6-buscar-y-reemplazar)
7. [Copiar, cortar y pegar (yankear)](#7-copiar-cortar-y-pegar-yankear)
8. [Trucos útiles y productividad](#8-trucos-útiles-y-productividad)
9. [Recursos para seguir aprendiendo](#9-recursos-para-seguir-aprendiendo)

---

## 1. ¿Qué es Vim y por qué usarlo?

Vim (Vi Improved) es una versión mejorada del editor `vi`. Está diseñado para ser ligero, eficiente y extremadamente personalizable. Lo puedes usar en servidores, sistemas embebidos, o como tu editor principal.

**Ventajas:**

- Carga instantánea, incluso en sistemas remotos
- Potente para edición masiva y repetitiva
- No requiere ratón
- Funciona en modo texto puro
- Ampliamente disponible (casi universal en Unix/Linux)

---

## 2. Modos de operación

Vim no es como otros editores. Tiene distintos **modos de trabajo**:

| Modo            | Qué hace                                       |
|-----------------|------------------------------------------------|
| `Normal`        | Navegar, borrar, copiar, pegar                 |
| `Insert`        | Escribir texto                                 |
| `Visual`        | Seleccionar texto                              |
| `Command-line`  | Ejecutar comandos (guardar, salir, etc.)       |

### 🔁 Cambiar entre modos:

- `i` → Modo Insertar
- `Esc` → Volver a Modo Normal
- `:` → Modo Comando
- `v` → Modo Visual (selección por carácter)
- `V` → Modo Visual (selección por línea)

---

## 3. Navegación básica

| Acción                  | Tecla(s)           |
|-------------------------|--------------------|
| Mover cursor            | `h` `j` `k` `l`     |
| Palabra siguiente       | `w`                |
| Palabra anterior        | `b`                |
| Ir al inicio de línea   | `0`                |
| Ir al final de línea    | `$`                |
| Ir al principio del archivo | `gg`           |
| Ir al final del archivo     | `G`            |
| Ir a línea N            | `:N` o `Ngg`       |
| Página arriba/abajo     | `Ctrl + u / Ctrl + d` |

---

## 4. Edición de texto

| Acción                        | Tecla(s)                |
|-------------------------------|-------------------------|
| Insertar antes del cursor     | `i`                     |
| Insertar al final de línea    | `A`                     |
| Borrar carácter bajo cursor   | `x`                     |
| Borrar desde cursor a final   | `D`                     |
| Reemplazar un carácter        | `r` seguido de tecla    |
| Rehacer acción                | `Ctrl + r`              |
| Deshacer acción               | `u`                     |

---

## 5. Guardar, salir y combinaciones importantes

| Comando        | Acción                           |
|----------------|----------------------------------|
| `:w`           | Guardar                          |
| `:q`           | Salir                            |
| `:q!`          | Salir sin guardar                |
| `:wq` o `:x`   | Guardar y salir                  |
| `ZZ`           | Guardar y salir (modo normal)    |

---

## 6. Buscar y reemplazar

### 🔍 Buscar texto:

- `/palabra` → Buscar hacia abajo
- `?palabra` → Buscar hacia arriba
- `n` → siguiente ocurrencia
- `N` → ocurrencia anterior

### 🔁 Reemplazar texto:

```vim
:%s/palabra/nueva/g
```

- `%` → en todo el archivo
- `g` → todas las ocurrencias en la línea

---

## 7. Copiar, cortar y pegar (yankear)

| Acción            | Tecla(s)           |
|-------------------|--------------------|
| Copiar línea      | `yy`               |
| Cortar línea      | `dd`               |
| Pegar después     | `p`                |
| Pegar antes       | `P`                |
| Copiar selección  | `y` en modo visual |
| Cortar selección  | `d` en modo visual |

---

## 8. Trucos útiles y productividad

- `.` → Repite el último comando
- `u` → Deshacer
- `Ctrl + r` → Rehacer
- `:set number o :set nu` → Mostrar números de línea
- `:set nonumber o :set nonu` → Para ocultar los números de línea
- `:set relativenumber` → Líneas relativas
- `:syntax on` → Coloreado de sintaxis
- `:noh` → Quitar resaltado de búsqueda

Para que aparcezcan todas esas opciones siempres, habrá que crear o modificar ~/.vimrc.

`set nu`

---

## 9. Recursos para seguir aprendiendo

- `vimtutor` (en tu terminal)
- https://www.openvim.com/
- https://vim-adventures.com/
- Libro: *Practical Vim* de Drew Neil
- Curso en YouTube: "Vim for Beginners"

---
