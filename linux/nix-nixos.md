
#### Lista de paquetes

   https://search.nixos.org/packages
   
#### Reconstruir una nueva imagen y cambiar en el momento (sin reboot)

```bash
   $ sudo nixos-rebuild switch
```

#### Instalar paquetes de forma "temporal"
Crea un shell temporario, donde se podrá acceder al paquete instalado, al salir no quedarán rastros del paquete.

```bash
   $ sudo nix-shell -p neofetch
```

#### Habilitar y usar flatpaks

Editar /etc/nixos/configuration.nix , en la parte de servicios, agregar:

```bash
   services.flatpak.enable = true;
```
Habilitar el repo flathub

```bash
   flatpak remote-add — if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
```

