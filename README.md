# Practica_08_ChristianTorresGonzalez

Para la realización de esta octava práctica, partiré de la escena desarrollada para la práctica anterior, de tal forma que partiendo de las implementaciones y scripts anteriores, continuaré con los puntos que se solicitan. Esos puntos que se solicitan son los siguientes:
- Scroll con movimiento del fondo. El personaje salta sobre objetos que aparecen en la escena.
- Scroll con movimiento del personaje. El fondo se repite hasta que pare el juego
- Fondo con efecto parallax. El efecto empieza cuando el jugador empieza a moverse, esto se debe comunicar mediante eventos.
- Utilizar la técnica de pool de objetos para ir creando elementos en el juego sobre los que debe saltar el jugador evitándolos o para adquirir puntos si salta sobre ellos

Como consideración, hay que tener en cuenta, que la idea de esta practica es trabajar con el plugin **Cinemachine**  el cual tendré que instalar de **Unity Registry**. Para ponernos un poco en contexto, este plugin permite añadir cámaras virtuales, entre las cuales se podrá ir cambiando, además de otras funcionalidades como añadir una zona de confinamiento, es decir, una zona que funcionara como limite de movimiento de nuestra cámara.
 

## Seguimiento de personajes
La primera tarea de esta practica, es la de añadir dos cámaras para seguir a dos personajes, respectivamente. La cámara del personaje A, será la cámara que ya tenemos incluida en nuestra escena, es decir la cámara principal. Para el personaje B, añadiré una cámara virtual, la cual se cambiara como cámara principal en el momento que mueva este personaje, además, la zona que abarca esta segunda cámara será mayor que la cámara del personaje A. Para poder realizar esta primera tarea, para realizar el cambio de camara, lo que he hecho ha sido añadir una nueva camara a mi escena, la cual le he asignado que siga el personaje B, y para poder ponerla como principal, lo que he hecho ha sido añadirle una prioridad mayor:

- Cámara del personaje A
  ![Alt text](/img/camaraA.png)
  ![Alt text](/img/camaraA.gif)
  
- Cámara del personaje B
  ![Alt text](/img/camaraB.png)
  ![Alt text](/img/camaraB.gif)

## Seguimiento de varios personajes
Para esta segunda parte de la practica, se solicita que ahora se añada una nueva cámara que permita hacer el seguimiento de varios personajes a la vez, es decir, que en todo momento estén dentro del plano de la cámara, los personajes que se le indiquen independientemente del movimiento que estén realizando. Para crear esto, es bastante sencillo: ya que Cinemachine, te da la opción de crear una cámara que haga el seguimiento de varios personajes. Para ello, si me voy al inspector, selecciono cinemachine y creo una "Target Group Camera"

- Crear una **"Cámara de objetivo múltiple"**

![Alt text](/img/target1.png)

![Alt text](/img/target2.png)

![Alt text](/img/target3.png)

- Una vez he seleccionado este objeto, automáticamente se me crean en mi escena una nueva cámara virtual, y un GameObject llamado TargetGroup. Lo único que me queda por hacer, es indicar que objetos quiero que siga la cámara dentro del nuevo GameObject que se ha creado, de resto no es necesario hacer nada mas, porque ya viene todo configurado.
![Alt text](/img/target.gif)



## Zonas de confinamiento
Para la tercera parte de la practica, se solicita que se creen unas zonas de confinamiento, es decir, se delimite mediante un objeto con la propiedad "Polygon Collider" cuales serán los limites por los que se podrá mover la cámara, por lo que cuando la cámara llega a este punto de la escena, el personaje podrá seguir moviéndose, pero la cámara se quedara fija, a no ser que se mueva en la dirección opuesta al limite establecido para la frontera de movimiento para la cámara. 
- Para poder llevar esto a cabo, lo primero que tengo que hacer es crear un GameObject vacío, el cual llamare como **Boundaries** y le añadiré la propiedad Polygon Collider. Una vez añadida esta propiedad, solo queda definir dichos limites en la escena.

![Alt text](/img/fronteraA.png)

- Una vez definido los limites, cuando ejecutamos nuestro juego, tal y como se ve en el video, cuando el personaje se acerca al borde derecho del mapa, la cámara se queda quieta, pero cuando vuelve a moverse hacia la izquierda, la cámara recupera su movimiento.

![Alt text](/img/fronteraA.gif)

- Para la segunda parte de esta tarea, se debe crear una zona de confinamiento mas pequeña, pero para la cámara del personaje B, por lo que los pasos son los mismos que los anteriores, pero ahora definiremos el Polygon Collider un poco mas pequeño que el de la cámara del personaje A.
- Para la zona de confinamiento del personaje B, lo que hare será definir los limites en el puerto, para comprobar su correcto funcionamiento.

![Alt text](/img/fronteraB.png)

- Tal y como se aprecia en el video, en el momento en el que la cámara llega a la frontera establecida, se queda fija en esa posición, pero el personaje sigue su movimiento por la escena.

![Alt text](/img/fronteraB.gif)

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
