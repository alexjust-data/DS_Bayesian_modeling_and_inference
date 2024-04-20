## Simulación en R

El programa R está armado con una potente batería para trabajar con la gran mayoría de las distribuciones de probabilidad de variables aleatorias discretas y continuas conocidas. En concreto R incorpora procedimientos de simula- ción de variables con formas conocidas evitándonos en muchos casos la nece- sidad de programar explícitamente el método de Montecarlo.

En R cada distribución tiene una etiqueta que la identifica. Por ejemplo, ya hemos visto al principio del tema que beta es la terminología interna en R para denotar la distribución Beta. En la Tabla 3 hemos recogido las etiquetas usadas para las distribuciones más habituales.

> ###### Tabla 3. 
> Etiquetas usadas en R para distinguir algunas de las distribuciones de variables aleatorias mas comunes. Usa, por ejemplo, help(dbinom) para acceder a la definición de los parámetros de los que depende la distribución binomial.


| Discretas              |        | Continuas        |        |
|------------------------|--------|------------------|--------|
| **Nombre**             | **Etiqueta** | **Nombre**       | **Etiqueta** |
| Binomial               | binom   | t-Student        | t      |
| Poisson                | pois    | Gamma            | gamma  |
| Geométrica             | geom    | Chi cuadrado     | chisq  |
| Binomial Negativa      | nbinom  | Exponencial      | exp    |
| Hipergeométrica        | hyper   | F-Snedecor       | f      |
|                        |         | Beta             | beta   |
|                        |         | Uniforme         | unif   |


Con lo anterior, la sintaxis de los comandos se confecciona añadiendo al principio de cada etiqueta una de las siguientes letras: d para la función de densidad; p para la función de distribución; q para percentiles y la que particularmente nos interesa en este punto $r$ para la generación de simulaciones de la variable aleatoria (utilizando el método de Montecarlo o algún otro método de simulación más adecuado para el caso). Anteriormente ya hemos utilizado `runif` para generar números aleatorios de una uniforme en $(0,1)$. Hay que acudir en ayuda de R para saber cómo se definen correctamente los parámetros de los que depende cada distribución. En la generación de simulaciones, el argumento n establece el tamaño de la simulación (lo que en el apartado anterior denotábamos por $N$).

A modo de ejemplo, si queremos una muestra simulada de tamaño $N = 100$ de una variable aleatoria binomial de parámetros $n = 20$ y probabilidad de éxito $p = 0.1$ escribimos:

```r
> simB<- rbinom(n=100, size=20, prob=0.1)
```

Hemos introducido la simulación en el objeto simB, que es un vector con 100 posiciones:

```r
> length(simB)
[1] 100

> simB[1:5]
[1] 1 2 2 0 4
```

Una forma adecuada de representar esta muestra, que corresponde a una variable aleatoria discreta, es:

```r
> barplot(table(simB))
```

Un último comando que queremos destacar para la simulación en R es sample, que simula la extracción de una muestra con o sin reemplazamiento (dependiendo de cómo definamos el argumento `replace`) de una variable aleatoria que puede tomar valores en el conjunto dado por el argumento $x$. Un caso muy sencillo sería simular $N = 10$ lanzamientos de un dado, lo que podemos conseguir ejecutando:

```r
> sample(x=1:6, size=10, replace=TRUE)
[1] 5 4 2 4 2 3 3 5 4 5
```

Con estos comandos, y utilizando el principio visto en la sección anterior del uso de la simulación para aproximar aspectos descriptivos de una distribución, vamos a rescatar el ejemplo 4 de la página 14. Allí obtuvimos que la distribución _a posteriori_ de $\mu$ en el caso de una observación $Y$ y de un modelo normal con desviación típica conocida (0.01) y suponiendo una distribución _a priori_ sobre $\mu$ también normal es:

$$
p(\mu | y) = \text{normal} \left( \mu \middle| A, \frac{1}{B^2} \right) = \text{normal} \left( \mu \middle| \frac{\frac{y}{0.01^2} + \frac{\mu_y}{\sigma_y^2}}{\frac{1}{0.01^2} + \frac{1}{\sigma_y^2}}, \frac{0.01 \cdot \sigma_y}{\sqrt{\frac{1}{0.01^2} + \frac{1}{\sigma_y^2}}} \right)
$$


Aquí $A$ y $B$ dependen de $y$, y de la media y varianza _a priori_ de $\mu$: $\mu_y$ y $\sigma_y^2$ según la ecuación 5.

Vamos a simular de esta distribución para aproximar características de la distribución _a posteriori_ (más allá de la media y varianza _a posteriori_ que, como ya vimos, tienen una forma muy sencilla). Como en el gráfico a) de la Figura 1 vamos a suponer que $y = 0.15$, $\mu_y = 0.1$ y $\sigma_y = 0.025$. Guardamos la simulación (de tamaño $N = 10000$) en un vector que llamamos `mu.sim`:


```r
> Mmu<- 0.1; Smu<- 0.025; sigmaY <- 0.01; y<- 0.15 
> A<- y/sigmaYˆ2 + Mmu/Smuˆ2
> B<- 1/sigmaYˆ2 + 1/Smuˆ2
> mu.sim<- rnorm(n=10000, mean=A/B, sd=1/sqrt(B))
```

Ahora, cualquier característica muestral que obtengamos de la simulación `mu.sim` es una aproximación numérica a su correspondiente característica matemática. De esta forma, `mean(mu.sim)` es una aproximación de la media _a posteriori_ de $\mu$ y `sd(mu.sim)` lo es de la desviación típica _a posteriori_.

Como veremos con más detenimiento más adelante, un aspecto muy revelador de una distribución _a posteriori_ son los intervalos de probabilidad, es decir, intervalos en los que está el parámetro con una probabilidad prefijada $1 - \alpha$. Podemos obtener estos intervalos a partir de los percentiles de la muestra simulada: el percentil $\alpha/2$ deja esta proporción de valores simulados por abajo y el percentil $1 - \alpha/2$ deja esa proporción por arriba. Por tanto, estos percentiles contienen la deseada proporción $1 - \alpha$ y son aproximaciones numéricas al intervalo que deja esa probabilidad. Obtenemos este intervalo en R usando una probabilidad de $1 - \alpha = 0.95$:

```r
> quantile(mu.sim, probs=c(0.025, 0.975))
2.5% 97.5% 
0.1249917 0.1612538
```

Por tanto, el intervalo $[0.13,0.16]$ contiene una probabilidad de $0.95$ al parámetro de interés $\mu$.