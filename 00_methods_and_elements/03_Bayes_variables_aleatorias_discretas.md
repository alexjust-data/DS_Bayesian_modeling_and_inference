### 1.2 Teorema de Bayes en variables aleatorias discretas

En variables aleatorias discretas, la probabilidad condicional $p(X = x | Y = y)$ es la probabilidad de que $X$ valga $x$ sabiendo que $Y = y$. La función que retorna, para cada valor de $x$ en su rango, la probabilidad $p(X = x | Y = y)$ se llama `distribución condicional` de $X$ dado $Y = y$.

El teorema de Bayes establece que la probabilidad condicional puede calcularse como un sencillo cociente:

$$
p(X = x | Y = y) = \frac{p(X = x, Y = y)}{p(Y = y)} = \frac{p(Y = y | X = x)p(X = x)}{p(Y = y)}
$$

![](.../img/1.png)

Si el rango de $X$ es el conjunto $R \subseteq \mathbb{R}$ (R como subconjunto de los números reales), entonces:

$$
p(X = x | Y = y) = \frac{p(Y = y | X = x)p(X = x)}{\sum_{x' \in R}p(Y = y | X = x')p(X = x')}
$$


Vamos a ver todos estos elementos en un ejemplo que contiene los principales ingredientes en el aprendizaje bayesiano:


**Ejemplo 2**

En la industria aeronáutica, la chapa que forma el chasis de las naves se compone de una aleación de aluminio y litio. En gran medida, la resistencia de este material depende de las impurezas que se encuentran en la superficie de la chapa como consecuencia de defectos en el proceso de fabricación. Para conseguir la mayor fiabilidad, la maquinaria utilizada en la fabricación está sujeta a severos controles cuya frecuencia se establece entre 1 a 3 controles por mes.


Como consecuencia de lo anterior, el número de desperfectos `Y` por cada 10m2 de chapa fabricada es una variable aleatoria que depende de la frecuencia mensual de controles pautada. En concreto, se ha determinado que para una chapa fabricada con una frecuencia media de $\theta$ controles mensuales, la distribución condicional de $Y | \theta = \theta$ (lo que se denota simplemente Y | θ) es una `Poisson` de media $10/\theta$:


$$
P(Y = y | \theta) = p(y | \theta) = \text{Pois}(y | 10/\theta) = \frac{e^{-10/\theta} (10/\theta)^y}{y!}, \quad y \in \{0,1,2,\ldots\}
$$

De forma más compacta podemos escribir:

$$
Y | \theta \sim \text{Pois}(10/\theta)
$$

> La probabilidad de que la variable aleatoria $Y$ tome el valor $y$, dado el parámetro $\theta$, es igual a la función de masa de probabilidad de una distribución de Poisson con media $10/\theta$... [pero porqué Poisson](03_Poisson.md).


Recientemente ha llegado a un almacén un lote de material de chapa del que se desconoce su origen, por lo que no sabemos el número de controles que tuvo en el proceso de fabricación. No obstante, por la información histórica disponible del proveedor, se estima la probabilidad por cada valor posible de $y$ que hay recogida en la Tabla 1.


| $\theta$ | p($\theta$) |
|------------|--------------|
| 1          | 0.25         |
| 2          | 0.50         |
| 3          | 0.25         |

> ##### Tabla 1 
> Distribución de probabilidad sobre $\theta$, el número de inspecciones realizadas en el proceso de fabricación de la chapa muestreada

De este lote se ha inspeccionado una muestra de chapa de $10 m^2$ encontrando $Y = 5$ desperfectos. Se quiere saber cuál es la probabilidad de que $\theta = 1$ (de que esta chapa haya pasado por un proceso de fabricación con un control mensual) condicionado a la información disponible. En forma compacta, la probabilidad que se quiere determinar es $p(\theta = 1 | Y = 5)$.

- $\theta = 1$: Este es el parámetro que representa el número de inspecciones realizadas en el proceso de fabricación de la chapa. Estamos interesados en la probabilidad de que haya habido una sola inspección.

- $Y = 5$: Corresponde al número de defectos encontrados durante la inspección de $10 m^2$ de chapa.

- $P(\theta = 1 | Y = 5)$: Es la probabilidad condicional que queremos calcular, es decir, la probabilidad de que se haya realizado una inspección ($ \theta = 1 $), dado que se encontraron 5 defectos.

- $P(Y = 5 | \theta = 1)$: Representa la probabilidad de encontrar 5 defectos si se sabe que hubo una inspección. Esta se calcula usando la distribución de Poisson con una tasa $\lambda = \frac{10}{\theta}$, que para $\theta = 1$ es $\lambda = 10$.

- $P(\theta = 1)$: Es la probabilidad a priori de que se haya realizado una inspección, la cual se proporciona en la tabla de distribución de probabilidad como 0.25 para $\theta = 1$.


La notación $\text{Pois}(5 | \lambda)$ se refiere a la función de masa de probabilidad de la distribución de Poisson con media $\lambda$ evaluada en 5 defectos encontrados.


Aplicando el teorema de Bayes en la forma de la ecuación (1) se puede calcular.



Para calcular como:

$$
P(\theta = 1 | Y = 5) = \frac{P(Y = 5 | \theta = 1)P(\theta = 1)}{C} = \frac{\text{Pois}(5 | \frac{10}{1})0.25}{C}
$$

donde la constante $C$, que recibe el nombre de constante de proporcionalidad (la constante que hace que una función de probabilidad sume o integre 1) es

$$
C = P(Y = 5 | \theta = 1)P(\theta = 1) + P(Y = 5 | \theta = 2)P(\theta = 2) + P(Y = 5 | \theta = 3)P(\theta = 3)
$$

$$
= \text{Pois}(5 | \frac{10}{1})0.25 + \text{Pois}(5 | \frac{10}{2})0.5 + \text{Pois}(5 | \frac{10}{3})0.25
$$

donde $\text{Pois}(y | \lambda)$ es la función de masa de una distribución Poisson de media $\lambda$ evaluada en $y$.


```r

C <- dpois(x=5, lambda=10/1)*0.25 + 
     dpois(x=5, lambda=10/2)*0.5 + 
     dpois(x=5, lambda=10/3)*0.25

```

y ahora la probabilidad $P(\theta = 1 | Y = 5)$ se obtiene como:

```r
dpois(x=5, lambda=10/1)*0.25/C
[1] 0.07402225
```

Por tanto, $P(\theta = 1 | Y = 5)  = 0.07$. La información muestral ha permitido actualizar la valoración inicial de $P(θ = 1)$, disminuyendo esta probabilidad sustancialmente: hemos pasado de $0.25$ a $0.07$.

>En el contexto del aprendizaje bayesiano, este es un proceso de actualización de creencias o probabilidades a priori con nueva evidencia. Inicialmente, sin considerar la cantidad de defectos encontrados, se estimó que la probabilidad de que hubiera solo una inspección era del 25% (es decir, $P(\theta = 1 = 0.25))$
>
>Sin embargo, una vez que se incorpora la evidencia de los 5 defectos y se aplica el teorema de Bayes utilizando la distribución de Poisson como modelo de probabilidad de defectos, esta probabilidad se ha revisado a la baja, hasta el 7%. Esto significa que, basándose en la observación de los defectos, es menos probable que la chapa solo haya pasado por una inspección de lo que se pensaba inicialmente.



De forma semejante, en el ejemplo anterior podemos calcular la probabilidad condicional para $\theta$ para cada valor en su rango, en este caso $\{1,2,3\}$ (como $\theta$ es un parámetro, a este conjunto de valores que puede tomar se le llama espacio paramétrico, normalmente simbolizado con la letra griega mayúscula $\theta$). En este caso, lo que obtenemos es la distribución condicional recogida en la Tabla 2.

Tabla 2 Distribución de probabilidad sobre $\theta$, el número de inspecciones realizadas en el proceso de fabricación de la chapa muestreada, condicional a que $Y = 5$


| $\theta$   | $p(\theta \| Y = 5)$ |
|--------------|-----------------------|
| 1            | 0.07                  |
| 2            | 0.69                  |
| 3            | 0.24                  |

> ##### Tabla 2
> Distribución de probabilidad sobre θ, el número de inspecciones realizadas en el proceso de fabricación de la chapa muestreada, condicional a que Y = 5
> 

Notad que $\theta$ no es una variable aleatoria (tiene un valor constante) y la distribución que le asignamos en la Tabla 1 corresponde a una cuantificación personal de lo posible de cada uno de los valores.
