## Logging Patterns

  * 1- DaemonSet: cada nodo en el cluster tiene un pod con el agente de logging. Lee los logs de /var/logs y los envía al storage backend.


  * 2- Sidecar Pattern: un contenedor dedicado junto a cada aplicación. 