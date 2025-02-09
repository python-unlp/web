---
date: 2023-04-29
categories:
  - Python
  - Entornos virtuales
---

# Entornos virtuales

**venv** es una herramienta usada para crear un ambiente aislado de
**Python**. Este ambiente tiene su propio directorio de instalación que no
comparte librerías con otros ambientes virtuales ni con el sistema operativo.

Esto tiene la ventaja que separa las librerías específicas que necesitamos en
cada entorno virtual.

Es útil hacer esta separación porque en el desarrollo de software es muy común
que queramos usar en distintos proyectos distintas versiones de la misma
librería.

<!-- more -->

Por ejemplo, podemos tener un proyecto que hicimos hace un tiempo que usa una
versión de `numpy` que ahora no es la última. Para ese proyecto puede estar
perfecta esa versión y algunas veces puede ser peligroso actualizar una
librería. Por el contrario si vamos a arrancar un nuevo proyecto seguramente
queremos poder usar la última versión de `numpy`.

La solución que nos da **venv** es crear la cantidad de directorios
virtuales que queramos con su propia versión de **Python** y sus propias librerías
externas de forma aislada.

Una práctica muy común con **venv** es tener un entorno virtual por
proyecto aislando cada proyecto y evitando cualquier problema de compatibilidad.

## ¿Cómo crear un entorno virtual?

Para crear un entorno virtual primero tenemos que ubicarnos en el directorio
donde está el código de nuestra aplicación.

En este ejemplo crearemos un directorio para un nuevo proyecto y nos ubicaremos
en el mismo:

```bash
mkdir mi_proyecto
cd mi_proyecto
```

Ahora vamos a crear un directorio virtual llamado `venv` para la versión de
**Python** que hayamos configurado como global

```bash
python -m venv venv
```

!!! warning

    Recuerden tener en cuenta tener configurada la versión de Python con la que
    quieren arrancar el proyecto. En nuestro caso la versión `3.11`

    Se pueden asegurar ejecutando:

    `$ python --version`

    Si la versión no coincide e instalaron **Python** con venv, pueden usar
    `pyenv global 3.11.x` para configurarla o bien `pyenv shell 3.11.x` para
    usarla temporalmente (donde `x` es el último dígito de la versión específica
    que instalaron).

Ya estamos listos para usar nuestro entorno virtual. Tanto la versión de
**Python** con las librerías se van a almacenar dentro del directorio `venv`
creado.

## ¿Como usar mi entorno virtual?

Para activar el entorno ejecutamos

```bash
source venv/bin/activate  # Linux
```
```bash
venv\Scripts\activate  # Windows
```

Ahora si localizamos donde está el ejecutable de **Python** que utilizamos
veremos que es el que está dentro del directorio virtual

```bash
which python
mi_proyecto/venv/bin/python
```

Es necesario desactivar si queremos volver a usar el **Python** que instalamos
globalmente

```bash
deactivate
```

Ahora si necesitamos instalar una librería tenemos que activar el entorno y
usar `pip`

```bash
pip install numpy
```
