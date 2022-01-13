# Practica_08_ChristianTorresGonzalez

Para la realización de esta octava práctica, partiré de la escena desarrollada para la práctica anterior, de tal forma que partiendo de las implementaciones y scripts anteriores, continuaré con los puntos que se solicitan. Esos puntos que se solicitan son los siguientes:
- Scroll con movimiento del fondo. El personaje salta sobre objetos que aparecen en la escena.
- Scroll con movimiento del personaje. El fondo se repite hasta que pare el juego
- Fondo con efecto parallax. El efecto empieza cuando el jugador empieza a moverse, esto se debe comunicar mediante eventos.
- Utilizar la técnica de pool de objetos para ir creando elementos en el juego sobre los que debe saltar el jugador evitándolos o para adquirir puntos si salta sobre ellos
 

## BakcGorund Scroll
Para esta primer aparte de la practica, se solicita que se de un efecto de fondo infinito al fondo de nuestra escena, mediante una técnica denominada background scrolling. Esta técnica consiste en ir moviendo el fondo de nuestra escena a medida que nos movemos por el juego, de tal forma que esto daría un efecto de fondo infinito por la escena.
Para ello, lo único que debo hacer es duplicar el fondo en la escena y mediante el siguiente script, lo único que voy a ir haciendo es ir desplazando el fondo por la escena una cantidad igual a su tamaño, de esta forma quedaría el efecto de fondo infinito.

![Alt text](/img/background.png)

![Alt text](/img/background.gif)

## Parallax
Para la tercera parte de la practica, se solicita que mediante la tecnica llamada **Parallax**, cree un efecto en la escena de que el entorno se mueve, es decir el fondo de la escena parece que tiene un movimiento a la vez que el jugador se desplaza. 
- Para poder llevar esto a cabo, lo primero que tengo que hacer es crear un GameObject vacío, el cual llamare como **Background** y le añadiré los diferentes sprites que conforman el fondo de la escena. E aquí la clave de todo, ya que toda esta técnica se fundamente en que el fondo de nuestro juego tiene que estar dividido en varias capas, de tal forma que a cda una de ellas se le pueda indicar una velocidad de movimiento diferente.

![Alt text](/img/fondoParallax.png)

- Una vez definido el fondo de la escena, dividido en varias capas, lo siguiente que debo hacer es crear el script que se va a encargar de determinar el desplazamiento que debe realizar el fondo de nuestra escena para dar la sensación de movimiento, en función del movimiento que realice la cámara.

![Alt text](/img/camara.png)

- Tal y como se aprecia en el script, lo unico que hago es ir modificando la posicion de la imagen en el eje X, es decir, desplazarla horizontalmente, en funcion del efecto parallax, es decir del movimiento de la camara, bien sea tanto para la derecha como para la izquierda.

- Finalmente, para ver reflejada esta implementacion, podemos ver este gif, donde se aprecia el resultado.
- 
![Alt text](/img/camara.gif)

## Pooling Objects
Para este ultimo punto se solicita que se implemente una técnica de creación de objetos que mejore la optimización del juego, ya que esta se basa en crear una cantidad de objetos limitada, los cuales iremos activando en función de nuestras necesidades. Una vez hemos usado el objeto, simplemente lo desactivamos, de tal forma que lo volvemos a tener disponible para usarlo de nuevo.

Tal y como vemos en esta imagen, vemos el script referente a la creación de nuestro contenedor de objetos, donde estarán almacenados, pero desactivados de manera inicial, de esta forma, cuando queramos utilizar uno, lo único que hacemos es buscar un objeto que no esté activo y lo usamos.

![Alt text](/img/pooling.png)

Una vez creado el script de ObjectPooling, lo que hago es inicializar la posición del objeto en la posición deseada y lo único que hago es indicar que el objeto se mueva hacia la derecha para que simule un obstáculo que tiene que evitar el jugador.

![Alt text](/img/obstaculo.png)

Finalmente, una vez el objeto sale de la escena, lo único que tengo que hacer es desactivar el objeto, ya que la próxima vez que lo vaya a utilizar, las coordenadas se inicializan, por si solas.

![Alt text](/img/desactivar.png)

Finalmente, en este gif, vemos una representación del resultado.

![Alt text](/img/resultado4.gif)
