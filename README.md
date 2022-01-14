# Bibliohack Stack 

Este repositorio contiene el stack de software y las dependencias necesarias para instalar el software de digitalización y post-proceso de Bibliohack. 

Puede leer una referencia rápida de los componentes del stack [en esta página](http://codex.bibliohack.org/Bibliohack_Stack/).

**Las aplicaciones de bibliohack stack que se gestionan por fuera de APT se instalarán en `/opt/bibliohack`**

## Instalar (solo para Ubuntu 18.04)

descargar el paquete de instalación desde:

    cd ~
    wget http://files.bibliohack.org/bibliohack_install.tar.gz

descomprimir el archivo descargado:

    tar xzvf bibliohack_install.tar.gz

ejecutar el script de instalación (**NO usar sudo**, el script pedirá credenciales de `sudo` cuando lo necesite):

    cd bibliohack_install
    bash install

Una vez finalizada la instalación, la carpeta `bibliohack_install` ya no es necesaria y se puede borrar. Esta carpeta ha sido pensada para tenerla disponible en un pendrive USB y realizar las instalaciones desde allí en diferentes equipos que a veces no tienen conexión a internet.

Más detalles de la instalación de Ubuntu 18.04 "Bionic Beaver" en <http://codex.bibliohack.org/Bibliohack_instalador/>

**El script no genera ningún icono de acceso en el menú de aplicaciones o en el escritorio**, se deben iniciar desde la consola o crear los lanzadores manualmente

**Rutas de acceso a los programas**

- Dalclick (captura con CHDK) `/opt/bibliohack/dalclick/dalclick`
- Gestor de Post-proceso `/opt/bibliohack/dalclick/ppm/ppm_daemon.sh`
- Scantailor Advanced `/opt/bibliohack/components/scantailor-advanced/scantailor`
- Scantailor Universal (con cli mode) `/opt/bibliohack/components/scantailor-universal/scantailor`
- Pdfbeads: `/opt/bibliohack/components/pdfbeads-kopi/bin/pdfbeads` 
- Tesseract: `tesseract`

## Instalación de los componentes en forma manual

* Scantailor en todas sus versiones: <http://codex.bibliohack.org/scan_tailor/>
* Tesseract OCR: <http://codex.bibliohack.org/tesseract-ocr/>
* PDFbeads: <http://codex.bibliohack.org/pdfbeads/> (`pdfbeads-kopi` <https://github.com/Bibliohack/pdfbeads-kopi> es un fork de pdfbeads que se instala en las últimas versiones de Ubuntu/Debian)
* CHDKPTP: <http://codex.bibliohack.org/chdkptp/> (extensión Picture Transfer Protocol para Canon Hack Development Kit <https://app.assembla.com/wiki/show/chdkptp>)
* CHDK: recursos para la instalación de CHDK <http://codex.bibliohack.org/CHDK/>

## Problemas con librerías Tecgraf

En caso de haber borrado accidentalmente el directorio `/opt/bibliohack`, el script `install` no podrá
volver a instalar las aplicaciones hasta que no se desinstalen del sistema las librerías **Tecgraf** 
(y para desinstalar estas librerías son necesarios los scripts de desinstalción de Tecgraf que quedan 
guardados en `/opt/bibliohack`!)

`uninstall_tecgraf_libs` intenta desinstalar Tecgraf con los paquetes disponibles en el repositorio. 
En caso de tener las librerías Tecgraf ya instaladas en el sistema por otra aplicación (algo muy raro), 
en versiones diferentes a las requeridas por el paquete de bibliohack, este script no podrá borrarlas y debe desinstalarlas a mano.

## Compilar el paquete de instalación

Este repositorio contiene todo el código fuente del stack de software. El paquete de instalación (`bibliohack_install.tar.gz`) se genera usando el script `.build_package`. Para clonar el repositorio es necesario tener instalado `git-lfs` en el sistema.

Instalar *Git Large File Storage (LFS)* en el sistema. Más info en <https://git-lfs.github.com/>

Descargar e instalar LFS:

    curl -s https://packagecloud.io/install/repositories/github/git-lfs/script.deb.sh | sudo bash
    sudo apt-get install git-lts
    git install lts

clonar este repositorio recursivamnte:

    git clone --recursive https://github.com/Bibliohack/bibliohack_stack bibliohack_stack
    cd bibliohack_stack
    
ejecutar

    bash .build_package

El script copia los archivos, omite las carpetas .git y otros archivos de git, y finalmente comprime el paquete en tar.gz
