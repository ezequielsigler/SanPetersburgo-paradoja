# SanPetersburgo-paradoja

## Se analizó desde un punto de vista empírico la paradoja de San Petersburgo

Imaginate que te encuentras 1713 en San Petersburgo, ciudad Rusa financiada por los zares, en donde se encuentran grandes pensdores de la epoca, decides participar en una discusion matematica donde aparece una un nuevo problema, que representa un dilema para todos los matematicos de la ciudad. 

Se trata de un simple juego, el jugador paga una suma inicial al organizador para poder participar, luego se lanza una moneda al aire, de salir cara se avanza a la siguiente ronda y de salir ceca el jugador recibe $1. En las rondas sucesivas se repite el proceso pero el pago depende del numero de rondas, cocretamente seran de $1 * 2^(numero de rondas - 1)
es decir, si sale seca en la:
   segunda ronda entonces el pago es de 2$
   tercera ronda entonces el pago es de 4$
   cuarta ronda entonces el pago es de 8$

Las pregunta que todos se estan haciendo es ¿Cuanto estaria dispuesto a pagar por participar en este juego? y luego se desprende una segunda pregunta ¿Cual es el pago inicial que sea justo tanto para el jugador como para el organizador?

Muchas de las personas que participan de la discusion responden que ellos estan dispuestos a pagar al rededor de $10 por participar, sin embargo hay otros que dicen que el pago inicial justo es una cifra muchisimo mas grande, que de hecho es tan grande que ni la fortuna de los zares alcanzaria para alcanzar este monto.

Vamos a analizar esta paradoja utilizando la capacidad de computo que nos proporciona R

## ¿Cuanto estaria dispuesto a pagar por participar en este juego?

Esto es una cuestion subjetiva, que la vamos a dejar a libertad del lector, imagina que puedes participar en este juego solo una vez, lo minimo que puedes recibir es 1$ pero lo maximo que podriamos recibir es mucho dinero, imaginemos que conseguimos que salga cara 6 veces seguidas, ya tendriamos asegurados $32 y esta cifra podria incrementarse muchisimo mas de seguir saliendo cara. ¿Cual seria el monto que estarias dispuesto a pagar?

## ¿Cual es el pago inicial que sea justo tanto para el jugador como para el organizador?

Para aproximarnos a una respuesta decidimos observar que pasa cuando la gente juega, decidimos tomar cientos de observaciones y calcular el pago promedio que reciben los jugadores, concretamente tomamos 500 observaciones y encontramos que el pago promedio fue de $
