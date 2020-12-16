# SanPetersburgo-paradoja

Los códigos utilizados en este análisis pueden ser encontrados en los siguientes links:

https://www.kaggle.com/ezequielsigler/paradoja-san-petersburgo

https://github.com/ezequielsigler/SanPetersburgo-paradoja/blob/master/R

## Se analizó desde un punto de vista empírico la paradoja de San Petersburgo



Imagina que te encuentras 1713 en San Petersburgo, ciudad de Rusia financiada por los zares, en donde se encuentran grandes pensadores de la época, decides participar en una discusión matemática donde aparece una un nuevo problema, que representa un dilema para todos los matemáticos de la ciudad.

Se trata de un simple juego, el jugador paga una suma inicial al organizador para poder participar, luego se lanza una moneda al aire, de salir cara se avanza a la siguiente ronda y de salir ceca el jugador recibe $1. En las rondas sucesivas se repite el proceso, pero el pago depende del número de rondas, concretamente el pago será de $1 * 2^(número de rondas - 1), es decir, si sale seca en la:
   segunda ronda entonces el pago es de 2$
   tercera ronda entonces el pago es de 4$
   cuarta ronda entonces el pago es de 8$

La pregunta que todos se están haciendo es ¿Cuánto estaría dispuesto a pagar por participar en este juego? y luego se desprende una segunda pregunta ¿Cuál es el pago inicial que sea justo tanto para el jugador como para el organizador?

Muchas de las personas que participan de la discusión responden que ellos están dispuestos a pagar alrededor de $10 por participar, sin embargo hay otros que dicen que el pago inicial justo es una cifra muchísimo más grande, que de hecho es tan grande que ni la fortuna de los zares alcanzaría para alcanzar este monto.

Vamos a analizar esta paradoja utilizando la capacidad de cómputo que nos proporciona R.


### ¿Cuánto estaría dispuesto a pagar por participar en este juego?

Esto es una cuestión subjetiva, que la vamos a dejar a libertad del lector, imagina que puedes participar en este juego solo una vez, lo mínimo que puedes recibir es 1$ pero lo máximo que podríamos recibir es mucho dinero, imaginemos que conseguimos que salga cara 6 veces seguidas, ya tendríamos asegurados $32 y esta cifra podría incrementarse muchísimo más de seguir saliendo cara.

### ¿Cuál es el pago inicial que sea justo tanto para el jugador como para el organizador?

Para aproximarnos a una respuesta decidimos observar que pasa cuando la gente juega, decidimos tomar cientos de observaciones y calcular el pago promedio que reciben los jugadores, concretamente tomamos 1.000 observaciones y encontramos que el pago promedio fue de $5.70. Con este dato empírico podríamos decidir jugar cada vez que la suma inicial sea menor a $5.70, o ser organizadores cada vez que la suma inicial sea mayor a $5.70. Este valor permite dudar de la opinión de algunos matemáticos que dicen que el pago justo debería ser una suma extremadamente grande.

Establecer el pago correcto a través de un experimento empírico parece tener sentido, pero podrían existir grandes diferencias entre los datos de un experimento empírico y el verdadero promedio, para estar más seguros, decidimos tomar otra muestra de 1000 observaciones, esta vez el pago promedio fue de $8.66

Vemos que el valor del "precio justo" cambio significativamente respecto de la muestra anterior, por esta razón decidimos repetir esta muestra 200 veces más (cada una con 1000 observaciones) y tomar nota de cada valor promedio.


![Caption for the picture.](/Histograma.png)

Podemos observar que en la mayoría de las observaciones el pago promedio es menor a $10, sin embargo, se ve que siguen existiendo observaciones muy por encima de los $10. Observamos que existen valores extremadamente grandes.

### Esperanza Matemática

Es momento de dejar de tomar observaciones y plantear el problema desde un punto de vista matemático, concretamente debemos determinar el resultado esperado de participar de este juego o su esperanza matemática.

![sigma](https://latex.codecogs.com/svg.latex?E\left(X\right)=1\cdot%20\frac{1}{2}+2\cdot%20\frac{1}{4}+4\cdot%20\frac{1}{8}+...)

El valor esperado es equivalente a multiplicar cada resultado posible por su probabilidad de ocurrencia, por lo tanto, la ecuación de arriba precisa de infinitos términos, que se pueden expresar con la siguiente sumatoria:

![sum2](https://latex.codecogs.com/svg.latex?E\left(X\right)=\sum%20_{n=1}^{\infty%20}\left(2^{n-1}\right)\cdot%20\left(\frac{1}{2^n}\right))

Resolviendo la ecuación:

![sum2](https://latex.codecogs.com/svg.latex?E\left(X\right)=0.5+0.5+0.5+0.5+0.5+0.5+0.5+...)

Podemos ver que el valor esperado es la suma de infinitos términos de $1, es decir que el valor esperado es infinito.

Surge un interrogante, como es posible que en las muestras realizadas previamente los pagos promedios de un numero grande de juegos tuvieron valores pequeños, concretamente de $5.70 para la primera muestra y de $8.366 para la segunda muestra. Estos valores están extremadamente alejados de infinito.

### Elevando el tamaño de la muestra

Se evaluó en forma separada el pago de cada una de las rondas, calculando el beneficio promedio de todos los juegos que terminaron en la primera ronda, en la segunda y así sucesivamente. Acorde a la fórmula de la esperanza matemática cada ronda debería aportar en promedio $0.5

![Caption for the picture.](/promedio_por_ronda.png)

Podemos ver que cuando se evalúa con 100 juegos, solo las primeras rondas aportaron su valor promedio, pero no ocurrió ningún resultado en donde se consiga avanzar múltiples rondas, concretamente la observación con el pago más alto avanzo hasta la quinta ronda. A medida que aumentamos el número de juegos en la muestra observamos que cada vez más rondas aportan su valor promedio, concretamente para la muestra con 10.000.000 de juegos múltiples rondas aportaron su valor promedio y la observación con el pago más alto avanzo hasta la ronda 22.


### Conclusión

Podemos concluir que elevando el número de juegos lo suficiente, podríamos encontrar un punto en donde todas las rondas aporten su valor promedio y efectivamente el pago esperado será infinito, pero siempre que se tomen muestras pequeñas, la probabilidad de encontrarnos con pagos demasiado elevados es extremadamente baja.

Sería interesante continuar este análisis evaluándolo desde la perspectiva de un organismo regulador, evaluar cual sería el capital mínimo exigido por las normal de solvencia en este caso.

