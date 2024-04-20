## Verosimilitud binomial, distribución previa beta

#### Uso

El procedimiento de aprendizaje con verosimilitud Bernoulli (binomial) y distribución previa tipo beta se utiliza cuando nuestra muestra consiste en observar el resultado de experimentos independientes donde la variable estudiada solo puede tomar dos valores. El ejemplo clásico es el resultado del lanzamiento de una moneda (cara/cruz), pero lo cierto es que esta situación se da de forma muy habitual siempre que queremos comprobar si algo sucede o no.

#### Verosimilitud y parámetro de interés

Cuando una variable sigue una distribución de Bernoulli la denotamos por:

$$ Y | \theta \sim \text{Bernoulli}(\theta) $$

y su función de probabilidad es:

$$ P(Y = 1 | \theta) = \theta \quad P(Y = 0 | \theta) = 1 - \theta $$

también expresada de forma compacta como:

$$ p(Y = y | \theta) = \theta^y(1 - \theta)^{1-y} $$

Podemos observar que $\theta$ es la probabilidad de que suceda el evento de interés. Esta será la cantidad de interés en el caso binomial-beta y su espacio paramétrico es el intervalo [0,1].

La media y la varianza de esta distribución se relacionan con $\theta$ como:

- $E(Y) = \theta$
- $Var(Y) = \theta(1 - \theta)$

En términos de la función de verosimilitud, cuando observamos una muestra aleatoria y = $(y_1, y_2, \ldots, y_N)$ de $N$ procesos Bernoulli independientes la verosimilitud tomará la forma:

$$ L(\theta; y) = \prod_{i=1}^{N} \theta^{y_i} (1 - \theta)^{1-y_i} = \theta^{\sum y_i}(1 - \theta)^{N - \sum y_i} $$ (1)

#### Previa conjugada

Si observamos con detenimiento la forma de la verosimilitud y cómo aparece en ella nuestro parámetro de interés $\theta$, observamos una estructura similar a la de la densidad de una distribución beta. Además, teniendo en cuenta que la distribución beta está definida justamente en el intervalo [0,1], es perfectamente razonable utilizar una previa de esta familia.

Concretamente, diremos que la distribución a priori conjugada para $\theta$ es una distribución beta:

$$ \theta | a,b \sim \text{beta}(a,b) $$

cuya función de densidad se expresa como:

$$ p(\theta | a,b) = \text{beta}(\theta | a,b) = \frac{\theta^{a-1}(1 - \theta)^{b-1}}{B(a,b)} $$

donde $a$ y $b$ son valores positivos y $B(a,b)$ es la función beta siguiente:

$$ B(a,b) = \int_{0}^{1} \theta^{a-1}(1 - \theta)^{b-1} d\theta $$

que actúa como constante normalizadora.

Los principales momentos de esta distribución y su relación con los parámetros $a$ y $b$ son:

- $E(\theta) = \frac{a}{a+b}$
- $Var(\theta) = \frac{ab}{(a+b)^2(a+b+1)}$

#### Distribución a posteriori

Pensad ahora que observamos $N$ realizaciones independientes de este proceso obteniendo el evento de interés en $r$ de ellas. Utilizando esta información (datos) actualizamos nuestra distribución previa mediante el teorema de Bayes.

El resultado será que, a posteriori, $\theta$ sigue, de nuevo, una distribución beta con parámetros `a + r` y `b + N - r`. Esto es:

$$ (\theta | N,r) \sim \text{beta}(a + r, b + N - r) $$

El hecho de haber utilizado una distribución previa con la misma estructura que la de la verosimilitud para $\theta$ da como resultado la obtención de una distribución posterior de la misma familia que la distribución previa para $\theta$ solo cambian los parámetros. Otra cosa interesante de esta distribución posterior es que, como podemos ver, los parámetros combinan la información previa (contenida en a y b) con la información contenida en los datos (N y r).