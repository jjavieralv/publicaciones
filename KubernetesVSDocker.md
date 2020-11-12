

# Kubernetes VS Docker

Segun he visto, hay mucha gente que aun no tiene claro esta diferencia, y eso que utilizan estas tecnologías. Además, puede ser una buena introduccion para aquellas personas que tengan curiosidad o quieran aprender un poquito de algo chachi. PD: ESTO NO ES UNA GUIA DE COMO SE USAN

## Docker

Hay muchas maneras en las que esto puede ser explicado, que si contenedores, que si funcionan como si fuesen un programa, que si quiere bolsa... Así que vamos a abstraerlo a tope para aclarar el qué es.

### Docker es como un plato de comida, y te lo voy a demostrar

Imagínate que estas en casa y te quieres hacer una ensalada, ¿A que no te compras una maceta, plantas las semillas, lo riegas, pones fertilizante...? Si no que bajas al supermercado, te compras tu bolsita de ensalada, y te subes a comertela. Ya alguien se ha encargado de comprar la tierra, plantarla, regar, envasarla...

Pues eso es exáctamente Docker. En lugar de tener que montar todo el Sistema Operativo y trabajar sobre él(como en una máquina convencional), tan solo tomas lo que realmente necesitas y te olvidas de todo lo demás.  
Con esto ganamos 2 cosas, facilidad (no te hace falta tener la casa llena de macetas), replicabilidad (la bolsita de lechuga que tu compras aquí es igual que la que compra el vecino).  
Claro que si tu tuvieses tus macetas te encargarías de todo el proceso y lo tendrias exactamente a tu gusto. Teniendo que aprender a regar, fertilizantes, botanica..., pero, ¿realmente te interesa todo eso para hacerte una ensalada?

### Las partes que tiene Docker

Voy a continuar con la metáfora del plato de comida para continuar la explicacion: 

- [Dockerfile]: La receta
- [Build]: Cocinar la receta, preparando los ingredientes.
- [Imagen]: Los alimentos cocinados
- [Contenedor]: El plato listo para servir, emplatado y todo
- [Secret]:Ingrediente secreto, solo lo saben los cocineros.

En Docker lo que haces es coger el Dockerfile. Con el cual haces una build y te da como resultado una imagen. Esta imagen la utilizarás más adelante para hacer tus contenedores. Ahora lo traduzco al ejemplo :).  

Cuando quieres hacer un plato de comida, buscas la receta, la modificas (si quieres) y cocinas todos los ingredientes, quedándote así los ingredientes cocinados. Cuando quieres comer, tomas esos ingredientes cocinados, los pones en un plato y a comer. Además, alguno de los ingredientes puede ser *tu ingrediente secreto*, que nadie sabe excepto tu durante la preparación, pero a veces pueden deducirlo si tienen buen paladar o si se lo dices cuando sirvas.  
También, podrías usar esos ingredientes que ya has cocinado y crear una receta nueva añadiendo algun ingrediente más para tener un plato final diferente. Como si cocinas arroz, y luego lo añades un platano frito(no judgueis, probadlo :) ).  

En el caso de docker, tienes un Dockerfile. Este documento (que podemos modificar al gusto) contiene una serie de instrucciones que ha de seguir el proceso de build, que da como resultado una imágen. Esta imagen contiene todo lo que necesitamos para que nuestro programa se ejecute(librerias, nuestro propio programa descargado, archivos, software...). En el proceso de build, podemos incluir secrets(como tokens o claves SSH), que estarán ocultos en el resultado final a no ser que los guardemos, o, los incluyamos como variables. La imagen es la que utilizaremos más adelante para generar tantos contenedores idénticos como deseemos. Una vez creada esa imagen, se puede usar como base a la hora de crear otras imágenes. También, podemos usar diferentes Dockerfile para crear diferentes imágenes. 



## Kubernetes

Es un **orquestador de contenedores**, *"pa' los del fondo"*, un programa que se encarga de gestionar Docker y dejar las cosas bonitas(aunque se puede usar con otras tecnlogias). También, todo en Kubernetes es considerado un objeto.
Para continuar con la comparación, si habíamos dicho que Docker es como preparar un plato de comida, Kubernetes es un restaurante. En él, hay personas encargadas de cada parte del proceso a las que tan solo les dices lo que quieres y ya se encargan ellos de montarlo y mantenerlo en funcionamiento.

