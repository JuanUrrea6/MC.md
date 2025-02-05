###27 de Mayo de 2015
##Comandos Básicos de la Terminal
Hola, mundo. Aquí comienza el curso Métodos Computacionales del periodo vacacional 2015-19.
Herramientas del curso:

 + Git 
 + GitHub 
 + Bash 
 + C 
 + Python 

Los métodos a "estudiar" son los siguientes:

 + Interpolación
 + Análisis de Fourier
 + Diferenciación e Integración Numéricas
 + Ecuaciones Diferenciales Ordinarias
 + Ecuaciones Diferenciales Parciales

***

Se habló de distintas herramientas que se pueden utilizar en la terminal, como son los comandos en AWK:
````
#Elegir la n-sima fila e imprimirla de un archivo
awk '{print $n}' archivo

#cambiar el delimitador en un archivo. Se cambia a algo nuevo.
awk -F"ALGO"

#Operaciones entre columnas de un archivo. Se muestra la suma, pero puede ser cualquier otra operación.
awk '{print $n + $m}' archivo

#Operaciones lógicas. La acción puede ser reemplazada por la que se requiera.
awk 'if(condicion) print ALGO'
````

También se habló del uso del comando SED y CURL:
```
#Se toma ALGO1 y se reemplaza po ALGO2
sed 's/ALGO1/ALGO2/g'

#Importar código de una URL
curl URL

#Conexión remota con SSH a una máquina llamada machine
ssh usuario@MACHINE
````

Otros comando bastante útiles son aquellos para el desplazamiento y manipulación de archivos en la terminal
```
#Crear un archivo de texto.
nombreEditor nombreArchivo

#Moverse a un directorio
cd nombreDiectorio

#Ver los contenidos del directorio
ls

#Enviar archivo a un destino
archivo1 > archivo2
````
***
También se habló de como manipular archivos de GitHub desde la terminal:
```
#Crear archivo en editor de texto y editarlo.
emacs NombreArchivo

#Añadir el commit correspondiente.
git commit

#Añadiendo a GitHub
git add

#Actualizando Github
git push origin master

#También se puede extraer el repository de GitHub
git pull origin master
```
 En resumen:
 
| Paso | Procedimiento|
|------|--------------|
|   1  | Crear archivo de texto y editar su contenido|
|   2  | Añadir un commit|
|   3  | Añadir a GitHub |
|   4  | Actualizar GitHub |

Para recordar también un ejemplo realizado en clase, se muestran algunos método importantes para lo visto.
####Imprimir en Pantalla Mensajes Simples
````
echo "mensaje"
````
####Imprimir en Pantalla Mensaje Complejos de String
```
printf "%s\n" Mensaje
````
Cabe notar que ambas formas se pueden utilizar en la consola de Mac, aunque con el comando `printf` se pueden hacer cosas más interesantes, como organizar espaciado o la precisión de decimales.

####Creación de un ejecutable genérico
En un editor de texto, insertar los comandos correspondientes:
````
echo "Mensaje"
````
Este archivo de texto, sin formato, se guarda con la terminación **.sh**. Una vez ya se ha guardado, se debe usar la terminal para modificar los permisos del ejecutable. Luego, se procede a ejecutarlo.
````
#Manejo de permisos
sudo chmod 700 archivo.sh

#Ejecución del archivo
./archivo.sh
````

####Creación de un Nuevo Repositorio
Para crear un nuevo repositorio, se crea su nombre en GitHub y luego se utiliza la terminal como se indica:

```
#Crear el archivo readme
touch README.md

#Inicializar Git
git init

#Añadir el archivo readme
git add README.md

#AÑadir el primer commit
git commit -m "comentario"

#Añadir un origen para subir todo
git remote add origin https://github.com/LuchoCastillo/Repositorio.git

#Indexar el archivo al origen creado
git push -u origin master
```
###29 de Mayo de 2015
##Taller en Clase de Comandos Básicos
Se trabajó en el taller dado, donde lo primero que se hizo fue crear un documento en MarkDwon con los comandos explicados en la entrada anterior de esta bitácora. Sin embargo, también se trabajó código en BASH basado en las lecturas enviadas.

* Variables en BASH: `$variable = valor`

####Creación de loops en Bash
```
#Creación de un loop genérico
for i in {Lim1..Lim2}
 do
 #Aquí se ponen los comandos para hacer. 
 $variable = i
 printf $variable
 done
```
También se trabajó indexación. Se muestra una receta para crear números e indexarlos a un archivo.
####Indexación Genérica
```
#Método para crear n enteros e indexarlos a un archivo csv
#!/bin/bash
for i in {1..n}
 do
 printf "%d,%d\n" $i >> archivo.csv
 done
