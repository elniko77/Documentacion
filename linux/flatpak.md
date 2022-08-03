#### Integrar con software de gnome

    sudo apt install gnome-software-plugin-flatpak
  
#### Instalar flatseal para manejar permisos
    
    flatpak install flathub com.github.tchx84.Flatseal

#### Aplicar temas gtk para que sea visualmente mas consistente

    sudo flatpak override --filesystem=$HOME/.themes
    sudo flatpak override --env=GTK_THEME=chosen-theme 
    (Revertir los cambios:)
    sudo flatpak override --reset

#### Actualizar todos los paquetes

    flatpak update

#### Borrar los runtime sin uso

    flatpak uninstall --unused
    

