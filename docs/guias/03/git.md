# Guía de Git

Git es una herramienta fundamental a la hora de escribir código y aún más
importante cuando lo hacemos de forma colaborativa.

Esta guía te mostrará distintas formas de instalar la herramienta en tu máquina
para comenzar a utilizarla.

## Instalación

### En Debian-based

```bash
sudo apt update
```

```bash
sudo apt upgrade
```

```bash
sudo apt install git
```

### En Red Hat-based

```bash
sudo yum upgrade
```

```bash
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

Descargar en instalar de [gitforwindows](https://gitforwindows.org/) o de
[git-scm](https://git-scm.com/download/win). Tener en cuenta que en la cátedra
vamos a utilizar `GitBash` por lo cual deben asegurarse que se instale.

## Configurar información en Git

En `git` cuando se va a realizar una operación para generar una nueva versión del
código es necesario contar con información de usuario. Por esto es necesario que
configuremos lo siguiente:

```bash
git config --global user.name "John Doe"
git config --global user.email johndoe@example.com
```

Para ver la configuración:

```bash
git config --list
```