### Las partes que tiene Kubernetes

Una vez que ya hemos explicado las partes de Docker, vamos a entrar en Kubernetes añadiendo algunas más.

- [Pod]: Es el menu de platos combinados. Puede tener un solo plato o muchos
- [Deployment]: Emplatar y llevar los platos a los clientes
- [Service]: 
- [Replicas]: "*Mis amigos tomarán lo mismo que yo*"
- [Healthchecks]: Que nadie se quede con hambre
- [Namespace]: Cada una de las mesas individuales
- [Réplica]: Pods idénticos, se suelen usar como si fuese 1 solo.
- [Volumenes]: Tupper en el que guardas lo que quieras

Imaginemos que en un restaurante recibe una comanda. En esta pone todo lo que el cliente quiere. Si es un plato combinado, pues hará falta preparar varios platos y servirlos juntos como uno solo. Pues el camarero ve si estan esos platos ya listos para llevarselos, si no, avisa al cocinero. Si el cliente solicita que sea un plato recien cocinado, le toca al cocinero coger la receta y preparar todos los ingredientes. Ahora, una vez que tiene todo listo, llama a los camareros para que cojan el plato y se lo lleven al cliente. El camarero ya se encarga de que todo este al gusto del cliente, tenga una buena comida, si hay algo que no este a su gusto intentar arreglarlo.

En Kubernetes cuando queremos desplegar algo, necesitamos la imagen (como con Docker).Si no tenemos lista la imagen, lo que hacemos es hacer una build con Docker. O podemos usar una ya construida y lista para usarse, por ejemplo, visitando [DockerHub](https://hub.docker.com/) en el que hay miles de imagenes y configuraciones creadas y listas para usarse.  
Una vez que tenemos la imagen, el objeto creado de Deployment(EL DEPLOYENT NO LA TOMA(ESTO ES EN OPENSHIFT)) coge esa imagen, toma todos los recursos que le hayas indicado (CPU,RAM,Volúmenes,secrets...) y crea e inicializa los contenedores. En caso de que surja algún problema, intentará repetir el proceso o solucionar el error, y si no puede, te arrojará el fallo que ha ocurrido.  
  

Volvemos al restaurante. Imaginate que estas en el restaurante sentado en tu mesa, y de repente vienen muchos amigos tuyos con hambre. Pues no vais a comer todos del mismo plato por que no hay comida suficiente para todos. Así que el camarero empieza a traer platos con lo mismo que estabas comiendo tu, dando así de comer a todo el mundo.(PONER ESTA PARTE COMO SI FUESEN RACIONES DE LAS QUE VA COMIENDO TODO EL MUNDO QUE VA LLEGANDO)

Imaginemos que nuestra aplicacion es una pagina web. En algunos momentos tendremos muchas peticiones y en otras casi ninguna. Si montamos una maquina con mucha potencia, cuando hay pocas peticiones estamos malgastando recursos. Y si la montamos con poca potencia, cuando hay muchas peticiones revienta. ¿Cómo solucionamos este problema? Pues con la magia de Kubernetes y sus réplicas. Lo que hace, es levantar tantos pods idénticos como se demanden. Entonces hay pocas replicas cuando hay pocas peticiones y cuando detecta que hay muchas, levanta réplicas para poder hacer frente a la demanda. El indicador de si hay que aumentear o disminuir las replicas se llama healthcheck.  
Un healthcheck es un sistema que usamos para controlar la funcionalidad y actividad de un pod. Con esto comprobamos que todo este funcionando correctamente dentro de unos parámetros, y si no es así, ejecutará la tarea que le hayamos indicado, como por ejemplo, reiniciar los pods o aumentar el número de réplicas.  
  
  
Volviendo al restaurante, una vez que te has acabado el plato de comida, te lo quitan. Puedes pedir otro, y te traerán uno nuevo. Imagina que quieres guardar algo, como por ejemplo, una salsa que 
