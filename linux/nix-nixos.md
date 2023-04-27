
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
#### Habilitar el repo flathub

```bash
   flatpak remote-add — if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
```

#### Update
Nixos no actualiza automáticamente, para actualizar todo y rebootear:

```bash
    $ sudo nixos-rebuild boot — upgrade
```
#### Garbage collection
Cada vez que se hace un rebuild, en grub se tendrá una lista de las distintas versiones. Con el siguiente comando se borrarán todas las versiones salvo la actual.

```bash
    $ sudo nix-collect-garbage -d
```

Borrar versiones mas antiguas que 30 días

```bash
    $ sudo nix-collect-garbage — delete-older-than 30d
```
















