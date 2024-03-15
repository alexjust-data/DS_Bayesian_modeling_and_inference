### Observaciones independientes, pero no idénticamente distribuidas

Consideremos ahora la siguiente situación:

>###### Ejemplo 7
>
>De las empresas S. A. que se han declarado en suspensión de pagos los últimos seis meses, observamos $Y_i$ días desde su constitución hasta la declaración de suspensión de pagos; observando también $X_{1i}$, capital inicial y $X_{2i}$ número medio de empleados en el periodo de estudio.

Sin información adicional que nos hiciera sospechar lo contrario, la hipótesis de independencia de los distintos $Y_i$ (entre las distintas empresas) es bastante razonable. Además, y quizás después de una transformación (logarítmica o raíz cuadrada) podemos suponer normalidad para $Y_i$. Sin embargo, la hipótesis de que se distribuyan igual no es adecuada ya que no debemos esperar que el tiempo de supervivencia de una empresa se comporte de la misma manera sin tener en cuenta variables explicativas como las medidas en $X_{1i}$ (capital inicial) o $X_{2i}$ (número medio de empleados). De hecho, es lógico pensar que estas variables incidirán de alguna forma en la variable de interés e incluso es posible que dicha relación sea uno de los objetivos del estudio. En esta situación una posibilidad es utilizar un modelo de regresión múltiple del tipo:

$$
Y_i = \alpha + \beta_{1}X_{1i} + \beta_{2}X_{2i} + \epsilon_{i},
$$

con $\epsilon_i \sim^{iid} \text{normal}(0, \sigma)$ y $X_{1i}, X_{2i}$ son los correspondientes valores observados de ambas variables en la empresa i. Esto implica que

$$
p(Y_i \mid \alpha, \beta_{1}, \beta_{2}, \sigma) = \text{normal}(Y_i \mid \alpha + \beta_{1}X_{1i} + \beta_{2}X_{2i}, \sigma)
$$

Además, por la independencia asumida entre las variables $Y_i$, la función de densidad conjunta se obtiene simplemente multiplicando:


$$
p(Y \mid \alpha, \beta_{1}, \beta_{2}, \sigma) = \prod_{i=1}^{n} \text{normal}(Y_i \mid \alpha + \beta_{1}X_{1i} + \beta_{2}X_{2i}, \sigma)
$$

$$
= \prod_{i=1}^{n} \frac{1}{\sqrt{2\pi} \sigma} \exp \left( -\frac{1}{2\sigma^2} (Y_i - (\alpha + \beta_{1}X_{1i} + \beta_{2}X_{2i}))^2 \right),
$$

y por tanto define la función de verosimilitud. En este caso, el modelo depende de 4 parámetros. El parámetro $\alpha$ se conoce como "intercepto" y puede interpretarse como el valor medio de $Y_i$ para empresas en las que $X_{1} = 0$ y $X_{2} = 0$. Los parámetros $\beta_{1}$ y $\beta_{2}$ establecen la pendiente del plano de regresión y en concreto $\beta_{1}$ es la variación en la media de $Y$ por cada unidad que aumentemos $X_{1}$ (y similarmente para $\beta_{2}$).

