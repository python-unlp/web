---
date: 2023-05-01
categories:
  - Python
  - Manejo de paquetes
  - Dependencias
  - pip
  - requirements.txt
---

# Gestión de dependencias en Python

El manejo de paquetes en Python es esencial para la organización y portabilidad de los proyectos. Python utiliza `pip` como su gestor de paquetes para instalar, actualizar y administrar bibliotecas externas que no forman parte del núcleo del lenguaje.

Estas bibliotecas se descargan desde el repositorio oficial [`PyPI`](https://pypi.org/), aunque es posible configurar `pip` para utilizar repositorios personalizados.

<!-- more -->

## Instalación de `pip`

Generalmente, `pip` viene preinstalado con Python. Sin embargo, si no está disponible, podemos instalarlo manualmente siguiendo estos pasos:

1. Descargar el script de instalación desde [aquí](https://bootstrap.pypa.io/get-pip.py).
2. Ejecutar el siguiente comando:
   ```bash
   python get-pip.py
   ```

Para más detalles, consulta la [documentación oficial](https://pip.pypa.io/en/stable/installing/).

## Instalación de paquetes con `pip`

Para instalar una librería en Python, utilizamos el siguiente comando:

```bash
pip install nombre_del_paquete
```

Si necesitamos una versión específica de una librería, podemos indicarlo así:

```bash
pip install nombre_del_paquete==versión
```

Ejemplo:
```bash
pip install numpy==1.18.1
```

## Uso de `requirements.txt`

Para facilitar la instalación de múltiples dependencias en un proyecto, es recomendable crear un archivo `requirements.txt` que contenga la lista de paquetes y sus versiones.

Ejemplo de `requirements.txt`:
```bash
numpy==1.18.1
pandas==1.0.1
matplotlib==3.1.3
```

Para instalar todas las dependencias listadas en el archivo, ejecutamos:
```bash
pip install -r requirements.txt
```

## Buenas prácticas para gestionar dependencias

1. **Usar entornos virtuales:** Se recomienda instalar las dependencias en un entorno virtual para evitar conflictos entre proyectos. Consulta la guía sobre [Entornos Virtuales](https://docs.python.org/3/library/venv.html) si necesitas más información.
2. **Registrar las dependencias en `requirements.txt`:** Después de instalar un paquete, es recomendable actualizar este archivo.
3. **Obtener la lista de paquetes instalados:** Si olvidamos qué paquetes hemos instalado, podemos generar la lista con:
   ```bash
   pip freeze > requirements.txt
   ```
4. **Mantener actualizado `requirements.txt`** para garantizar que el sistema funciona con las versiones correctas de las librerías.

## Estructura recomendada del proyecto

Se recomienda incluir `requirements.txt` en la raíz del proyecto para que todos los integrantes del equipo puedan instalar las dependencias fácilmente:

```
.
├── main.py
├── requirements.txt
└── modulo1
    ├── __init__.py
    ├── reader.py
    └── view.py
```

### Instalación de dependencias en equipos de trabajo

Si trabajamos en equipo, cualquier nuevo integrante debe ejecutar:
```bash
pip install -r requirements.txt
```
para instalar todas las dependencias necesarias sin tener que hacerlo manualmente una por una.

## Recursos adicionales
- [Documentación oficial de `pip`](https://pip.pypa.io/en/stable/reference/)
- [Repositorio oficial de paquetes (`PyPI`)](https://pypi.org/)

Mantener un correcto manejo de dependencias es clave para garantizar que el código sea reproducible y fácil de compartir. ¡Sigue estas prácticas para un desarrollo más ordenado y eficiente! 🚀
