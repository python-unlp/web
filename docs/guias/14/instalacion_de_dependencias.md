
# Añadiendo dependencias a nuestro sistema

---
### Objetivo
La presente guía pretende ser un punteo de los pasos a seguir para añadir cualquier dependencia/librería a nuestro sistema.

Cuando hablamos de dependencia -en este documento- nos referimos justamente a cualquier librería externa y NO incluida de manera estándar por Python que nuestro sistema la requiere para funcionar.

Algunos de los ejemplos más comunes es la incorporación de:

- pandas
- numpy
- matplotlib
- requests
- path

---
### Paso a paso

1. Se recomienda, y en esta materia utilizamos, los entornos virtuales de Python como _ambiente controlado_ para la instalación de librerías. Por lo tanto el primer paso es activar el entorno virtual (se recomienda leer la guía denominada **Entornos virtuales** si es necesario).

2. Realizar la instalación mediante el manejador de paquetes Pip de la librería necesaria para el sistema:
		
	```bash
	pip install jupyter
	```

**En este punto ya tenemos la librería disponible para ser importada y utilizada en nuestro sistema, sin embargo, -como buena practica de programación- debemos dejar explícitas las librerías utilizadas por nuestro sistema. Es importante recordar que la librería fue instalada en nuestro entorno virtual pero este no es subido al repositorio por lo que si deseamos trabajar en equipo no hemos establecido cuales son los requerimientos del sistema**. 

3. Mediante el comando pip freeze obtener la versión de la librería instaladas (este paso es necesario solo si al momento de instalar la librería no se especificó la versión)
	```bash
	pip freeze
	```

	Del listado solo copiar la librería y su versión, debería ser algo similar a:
	```bash
	jupyter==1.0.0
	```

4. Crear un archivo denominado **requirements.txt** y en él simplemente pegar la dependencia. Cabe aclarar que cada nueva dependencia se debe escribir en una nueva linea de este archivo.
	El contenido del archivo para nuestro ejemplo es:
	```bash
	jupyter==1.0.0
	```

5. Este archivo **requirements.txt** debe ser añadido al repositorio del proyecto. Si bien puede ser añadido en cualquier sitio de nuestro repositorio se recomienda que esté en la raiz:
```
.
├── main.py
├── requirements.txt
└── modulo1
    ├── __init__.py
    ├── reader.py
    └── view.py
```

6. En caso de trabajar en equipo cualquier integrante del equipo ante un cambio en este archivo debe ejecutar en su entorno virtual:
	```bash
	pip install -r requirements.txt
	```


**Procurar siempre tener el **requirements.txt** actualizado a las necesidades de nuestro sistema, ya que en él se establecen las librerías y versiones para las cuales garantizamos que nuestro sistema funciona correctamente.**

* README.md: Documentación básica del proyecto
* LICENSE: Licencia de uso y distribución

