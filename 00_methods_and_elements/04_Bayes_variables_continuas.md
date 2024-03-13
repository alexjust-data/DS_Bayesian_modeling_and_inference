### 1.3. Teorema de Bayes en variables aleatorias continuas

En variables aleatorias continuas, la función de densidad condicional para $X$ dado que $Y = y$ se denota $p_{X|Y}(x | Y = y)$ (el subíndice indica cuál es la variable aleatoria, en este caso $X$, pero si el contexto lo deja claro, a veces se elimina). Mediante integración, esta función puede utilizarse para calcular probabilidades condicionales, de tal forma que:

$$
P(X \in A | Y = y) = \int_{A} p_{X|Y}(x | Y = y) \, dx.
$$

El teorema de Bayes en su versión continua establece una fórmula para la distribución condicional:

$$
p_{X|Y}(x | Y = y) = \frac{p_{X,Y}(x, y)}{p_{Y}(y)} = \frac{p_{Y|X}(y | X = x)p_{X}(x)}{p_{Y}(y)}
$$

Si el rango de la variable aleatoria $X$ es el intervalo $R \subseteq \mathbb{R}$, entonces la fórmula anterior puede escribirse como:

$$
p_{X|Y}(x | Y = y) = \frac{p_{Y|X}(y | X = x)p_{X}(x)}{\int_{R} p_{Y|X}(y | X = x')p_{X}(x') \, dx'}
$$

Como ya hemos comentado, en muchas ocasiones no hay posibilidad de confusión y la notación puede simplificarse considerablemente obviando los subíndices y las variables que tienen asignado un valor. En notación simplificada, la regla de Bayes queda:

$$
p(x | y) = \frac{p(y | x)p(x)}{\int_{R} p(y | x')p(x') \, dx'}.
$$

Veamos ahora un ejemplo del uso del teorema de Bayes en variables aleatorias continuas.


### Ejemplo 3

Un grupo de biólogos y biólogas marinos está estudiando las características de reproducción de una especie de pez que vive en la zona abisal del océano. El tiempo hasta la eclosión en una puesta de estos peces depende de la concentración media de sal, $\theta$ (medida en gramos de sal por centilitro de agua), en esa parte del océano. En concreto, se establece que pasadas 24 h de la puesta, el tiempo (en horas) $Y$ hasta que eclosionan los huevos es una variable aleatoria cuya distribución condicionada a $\theta$ es una exponencial de media $1/\theta$:

$$
p(Y | \theta) = \theta e^{-\theta Y}, \quad Y > 0.
$$

Equivalentemente

$$
Y | \theta \sim \text{exp}(\theta).
$$

> ¿Porqué una variable aleatoria con una distribución exponencial condicionada?. [Link](04_exponencial.md)

En la actualidad, este proyecto de investigación se centra en una zona del océano Atlántico donde la concentración media de sal $\theta$ es $[0.3,0.4]$ (que define el espacio paramétrico $\Theta$ asociado a este parámetro). Se desconoce el valor exacto de este parámetro pero estudios anteriores sugieren la siguiente distribución sobre $\theta$ :

#### 

$$
p(\theta) = \frac{1}{C_1 \theta}, \quad \theta \in [0.3,0.4] \tag{3}
$$

con $C_1 = \log(4/3)$ (que es la constante de proporcionalidad de esta función de densidad).

De particular interés científico es cuantificar la probabilidad de que la concentración salina esté entre los valores 0.33 y 0.37, que es el intervalo de salinidad media en profundidades no abisales en el océano. Sobre la base de la cuantificación establecida de los posibles valores de $\theta$ según $p(\theta)$ están probabilidad es

$$
P(\theta \in [0.33,0.37]) = \int_{0.33}^{0.37} \frac{1}{C_1 \theta} d\theta = \frac{\log(0.37/0.33)}{\log(4/3)} \approx 0.40.
$$

Alternativamente, podríamos haber calculado numéricamente en R esta probabilidad usando el símil de sugestión que en el que primero definimos la función $p(\theta)$ en la ecuación 3 que aquí llamamos _prior_:


```r
prior <- function(theta){1/(theta*log(4/3))}

integrate(prior, lower=0.33, upper=0.37)
[1] 0.3976972 with absolute error <4.4e-15
```

Este grupo de investigación ha diseñado una expedición submarina para actualizar, para esta parte de la zona abisal, la información sobre $\theta$ derivada de avances de la colonia de huevos de estos peces. En una reciente inmersión se ha grabado el proceso de puesta y eclosión de una colonia de estos huevos, observando que $Y = 21.75$ (como $Y$ es el tiempo pasado las primeras 24 horas iniciales, entonces han transcurrido 24 + 21.75 horas hasta que han eclosionado los huevos).

¿Cuál es la probabilidad de que $\theta$ esté en $[0.33,0.37]$ condicional a la información muestral $Y = 21.75$? Para calcular esta probabilidad tenemos que integrar sobre la distribución condicional $p(Y | \theta)$, que en virtud de la ecuación $[2]$ es

<br>

$$
p(\theta | Y = 21.75) = \frac{p(21.75 | \theta)p(\theta)}{\int_{0.3}^{0.4} p(21.75 | \theta')p(\theta') d\theta'} = \frac{\theta e^{-21.75\theta} \frac{1}{C_1\theta}}{\int_{0.3}^{0.4} \theta' e^{-21.75\theta'} \frac{1}{C_1\theta'} d\theta'} = \frac{e^{-21.75\theta}}{\int_{0.3}^{0.4} e^{-21.75\theta'} d\theta'}, \quad \theta \in [0.3,0.4].
$$


<br>

La integral definida en la ecuación anterior es la constante de proporcionalidad (la segunda que nos aparece en el problema) de esta distribución condicional. Para simplificar la notación, llamemos $C_2$ a esta constante que la podemos obtener analíticamente aplicando la regla de Barrow:

<br>

$$
C_2 = \int_{0.3}^{0.4} e^{-21.75\theta'} d\theta' = \frac{1}{21.75} \left( e^{-21.75\cdot 0.3} - e^{-21.75\cdot 0.4} \right).
$$

<br>

Con todo esto, la probabilidad actualizada de $\theta$ en $[0.33,0.37]$ teniendo ahora en consideración la información muestral se obtiene como:

<br>

$$
P(\theta \in [0.33,0.37] | Y = 21.75) = \frac{\int_{0.33}^{0.37} p(Y = 21.75|\theta) d\theta}{C_2} = \frac{1}{C_2 \cdot 21.75} \left( e^{-21.75\cdot 0.33} - e^{-21.75\cdot 0.37} \right) \approx 0.34.
$$

<br>

> [4] Regla de Barrow : Establece que el cálculo de una integral definida se puede obtener como la diferencia de una función primitiva evaluada en los límites de integración.

Para evitar el cálculo de las integrales anteriores de forma analítica, en R podemos usar el siguiente código que resuelve las integrales numéricamente. En primera lugar definimos como *posterior* la función en la ecuación $[4]$ sin su constante de integración:

```r
Cposterior <- function(theta){exp(-21.75*theta)}
```

La constante de integración $C_2$ es por tanto la integral:

```r
C2 <- integrate(Cposterior, lower=0.3, upper=0.4)[[1]]
```

Por último, la probabilidad se obtiene como el cociente:

```r
integrate(Cposterior, lower=0.33, upper=0.37)[[1]]/C2
[1] 0.3413575
```

Por tanto, la observación $Y = 21.75$ rebaja la probabilidad de concentración salina equivalente a la de zonas no abisales de $0.40$ (antes de considerar la información experimental) a $0.34$ (condicional a la información experimental).



