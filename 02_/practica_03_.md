

<div style="background-color: lightblue; color: black; padding: 10px;">

Apu Nahasapeemapetilon, el dueño del Badulaque en Springfield está cabreado, ya que algunos clientes se han quejado de que algunas galletas llegan a los hogares rotas, y todos sabemos que mal sienta coger una galleta del paquete y que se rompa en mil pedazos!. Él, como jefe de producción decidió hacer un estudio para saber cuántas galletas aproximadamente se rompen cada vez que se envasan. Para ello, se seleccionaron 10 paquetes al azar de 25 galletas cada uno, y se contó el número de galletas que se habían roto en el proceso de envasado. Los resultados fueron los siguientes:

> 0 3 4 2 4 1 1 3 4 3

Apu nos ha contratado a nosotros para intentar demostrar al proveedor que lo que está ocurriendo es una realidad y que en el proceso de envasado o de transporte algo está ocurriendo. ¡Ayudémosle!

> a. Determinemos en primer lugar la verosimilitud, ¿qué distribución utilizaríamos para modelizar la variable número de galletas rotas sobre un total?
>  * Utilizaríamos una verosimilitud Binomial
>  * Utilizaríamos una verosimilitud Gamma
>  * Utilizaríamos una verosimilitud Exponencial
>  * Utilizaríamos una verosimilitud Poisson

> b. No disponemos de ningún tipo de información previa sobre el parámetro de interés: proporción de galletas rotas. ¿Podrías indicar qué distribución previa utilizarías?
>  * La distribución a priori es una gamma(1,1)
>  * La distribución a priori es una beta(1,1)
>  * La distribución a priori es una gamma(0.5,0.5)
>  * La distribución a priori es una beta(3.435,4.345)

>c. Con esa distribución previa, ¿podrías calcular la probabilidad de que esa proporción sea menor que 0.37?

> d. Resulta que se nos había escapado un estudio que se hizo recientemente, donde la proporción de galletas rotas era de 0.16, pero no sabemos nada más. ¿Qué distribución a priori elegirías para expresar ese conocimiento previo?
>  * La distribución a priori es una gamma(4.221, 33.239)
>  * La distribución a priori es una gamma(8.442, 44.318)
>  * La distribución a priori es una beta(8.442, 44.318)
>  * La distribución a priori es una beta(8.223, 3.883)

> e. Con esta nueva distribución previa, ¿podrías calcular la probabilidad de que esa proporción sea menor que 0.37?

> f. En nuestro proceso de investigación seguimos avanzando, ya hemos elegido una distribución a priori para la proporción de galletas rotas, que será aquella que nos proporciona más información. Determina cuál es la distribución a posteriori para esa proporción.
>  * La distribución a posteriori es una gamma(0,5, 0,75)
>  * La distribución a posteriori es una beta(33.442, 269.318)
>  * La distribución a posteriori es una beta(38.442, 29.318)
>  * La distribución a posteriori es una gamma(1,5, 2,75)

> g. Calcula la probabilidad en base a la información que hemos obtenido (distribución a priori y datos) de que la proporción de galletas rotas sea mayor que 0.12.

</div>

<br>

Vamos a abordar cada punto:

**a.** Para modelizar el número de galletas rotas en cada paquete, podríamos asumir que cada galleta tiene una probabilidad independiente y constante de romperse durante el envasado. Esto se asemeja a una serie de ensayos de Bernoulli, por lo que una distribución apropiada para modelizar el número de éxitos (en este caso, galletas rotas) en una serie de ensayos independientes es la **distribución binomial**. 

La función de verosimilitud para la distribución binomial, dados los datos observados, estaría basada en el producto de las probabilidades de obtener exactamente el número de galletas rotas que observamos en cada paquete, dados los parámetros $n$ (número de ensayos, que en este caso serían 25 galletas por paquete) y $p$ (la probabilidad de que una galleta se rompa).

**b.** Cuando no disponemos de información previa sobre el parámetro de interés, una elección común es la distribución previa no informativa. Una opción sería utilizar una distribución Beta con parámetros \(\alpha = 1\) y \(\beta = 1\), que es equivalente a una distribución uniforme en el intervalo [0, 1]. Esta es una distribución previa no informativa porque asigna igual probabilidad a todas las proporciones de galletas rotas posibles.

