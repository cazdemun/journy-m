# Quorum, el retorno de c9

Al parecer no es necesario instalar el virtual box, ya que, según https://github.com/jpmorganchase/quorum-examples/blob/master/vagrant/bootstrap.sh , lo único que hace vagrant y VB es... crear una máquina virutal de Ubuntu xenial64 y ejecutar un archivo sh dentro...

## Digital Ocean

Entonces, la idea será esta... usar digitalOcean para levantar el nodo en la máquina virtual y usar c9 para el desarrollo y la conexión con los nodos de esa máquina virtual.

scp bootstrap.sh root@159.203.62.39

O sino full nano, creo que es lo mejor.

Por cierto, el archcivo no puedo ejecutarlo con sh, tiene que ser con bash (encima lo dice en la primera línea del archivo, duh).

Umm... creo que lo he hecho mal, creo que tengo que crearme un usuario ubuntu... y tengo que modificar en algo el sh, lo de copiar el git, porque está tratando de sacarlo de vagrant... lo cual no tiene mucho sentido, porque es un sh, pero bueno