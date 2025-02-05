#Taller 3
*Métodos Computacionales - Laboratorio*

05-Jun-2015

Haga una copia de este archivo en su repositorio de GitHub en la carpeta /MC/Talleres/Taller3/. No olvide al final hacer un *commit* y un *push*.

# gcc, gnuplot y bash

Clone el repositorio [c-examples](https://github.com/tisnik/c-examples) de Pavel Tišnovský. **¡No lo clone al interior de su repositorio personal!**

1. Escriba un comando en `bash` que tome el código de todos los ejemplos en la carpeta `/c-examples/src/` y construya un archivo en Markdown con el código de los archivos en bloques de código bajo headers con el nombre del archivo correspondiente.

2. Ahora borre los archivos `c31_goto.c`, `c83_terminal_io.c` y `cA5_thread_join.c` y haga lo siguiente para los primeros (en orden alfabético) treinta archivos de C restantes.  Escriba un comando de `bash` que compile cada archivo de C, que luego imprima la línea que contiene la palabra *Example* y [la que le sigue](http://stackoverflow.com/questions/19274127/how-do-you-grep-a-file-and-get-the-next-5-lines), que luego ejecute el ejecutable, y que finalmente espere a que [el usuario presione alguna tecla](http://www.linuxquestions.org/questions/linux-general-1/how-to-make-shell-script-wait-for-key-press-to-proceed-687491/) para continuar con el siguiente archivo. 

3. Escriba un programa en C que genere 1000 puntos aleatorios uniformemente distribuidos sobre una esfera de radio unitario. Implemente la idea descrita al final del artículo [Sphere point picking](http://mathworld.wolfram.com/SpherePointPicking.html) y utilice la implementación para generar número con distribución normal [aquí](http://c-faq.com/lib/gaussian.html) detallada. Compile, ejecute y rediriga la salida al archivo `aleatorios_esfericos`. Luego escriba una secuencia de comandos de `gnuplot` para graficar estos puntos usando `splot`.


**Al terminar la clase ejecute `lottery.sh` para saber si su taller va a ser revisado.**

##Solución
###Punto 1
Para realizar la instrucción, se utiliza el manejo de archivos en una iteración como se muestra a continuación:
```
#!/bin/bash
#Método para pasar código a MarkDown
#Se borra el archivo
rm archivo.md

#Se inicia un ciclo para todo archivo terminado en .c
for file in $(ls *.c)
do
#Se crea cada encabezado
echo "##"nombre de archivo: $file >> archivo.md
#Se inicia el bloque de código
echo "\`\`\`" >> archivo.md
#Se copia el contenido
cat $file >> archivo.md
#Se cierra el bloque de código
echo "\`\`\`" >> archivo.md
done
```

###Punto 2
Para realizar el punto 2, se utiliza el siguiente código.
```
#!/bin/bash
#Método para resolver el segundo punto
rm c31_goto.c
rm c83_terminal_io.c
rm cA5_thread_join.c

for file in $(ls *.c)
do
cc $file
grep -A 1 "Example" $file
./a.out
read -p "Presione alguna tecla" -n 1 -s
done
```
