# Taller de creacion de servidores

Lo primero, ¿qué es un servidor? Eso es una pregunta que muchas veces, ivluso gente que estudia informatica, no tiene muy claro. A groso modo, un servidor no es más que un ordenador normal y corriente, pero con la idea de que no se apague nunca. Además, un ordenador suele ser para uso personal, mientras que en un servidor lo que se busca es poder exponer un servicio para que sea usado desde aguera. Este servicio puede ser una web, una VPN, una API...

A nivel de software, el software y el sistema operativo es identico al que puedes utilizar en un ordenador común. Por ejemplo, instalr Ubuntu, Debian, CentOs... Otros, como Windows, tienen una version especial dedicada a los servidores, llamada Windows server. 

Donde si que se diferencia es en el tipo de programas que utilizas en un servidor, que es esta más orientado a la gestion y a la exposición de servicios. Por ejemplo, en un servidor tienes software para gestionar redes, como DNS, Proxy; o OCM como Wordpress; web como Nginx, Apache, APIs de Node... Básicamente cualquier red que tienes expuesta en local, en un servidor la puedes exponer en un servidor al mundo.

A nivel de hardware, los servidores reales estan preparados para qué tengan partes para este uso especifico. Por ejemplo, los discos duros se pueden cambiar en caliente, cambiar tarjetas de red y otros componenetes sin tener que apagar el servidor o incluso componentes con redundancia para que en caso de que alguno de ellos deje de funcionar pueda seguir fucncionando el otro sin perder servicio. Aún así, cualquier ordenador puede ser usado como un servidor. La idea, como he dicho es que este expuesto a internet los sistemas que quieras, ya sea una web api...

Una vez que tenemos esto claro, puedes crearte un servidor en tu propio portatil. Pero como este lo enciende, apagas, cambias de red... es mejor utilizar un oc vieho o algun otro sistema (como una RaspberryPi) para dejarlo encendido y con tus servicios expuestos.

## Instalación

Una vez que ya sabes en que máquina vas a tener instalado tu servidor, vamos a ello.

Cómo he dicho antes, puedes tener instalado tu sistema operativo con escritorio. Eso significa tener un entorno gráfico al igual que el que sueles tener en tu PC habitual. En los servidores, puesto que lo que queremos es ahorrar la mayor cantidad de recursos posibles (cuántos menos recursos malgastemos, más tendremos disponibles para usarlos en los servicios y menos cantidad de recursos y energia estaremos desperdiciando). Por eso en los servidores lo qe se suele utilizar es la version de terminal (llamada version Server) que es una version que solo viene con un terminal y los minimos apquetes instalados. Cuando estas empezando es mas comodo si tienes una version con escritorio para irte acostumbrando a usar el terminal, pero aun asi tener un comodo entorno gráfico. Igualmente, aunque instalemos la version de Servidor, podemos instalar "el programa Escritorio", y activarlo unicamente cuando lo necesitemos, y cuando no, estaremos ahorrando una buena cantidad de recursos.

Para instalar el sistema operativo, e instalar y habilitar el escritorio, hay mil webs. Aunque al principio recomiendo el uso de una máquina virtual, para que ea más sencillo hacer pruebas(creando puntos de restauracion(como si de checkpoints de un videojuego se tratase)), y en caso de que algo alle, poder reinstalar todo de manera sencilla.  

# Introducción a Conectividades

Aquí es donde sobre todo empueza la fiesta. Para extender tu "localhost" a todo internet hay que hacer un par de cositas entre medias. Esta parte la voy a intentar explicar de la manera más clara posible. 

Cuando tu te conectas a un Wifi, este te asigna una IP. Esta IP sirve para identificarte. Por eso cuando en tu PC levantas una web (ya sea con Node, Nginx...) puedes acceder a ella si desde otro PC que este conectado a la misma red pones la IP del PC que expone la aplicacion (normalmente es 192.168.1...). Si esto solo diese así, en cada IP solo podriamos acceder a un servicio, pero esto sería muy poco eficiente. Por ello, cada IP tiene puertos. Para hacernos una idea de cómo funciona esto. Imagina una red como si fuese un hotel. Cada planta es una IP y cada puerto es una habitación. En cada habitación podemos tener un servicio diferente funcionando. Cuando creamos un servicio (API, Web...) lo exponemos en un puerto específico. 

Además existen algunas habitaciones especiales. Cuando ves lo que hay en ellas, te dicen que el servicio que estas buscando esta en otra habitación. Pero de esto hablaremos más adelante.

# Conectividades remotas

Una vez que ya tenemos claro el apartado anterior, voy a decir una definición bastante fea jejeje. Internet no es más que un router gordo. En este router hay conectados otros routers, creando redes más pequeñas. Las IP de este router gordo son conocidas como IP públicas, y son accesibles desde cualquier sitio de internet. Pueden ser usadas por empresas, o en la mayoria de los casos, el router de vuestra casa ya tiene su propia IP pública (o si no puedes pagar un poco más en tu factura (unos 12€/año)para que te den una). Esto lo pueden hacer de 2 maneras, o asignados siempre la misma IP, o cambiando la IP, pero siendo siempre una IP pública. 

Las llevas usando años, pero no te has dado cuenta ya que normalmente usas un nombre, como por ejemplo google.com . Esto lo podemos hacer gracias a una tecnología llamada DNS(Dinamic Name Server). Esto funciona muy parecido a tu agenda de telefonos, ¿te sabes los numeros de todo el mundo o los buscar por su nombre? Pues eso es un DNS, un servicio que asocia IP a un nombre, de modo que sea más facil buscarlo, y, al igual que en la agenda del telefono, aunque el numero cambie tu vas a seguir buscando por el mismo nombre.

Con esto clarito, creo que ya sabeis por donde vamos. Vamos a aprender a direccionar el tráfico para que desde cualquier punto del mundo se pueda acceder a vuestro "localhost".

