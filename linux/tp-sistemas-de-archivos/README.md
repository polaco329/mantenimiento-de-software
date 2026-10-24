# TP: Sistema de Archivos en Linux

* **Materia:** Mantenimiento de Software
* **Estudiante:** Francisco S. Sfiligoy Borkoski
* **Fecha de entrega:** 2026

> **Evidencias:** las cinco capturas se obtuvieron en una terminal real de
> Linux Mint y muestran el usuario y el equipo en el prompt, los comandos y sus
> salidas.

---

## 1. Estructura del arbol de directorios

Comando:

```bash
ls -l /
```

![Listado de la raiz](assets/01_raiz_ls.png)

| Directorio | Funcion |
| :--- | :--- |
| `/etc` | Contiene archivos de configuracion del sistema y de muchos programas instalados. |
| `/home` | Contiene los directorios personales de los usuarios y sus archivos y configuraciones. |
| `/dev` | Expone dispositivos del sistema mediante archivos especiales, como los que representan discos, terminales o puertos. |
| `/var` | Guarda datos variables que cambian durante el uso del sistema, como registros (logs), colas de impresion y caches. |

## 2. Sensibilidad a mayusculas y minusculas

Comandos:

```bash
touch Ejercicio.txt
touch ejercicio.txt
ls -l ejercicio* Ejercicio*
```

![Sensibilidad a mayusculas y minusculas](assets/02_case_sensitivity.png)

**Respuesta:** En los sistemas de archivos Linux habituales, las mayusculas y
las minusculas se consideran caracteres distintos. Por eso `Ejercicio.txt` y
`ejercicio.txt` son dos nombres diferentes y pueden coexistir en un mismo
directorio. En Windows, el sistema de archivos normalmente conserva como se
escribio el nombre, pero no distingue mayusculas de minusculas al buscarlo; por
eso esos dos nombres suelen considerarse el mismo archivo.

## 3. Visualizacion y gestion de archivos ocultos

Comandos:

```bash
touch .mi_configuracion_oculta
ls
ls -la
```

![Archivos ocultos](assets/03_archivos_ocultos.png)

**Respuesta:** El punto inicial permite identificar convencionalmente archivos y
directorios ocultos. Se usa, por ejemplo, para mantener menos visibles en los
listados habituales archivos de configuracion y preferencias del usuario. No es
un mecanismo de seguridad: el archivo sigue estando accesible si se conoce su
nombre, y `ls -la` permite mostrarlo junto con los demas.

## 4. Buenas practicas en nombres de archivos

Comandos:

```bash
mkdir tp_sistema_ficheros_2026
ls -ld tp_sistema_ficheros_2026
```

![Creacion de un directorio](assets/04_creacion_directorio.png)

**Respuesta:** `tp_sistema_ficheros_2026` usa letras sin acentos, numeros y
guiones bajos, y no contiene espacios ni signos de puntuacion. Asi es mas
sencillo escribirlo en la terminal y referenciarlo en scripts y distintos
programas. En cambio, `TP Sistema de Ficheros (Año 2026)!.doc` tiene espacios,
mayusculas, parentesis, un signo de exclamacion y la letra `ñ`. La guia tambien
recomienda evitar letras acentuadas. Algunos de esos caracteres requieren
comillas o escapes en la terminal y pueden causar inconvenientes de
compatibilidad.

## 5. Exploracion de dispositivos y procesos

Comandos:

```bash
ls /proc
ls /dev
```

![Contenido de /proc y /dev](assets/05_proc_dev.png)

**Respuesta:** `/proc` es un sistema de archivos virtual que el kernel presenta
dinamicamente. Expone informacion sobre los procesos en ejecucion y el estado y
la configuracion del kernel, por ejemplo, datos de CPU y memoria. Su contenido
no es un conjunto de archivos ordinarios guardados permanentemente en el disco:
se genera a partir del estado actual del sistema.
