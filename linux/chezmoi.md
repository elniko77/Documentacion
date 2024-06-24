#### Instalar 

```bash
  sh -c "$(curl -fsLS get.chezmoi.io)"
  sudo mv bin/chezmoi /usr/local/bin/
```
#### Si ya se tiene el repo dotfiles, instalar y usar en una sola línea
```bash
  export GITHUB_USERNAME=elniko77
  sh -c "$(curl -fsLS get.chezmoi.io)" -- init --apply $GITHUB_USERNAME
```

#### Inicializar
```bash
   $ chezmoi init
   # Crea el repo en ~/.local/share/chezmoi/
   # Agregar archivos
   $ chezmoi add ~/.bashrc
   $ chezmoi edit ~/.bashrc
```

#### Ver los cambios
```bash 
   $ chezmoi diff
   # Apply the changes:
   $ chezmoi -v apply
```

#### Next, open a shell in the source directory, to commit your changes:
```bash 
   $ chezmoi cd
   $ git add .
   $ git commit -m "Initial commit"
   # Create a new repository on GitHub called dotfiles and then push your repo:

   $ git remote add origin https://github.com/$GITHUB_USERNAME/dotfiles.git
   $ git branch -M main
   $ git push -u origin main
``` 

#### Aplicar los cambios
```bash
   $ chezmoi apply -v
```

#### On any machine, you can pull and apply the latest changes from your repo with:
```bash
   $ chezmoi update -v
```