```
Continuando con el taller, se copió y descomprimió el directorio dado. Se encontró que la fecha del segundo commit realizado fue el sábado 5 de enero de 2013 a las 19:28:57. También, se sabe que el tema de la semana 15 de ese curso fue el **Método de Inferencia Bayesiana**

###Martes 2 de Junio de 2015
##Expresiones Regulares
En esta clase se explicaron caracteres que se pueden utilizar para distintos comandos de expresiones regulares.

* Comienzo de línes `^`
* Fin de línea `$`
* Intervalos `(a|b)`
* Uso de caracteres especiales como entrada. `\@`
* Buscar varios caracteres `[hfahf\@]`
* Dígitos `\d`
* NO dígitos `\D`

Se utilizó TextWrangler para copiar el archivo de los "Jovian Satellites Orbital Parameters". Con eso en ese archivo, se utilizan expresiones regulares para empezar a modificar el archivo.
Ejemplo para reemplazar espacios al comienzo de la línea por un vacío. 
`^ ` por ` `.
**Nota:** Para no solo seleccionar un caracter, sino todos los que se encuentren seguidos iguales, se utiliza `@+`, donde @ es el caracter deseado.
Para continuar, se aprendió el uso de GNUPLOT, iniciándolo con:
```
#Iniciando gnuplot
gnplot

#Graficar la función seno
plot sin(x)

#Gráficas paramétricas y quitarla
set parametric
unset parametric

#Gráfica paramétrica
plot sin(t),cos(t)
```

También es posible graficar utilizando datos de otros archivos.
**Ejemplo:**
`plot "archivo.csv" using columna1:columna2`

##Taller 2: GNUPlot
**Punto 1:**

Expresión regular con cuatro caracteres al comienzo de una línea y un espacio
`^... `
Aquí se utiliza `^` para indicar que se encuentran al comienzo de la línea. Luego, haciendo uso de `.` asigno cualesquiera cuatro caracteres seguidos. Por último, con el espacio se denota la presencia de un espacio ahí. Este ejemplo genérico sirve para aprender a manejar los distintos comandos para expresioens regulares, que luego podría utilizarse para búsquedas y reemplazos para modificar archivos grandes sin necesidad de modificar entrada por entrada cada una.

**Punto 3:**
Para ralizar este punto, se copia manualmente lo encontrado en la página web a un archivo de texto en TextWagler. Una vez ahí, se utiliza Ctrl-F y se introduce el siguiente código:
```
#Buscar: Con este comando, se busca una agrupación de 20 caracteres seguidos
(....................)

#Reemplazar: Con este comando se indica que la agrupación encontrada anteriormente se debe reemplazar por si mismo, pero con un enter para iniciar una nueva línea.
\1\n
```
Este método resulta importante ya que proporciona un primer acercamiento básico al manejo de datos masivos y su organización, pues al hacer la dicisión de líneas que se requería en este punto, se vuelve más entendible el contenido.
**Graficación**
Para realizar las gráficas usando GNUPlot, se utilizó el siguiente código:
```
#Con este comando, se grafican las columnas 2 y 3 del archivo seleccionado, marcando los puntos de los datos conocidos y mostrando la recta de intrpolación.
set datafile separator "," ; plot "joviansatellites.csv" using 2:3 with linesp
```
Este comando, junto con las distintas modificaciones que se le pueden aplicar, resulta bastante útil para la visualización gráfica de conjuntos de datos a analizar, al igual que para visualizar una función definida sobre un dominio y rango. Por ejemplo, es posible realizar gráficas paramétricas para análisis donde varios grupos de datos se unen por medio de una palabra.
```
#Este comando grafica un círculo parametrizado.
set parametric
plot sin(x),cos(x)
```
###3 de Junio de 2015
##Más Usos de GNUPlot
En clase se vieron más aplicaciones y usos de GNUPlot, como los que se muestran a continuación:

* Nomenclatura de Ejes
```
#En GNUPlot
set title "Títulode la Gráfica"
set xlabel "Eje X"
set ylabel "Eje Y"
```
* Estética de Gráfica
```
#En GNUPlot
#Se grafica con una línea
plot f(x) with line

#Se grafica con línea y puntos.
plot f(x) with linesp

