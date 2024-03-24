### Independencia condicional y observaciones independientes e idénticamente distribuidas

La definición de variables aleatorias iid es la siguiente:

>###### Definición 2 (Variables aleatorias iid)
>El modelo de observaciones independientes idénticamente distribuidas (iid) es aquel que supone que las variables aleatorias $Y_i$:
>
>- son mutuamente independientes, condicionadas a que conocemos el valor de cierto parámetro desconocido $\theta$ y,
>- se distribuyen todas igual con distribución común: $p(y | \theta)$.
>
>A la muestra resultante se le llama _muestra aleatoria simple_. Una notación bastante usada para este supuesto es $Y_i \sim^{iid} p(y | \theta)$.

En el contexto de modelos iid, a la distribución común $p(y | \theta)$ se le llama _población_ y es el único elemento que hay que especificar para poder tener definido el modelo. Esto es así porque en este caso, y debido a la independencia entre las variables aleatorias, la distribución conjunta de la muestra (el modelo asumido) es

$$
p(y | \theta) = \prod_{i=1}^{n} p(y_i | \theta).
$$

De igual forma, la función de verosimilitud es

$$
L(\theta,y) = \prod_{i=1}^{n} p(y_i | \theta).
$$

Un ejemplo al que se acomoda un modelo iid es el siguiente, en el que vamos a profundizar en la idea de independencia condicional que está presente en la construcción de modelos estadísticos.

###### Ejemplo 5

>En un experimento que una astronauta llevó a cabo en la estación espacial internacional, se lanzaba en ciertas condiciones de gravedad 5 veces un dado anotando la puntuación en la cara superior en cada lanzamiento: $Y_1, \ldots, Y_5$. Lo particular del experimento es que el dado se escogió al azar de una caja que contenía 3 tipos de dados en iguales proporciones: dados de color rojo con 6 caras; dados de color azul con 8 caras y dados de color verde con 16 caras. Todos los dados tienen una numeración que va del 1 al número de caras. Consideremos el color del dado como una suerte de parámetro desconocido de mucha importancia para la investigación.

Llamemos $\theta$ al número de caras que tiene el dado que se lanzó. Por tanto, el espacio paramétrico es $\Theta = \{6,8,16\}$ para cada uno de los colores posibles. Ahora, si conociéramos el valor de $\theta$ (el tipo de dado con el que se realizó el experimento), entonces podríamos asumir que las observaciones son independientes tal y como asumimos cuando lanzamos una moneda consecutivas veces al aire o un dado estándar. Sin embargo, las variables aleatorias que conforman la muestra $Y_1, \ldots, Y_5$, no son marginalmente independientes. En efecto, es sencillo obtener que la probabilidad de que $Y_2 = 1$ condicional a $Y_1 = 15$ (en cuyo caso seguro que el dado es verde) es mucho más pequeña que la probabilidad de que $Y_2 = 1$ condicional a $Y_1 = 1$ (y que por tanto no podemos descartar ningún color de dado) y en consecuencia no son independientes ($Y_2$ depende del valor de $Y_1$).

Conocido el valor de $\theta$, la probabilidad de que $Y_i = y$ es

$$
p(y_i | \theta) = \frac{1}{\theta} \quad \text{si } y_i \in \{1,2,\ldots,\theta\},
$$

y cero en el resto. Como hemos argumentado, las $Y_i$ son condicionalmente independientes entre sí, por lo que es razonable utilizar el siguiente modelo iid:

$$
p(y_1,y_2,\ldots,y_5 | \theta) = \prod_{i=1}^{5} \frac{1}{\theta} \quad \text{si } y_i \in \{1,2,\ldots,\theta\}.
$$

La función de verosimilitud, que recordamos es una función de $\theta$ (vistos los valores que han sido observados para la muestra) y en este caso $\theta$ solo puede tomar tres valores, es:

$$
L(\theta | y_1,y_2,\ldots,y_5) = \frac{1}{\theta^5} \quad \text{si } y_i \in \{1,2,\ldots,\theta\},
$$

y cero en otro caso. Por tanto, para cada valor de $\theta$, la función de verosimilitud solo depende de si todos los $y_i$ están en $\{1,2,\ldots,\theta\}$ o no:

$$
L(\theta = 6 | \text{algún } y_i > 6) = 0, \quad L(\theta = 6 | \text{todos los } y_i \leq 6) = \frac{1}{6^5}.
$$

De igual forma para:

$$
L(\theta = 8 | \text{algún } y_i > 8) = 0, \quad L(\theta = 8 | \text{todos los } y_i \leq 8) = \frac{1}{8^5}.
$$

y por último

$$
L(\theta = 16) = \frac{1}{16^5}.
$$

En la Figura [2]() hemos representado la función de verosimilitud para $\theta$ en este ejemplo para las distintas situaciones de valores observados de $y$.

