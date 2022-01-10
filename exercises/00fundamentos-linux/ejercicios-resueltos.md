# Ejercicios

## Ejercicios CLI

### 1. Crea mediante comandos de bash la siguiente jerarquía de ficheros y directorios.

```
mkdir -p $HOME/foo/{dummy,empty}
echo "Me encanta la bash!!" > $HOME/foo/dummy/file1.txt
touch $HOME/foo/dummy/file2.txt
```

### 2. Mediante comandos de bash, vuelca el contenido de file1.txt a file2.txt y mueve file2.txt a la carpeta empty.

```
cat $HOME/foo/dummy/file1.txt > $HOME/foo/dummy/file2.txt
mv $HOME/foo/dummy/file2.txt  $HOME/foo/empty
```

### 3. Crear un script de bash que agrupe los pasos de los ejercicios anteriores y además permita establecer el texto de file1.txt alimentándose como parámetro al invocarlo.

Si se le pasa un texto vacío al invocar el script, el texto de los ficheros, el texto por defecto será:

```
Que me gusta la bash!!!!
```


```
#!/bin/bash

if [ $# -gt 0 ] ; then
   TEXTO=$1
else
   TEXTO="Me encanta la bash!!"
fi

mkdir -p $HOME/foo/{dummy,empty}
echo $TEXTO > $HOME/foo/dummy/file1.txt
touch $HOME/foo/dummy/file2.txt

cat $HOME/foo/dummy/file1.txt > $HOME/foo/dummy/file2.txt
mv $HOME/foo/dummy/file2.txt  $HOME/foo/empty
```


### 4. Opcional - Crea un script de bash que descargue el contenido de una página web a un fichero.

Una vez descargado el fichero, que busque en el mismo una palabra dada (esta se pasará por parametro) y muestre por pantalla el núemro de linea donde aparece.

```
#!/bin/bash

if [ $# -gt 0 ] ; then
   curl --silent https://google.com/ -o url.txt
   grep -in $1 url.txt
else
   echo "Introducir palabra a buscar como argumento"
fi
```