**c.** Para calcular la probabilidad de que la proporción de galletas rotas sea menor que 0.37 con la distribución previa, necesitaríamos actualizar nuestra creencia a posteriori utilizando los datos observados. Esto se hace mediante el teorema de Bayes, que combina la verosimilitud y la distribución previa para obtener la distribución a posteriori.

Sin embargo, para calcular la probabilidad de que la proporción sea menor que 0.37, necesitaríamos llevar a cabo la inferencia bayesiana completa, actualizando la distribución Beta previa con los datos observados para obtener la distribución a posteriori Beta(1 + éxitos totales, 1 + fallos totales), donde los "éxitos" son las galletas rotas y los "fallos" las galletas intactas.

Sumando los datos que tenemos, hay un total de 25 galletas por paquete y 10 paquetes, lo que nos da un total de 250 galletas. El total de galletas rotas es 

$$0+3+4+2+4+1+1+3+4+3 = 25$$

Por lo tanto, nuestra distribución a posteriori sería 

$$\text{Beta}(1 + 25, 1 + (250 - 25))$$

$$\text{Beta}(26, 226)$$

Podemos calcular la probabilidad acumulada de que $p$ sea menor que 0.37 con la distribución a posteriori usando la función de distribución acumulativa (CDF) de la distribución Beta actualizada.

```r
# Establecer opciones para imprimir 3 decimales
options(digits=4)

# Parámetros de la distribución Beta a posteriori
alpha_posterior <- 1 + 25  # 1 + número de galletas rotas
beta_posterior <- 1 + (250 - 25)  # 1 + número de galletas no rotas

# Calculamos la probabilidad acumulada de que p sea menor que 0.37
probabilidad <- pbeta(0.37, alpha_posterior, beta_posterior)

# Mostramos el resultado
print(probabilidad)

# resultado
[1] 1
```

El resultado de 1 en R al ejecutar la función `pbeta(0.37, alpha_posterior, beta_posterior)` indicaría que la probabilidad de que la proporción de galletas rotas sea menor que 0.37 es casi segura bajo la distribución a posteriori Beta(26, 226). Esto puede parecer contraintuitivo a primera vista, pero recordemos que una distribución Beta con estos parámetros se inclinará fuertemente hacia valores más bajos de $\theta$, es decir, habrá una alta densidad de probabilidad acumulada antes de llegar a 0.37.

```r
# Secuencia de valores de theta
theta_values <- seq(0, 1, length.out = 1000)

# Densidad de la distribución Beta para los valores de theta
density_values <- dbeta(theta_values, alpha_posterior, beta_posterior)

# Crear un gráfico de la densidad
plot(theta_values, density_values, type='l', 
     main='Densidad de Beta(26, 226)', 
     xlab='theta', ylab='Densidad',
     xlim=c(0,0.5))

# Agregar una línea vertical en theta = 0.37
abline(v = 0.37, col = "red", lty = 2)
```
![](/img/16.png)

Dado que la densidad es muy baja después de $\theta=0.37$ y dado que la función de densidad acumulativa (CDF) de una distribución es la integral de la función de densidad hasta ese punto, si el valor de la CDF es cercano a 1 en $\theta=0.37$, significa que la mayor parte del área bajo la curva de la distribución Beta se encuentra antes de este punto. Esto concuerda con el resultado de `pbeta(0.37, alpha_posterior, beta_posterior)` siendo cercano a 1, indicando una alta probabilidad de que la proporción verdadera de galletas rotas sea menor que 0.37.


**d.** La respuesta correcta es la distribución $\text{Beta}(8.442, 44.318)$. 

La distribución Beta es la elección apropiada para modelar proporciones, ya que está definida en el intervalo [0,1] y es la previa conjugada para la verosimilitud binomial, que es la que utilizamos cuando tenemos datos que representan el número de éxitos y fallos.

Para determinar si los parámetros dados son correctos, necesitamos asegurarnos de que la media de la distribución Beta sea igual a la proporción previa conocida, que es 0.16 en este caso. La media de una distribución Beta se calcula como:

\[ \text{Media} = \frac{\alpha}{\alpha + \beta} \]

Para la distribución $\text{Beta}(8.442, 44.318)$, la media es:

\[ \text{Media} = \frac{8.442}{8.442 + 44.318} \approx 0.16 \]

Lo cual coincide con nuestro conocimiento previo de la proporción de galletas rotas. Por lo tanto, esta es la distribución previa adecuada para reflejar el conocimiento previo del 0.16.

El 0.16 es la media de la distribución a priori Beta que refleja nuestro conocimiento previo o creencia sobre la proporción de galletas rotas. Escogimos los parámetros $\alpha$ y $\beta$ de la distribución Beta de manera que la media fuera 0.16. En otras palabras, antes de considerar los nuevos datos, creemos que el 16% de las galletas se romperán. El 0.37, por otro lado, no es una media, sino un umbral que estamos utilizando para una pregunta específica: ¿Cuál es la probabilidad de que la proporción real de galletas rotas sea menor que 0.37? 

En contraste, las distribuciones Gamma proporcionadas no son apropiadas para este contexto, ya que la Gamma no es la previa conjugada para la verosimilitud binomial y se utiliza para modelar tasas o escalas de tiempo en lugar de proporciones.

**e.** Con esta nueva distribución previa, la probabilidad de que la proporción de galletas rotas sea menor que 0.37 es:

```r
# Parámetros de la distribución Beta a priori
alpha_prior <- 8.442
beta_prior <- 44.318

# Calculamos la probabilidad acumulada de que la proporción sea menor que 0.37
probabilidad_menor_037 <- pbeta(0.37, alpha_prior, beta_prior)

# Mostramos el resultado con 3 decimales usando formatC
probabilidad <- formatC(probabilidad_menor_037, format = "f", digits = 3)
print(probabilidad_)

# Resultado
[1] 1.000
```


**f.** Para calcular la distribución a posteriori, aplicaremos el teorema de Bayes actualizando nuestra distribución a priori con los datos observados. Tenemos la información de que 25 de las 250 galletas se rompieron. Además, hemos establecido una distribución a priori Beta con parámetros $\alpha = 8.442$ y $\beta = 44.318$, basada en el conocimiento previo de que la proporción esperada de galletas rotas es de 0.16.

La fórmula para la distribución a posteriori Beta, después de observar $r$ galletas rotas de $N$ total de galletas, partiendo de una distribución previa Beta(α, β) es Beta(α + r, β + N - r).

Dado que $r = 25$ y $N = 250$, los nuevos parámetros para la distribución a posteriori son:

- $\alpha_{posteriori} = \alpha + r = 8.442 + 25$
- $\beta_{posteriori} = \beta + N - r = 44.318 + 250 - 25$

Podemos calcular y actualizar los parámetros en R con el siguiente código:

```r
# Parámetros de la distribución Beta a priori basados en el conocimiento previo
alpha_prior <- 8.442
beta_prior <- 44.318

# Datos observados
galletas_rotas <- 25
total_galletas <- 250

# Actualizamos los parámetros para obtener la distribución Beta a posteriori
alpha_posterior <- alpha_prior + galletas_rotas
beta_posterior <- beta_prior + total_galletas - galletas_rotas

# Los parámetros a posteriori son:
print(alpha_posterior)
print(beta_posterior)

# resultado
[1] 33.442
[1] 269.318
```

**g.** Con los parámetros a posteriori $\alpha = 33.442$ y $\beta = 269.318$ para la distribución Beta, podemos calcular la probabilidad de que la proporción de galletas rotas sea mayor que 0.12. Utilizamos la complementariedad de la función de distribución acumulativa (CDF) de la distribución Beta para calcular esta probabilidad.

El código en R para realizar este cálculo es el siguiente:

```r
# Parámetros de la distribución Beta a posteriori obtenidos anteriormente
alpha_posterior <- 33.442
beta_posterior <- 269.318

# Calculamos la probabilidad de que la proporción sea mayor que 0.12
probabilidad_mayor_012 <- 1 - pbeta(0.12, alpha_posterior, beta_posterior)

# Mostramos el resultado
print(probabilidad_mayor_012)

# respuesta
[1] 0.286386
```

