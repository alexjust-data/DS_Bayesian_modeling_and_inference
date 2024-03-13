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

En la actualidad, este proyecto de investigación se centra en una zona del océano Atlántico donde la concentración media de sal $\theta$ es $[0.3,0.4]$ (que define el espacio paramétrico $\Theta$ asociado a este parámetro). Se desconoce el valor exacto de este parámetro pero estudios anteriores sugieren la siguiente distribución sobre $\theta$ :

$$
p(\theta) = \frac{1}{C_1 \theta}, \quad \theta \in [0.3,0.4] \tag{3}
$$

con $C_1 = \log(4/3)$ (que es la constante de proporcionalidad de esta función de densidad).

De particular interés científico es cuantificar la probabilidad de que la concentración salina esté
