### Tips de administración para exchange onprem



#### Lista de directorios de autodiscover

    Get-AutodiscoverVirtualDirectory -server <ServerName> | fl name, url

#### En powershell habilitar el shell de exchange
    
    Add-PSSnapin Microsoft.Exchange.Management.PowerShell.SnapIn;
    
#### Ver estado del indexado:

    Get-MailboxDatabaseCopyStatus * | sort name | Select name,status,contentindexstate


#### Conexión a un pwsh remoto: 

    $cred=Get-Credential
    $sess = New-PSSession -Credential $cred -ComputerName <remotemachinename>
    Enter-PSSession $sess
    Add-PSSnapin Microsoft.Exchange.Management.PowerShell.SnapIn;

#### Permisos a un usuario para crear/borrar buzones
    Agregar al usuario a los siguientes grupos:
    "Recipient Management"
    "View-Only Organization Management"


### Recovery


#### Chequear el status de una mailbox database:
 
    eseutil /mh E:\exchange\DBMails1\DBmails1.edb
    
#### Chequear los logs:

    eseutil /ml E:\Exchange\DBMails1_Log\

#### Montar base:

    Mount-Database ‘DB01’

#### Problemas de indexado:

``` cpp
    # Parar los servicios desde powershell
    [PS] C:\>Stop-Service MSExchangeFastSearch
    [PS] C:\>Stop-Service HostControllerService
    
    # Borrar el directorio de los indices donde está la base, ej: D2D24030-001F-46DA-8176-0A232325A4B6D12.1.Single
    
    [PS] C:\>Start-Service MSExchangeFastSearch
    [PS] C:\>Start-Service HostControllerService
    
```