#Nombrar gráfica, eje X y eje Y
set title "Título"
set xlabel "Eje X"
set ylabel "Eje Y"
```
* Regresiones

Esta aplicación es notablemente importante, pues muchos análisis de datos se basan en regresiones y comportamientos de una serie de datos.
```
#Declarar el ajuste modelo y luego realizar el fit.
f(x) = f(x, a, b, c)
fit f(x) "Archivo" using columna1:columna2 via a, b, c
```
Una buena guía para este procedimiento está en (http://gnuplot.sourceforge.net/docs_4.2/node82.html)

###Viernes 5 de Junio
##Manejo de C y Python
Se vieron más funciones básicas en el lenguaje C, como lo son la declaración de variables y métodos en C. La estructura básica de estos se muestra a continuación.
```
#include <stdio.h>
/*
* Así se comenta en C. Se crea un método básico.
*/
int main(void)
{
 /*
 * Es posible recibir variables como entrada. Primero se declaran con su tipo.
 */
 int numero1;
 
 /*
 * Luego, se pide introducirlas y se leen, enviándo el contenido a la variable declarada antes.
 */
 printf("Introduzca un número. \n")
 scanf("%d", &numero1)
 
 /*
 * Es posible luego imprimir el contenido de la variable.
 */
 printf("Usted introdujo el número:\n")
 printf(numero1)
}
```
Luego de ver más aplicaciones de C, se suponía que se investigaría sobre el comando **make** y eso se incluiría en la bitácora. Sin embargo, se cpnsideró que no había tiempo, por lo que se procedió a trabajar en el Hands-On que sería introductorio para python. Para este, se utilizó el comando que permite leer contenido dado por el usuario.

* `entrada=raw_input("Introduzca algo")` Este comando recibe una entrada del usuario y la guarda en una variable. Específicamente para la instrucción dada, fue necesario obligar a que la entrada se tomara como un entero, de la forma `numero = int(raw_input("Introduzca un número"))`

###Martes 9 de Junio
##Bases de Make
Muchas veces surge la necesidad de repetir procesos que no siempre resultan muy sencillos "a mano". Por este motivo resulta conveniente un programa que automatice este proceso con el uso de comandos específicos de cada proceso necesario para que sea independiente del usuario.

Este proceso de automatización sigue instrucciones muy específicas, como lo son objetivos, pre-requisitos y acciones. Si se traduce a lenguaje cotidiano, se podría afirmar que el archivo **make** sigue la lógica siguiente:

* Se debe hacer algo con el objetivo
* Solo se hace una vez se cumplen los pre-requisitos
* Cuando se cumplen, se deben realizar las acciones.

Es posible visualizar este razonamiento en forma de código para el archivo **.mk**.
```
#Se realiza un comentario, como siempre.
archivoObjetivo : archivoPrerequisito
 acciones a realizar
```
Una vez se ha construido el archivo, es posible ejecutarlo. Esto se hace con el comando `gmake -f archivo.mk`. Cabe notar que el ejemplo es el más sencillo que existe. Generalmente se ponen más pre-requisitos y reglas, a la vez que más acciones a realizar cuando se ejecuta el **.mk**. Para manejo de varias instrucciones que involucran muchos archivos, se crean distintas condiciones que permitan mantener un orden claro. 

###Miércoles 10 de Junio de 2015
##Manejo de MatPlotLib
Se trabajó en las diferentes funcionalidades de MatPlotLib. Para entender mejor esto, se realizaron los ejercicios sugeridos en el hands-on correspondiente a la clase. A continuación se muestra el código que permite la creación de una figura de 5x5 paneles con 25 gráficas, cada una mostrando una figura de lissajous distinta. Esta temática, al igual que el uso de la graficación estándar en Python, se exploró también en el laboratorio, donde no solo se aprendió a realizar histogramas, sino que también se realizaron ajustes de curva al histograma en si.
```
%pylab inline
from random import randint

#Se pone el estilo por defecto.
rcdefaults() 
#Se establece el tamaño de la figura.
figure(figsize=(10,10))
#Se crea el parámetro T para senos y cosenos.
t = linspace(0,6.28, 100)
#Se inicia el for para generar 25 paneles.
for i in range(25):
    #Se definen las funciones para X y Y.
    def X(h, d):
        return sin((randint(1,5))*h + d)
    def Y(h):
        return cos(randint(1,5)*h)
    #Se crea un panel
    subplot(5,5,i+1)
    #Se quita su cuadrícula.
    grid(False)
    #Se quitan los ejes.
    axis('off')
    #Se genera un desfase aleatorio.
    desfase = randint(1,3)
    #Se grafica la figura en cada panel.
    plot(X(t, desfase),Y(t))
```
Con este código en iPython Notebook se generan distintas figuras de Lissajous según indica la instrucción. Esta fue tan solo una pequeña aplicación de todas las funcionalidades de esta biblioteca de Python. El correcto manejo de esta librería permite la realización de gráficas de todo tipo, donde no solo se trabaje con puntos o líneas, sino superficies y volúmenes, lo que facilita el análisis gráfico y la visualización de resultados obtenidos después de varios cálculos.
La imagen de las 25 figuras de Lissajous que resulta de la ejecución del código anterior se muestra a continuación.

![alt text](https://raw.githubusercontent.com/JuanUrrea6/MC/master/Lissajous.png)

###Sábado 13 de Junio de 2015
##Apuntes sobre Error e Imprecisión
Leyendo el libro de Landau acerca del manejo de Python, se obtuvieron nociones básicas de los tipos de errores que pueden aparecer a lo largo de la implementación de cálculos y algoritmos computacionales. Lo primero que se vio fueron los distintos tipos de errores, los cuales se enuncia a continuación:
* **Teóricos:** Dependen del trasfondo teórico en el cual se basa todo el procedimiento. Si estos ocurren, el procedimiento está condenado al fracaso.
*  **Aleatorios:** Debidos a eventos fuera de nuestro control, como accidentes o fenómenos aleatorios durante el experimento.
*  **Aproximación 1:** Debido a aproximaciones de procdimiento que teóricamente deberían ser infinitos, como series o integrales impropias.
*  **Aproximación 2:** Debido a las aproximaciones y redondeos decimales que realiza el computador. Al realizar varios procesos con decimales, este error se propaga notablemente.

También, además de la explicación y realización de diversos ejemplos para demostrar la presencia de errores en cálculos hechos por computador, se habló de maneras de abordarlos para poder corregirlos, o evitarlos en la medida de lo posible. Por ejemplo, se habló de como operaciones que involucran número muy grandes y numeros muy pequeños con decimales causan una gran presencia de error, pues por el orden de magnitud mayor, se desprecian los valores de orden de magnitud mucho menor. Algo similar ocurre cuando se trabajo con series, pues a mayor número de términos que se usan para dar exactitud al resultado, se pierde precisión en la suma de números de bajo orden de magnitud.

###Martes 16 de Junio de 2015
##Interpolación y Ajustes
Durante clase se aprendió el manejo básico de las funciones de ajuste como lo son **polyfit** de numpy y **curve_fit** de scipy. Para aplicar lo visto, se realizó el hands on, de donde se puede resaltar el siguiente punto.
```
%pylab inline
from scipy.optimize import curve_fit

