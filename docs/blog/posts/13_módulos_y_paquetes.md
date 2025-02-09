---
date: 2024-03-02
categories:
  - Python
  - Módulos
  - Paquetes
---

# Módulos y paquetes

Python permite organizar el código en al menos 2 formas:

1. Módulos: Esto es simplemente un archivo con extensión `.py`
    * Se pueden importar desde otros módulos.
    * Se pueden ejecutar como scripts.
    * Desde el código del módulo podemos hacer cosas distintas dependiendo de si se importa o se usa como script comparando la variable `__name__` con `"__main__"`.

2. Paquetes: Una carpeta que tiene un archivo `__init__.py` adentro.
    * Permiten agrupar módulos y otros paquetes.
    * Se pueden importar desde módulos.

<!-- more -->

Casos de uso
------------

### Se necesita probar un ejemplo muy pequeño o escribir un programa muy sencillo y corto

Es posible escribir todo en un módulo, por ejemplo:

hola.py

```python
print("Hola mundo")
```

Se ejecuta con `python hola.py`

### Se necesita un programa más realista y modularizado

Un proyecto más realista tiene una serie de desafíos:

* El código es un poco largo para un solo achivo.
* Seguramente se usan bibliotecas externas (los usuarios tienen que tener algún mecanismo para instalarlas).
* Posiblemente necesite archivos que no son código **Python** pero que deben ser distribuídos con el programa como íconos o plantillas de texto.

La forma de solucionar esto es crear alguna estructura prolija para el programa. Existen varias formas de hacer esto con proyectos **Python**. Veremos una en particular:

1. Crearemos un directorio para nuestro programa. El mismo será también un repositorio git.

```sh
mkdir noticias_unlp
cd noticias_unlp
git init
```

2. Es recomendable crear un entorno virtual con `venv` para instalar las bibliotecas que sean necesarias para este proyecto, esta carpeta **no debe ser agregada al repositorio git** ya que su contenido sólo funciona en el entorno en el que es creada:

```sh
python3.11 -m venv venv
source venv/bin/activate # activamos el virtual env para esta sesión
# debemos hacer esto cada vez que abrimos una terminal para trabajar en el proyecto
```

3. Dentro de ese directorio crearemos un **paquete Python** (es decir un directorio con un archivo `__init__.py`) con el nombre `unlp_news`. En ese directorio pondremos casi todos los módulos del
programa. La estructura de archivos y directorios dentro de `noticias_unlp` será:

```
.
└── unlp_news
    └── __init__.py

```

4. Agregaremos la funcionalidad del programa en módulos dentro del paquete `unlp_news`. Por ejemplo si agregamos 2 módulos la estructura es la siguiente:

```
.
└── unlp_news
    ├── __init__.py
    ├── reader.py
    └── view.py
```

5. Creamos un script, es decir un módulo que será ejecutable como programa, lo ubicaremos fuera de la carpeta `unlp_news`, ésto es estratégico para que el programa se inicialice bien y los imports funcionen correctamente. Puede tener cualquier nombre pero en este caso se llamará `main.py`:


```
.
├── main.py
└── unlp_news
    ├── __init__.py
    ├── reader.py
    └── view.py
```

Éste script puede importar a los módulos usando imports absolutos, por ejemplo:

```python
import unlp_news.reader
```

o bien

```python
from unlp_news import reader
```

Y deberá contener el programa principal que ejecuta al resto de la funcionalidad.

6. Como se mencionó más arriba, la mayoría de los programas dependen de bibliotecas externas, específicaremos esas bibliotecas y sus versiones en el archivo `requirements.txt` para que cualquiera las pueda instalar (se pueden instalar con `pip install -r requirements.txt`):

```
beautifulsoup4==4.12.3
requests==2.31.0
rich==13.7.1
```

7. Finalmente la estructura del programa será la siguiente:

```
.
├── main.py
├── requirements.txt
└── unlp_news
    ├── __init__.py
    ├── reader.py
    └── view.py
```

En algún momento debemos hacer `git add` a todos estos archivos y los correspondientes `git commit` y `git push` para que estén disponibles en el repositorio.

A esta estructura mínima se le pueden agregar distintos archivos para completar el proyecto como:

* README.md: Documentación básica del proyecto
* LICENSE: Licencia de uso y distribución

Bonus
-----

Probá descargarte el ejemplo anterior y hacerlo funcionar para practicar:

```sh
git clone https://github.com/fernandolopez/noticias_unlp.git
```

Usá un entorno virtual y `pip install -r requirements.txt` para instalar las bibliotecas requeridas y ejecutá el `main.py` para ver si se ejecuta correctamente.
