## Verosimilitud normal

#### Uso

La distribución normal es una de las más conocidas dentro de la modelización estadística. Además, el hecho de que la observemos de manera natural en muchas variables relacionadas con la naturaleza, así como sus propiedades matemáticas, hacen que sea una de las más utilizadas a la hora de modelizar variables continuas.

#### Verosimilitud y parámetro de interés

Decimos que una variable aleatoria $Y$ es normal de media $\mu$ y desviación estándar $\sigma$ y lo denotamos por:

$$(Y | \mu,\sigma) \sim \text{normal}(\mu,\sigma)$$

si su densidad tiene la forma siguiente:∫

$$p(Y | \mu,\sigma) = \frac{1}{\sigma\sqrt{2\pi}} e^{-\frac{(y-\mu)^2}{2\sigma^2}}$$

Es importante señalar que, al contrario de lo que pasaba con algunas de las distribuciones estudiadas, los parámetros que aparecen en esta función de densidad son exactamente $\mu = E(Y)$ y $\sigma^2 = Var(Y)$ para la variable aleatoria $Y$.

Después de obtener $N$ observaciones independientes de esta distribución y = $(y_1, y_2, \ldots, y_N)$ podemos expresar la verosimilitud correspondiente como:

\[ L(\mu, \sigma, y) = \prod_{i=1}^{N} \frac{1}{\sigma \sqrt{2\pi}} e^{-\frac{(y_i-\mu)^2}{2\sigma^2}} \]

\[ = \left( \frac{1}{\sigma \sqrt{2\pi}} \right)^N e^{-\frac{1}{2\sigma^2}\sum_{i=1}^{N}(y_i-\mu)^2} \] (4)

Es importante notar que en esta verosimilitud existen dos parámetros que pueden ser desconocidos. A continuación vamos a trabajar con los casos en los que solo uno de ellos lo es, mientras suponemos que conocemos el valor del otro. Reservamos para los videos disponibles en el aula virtual el caso en que ambos parámetros son desconocidos.

#### Previa conjugada para $\mu$ desconocida y $\sigma$ conocida

Como ya hemos hecho en los casos anteriores, a la hora de establecer la distribución a priori de manera conjugada es importante fijarse en la forma funcional de la verosimilitud con respecto al parámetro de interés. Si observamos (4), podemos ver que la parte que aparece etiquetada como $A$ únicamente depende de $\mu$, por lo que podemos considerarla constante si este parámetro es conocido. La verosimilitud para $\mu$ nos quedará entonces como:

\[ L(\mu, y, \sigma) \propto e^{-\frac{1}{2\sigma^2}\sum_{i=1}^{N}(y_i-\mu)^2} \].

Expresada de esta forma es fácil ver que tiene la forma de una normal sobre $\mu$ y, por tanto, tiene sentido considerar una distribución de este tipo como previa. En concreto, estableceremos $\mu \sim \text{normal}(\mu_0, \sigma_0)$.

#### Distribución a posteriori para $\mu$

Al combinar una distribución previa normal para $\mu$ con la verosimilitud en (4) mediante el teorema de Bayes, obtenemos una distribución posterior normal:

$$\mu | y \sim \text{normal}(\mu_N, \sigma_N)$$

donde

- $\sigma_N^2 = \sigma^2 / (\sigma^2/\sigma_0^2 + N)$
- $\mu_N = (\mu_0/\sigma_0^2 + \sum y_i/\sigma^2) / (\sigma^2/\sigma_0^2 + N)$

#### Previa conjugada para $\sigma$ conocida y $\mu$ desconocida

Cuando $\mu$ es conocida y $\sigma$ es desconocida, debemos fijarnos en la forma funcional de (4) para poder establecer cuál sería la previa conjugada en este caso. A simple vista no es obvio cuál debería ser esta distribución, pues en la verosimilitud $\sigma$ aparece todo el tiempo como $A$. Sin embargo, si pensamos en esa expresión como variable en función de la cual expresamos la verosimilitud, entonces sí que hay una distribución que tiene esa forma funcional. Se trata de la distribución $\chi^2$.

Diremos que una variable $Y$ tiene una distribución $\chi^2$ cuadrada con parámetro $\nu$ y lo denotaremos por $Y \sim \chi^2(\nu)$ si su función de densidad puede expresarse como:

\[ p(y | \nu) = \frac{2^{-\nu/2}}{\Gamma(\nu/2)} y^{\nu/2-1} e^{-y/2}, y > 0. \]

Al parámetro $\nu$ se le denomina grados de libertad, y su relación con la media y la varianza de la distribución es:

- $E(Y) = \nu$
- $Var(Y) = 2\nu$

Volviendo a la distribución previa para $\sigma$, elegiremos $p(\sigma^2)$, de forma que:

\[ p(\sigma^2) \sim \chi^2(\ell), \]

siendo $\alpha$ y $\beta$ los parámetros a priori.

#### Distribución a posteriori para $\sigma$

Utilizando el teorema de Bayes para la verosimilitud normal con media conocida y varianza desconocida y una distribución previa de la forma (5), obtenemos una distribución a posteriori para $\sigma^2$ de la forma siguiente:

\[ \sigma^2 | N,y \sim \chi^2(\alpha + N,\beta + s), \]

donde $N$ es el número de observaciones y $s$ es su variabilidad.

#### Previa conjugada conjunta para $\mu$ y $\sigma$ desconocidas

Este caso lo estudiamos en profundidad en los tres videos correspondientes a este tema que tenéis disponibles en el aula virtual.
