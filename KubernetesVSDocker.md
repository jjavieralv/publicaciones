

# Kubernetes VS Docker

Segun he visto, hay mucha gente que aun no tiene claro esta diferencia, y eso que utilizan estas tecnologías. Además, puede ser una buena introduccion para aquellas personas que tengan curiosidad o quieran aprender un poquito de algo chachi. PD: ESTO NO ES UNA GUIA DE COMO SE USAN

## Docker

Hay muchas maneras en las que esto puede ser explicado, que si contenedores, que si funcionan como si fuesen un programa, que si quiere bolsa... Así que vamos a abstraerlo a tope para aclarar el qué es.

### Docker es como un plato de comida, y te lo voy a demostrar

Imagínate que estas en casa y te quieres hacer una ensalada, ¿A que no te compras una maceta, plantas las semillas, lo riegas, pones fertilizante...? Si no que bajas al supermercado, te compras tu bolsita de ensalada, y te subes a comertela. Ya alguien se ha encargado de comprar la tierra, plantarla, regar, envasarla...

Pues eso es exáctamente Docker, en lugar de tener que montar todo el Sistema Operativo y trabajar sobre el(como en una máquina convencional), tan solo tomas lo que realmente necesitas y te olvidas de todo lo demás.  
Con esto ganamos 2 cosas, facilidad (no te hace falta tener la casa llena de macetas), replicabilidad (la bolsita de lechuga que tu compras aquí es igual que la que compra el vecino).  
Claro que si tu tuvieses tus macetas te encargarías de todo el proceso y lo tendrias exactamente a tu gusto. Teniendo que aprender a regar, fertilizantes, botanica..., pero, ¿realmente te interesa todo eso para hacerte una ensalada?

### Las partes que tiene Docker

Voy a continuar con la metáfora del plato de comida para continuar la explicacion: 

- [Dockerfile]: La receta
- [Build]: Cocinar la receta, preparando los ingredientes.
- [Imagen]: Los alimentos cocinados
- [Contenedor]: El plato listo para servir, emplatado y todo

En Docker lo que haces es coger el Dockerfile. Con el cual haces una build y te da como resultado una imagen. Esta imagen la utilizarás más adelante para hacer tus contenedores. Ahora lo traduzco al ejemplo :).  

Cuando quieres hacer un plato de comida, buscas la receta, la modificas (si quieres) y cocinas todos los ingredientes, quedándote así los ingredientes cocinados. Cuando quieres comer, tomas esos ingredientes cocinados, los pones en un plato y a comer.  
También, podrías usar esos ingredientes que ya has cocinado y crear una receta nueva añadiendo algun ingrediente más para tener un plato final diferente. Como si cocinas arroz, y luego lo añades un platano frito(no judgueis, probadlo :) ).

En el caso de docker, tienes un Dockerfile. Este documento (que podemos modificar al gusto) contiene una serie de instrucciones que ha de seguir el proceso de build, que da como resultado una imágen. Esta imagen contiene todo lo que necesitamos para que nuestro programa se ejecute(librerias, nuestro propio programa descargado, archivos, software...). La imagen es la que utilizaremos más adelante para generar tantos contenedores idénticos como deseemos. Una vez creada esa imagen, se puede usar como base a la hora de crear otras imágenes. También, podemos usar diferentes Dockerfile para crear diferentes imágenes. 



## Kubernetes

Es un **orquestador de contenedores**, *"pa' los del fondo"*, un programa que se encarga de gestionar Docker y dejar las cosas bonitas(aunque se puede usar con otras tecnlogias).  
Para continuar con la comparación, si habíamos dicho que Docker es como preparar un plato de comida, Kubernetes es un restaurante. 

### Las partes que tiene Kubernetes

- [Pod]: Es el menu de platos combinados. Puede tener un solo plato o muchos. 
- [Deployment]: Es
- [Service]:
- [Build]:
- [Images]:
- 