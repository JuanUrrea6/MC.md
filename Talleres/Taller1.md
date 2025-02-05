##Instrucciones
#Taller 1
29-May-2015

Haga una copia de este archivo en su GitHub en la carpeta /MC/Talleres/. No olvide al final hacer un *commit* y un *push*.

1. Escriba en *Markdown* un documento con una sección, dos subsecciones, una lista numerada, una lista sin numerar, un link, y un trozo de código inline y otro en bloque. Ver: [Markdown cheatsheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet).

2. Escriba un script de `bash` que produzca un archivo csv con los primeros mil números enteros junto con sus cuadrados. Para hacer la aritmética utilice [The Double-Parentheses Construct](http://www.tldp.org/LDP/abs/html/dblparens.html).

3. Escriba el código a usar en `awk` para sumar las columnas 1 y 2 de un archivo csv. Use el resultado del anterior ejercicio para hacer pruebas.

4. Escriba un script de `bash` que reciba dos números naturales y entregue de regreso su suma.

7. Escriba un reloj en `bash` que utilice `date`, `figlet`, `sleep`, `while` y `clear`.
 
8. Escriba un script de `bash` que descargue los primeros 150 comics de [xkcd](http://xkcd.com/). Puede hacerse utilizando `for`, `curl`, `grep`, `sed` y `wget`. Para hacerlo debe identificar y aprovechar el patrón en las url de los archivos a descargar.

9. Usando `ssh` abrir una cuenta en [sdf.org](http://www.sdf.org) y jugar `moon` o `tetris` por unos minutos.
+ Escriba código en `bash` que usando `sed` tome el archivo [hyg.csv](https://raw.githubusercontent.com/ComputoCienciasUniandes/HerramientasComputacionales/master/Lectures/2015-10/LaTeX/hipparcoscat/hyg.csv) y produzca un archivo llamado hyg.tsv con todas las comas reemplazadas por `tab`.

10. El archivo [monthrg.dat](https://raw.githubusercontent.com/ComputoCienciasUniandes/MetodosComputacionalesDatos/master/hands_on/solar/monthrg.dat) contiene 5 columnas descritas por el archivo [README](https://github.com/ComputoCienciasUniandes/MetodosComputacionalesDatos/blob/master/hands_on/solar/README). Escriba un script que imprima las siguientes tres cantidades: a) el número de manchas solares promedio en el mes de su nacimiento, b) la cantidad de meses entre 1900 y 1950 que tuvieron más de 30 manchas solares en promedio, y c) el año y el mes que más manchas solares promedio ha tenido en toda la historia. Para lo anterior utilice [awk](http://www.staff.science.uu.nl/~oostr102/docs/nawk/nawkA4.pdf).

11. Construya una expresión en `sed` que sirva para convertir un archivo de datos donde el separador es  `,` en otro donde el separador sea `tab`. 



# Varios

+ Para hacer en casa. Instale [GitHub for Windows](https://windows.github.com/) o [GitHub for Mac](https://mac.github.com/).
+ Para hacer en casa. Instalar un visualizador de MarkDown.
+ Para hacer en casa. Instalar alguna distribución de Linux en una máquina virtual.

Desarrollo:

#Sección
##Subsección 1: Lista Numerada

1. Item 1
2. Item 2
3. Item 3

##Subsección 2: Lista No Numerada

* Item 1
* Item 2
* Item 3

Código Inline : `printf Hola Mundo`

Código en Bloque:
```
#Este método imprime en pantalla
echo Hola Mundo

#Este método crea un nuevo directorio
mkdir NuevoDirectorio
```
Link [www.google.com]

###Creación de Script BASH
```
#!/bin/bash
#Método que crea los primeros 1000 números naturales y sus cuadrados en un archivo csv
for i in {1..1000}
do
 printf "%d,%d\n" $i $((i*i)) >> archivo1.csv
done
```

##Creación de Código AWK
```
#Método para sumar las co,umnas 1 y 2 de un archivo
awk -F '{print $1 + $2}' archivo
```

##Método para Sumar dos números naturales
```
#!/bin/bash
#Método para sumar dos números naturales
printf "%d\n" $(($1 + $2))
```
##Reloj en Bash
Manera creativa de mostrar un reloj en timpo real en la terminal, haciendo uso de la estética figlet.
```
#!/bin/bash
#Método Para reloj en BASH
#Se inicia un ciclo infinito
i=0
while :
do
#Se vacía la terminal y se imprime en figlet la hora cada 1 segundo
clear
tiempo=$(date +"%H:%M:%S")
figlet $tiempo
sleep 1
done
```
##Descarga de Comics
Para realizar este punto, se tuvo en cuenta el patrón en el URL de los distintos comics como se muestra a continuación:
```
#!/bin/bash
#Método para descargar los comics

Se sabe el patrón de los URL
for i in {1..150}
do
#Se borran los archivo temporales
rm fuente.txt
rm linkHallado.txt
rm linkFinal.txt

#Se obtiene el código fuente
curl http://xkcd.com/$i/ >> fuente.txt

#Se busca la línea que tiene el URL de la imagen.
grep URL fuente.txt >> linkHallado.txt

#Se elimina todo excepto el link
sed 's/Image URL (for hotlinking\/embedding): //g' linkHallado.txt >> linkFinal.txt
link=$(cat linkFinal.txt)

#Se descarga el archivo correspondiente.
wget $link
done
```
##Script para cambiar separador de COMA a TAB
Este ejecutable puede resultar bastante útil cuando se quiere cambiar el delimitador de un archivo para su uso futuro.
```
#!/bin/bash
#Método para cambiar de comas a tabs en uj archivo que entra como parámetro
#Se utiliza SED en el rachivo que llega como enrada.
sed 's/,/   /g' $1 >> nuevo.txt
```
