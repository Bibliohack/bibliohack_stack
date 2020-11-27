## Bibliohack Stack 

Este repositorio contiene el stack de software para digitalización y posproceso de Bibliohack

El script instalará las aplicaciones en `/opt/bibliohack`

## Instalar

descargar el paquete de instalación desde:

    wget http://files.bibliohack.org/bibliohack_install.tar.gz

descomprimir el archivo descargado:

    tar xzvf bibliohack_install.tar.gz

ejecutar el script de instalación:

    cd bibliohack_install
    bash install

El script pedira credenciales de sudo cuando lo necesite.

Una vez finalizada la instalación, ya se puede borrar `bibiohack_install`

**Rutas de acceso a los programas**

- Dalclick (captura con CHDK) `/opt/bibliohack/dalclick/dalclick`
- Gestor de Post-proceso `/opt/bibliohack/dalclick/ppm/ppm_daemon.sh`
- Scantailor Advanced `/opt/bibliohack/components/scantailor-advanced/scantailor`
- Scantailor Universal (con cli mode) `/opt/bibliohack/components/scantailor-universal/scantailor`
- Pdfbeads: `/opt/bibliohack/components/pdfbeads-kopi/bin/pdfbeads` 
- Tesseract: `tesseract`

## Problemas con librerias Tecgraf

En caso de haber borrado accidentalmente el directorio `/opt/bibliohack`, el script `install` no podrá
volver a instalar las aplicaciones hasta que no se desinstalen del sistema las librerías **Tecgraf**

Para esto ejecute `uninstall_tecgraf_libs`. En caso de tener las librerías Tecgraf instaladas en el 
sistema por otra aplicación, en versiones diferentes, este script no podrá borralas-

## Creación del paquete de instalacióm

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