#Creación de Arreglos
x=[2.3, 2.8, 3.2, 3.7, 4.3]
y=[34745, 19689, 12594, 7982, 5822]

u = linspace(2,5,100) #Linspace sobre el cual graficar.
def ajuste(t, m): #Definir la función modelo.
    return (((0.2)*m)/((t)**3))
fitpars, covmat=curve_fit(ajuste, x, y) #Realizar ajuste.

scatter(x, y, label = "Datos") #Plotear datos y ajuste.
plot(u, ajuste(u, *fitpars), color = "Red", label = "Ajuste Teórico", ls = "--")
xlim(2.2, 4.5)
legend()

#Intrapolación usando el valor obtenido para m (2118294.96442)
r = linspace(2.3, 4.3, 100) #Distancias a intrapolar
r2 = [] #Nuevo arreglo
for i in range(len(r)):
    actual = (423658.8)/(r[i])**3 #Obtenicón de datos
    r2.append(actual)

scatter(r,r2, color = "Green", label = "Datos Intrapolados") #Graficar os datos intrapolados
plot(u, ajuste(u, *fitpars), color = "Red", label = "Ajuste Teórico", ls = "--")
xlim(2.2, 4.5)
legend()
```
Los gráficos obtenidos al implementar este código se muestran a continuación:
![alt text](https://raw.githubusercontent.com/JuanUrrea6/MC/master/Python/Ajuste.png)
![alt text](https://raw.githubusercontent.com/JuanUrrea6/MC/master/Python/Intrapolacion.png)

###Miércoles 17 de Junio de 2015
##Transformada de Fourier y Solución de Ecuaciones
En el laboratorio y magistral, se aprendió el manejo básico y las distintas formas de realizar un ajuste por series de Fourier, en específico a una función escalón de altura pi cuartos. Para lograr esto, se hicieron sumas recursivas de la función del **seno cardinal**.
Al hacer esto, se obtuvo lo siguiente:
![alt text](https://raw.githubusercontent.com/JuanUrrea6/MC/master/Material/Fourier.png)

Luego de practicar un poco más los conceptos y aplicaciones de la transformada de Fourirer, se procedió a trabajar con la solución de ecuaciones y aproximaciones. Esto se puede trabajar, en polinomios, con la función `root`. Esto se hace como se muestra a continuación:
```
from scipy.optimize import root #Se importa de la biblioteca de optimización de SciPy
def funcion(x):
     ... #Aquí se define la función o polinomio, que se busca solucionar.
raiz = root(función,0.3) #Se usa root para hallar las raíces.
print(raiz) #Se muestran los valores determinados.
```
Para poner esto en práctica, se solucionó tanto la ecuación teórica de los puntos de Lagrange de los satélites de Jupiter como su aproximación, viendo la diferencia entre las raices de ambas expresiones y determinar la validez de la aproximación.
```
%pylab inline
from scipy.optimize import root

def funcion1(x): #Definir la función a solucionar
    result = (10000/(300-x)**2) -(100/x**2) - ((10000/(100+10000))*300 - x)*((10000 + 100)/300**3)
    return result
 
 print(root(funcion1, 0.3)) #Encontrar sus raices.
```
 x: array([ 42.44247395])
 
 nfev: 26
 
 fjac: array([[-1.]])
 
 fun: array([ 0.])
 
 r: array([-0.00416061])
 
 qtf: array([  1.94289029e-14])
 
 success: True
 
 message: 'The solution converged.'
 
 status: 1
```
print(300*(100/30000)**(1/3)) #Evaluar la aproximación.
```
Cuando se utilizan m1= 10000 y m2 = 100, con R = 300, se obtienen las soluciones exacta y aproximada anteriormente mostradas, siendo 42.442 la exacta y 44.814 la aproximada. Se obtuvo un error del 5.6%.

Cabe notar también que la representación de Fourier realizada se hizo de manera manual. Sin embargo, existen ya funciones incorporadas en la Python que permiten realizar transformadas de Fourier de distintos tipos a arreglos. La segunda se implemeta en la tarea. Para representaciones específicas, como para ondas tiepo sierra o triangular, la transformada se puede realizar manualmente también, calculando los coeficientes de Fourier con `scipy.integrate`.
```
fft(array) #Transformada de fourier discreta a un arreglo de una dimensión.

