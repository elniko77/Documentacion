### Tips de administración para exchange onprem



#### Lista de directorios de autodiscover

    Get-AutodiscoverVirtualDirectory -server <ServerName> | fl name, url

#### En powershell habilitar el shell de exchange
    
    Add-PSSnapin Microsoft.Exchange.Management.PowerShell.SnapIn;
    
#### Ver estado del indexado:

    Get-MailboxDatabaseCopyStatus * | sort name | Select name,status,contentindexstate



### Recovery


#### Chequear el status de una mailbox database:
 
    eseutil /mh E:\exchange\DBMails1\DBmails1.edb
    
#### Chequear los logs:

    eseutil /ml E:\Exchange\DBMails1_Log\

#### Montar base:

    Mount-Database ‘DB01’
