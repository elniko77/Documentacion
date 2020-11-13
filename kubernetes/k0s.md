k0s: es una distribución liviana de kubernetes, ideal para desarrollo y pruebas locales


Creando un cluster con un nodo (ejemplos en ubuntu 20.04)



Master:

Bajar la última versión:


     $ wget -c  https://github.com/k0sproject/k0s/releases/download/v0.7.0/k0s-v0.7.0-amd64
     $ sudo mv k0s-v0.7.0-amd64 /usr/local/k0s
    
Crear el token para unir al worker:
     $ k0s token create --role=worker

Correrlo:
     $ sudo k0s server


Worker:

Bajar k0s de la misma manera que en el server, y unirlo como worker con el token obtenido anteriormente:

     $ k0s worker <TOKEN>