fft2(array) #Transformada de fourier discreta a un arreglo de dos dimensiones.
```
###Viernes 19 de Junio de 2015
##Transformada de Fourier y Representaciones
Durante la clase, se explicó la aplicación de las transformadas de Fourier para el procesamiento de funciones e imágenes. Se hizo énfasis en dicho manejo de imágenes, modificando de diversas formas la imagen de Lena por medio de filtros de frecuencias. Para el Hands-On se trabajaron estos dos aspectos, primero realizando representaciones de Fourier a una onda triangular para luego hallar el negativo de Lena y girar la imagen.
El primer punto del Hands-On se realizó con el siguiente código:
```
%pylab inline
from scipy import integrate

#Definir la onda triangular.
x = linspace(0,6,6000)
x1 = linspace(0,1,1000)
x2 = linspace(0,2,2000)
y1 = []
y2 = []
y3 = []
y4 = []

for i in range(len(x1)):
    actual = x1[i]
    y1.append(actual)
    y3.append(actual)

for j in range(len(x2)):
    actual1 = 1 - (0.5*x2[j])
    y2.append(actual1)
    y4.append(actual1)

#Unión de Valores en Y
yTotal = y1 + y2 + y3 + y4

figure(figsize(7,5))
plot(x,yTotal)
title("Onda Triangular")
xlabel("X")
ylabel("Y")
savefig("OndaTriangular.png")
```
![alt text](https://raw.githubusercontent.com/JuanUrrea6/MC/master/Material/OndaTriangular.png)
```
#Realizar representación de Fourier
#Definir los coeficientes del primer trozo f(x)=x
def A(n, T):
    funcion = lambda x: x*cos((2*pi*n*x)/T)
    actual = quad(funcion, -T/2, T/2)
    return actual[0]
def B(n, T):
    funcion = lambda x: 1*x*sin((2*pi*n*x)/T)
    actual = quad(funcion, -T/2, T/2)
    return actual[0]
 
 #Realizar representación de Fourier
#Coeficientes del segundo trozo f(x) = 1-0.5x
def A2(n, T):
    funcion = lambda x: (1-0.5*x)*cos((2*pi*n*x)/T)
    actual = quad(funcion, -T/2, T/2)
    return actual[0]
def B2(n, T):
    funcion = lambda x: (1-0.5*x)*x*sin((2*pi*n*x)/T)
    actual = quad(funcion, -T/2, T/2)
    return actual[0]
 
 #Sumatoria de Fourier Para f(x)=x
def ajuste(n, T, x):
    arreglo = []
    suma = 0
    for j in range(len(x)):
        for i in range(n):
            actual1 = A(n, T)*cos(2*pi*n*x[i]/T)
            actual2 = B(n, T)*sin(2*pi*n*x[i]/T)
            suma = suma + actual1 + actual2
        arreglo.append(-suma)
    return arreglo
 
 #Serie de Fourier para f(x)=1-0.5x
def ajuste2(n, T, x):
    arreglo = []
    suma = 0
    for j in range(len(x)):
        for i in range(n):
            actual1 = (1/2)*A2(n, T)*cos(2*pi*n*x[i]/T)
            actual2 = (1/2)*B2(n, T)*sin(2*pi*n*x[i]/T)
            suma = suma + actual1 + actual2
        arreglo.append(suma + 1)
    return arreglo
 
 figure(figsize(7,5))
plot(x1, ajuste(2, 1, x1), color = "Red")
plot(linspace(1, 3, 2000), ajuste2(2,1,linspace(1,3,2000)), color = "Green")
plot(linspace(3,4,1000), ajuste(2,1, linspace(3,4,1000)), color = "Purple")
plot(linspace(4,6,2000), ajuste2(2,1,linspace(4,6,2000)), color = "Yellow")
title("Onda Triangular")
xlabel("X")
ylabel("Y")
```
![alt text](https://raw.githubusercontent.com/JuanUrrea6/MC/master/Material/FourierTriangular.png)

Para el procesamiento de la imagen conocida como Lena, se utilizó el siguiente código, que permitió obtener su negativo, girarla horizontalmente y girarla verticalmente.
```
from scipy import misc
from scipy.fftpack import *

lena = misc.lena()
figure(figsize(5,5))
imshow(1.5*lena, cmap = 'gray')
```
![alt text](https://raw.githubusercontent.com/JuanUrrea6/MC/master/Material/Lena.png)
```
#Sacar el negativo
#Se resta cada valor RGB a 255.
negativoLena = zeros((512,512))
for i in range(512):
    for j in range(512):
        negativoLena[i][j] = 255 - lena[i][j]
 imshow(negativoLena, cmap = 'gray')
```
![alt text](https://raw.githubusercontent.com/JuanUrrea6/MC/master/Material/NegativoLena.png)
```
#Voltear la imagen verticalmente
#Se invierten filas y columnas.
voltearLena = zeros((512,512))
for i in range(512):
    for j in range(512):
        voltearLena[i][j] = lena[511-i][511-j]
 imshow(voltearLena, cmap='gray')
