## Verosimilitud de Poisson y previa gamma 

Habitualmente utilizamos la distribución de Poisson cuando nuestra variable de interés es el “número de”, es decir, cuando es un conteo de sucesos que puede verse como la suma de infinitas realizaciones independientes de tipo Bernoulli (variables 0/1) con probabilidad de ocurrencia muy baja. Algunos ejemplos podrían ser el número de mensajes de WhatsApp que recibes en una hora, el número de llamadas a una centralita en un día, el número de fallecidos por cáncer en un determinado municipio en un año, etc.

#### Verosimilitud y parámetro de interés

Cuando tenemos una variable con distribución de Poisson la denotamos por:

$$Y | \lambda \sim \text{Poisson}(\lambda)$$

donde $\lambda > 0$ y su función de probabilidad es:

$$ p(Y = y | \lambda) = \text{Poisson}(y | \lambda) = \frac{e^{-\lambda}\lambda^y}{y!}$$

siendo $\lambda > 0$.

El parámetro $\lambda$ se relaciona con los principales momentos de esta distribución como:

- $E(Y) = \lambda$
- $Var(Y) = \lambda$

Cuando observamos un muestra aleatoria y = $(y_1, y_2, \ldots, y_N)$ de $N$ variables Poisson independientes, la función de verosimilitud tomará la forma:

\[ L(\lambda; y) = \prod_{i=1}^{N} \frac{e^{-\lambda} \lambda^{y_i}}{y_i!} = e^{-N\lambda} \lambda^{\sum y_i} \prod_{i=1}^{N} \frac{1}{y_i!} \] (2)

#### Previa conjugada

Si nos fijamos en la forma en que aparece $\lambda$ en la función de verosimilitud: $e^{-N\lambda} \lambda^{\sum y_i}$, tiene sentido pensar en una distribución tipo gamma como previa. Esto es:

$$ (\lambda | a,b) \sim \text{gamma}(a,b)$$

con parámetros $a > 0$, conocido como el parámetro de forma (shape), y $b > 0$, conocido como la tasa (rate). En base a estos parámetros, la función de densidad de una gamma se define como:

$$ p(\lambda|a,b) = \text{gamma}(\lambda|a,b) = \frac{b^a}{\Gamma(a)} \lambda^{a-1} e^{-b\lambda}$$

siendo $\Gamma$ la función gamma:

\[ \Gamma(z) = \int_{0}^{\infty} t^{z-1} e^{-t} dt \]

también conocida por ser la generalización del factorial.

En el caso de la densidad de la distribución gamma, cabe mencionar que también se puede encontrar definida utilizando una transformación de estos parámetros, en concreto en función de $a$ y $s = 1/b$. A la acción de reescribir una función de densidad cambiando los parámetros por una función de estos se le llama reparametrización, y es importante saber qué parámetros estamos usando a la hora de incorporar información previa o a la hora de programar en uno u otro software.

En base a la parametrización elegida, los principales momentos de la distribución son:

- $E(\lambda) = \frac{a}{b}$
- $Var(\lambda) = \frac{a}{b^2}$

#### Distribución a posteriori

Pensad ahora que observamos $N$ realizaciones independientes de este proceso obteniendo un determinado valor $r = \sum_{i=1}^{N} y_i$. Utilizando esta información (datos) actualizamos nuestra distribución previa mediante el teorema de Bayes. El resultado será que, a posteriori, $\lambda$ sigue, de nuevo, una distribución gamma con parámetros $a + r$ y $b + N$. Esto es:

$$ (\lambda | N,r) \sim \text{gamma}(a + r, b + N)$$
