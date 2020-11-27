## Bibliohack Stack 

Este repositorio contiene el stack de software para digitalización y posproceso de Bibliohack

Es script de instalación instalará las aplicaciones en `/opt/bibliohack`

### Instalar

descargar el paquete de instalacion desde:

    wget http://files.bibliohack.org/bibliohack_install.tar.gz

descomprimir:

    tar xzvf bibliohack_install.tar.gz

ejecutar el script de instalación:

    cd bibliohack_install
    bash install

el script pedira credenciales de sudo cuando lo necesite

Una vez finalizada la instalación, ya se puede borrar `bibiohack_install`

**Rutas de acceso a los programas**

Dalclick (captura con CHDK)
`/opt/bibliohack/dalclick/dalclick`

Gestor de Post-proceso
`/opt/bibliohack/dalclick/ppm/ppm_daemon.sh`

Scantailor Advanced 
`/opt/bibliohack/components/scantailor-advanced/scantailor`

Scantailor Universal (con cli mode)
`/opt/bibliohack/components/scantailor-universal/scantailor`

Pdfbeads:
`/opt/bibliohack/components/pdfbeads-kopi/bin/pdfbeads` 

Tesseract:
`tesseract`

#### Problemas con librerias Tecgraf

En caso de haber borrado accidentalmente el directorio `/opt/bibliohack`, el script `install` no podrá
volver a instalar las aplicaciones hasta que no se desinstalen del sistema las librerías **Tecgraf**

Para esto ejecute `uninstall_tecgraf_libs`. En caso de tener las librerías Tecgraf instaladas en el 
sistema por otra aplicación, en versiones diferentes, este script no podrá borralas-

#### Creación del paquete de instalacióm

ejecutar

    .build_package

El script copia los archivos, omite las carpetas .git y comprime en tar.gz