```
![alt text](https://raw.githubusercontent.com/JuanUrrea6/MC/master/Material/LenaVertical.png)
```
#Voltearla horizontalmente
#Se invierten solo las columnas.
lenaHorizontal = zeros((512,512))
for i in range(512):
    for j in range(512):
        lenaHorizontal[i][j] = lena[i][511-j]
 imshow(lenaHorizontal, cmap='gray')
```
![alt text](https://raw.githubusercontent.com/JuanUrrea6/MC/master/Material/LenaHorizontal.png)

###Martes 23 de Junio de 2015
## Filtros y Fourier
En la clase se trabajó con el análisis de Fourier para el análisis y filtrado de seÑales, para lo cual se realizó el Hands-On. Este se muestra a continuación.
```
%pylab inline
from scipy.fftpack import fft, ifft

datos = genfromtxt("SolarPeriod.txt", delimiter = ",") #Se importan los datos.
ano = datos[:,0] #Se separan las columnas en arreglos separados.
mes = datos[:,1]
diasUsados = datos[:,2]
media = datos[:,3]
desviacion = datos[:,4]

nuevoAno = [] #Se dividen los años por meses.
for i in range(len(ano)):
    actual = ano[i] + (mes[i] - 1)/12
    nuevoAno.append(actual)
    
plot(nuevoAno,media) #Se grafican las medias de manchas solares.
xlim(1900,1990)
ylim(0,200)
xlabel("t/año")
ylabel("manchas solares/mes")
```
![alt text](https://raw.githubusercontent.com/JuanUrrea6/MC/master/Material/ManchasSolares.png)
```
anoCortado = nuevoAno[3480:(len(nuevoAno)-1)] #Se crea la nueva partición de los años para evitar negativos.
nuevaMedia = media[3480:(len(media) - 1)] #Nuevo arreglo recortado de medias.
N = len(nuevaMedia) #Se determinan los parámetros del análisis de Fourier.
dt = (anoCortado[-1] - anoCortado[0])/N #Salto de Tiempo "Infinitesimal"
transform = fft(nuevaMedia) #Transformada de las Medias
frecuencia = fftfreq(N,dt) #Se transforma el salto a frecuencias.
scatter(frecuencia, abs(transform)) #Se grafican para visualizar.
xlim(-6,6)
ylim(0,10000)
```
![alt text](https://raw.githubusercontent.com/JuanUrrea6/MC/master/Material/Frecuencias.png)
```
transform[np.abs(frecuencia) > 0.1] = 0 #Se construye el filtro.
buenas = ifft(transform) #Se devuelven las pasadas a tiempo.
plot(anoCortado, buenas) #Se grafica para visualizar/
plot(anoCortado, media[3480:(len(media) - 1)])
```
![alt text](https://raw.githubusercontent.com/JuanUrrea6/MC/master/Material/Filtradas.png)

###Miércoles 24 de Junio de 2015
##Coordenadas Esféricas y Métodos Numéricos
En el laboratorio de hoy se trabajó en Python para poder analizar datos en un set de coordenadas y poderlos convertir a otras. En específico, se trabajó con coordenadas cilíndricas para encontrar las coordenadas cartesianas correspondientes en un recorrido por un sector de Bogotá. Para lograr esto, se implementó el código contenido en el notebook del taller 6 y se obtuvo el siguiente resultado.
![alt text](https://raw.githubusercontent.com/JuanUrrea6/MC/master/Material/Recorrido.png)

En la clase magistral, se habló de la teoría de bases de espacios vectoriales y métodos numéricos para obtener resultados bastante aproximados de integrales. En específico, se habló de los ajustes por polinomios de Lagrange, un método que ya se había utilizado antes. Para aplicar esto, se estudió en el Hands-On la regla **3/8 de Simpson**, la cual proporciona, por medio de su construcción como una función en Python, un resultado aproximado a una integral en un intervalo dado de una función.

###Viernes 26 de Junio de 2015
##Taller de Cinemática
Durante la sección de laboratorio se continuó trabajando con el taller de Cinemática, aprendiendo a usar con más detalle el módulo **smopy** y sus funciones para editar y utilizar mapas para distintas gráficas. 

###Martes 30 de Junio de 2015
##Ecuaciones Diferenciales y Mecánica Cuántica
Durante la sesión de la clase magistral se trabajó en la resolución de la ecuación de Schrodinger para la resonancia magnética nuclear, haciendo uso de matrices en Python y las funciones de scipy.integrate para evaluar y explorar las propiedades de unicidad y las distintas probabilidades involucradas en la teoría. Durante la clase también se explicó el manejo del método de ODE para la resolución de ecuaciones diferenciales con Python. Esto se realiza importando el módulo `scipy.integrate`, donde se encuentra la función `ode()` y `odeint()`. Estas permiten solucionar ecuaciones diferenciales que se den como parámetro sobre un intervalo.

###Miercoles 1 de Julio de 2015
##Uso de Sympy
Durante la clase se explicó el uso básico y fundamental de la librería Sympy de Python para la realización de cálculos simbólicos. Para profundizar en esto, se realizó el Hands-On, del cual se puede resaltar lo siguiente:
```
%pylab inline
from sympy import *

