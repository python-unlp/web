---
date: 2023-04-22
categories:
  - Git
  - Instalación
---

# Guía de Git

En la explicación práctica hablamos sobre los conceptos de `git`.

<!-- more -->

## Instalación

### En Debian-based

```bash
sudo apt update
sudo apt upgrade
sudo apt install git
```

### En Red Hat-based

```bash
sudo yum upgrade
sudo yum install git
```
### En Arch-based
```bash
sudo pacman -S git
```

### En MacOS

```bash
brew install git
```

### En Windows

Descargar el instalar de [gitforwindows](https://gitforwindows.org/) o de
[git-scm](https://git-scm.com/download/win). Tener en cuenta que en la cátedra
vamos a utilizar `GitBash` por lo cual deben asegurarse que se instale.

#### Tutorial para instalar Git en Windows

<iframe width="560" height="315" src="https://youtu.be/BVYCI62_rHM" title="Instalar Git en Windows" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

## ¿Cómo usar Git?

Vamos a ver dos formas para comenzar a trabajar con `Git`:

- Creando un repositorio desde cero y agregando los archivos iniciales.
- Descargando un proyecto ya creado y modificarlo.

### Configurar información en Git

En `git` cuando se va a realizar una operación para generar una nueva versión del
código es necesario contar con información de usuario. Por esto es necesario que
configuremos lo siguiente:

```bash
$ git config --global user.name "John Doe"
$ git config --global user.email johndoe@example.com
```

Para ver la configuración:

```bash
git config --list
```
