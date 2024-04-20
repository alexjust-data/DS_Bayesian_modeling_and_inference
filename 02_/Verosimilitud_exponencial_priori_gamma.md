## Verosimilitud exponencial distribución a priori gamma

#### Uso

La distribución exponencial suele utilizarse para modelizar el tiempo transcurrido entre dos eventos consecutivos. Una de las particularidades de la distribución exponencial es su falta de memoria. Esto es, la probabilidad de que el evento suceda en un tiempo $t + h$ dado que ya ha transcurrido un tiempo $h$ es exactamente la misma que la de que suceda en un tiempo $t$. Esto es:

$$P(T < t + h | T > h) = P(T < t)$$

#### Verosimilitud y parámetro de interés

Diremos que una variable aleatoria $T$ que toma valores en [0,∞) sigue una distribución exponencial de parámetro $\lambda > 0$ y lo denotamos como:

$$(T | \lambda) \sim \text{exponencial}(\lambda)$$

si su densidad tiene la forma siguiente:

$$P(T = t | \lambda) = \lambda e^{-\lambda t}$$

El parámetro $\lambda$ se relaciona con los principales momentos de esta distribución como:

- $E(T) = \frac{1}{\lambda}$
- $Var(T) = \frac{1}{\lambda^2}$

Cuando tenemos una serie de observaciones $t = (t_1,t_2,\ldots,t_N)$ independientes e idénticamente distribuidas exponencial(\(\lambda\)), la verosimilitud tomará la forma:

\[ L(\lambda,t) = \prod_{i=1}^{N} \lambda e^{-\lambda t_i} = \lambda^N e^{-\lambda \sum t_i} \] (3)

#### Previa conjugada

De nuevo, al observar la forma que tiene la verosimilitud con respecto al parámetro (similar a la de la densidad de la distribución de Poisson) tiene sentido utilizar una previa gamma(\(a,b\)) como la que habíamos utilizado en el caso de la verosimilitud de Poisson. Recordamos de nuevo que lo importante a la hora de elegir la previa para que esta sea conjugada es que la forma funcional de la densidad de la distribución previa para el parámetro coincida con la forma funcional de la verosimilitud para ese mismo parámetro.

#### Distribución a posteriori

Al aplicar el teorema de Bayes con la verosimilitud exponencial y la distribución gamma(\(a,b\)) como previa, obtenemos que, de nuevo, la distribución posterior pertenece a la familia gamma y sus parámetros pasan a ser (\(a + N,b + r\)), siendo \(N\) el número de observaciones y \(r\) la suma de los tiempos observados:

$$(\lambda) | N,r \sim \text{gamma}(a + N,b + r)$$