#Inicializar Sympy y declaración de símbolos
init_printing(use_unicode=False, wrap_line=False, no_global=True)
t,fn,fn1,h,tn,tn1=symbols('t fn fn1 h tn tn1')

#Adam Bahsforth de Orden 2
tn1 = tn - h
simplify(integrate(fn1*(t - tn)/(tn1 - tn) + fn*(t - tn1)/(tn - tn1), (t, tn,(tn + h))))

#Adam Bashforth de Orden 3
fn2,tn2=symbols('fn2 tn2')
tn2 = tn - 2*h
simplify(integrate(fn*((t-tn1)*(t-tn2))/((tn-tn1)*(tn-tn2)) + fn1*((t-tn)*(t-tn2))/((tn1-tn)*(tn1-tn2)) + fn2*((t-tn)*(t-tn1))/((tn2 - tn)*(tn2-tn1)), (t, tn,(tn+h))))

#Adam Bashforth de Orden 4
fn3,tn3=symbols('fn3 tn3')
tn3 = tn - 3*h
simplify(integrate(fn*(t-tn1)*(t-tn2)*(t-tn3)/((tn-tn1)*(tn-tn2)*(tn-tn3)) + fn1*(t-tn)*(t-tn2)*(t-tn3)/((tn1-tn)*(tn1-tn2)*(tn1-tn3)) + fn2*(t-tn)*(t-tn3)*(t-tn1)/((tn2-tn)*(tn2-tn3)*(tn2-tn1)) + fn3*(t-tn1)*(t-tn2)*(t-tn)/((tn3-tn1)*(tn3-tn2)*(tn3-tn)),(t, tn, tn+h)))
```
Con el código anterior se utiliza Sympy para resolver las distintas integrales que permiten definir las funciones del método de Adam-Bashforth de distintos órdenes. Para futuras referencias, se encuentra en este notebook:

https://github.com/JuanUrrea6/MC/blob/master/Material/Hands-On%2013.ipynb

para el manejo de Sympy, se vio que resulta fundamental la declaración de cada símbolo antes de usarlo en una expresión, al igual que en operaciones como integración y derivación, pues se debe indicar cuales son constantes y variables.

###Viernes 3 de Julio de 2015
##Introducción a Ecuaciones Diferenciales Parciales
Durante esta clase se continuó resolviendo el Hands-On anterior basado en el manejo de **Sympy**, a la vez que se comenzó a hablar de de la posible resolución de ecuaciones difeenciales parciales usando Python, tanto con métodos propios del lenguaje como con simulaciones. El Hands-On consistió en la resolución de de las ecuaciones para resonancia magnética, basándose en el uso y operación de las matrices de Pauli.
El desarrollo de este hands-on se encuentra en el siguiente notebook

https://github.com/JuanUrrea6/MC/blob/master/Material/Hands-On%2013.ipynb

###Martes 7 de Julio de 2015
##Ecuaciones Diferenciales Parciales 1
Durante esta clase se explicó el uso de herramientas como el método de relajación para la resolución de ecuaciones diferenciales parciales, como los son la ecuación de Onda o la de Poisson. El Hands-On consistió en la resolución del oscilador armónico basados en su ecuación diferencial, lo que dio un primer vistazo a la utilización de Python para este tipo de problemas. 

###Miércoles 9 de Julio de 2015
##Ecuaciones Diferenciales Parciales 2
En esta clase se continuó trabajando el tema de análisis y resolución de ecuaciones diferenciales parciales, explorando ejemplos más específicos, como la ecuación de Poisson para electricidad. El Hands-On consistió en la modificación del código ejemplo dado en los "slides" de la clase de manera que se pudiesen simular distintos tipos de condiciones de forntera para ondas propagándose en una cuerda. Esto resultó especialmente útil para el desarrollo de mi proyecto final en conjunto con Alfredo Ricci, pues la realización de una animación que muestre las oscilaciones de las cuerdas según se define por la propagación de la onda de sonido sirve como base de desarrollo a nuestra simulación de una guitarra.

Durante la sesión de laboratorio se planteó como taller resolver la propagación de una perturbación de tipo gaussiano en un cubo con condiciones de frontera que conectaran caras según muestra el diagrama del enunciado. Esto se empezó a realizar partiendo como guía del ejemplo resuleto para una cara cuadrada en los "slides" de la clase, y se continua el viernes.

###Viernes 10 de Julio de 2015
##Continuación del Taller de Laboratorio
Durante la sesión de laboratorio y clase magistral se continuó trabajando en el taller de la resolución de la perturbación Gaussiana en el cubo modelado según los parámetros dados por el enunciado. También se aprovechó el tiempo para resolver dudas acerca del desarrollo de la tarea.

###Martes 14 de Julio de 2015
##Taller de Ecuación de Onda y Exposición
Durante la sesión de laboratorio se trabajó en un taller que permitió profundizar en las aproximaciones numéricas necesarias para la resolución de ecuaciones diferenciales parciales, pues fue necesario realizar manualmente los despejes y aproximaciones para las distintas derivadas parciales involucradas en la ecuación de Onda bidimensional con amortiguamiento. Sin embargo, debido a problemas técnicos, el taller se canceló por ahora, por lo que se procedió con el Hands-On y el experimento probabilístico propuesto en el enunciado. Su resolución empírica puede encontrarse en este notebook, y su gráfica resultante se muestra a continuación.

https://github.com/JuanUrrea6/MC/blob/master/Material/Hands-On%2014.ipynb

![alt text](https://raw.githubusercontent.com/JuanUrrea6/MC/master/Material/DatosObtenidos.png)

Es notable, durante la resolución de este Hands-On, la utilización del comando `shuffle`, importado desde la librería **random** de Python, el cual toma un arreglo de objetos y lo revuelve de manera aleatoria. Fue de especial utilidad para este problema probabilístico y seguramente lo es para esta temática en general, pues permite la creación de arreglos organizados, para cumplir condiciones dadas, y luego desorganizarlos para quitar lo determinista del estudio. Su utilización se muestra a continuación:
```
#Se crea un arreglo con elementos
arreglo = [1,2,3]

