```bash
   systemctl list-timers

   #Ejecutar tareas manualmente
   systemctl start systemd-tmpfiles-clean
```


#### Ejecutar script x min después de booteo

```bash 
# cat /etc/systemd/system/run-script-with-delay.service
[Unit]
Description=Run script at startup

[Service]
Type=oneshot
ExecStart=/tmp/delay_script.sh
TimeoutStartSec=0
```

```bash
# cat /etc/systemd/system/run-script-with-delay.timer
[Unit]
Description="Run script after 5 minutes of boot"

[Timer]
OnBootSec=5min

[Install]
WantedBy=default.target

### Habilitar el timer
# systemctl disable run-script-with-delay.service
# systemctl enable run-script-with-delay.timer
```