En el ejemplo anterior hemos incidido en la importante noción de independencia condicional, pero la forma matemática del modelo es poco convencional. Vamos ahora a estudiar una situación más usual y la construcción de un posible modelo.

> _
> ###### Figura 2  
> Referida al ejemplo 5 sobre el lanzamiento de un dado en la estación espacial internacional. Función de verosimilitud para $\theta$ (número de caras en el dado) para cada uno de los posibles escenarios de nuestra observada. En el gráfico a) todas las $y_i$ $\leq 6$ (en cuyo caso la más verosímil es $\theta = 6$); en b) todas las observaciones $y_i$ $\leq 8$ y alguna $y_i > 6$ (en cuyo caso la observación es mayor que $8$ (en cuyo caso el único valor verosímil para $\theta$ es $16$). En todos los casos la función de verosimilitud en $\theta = 16$ es muy pequeña $(16^{-5})$, pero mayor que cero
>
>
>![](../img/4.png)
>_

---

> ###### Ejemplo 6
>
>Hacemos una encuesta a $n$ individuos y a cada individuo $i$ le preguntamos si estaría interesado en invertir en una emisión de letras del tesoro. Anotaremos $Y_i = 1$ en caso afirmativo y $Y_i = 0$ si no están interesados en este fondo.
>

Para este ejemplo, llamemos $\pi$ a la proporción poblacional de personas interesadas en invertir en este tipo de activos. Es razonable asumir que las respuestas $Y_i$ de los encuestados son, condicional a que se conoce $\pi$, independientes entre sí (algo que depende del proceso de toma de reclutamiento). Además, por el rango de los valores de $Y_i$ que es $\{0,1\}$, debemos asumir que su función de masa corresponde a la de una distribución Bernoulli con probabilidad de éxito $\pi$.

Esto es, $Y_i \mid \pi \sim \text{id} bern(\pi)$ por lo que un modelo que podemos asumir es

$$
p(y \mid \pi) = \prod_{i=1}^{n} p(y_i \mid \pi) = \prod_{i=1}^{n} bern(y_i \mid \pi) = \prod_{i=1}^{n} \pi^{y_i} (1-\pi)^{1-y_i}.
$$

En este caso, solo hay un parámetro desconocido $\pi$ que representa la magnitud desconocida "proporción de inversores compradores de las letras del tesoro" que además es la magnitud de mayor interés en este problema. El espacio paramétrico de $\pi$ es aquí $[0,1]$. La función de masa conjunta anterior define la verosimilitud Bernoulli:

$$
L(y,\pi) = \prod_{i=1}^{n} \pi^{y_i} (1-\pi)^{1-y_i} = \pi^{\sum_{i=1}^{n} y_i} (1-\pi)^{n-\sum_{i=1}^{n} y_i},
$$

a la que dedicaremos parte del tema siguiente. En la Figura 3 hemos representado esta función para dos muestras observadas.

> _
> ###### Figura 3
> Referido al ejemplo 6 sobre encuestas, la función de verosimilitud para $\pi$. En el gráfico a) para una muestra con $n = 32$ y $\sum_{i=1}^{n} y_i = 24$; en b) la muestra era de $n = 100$ y $\sum_{i=1}^{n} y_i = 75$. En ambos casos la proporción observada de éxito es la misma (0.75) pero en el caso b) la función de verosimilitud es más apuntada por tener más información. Nótese que la función de verosimilitud no es una función de densidad y por lo tanto no tiene porqué integrar 1
> ![](../img/5.png)
> _


Es importante observar que no se asume independencia entre las variables aleatorias sino independencia condicional, conocido el valor de la magnitud $\pi$. En el caso de las encuestas, es fácil advertir que si observáramos $Y_1 = 1, Y_2 = 1, \ldots, Y_{100} = 1$ es bastante probable que $Y_{101}$ sea también 1, y por lo tanto estas variables aleatorias (marginalmente) no son independientes. Lo que decimos con el modelo propuesto es que si conocemos cuál es la probabilidad de que $Y_i = 1$, entonces son independientes puesto que la información que comparten y que las hace dependientes (la probabilidad de éxito) ya es conocida. En este ejemplo, $\pi$ tiene un papel parecido al color del dado en el ejemplo de la estación espacial.

Aunque hay que tener presente la idea de independencia condicional, en adelante entenderemos que en la construcción de modelos esta (cuando se da) es condicional a los valores de los parámetros y hablaremos simplemente de independencia (para hacer más sencillo el lenguaje). De esta forma, en el ejemplo de las encuestas es habitual hablar de independencia entre las Yi aunque sobreentendemos que se trata de independencia condicional a los parámetros ($\pi$ en este caso). Utilizaremos esta forma de hablar en lo que sigue, siempre que no haya posibilidad de confusión.