#Se utiliza el comando shuffle. Esto revuelve los elementos aleatoriamente en el arreglo.
arreglo = shuffle(arreglo)
```
También se muestra la parte vital de código utilizada para realizar el experimento de los peruanos y colombianos. 
```
#Función para determinar la probabilidad buscada.
#Parámetro: N=número de colombianos en la mesa.
def proba(N):
    exitos = 0 #Cantidad de Exitos
    laMesa = [] #Mi mesa vacía.
    for __ in range(N+10): #Llenar la mesa de puestos. 0 es colombiano.
        laMesa.append(0)
    for i in range(10): #LLenar los demás puestos. 1 es Peruano.
        laMesa[i]=1
    shuffle(laMesa)
    
    i=1
    while i < len(laMesa)-1:
        if((laMesa[i] == 1) & (laMesa[i+1] == 0) & (laMesa[i-1] == 0)):
            exitos+=1
        i+=1
        
    if((laMesa[0] == 1) & (laMesa[1] == 0) & (laMesa[-1] == 0)):
            exitos+=1
    if((laMesa[-1]== 1) & (laMesa[len(laMesa)-2] == 0) & (laMesa[0] == 0)):
            exitos += 1
    return exitos/10
```
La función aquí creada luego se utiliza iterativamente para obtener los resultados, sin embargo lo que se muestra es lo que considero permite solucionar el problema del enunciado.

##Proyecto Final
###9 de Junio de 2015
Para el proyecto final me gustaría trabajar en un estudio de movimiento y trayectorias como el que fue mostrado en clase, haciendo uso de la creación de animaciones en Python. Considero que me sería bastante útil, ya que a la vez que amplía mi conocimiento en programación usando Python, resulta un complemento bastante bueno para mi carrera de física, en especial para el área de cosmología (que me atrae), e incluso para visualizar casos problema básicos de movimientos. Se me ocurre que sería posible simular los movimientos de cuerpos celestes o microscópicos en diferentes montajes.

###Martes 16 de Junio de 2015
Para el proyecto final sería posible, ahora que se sabe como realizar ajustes básicos a distintos tipos de curvas, la implementación de esto a distintos sets de datos, como podría ser para problemas de movimient, como se mencionó antes, o de cosmología, mi principal interés. Estas funciones podrían venir especialmente en la sección de contraste con teoría que se realice en el proyecto. Esto podría juntarse con una función que he venido investigando, **quiver()**, con la cual se pueden graficar distintos campos vectoriales, por lo que la realización de ajuste de curva podrá ayudar a visualizar el comportamiento de un movimiento bajo el efecto de dichos campos, creando un análisis gráfica bastante completo. El análisis y estudio de situaciones como la órbita de satélites sería bastante interesante cuando se toma el campo de fuerza gravitacional del cuerpo principal, los datos conocidos de posición y el ajuste para contrastar.

###Miércoles 24 de Junio de 2015
Investigando para el proyecto, y teniendo en mente el interés por problemas de ámbito astronómico, he estado construyendo un notebook que contiene mis "avances" encontrando algún problema específico para solucionar. Por ahora, he estado explorando la construcción de campos vectoriales, específicamente el gravitacional, cuyo modelo se muestra en el siguiente notebook. Espero más adelante poder enfocarme en un aspecto más específico, como el estudio de una determinada estrella o agrupación. 
https://github.com/JuanUrrea6/MC/blob/master/Proyecto%20Final/Quiver%20y%20Graficaci%C3%B3n.ipynb

Aquí se muestra el resultado parcial de este proceso, aunque faltan corregir aspectos como los puntos alrededor del planeta para visualizar el campo de manera totalmente simétrica.

![alt text](https://raw.githubusercontent.com/JuanUrrea6/MC/master/Material/Gravedad.png)
