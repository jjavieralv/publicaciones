

# Kubernetes VS Docker

Segun he visto, hay mucha gente que aun no tiene claro esta diferencia, y eso que utilizan estas tecnologías. Además, puede ser una buena introduccion para aquellas personas que tengan curiosidad o quieran aprender un poquito de algo chachi. PD: ESTO NO ES UNA GUIA DE COMO SE USAN

## Docker

Hay muchas maneras en las que esto puede ser explicado, que si contenedores, que si funcionan como si fuesen un programa, que si quiere bolsa... Así que vamos a abstraerlo a tope para intentar que quede claro.

### Docker es como un plato de comida, y te lo voy a demostrar

Imagínate que estas en casa y te quieres hacer una ensalada, ¿A que no te compras una maceta, plantas las semillas, lo riegas, pones fertilizante...? Si no que bajas al supermercado, te compras tu bolsita de ensalada y te subes (que ya alguien se ha encargado de comprar la tierra, plantar, regar...). 

Pues eso es exáctamente Docker, en lugar de tener que montar todo el sistema (como en una máquina convencional) tan solo tomas lo necesario y te olvidas de todo lo demás. Con esto ganamos 2 cosas, facilidad (no te hace falta tener la casa llena de macetas), replicabilidad (la bolsita de lechuga que tu compras aquí es igual que la que compra el vecino). Claro que si tu tuvieses tus macetas te encargarías de todo el proceso y lo tendrias exactamente a tu gusto teniendo que aprender a regar, fertilizantes, botanica...., pero, ¿realmente te interesa todo eso para hacerte una ensalada?

### Las partes que tiene Docker

Voy a continuar con la metáfora del plato de comida para continuar la explicacion: 

- [Dockerfile]: La receta
- [Build]: Cocinar la receta, preparando los ingredientes.
- [Imagen]: Los platos precocinados 
- [Contenedor]: El plato listo para servir, emplatado y todo

Cuando quieres hacer un plato, buscas la receta, la modificas si quieres y cocinas todos los inredientes, quedándote así un plato preparado. Ya que cocinas haces mucho, así que con el preparado puedes hacer muchos platos, añadiendo algún ingrediente extra en algun caso si quieres. Al final del todo, tomas ese plato, lo emplatas y ya esta listo para comer. Una receta se puede usar como base para poder cocinar otras recetas. Por ejemplo, hacer un bizcocho y luego en otra receta te dice que cubras el bizcocho con nata y framuesas.

En el caso de docker, tienes un Dockerfile. Este documento (que podemos modificar al gusto) contiene una serie de instrucciones que ha de seguir el proceso de build, que da como resultado una imágen. Esta imagen es la que utilizaremos más adelante para generar tantos contenedores como deseemos de esa imagen. Una vez creada esa imagen, se puede usar como base a la hora de crear otras imágenes. 



## Kubernetes

Es
### Las partes que tiene Kubernetes

- [Pod]: Es el menu de platos combinados. Puede tener un solo plato o muchos. 
- [Deployment]: Es
- []