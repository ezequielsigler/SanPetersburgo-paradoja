# SanPetersburgo-paradoja

## Se analizó desde un punto de vista empírico la paradoja de San Petersburgo

Imagina que te encuentras 1713 en San Petersburgo, ciudad Rusa financiada por los zares, en donde se encuentran grandes pensdores de la epoca, decides participar en una discusion matematica donde aparece una un nuevo problema, que representa un dilema para todos los matematicos de la ciudad. 

Se trata de un simple juego, el jugador paga una suma inicial al organizador para poder participar, luego se lanza una moneda al aire, de salir cara se avanza a la siguiente ronda y de salir ceca el jugador recibe $1. En las rondas sucesivas se repite el proceso pero el pago depende del numero de rondas, concretamente el pago seran de $1 * 2^(numero de rondas - 1)
es decir, si sale seca en la:
   segunda ronda entonces el pago es de 2$
   tercera ronda entonces el pago es de 4$
   cuarta ronda entonces el pago es de 8$

Las pregunta que todos se estan haciendo es ¿Cuanto estaria dispuesto a pagar por participar en este juego? y luego se desprende una segunda pregunta ¿Cual es el pago inicial que sea justo tanto para el jugador como para el organizador?

Muchas de las personas que participan de la discusion responden que ellos estan dispuestos a pagar al rededor de $10 por participar, sin embargo hay otros que dicen que el pago inicial justo es una cifra muchisimo mas grande, que de hecho es tan grande que ni la fortuna de los zares alcanzaria para alcanzar este monto.

Vamos a analizar esta paradoja utilizando la capacidad de computo que nos proporciona R

### ¿Cuanto estaria dispuesto a pagar por participar en este juego?

Esto es una cuestion subjetiva, que la vamos a dejar a libertad del lector, imagina que puedes participar en este juego solo una vez, lo minimo que puedes recibir es 1$ pero lo maximo que podriamos recibir es mucho dinero, imaginemos que conseguimos que salga cara 6 veces seguidas, ya tendriamos asegurados $32 y esta cifra podria incrementarse muchisimo mas de seguir saliendo cara.

### ¿Cual es el pago inicial que sea justo tanto para el jugador como para el organizador?

Para aproximarnos a una respuesta decidimos observar que pasa cuando la gente juega, decidimos tomar cientos de observaciones y calcular el pago promedio que reciben los jugadores, concretamente tomamos 1.000 observaciones y encontramos que el pago promedio fue de $6.45. Con este dato empirico podriamos decidir jugar cada vez que la suma inicial sea menor a $5.70, o ser organizadores cada vez que la suma inicial sea mayor a $5.70. Este valor permite dudar de la opnion de algunos matematicos que dicen que el pago justo deberia ser una suma extremandamente grande. 

Establecer el pago correcto a travez de un experimento empirico parece tener sentido, pero podrian existir grandes diferencias entre los datos de un experimento empirico y el verdadero promedio, para estar mas seguros, decidimos tomar otra muestra de 1000 observaciones, esta vez el pago promedio fue de $8.66

Vemos que el valor del "precio justo" cambio significativamente respecto de la muestra anterior, por esta razon decidimos repetir esta muestra 200 veces mas (cada una con 1000 observaciones) y tomar nota de cada valor promedio.


![Caption for the picture.](/Histograma.png)

Podemos observar que en la mayoria de las observaciones el pago promedio es menor a $10, sin embargo se ve que siguen existiendo observaciones muy por encima de los $10. Observamos que existen valores extremadamente grandes.


Es momento de dejar de tomar observaciones y plantear el problema desde un punto de vista matematico, concretamente debemos determinar el resultado esperado de participar de este juego o su esperanza matematica. 


![sigma](http://latex.codecogs.com/svg.latex?%5Csum_%7Bi%3D1%7D%5E%7B100%7Di)

<!-- \sum_{i=1}^{100}i -->

<!-- \sum_{i=1}^{100}(2i+1) -->

![Caption for the picture.](/promedio_por_ronda.png)

