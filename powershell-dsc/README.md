# Powershell dsc 

Powershell dsc (Desired State Configuration) es una plataforma para configurar y hacer management de equipos de forma declarativa. A grandes rasgos sería algo parecido a terraform.


Ejemplo para asegurarse que un servicio esté parado, crear un archivo llamado myservice.ps1:

```
    Configuration MyService {
        Node localhost {
            Service wsearch {
                Name = 'Wsearch'
                State = 'stopped'
            }
        }
    }
    MyService
```
#### Ejecutarlo en la consola:

     .\MyService.ps1

Esto generará un archivo .mof dentro de un dir con el mismo nombre.

#### Testear el script:

    Test-DscConfiguration -Path C:\Users\nss\OneDrive\Myservice    

Se obtendrá una salida similar a esta:

    PS C:\users\nss\Documents\Git> Test-DscConfiguration -Path C:\Users\nss\OneDrive\MyService\

    PSComputerName  ResourcesInDesiredState        ResourcesNotInDesiredState     InDesiredState
    --------------  -----------------------        --------------------------     --------------
    localhost       {[Service]wsearch}                                            True

Aplicar el script:

    Start-DscConfiguration -Path C:\Users\nss\OneDrive\Myservice\ -Verbose

