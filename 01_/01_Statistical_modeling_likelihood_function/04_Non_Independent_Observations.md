### Observaciones no independientes

En los modelos que hemos construido hasta ahora, hemos utilizado la hipótesis de independencia (condicional). No obstante, este supuesto no siempre es razonable y existen situaciones en las que hay que incorporar a la especificación del modelo herramientas que incorporen la naturaleza de dependencia. Esto ocurre en la siguiente situación.


> ###### Ejemplo 8
>Observamos las temperaturas en una zona del Ártico entre el periodo 2-11-2020 al 15- 12-2020 (que es el intervalo de tiempo que dura nuestra expedición) recogiendo la temperatura diaria $Y_i$ a las 12 h.

Analicemos ahora el problema del estudio de las temperaturas en el Ártico del ejemplo [8️]().  
Siguiendo con la estrategia anterior. Un posible modelo es $Y_i \sim \text{normal}(\mu, \sigma)$ por lo que la distribución conjunta de la muestra sería

$$p(y \mid \mu, \sigma) = \prod_{i=1}^{n} p(Y_i \mid \mu, \sigma) = \prod_{i=1}^{n} \text{normal}(Y_i \mid \mu, \sigma)$$
$$= \prod_{i=1}^{n} \frac{1}{\sqrt{2\pi} \sigma} \exp \left( -\frac{1}{2\sigma^2} (Y_i - \mu)^2 \right),$$

lo que nos da un modelo de dos parámetros $(\mu, \sigma)$ cuyo espacio paramétrico conjunto es $\Theta = \mathbb{R} \times \mathbb{R}^+$. De estas magnitudes, el parámetro $\mu$ es nuestro parámetro de mayor interés (ya que contiene la magnitud "temperatura media") mientras que $\sigma$ es necesario para dar flexibilidad y un concreto rango las variaciones en las observaciones de la temperatura respecto de su valor medio $\mu$. Aunque la anterior propuesta de modelo es sin duda razonable, sin embargo la hipótesis de independencia entre las variables es cuestionable. Si un día en concreto la temperatura es, por ejemplo, muy baja debemos de esperar razonablemente que el día siguiente también lo sea. Una alternativa muy diferente al modelo anterior es asumir que $Y \sim \text{normal}(\mu, \Sigma)$ donde $\mu \in \mathbb{R}^n$ y $\Sigma$ es una matriz simétrica de orden $n \times n$ definida positiva, ambas desconocidas. Esta posibilidad incluye todas las posibles relaciones entre las variables, pero está completamente desaconsejado porque está extremadamente parametrizado (tantos parámetros como elementos tiene $\mu$ y $\Sigma$).


En medio de ambas posibilidades están los modelos de series temporales muy usados en econometría. Estos introducen dependencia (lineal) entre observaciones y hacen uso de la noción de iid para modelar los errores o innovaciones. Uno de estos es el modelo conocido como autorregresivo de orden 1 que se presenta como

###### 6

$$ Y_i = \mu + \phi Y_{i-1} + \epsilon_{i}, \quad i = 1,2,...,n$$

con $\epsilon_i \sim \text{normal}(0, \sigma)$. Con este modelo, cada temperatura está basada en la temperatura del día anterior. El número de parámetros en este modelo es razonablemente pequeño: $\mu$ para el valor medio sobre el que oscilan las temperaturas en ese periodo del año; $\phi$ para inducir dependencia entre observaciones y $\sigma$, como anteriormente, para posibilitar variaciones en las observaciones respecto al valor medio. En este caso, la distribución conjunta de $ Y $ no puede obtenerse con la fórmula del modelo id porque las observaciones no son independientes. La ecuación 6 nos define la distribución de $ Y_i $, condicional a $ Y_{i-1} = 0 $ (y $\mu$ y $\phi$ en concreto establece la distribución de $ Y_i $).

###### 7

$$ Y_i \mid Y_{i-1} = y_{i-1},\mu,\phi \sim \text{normal}(\mu + \phi y_{i-1},\sigma) $$

La forma de obtener esta distribución conjunta es utilizando repetidamente la regla de la multiplicación. En concreto esta regla permite obtener la probabilidad de una intersección a partir de las condicionales de una forma muy concreta:

$$ p(y \mid \theta) = p(y_1,\dots,y_n \mid \theta)$$
$$ = p(y_1 \mid \theta)p(y_2 \mid y_1,\theta)\dots p(y_n \mid y_{n-1},\theta)$$

En el problema de las temperaturas árticas, y como consecuencia de la ecuación [7️]()

$$ p(y_i \mid y_{i-1},...,y_1,\mu,\phi,\sigma) = \text{normal}(y_i \mid \mu + \phi y_{i-1},\sigma),$$

por lo que la distribución conjunta queda:

$$ p(y \mid \mu,\phi,\sigma) = \prod_{i=1}^{n} \text{normal}(y_i \mid \mu + \phi y_{i-1},\sigma)$$
$$ = \prod_{i=1}^{n} \frac{1}{\sqrt{2\pi}\sigma} \exp \left( -\frac{1}{2\sigma^2}(y_i - (\mu + \phi y_{i-1}))^2 \right),$$

definiendo un posible modelo que incorpora la posibilidad de dependencia entre observaciones. La anterior función define la función de verosimilitud:

$$ L(\mu,\phi,\sigma \mid y) = \prod_{i=1}^{n} \text{normal}(y_i \mid \mu + \phi y_{i-1},\sigma)$$
$$ = \prod_{i=1}^{n} \frac{1}{\sqrt{2\pi}\sigma} \exp \left( -\frac{1}{2\sigma^2}(y_i - (\mu + \phi y_{i-1}))^2 \right),$$

La función de verosimilitud es una función de tres parámetros de $\mu, \phi$ y $\sigma$ y es posiblemente más compleja de analizar que un uso de varianza fija, lo que se comentará en el siguiente apartado. No obstante, la posibilidad de incluir un término de autorregresión es interesante desde un punto de vista científico, y $ \phi $ dan credibilidad para poder modelar la forma en la que ocurren las observaciones.

Para acabar este apartado, recalcamos que de lo adecuado del modelo escogido, depende en mucha medida la bondad de las inferencias que se obtengan.

Se han desarrollado multitud de técnicas para validar modelos pero a veces un simple histograma es muy revelador sobre la adecuación de un modelo u otro. Por último, existen transformaciones de las variables que ayudan a acomodar un modelo concreto. Las más populares son las transformaciones de Box-Cox que contemplan como caso particular la transformación logarítmica.