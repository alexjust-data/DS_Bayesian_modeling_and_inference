### distribución *a posteriori*, distribución *a priori*


En los dos ejemplos anteriores se han presentado los elementos básicos de la inferencia bayesiana. Por un lado tenemos los parámetros $\theta$ que representan las magnitudes desconocidas que son nuestro objeto de interés. En los ejemplos anteriores el parámetro de interés es unidimensional, pero en general será multidimensional. Además, veremos más adelante que también habrá parámetros en los que no estamos directamente interesados, pero cuya existencia tenemos que gestionar.


La información (mucha, poca o incluso ninguna) sobre estos parámetros antes de obtener información experimental está contenida en la función $p(\theta)$: la función de masa $p(\theta)$ en la Tabla [1](03_Bayes_variables_aleatorias_discretas.md#tabla-1) del ejemplo [2](03_Bayes_variables_aleatorias_discretas.md#ejemplo-2) y la función de densidad $p(\theta)$ en la ecuación [3](04_Bayes_variables_continuas.md#3). A estas distribuciones se las conoce como distribuciones a priori, destacando que esta asignación inicial se corresponde con la información sobre los parámetros desconocidos disponible sin tener en cuenta la información muestral.


Además tenemos un experimento que nos proporcionará conocimiento sobre $\theta$ por medio de la observación de Y. El vínculo entre ambas cantidades Y y $\theta$ está contenido en la distribución de probabilidad de Y condicionada a que sabemos el valor de $\theta: p(y | \theta)$. Esta distribución se corresponde con el modelo asumido para Y (Poisson en el ejemplo  [2](03_Bayes_variables_aleatorias_discretas.md#ejemplo-2) y exponencial en el ejemplo  [3](04_Bayes_variables_continuas.md#ejemplo-3)). Si vemos esta función como una función de los parámetros, obtenemos un elemento crucial en el ámbito de la estadística: la función de verosimilitud o *likelihood function* en inglés. Es bastante frecuente simbolizar esta función como $L(\theta,y)$. Más adelante indicaremos cómo asignar modelos y por tanto veremos la forma de las funciones de verosimilitud en situaciones concretas.



El aspecto particular del método bayesiano es actualizar la información sobre $\theta$ una vez conocidos los datos $y$ y por tanto sabemos el valor adoptado por la variable aleatoria $Y = y$ (en el ejemplo [2](03_Bayes_variables_aleatorias_discretas.md#ejemplo-2) observamos 5 desperfectos, $Y = 5$, mientras que en el ejemplo [3](04_Bayes_variables_continuas.md#3) observamos $Y = 21.75$). El objeto matemático que contiene esta actualización es la distribución condicional $p(\theta | y)$ que, como ya hemos visto, se obtiene en virtud del teorema de Bayes como:

$$
p(\theta | y) = \frac{p(y | \theta)p(\theta)}{p(y)}.
$$

A esta distribución condicional se le llama distribución _a posteriori_ y se corresponde con la actualización de la distribución para $\theta$ incluyendo la información en los datos. Las distribuciones _a posteriori_ de los ejemplos anteriores están en la Tabla [2](03_Bayes_variables_aleatorias_discretas.md#ejemplo-2) en el ejemplo [2](03_Bayes_variables_aleatorias_discretas.md#ejemplo-2) y en la ecuación [4](04_Bayes_variables_continuas.md#4) en el ejemplo [3](04_Bayes_variables_continuas.md#3).

En el mundo bayesiano es bastante común que, en las distribuciones sobre los parámetros, se emplee la letra griega $\pi$ y por tanto se escriba $\pi(\theta)$ (para la distribución _a priori_) y $\pi(\theta | y)$ (distribución _a posteriori_, condicional a $Y = y$). No obstante, aquí optaremos por la notación $p$, para ser consistentes con el resto de los materiales del curso.

Ya hemos visto que en el manejo de las distribuciones sobre los parámetros es bastante habitual encontrarnos con constantes de proporcionalidad. Las constantes de proporcionalidad están definidas por la obligación de la correspondiente distribución de probabilidad de integrar uno y por tanto su valor está implícitamente determinado por los factores que dependen de $\theta$. Esta observación permite avanzar en los cálculos sin especificar explícitamente su valor haciendo por tanto las matemáticas menos engorrosas. Esto se consigue introduciendo las funciones de probabilidad condicional es el símbolo $\propto$ de "proporcional a" con lo que el teorema de Bayes queda:

$$
p(\theta | y) \propto p(y | \theta)p(\theta),
$$

o introduciendo la noción de función de verosimilitud como:

$$
p(\theta | y) \propto L(\theta,y)p(\theta).
$$

En la anterior ecuación "la distribución _a posteriori_ es proporcional al producto de la verosimilitud y la distribución _a priori_" es, de alguna forma, la _piedra filosofal_ de la aproximación bayesiana.

Mantener los cálculos al nivel de "proporcional a" es incluso muy útil en la distribución _a priori_, ya que la constante de integración de la distribución _a priori_ "desaparece" en la distribución _a posteriori_. Quizás pasó desapercibido, pero ya hemos visto esta desaparición en el ejemplo [3](04_Bayes_variables_continuas.md#3) observa que en el hilo de ecuaciones en [4](04_Bayes_variables_continuas.md#4) la constante de proporcionalidad de la distribución _a priori_, $C_1$, cancela en el numerador y el denominador.

En general, la forma de operar es sencilla, pero merece la pena que la practiquemos con otro ejemplo en el que repasaremos todos los ingredientes presentados hasta ahora.

<br>

##### Ejemplo 4

Supongamos que estamos interesados en un parámetro desconocido $\mu$, cuya interpretación es la de una media poblacional (por ejemplo podemos pensar que $\mu$ es el rendimiento medio de un índice bursátil). La información disponible sobre $\mu$ nos lleva a asignar la siguiente distribución _a priori_:

$$
p(\mu) = \text{normal}(\mu | \mu_y, \sigma_y),
$$

es decir, una distribución normal de media $\mu_y$ y de desviación típica $\sigma_y$. Es bastante creíble que hayamos llegado a esta asignación usando datos históricos sobre la media de índices (rendimientos del índice). Usando la forma de la densidad normal, podemos escribir:

$$
p(\mu) = \frac{1}{\sigma_y \sqrt{2\pi}} \exp\left( -\frac{1}{2\sigma_y^2} (\mu - \mu_y)^2 \right),
$$

o alternativamente:

$$
p(\mu) \propto \exp\left( -\frac{1}{2\sigma_y^2} (\mu - \mu_y)^2 \right).
$$

En este caso, el espacio paramétrico de $\mu$ es $\mathbb{R}$.

Para aprender (más) sobre este parámetro, "diseñamos" un experimento en el que obtendremos información de $\mu$. En nuestro caso, vamos a observar una medición $Y$ que en el contexto del activo financiero puede ser el rendimiento que se observará mañana. Asumimos que la distribución de $Y$, condicional a $\mu$, es también normal, en este caso una normal de media $\mu$ y de desviación típica 0.01:

$$
p(Y | \mu) = \text{normal}(Y | \mu, 0.01).
$$

---

Este es el “modelo” observacional asumido que conecta el experimento con el parámetro desconocido $\mu$ que define la función de verosimilitud:

$$
L(\mu;y) = \text{normal}(y | \mu,0.01) = \frac{1}{0.01 \cdot \sqrt{2\pi}} \exp\left( -\frac{1}{2 \cdot 0.01^2}(y - \mu)^2 \right).
$$

Con todo esto, la distribución _a posteriori_ es la distribución de $\mu$ condicionada a que $Y$ ha tomado el valor $y$:

$$
p(\mu | y) \propto L(\mu;y)p(\mu),
$$

por tanto:

$$
p(\mu | y) \propto \exp\left( -\frac{1}{2 \cdot 0.01^2}(y - \mu)^2 \right) \exp\left( -\frac{1}{2\sigma_y^2} (\mu - \mu_y)^2 \right).
$$

La expresión anterior define implícitamente la distribución _a posteriori_. No obstante, para obtener conclusiones a partir de esta, nos va a ser útil conocer cuál es su forma exacta. Como estamos identificando una función de densidad para $\mu$, las constantes multiplicativas que no dependan de $\mu$ las podemos obviar. Esta observación, junto con el desarrollo de cuadrados en las exponenciales nos lleva a la siguiente expresión:

$$
p(\mu | y) \propto \exp \left\{ -\frac{1}{2} \left[ \frac{(y - \mu)^2}{0.01^2} + \frac{(\mu - \mu_y)^2}{\sigma_y^2} \right] \right\}
$$

$$
\propto \exp \left\{ -\frac{1}{2} \left[ \frac{\mu^2}{0.01^2} - \frac{2\mu y}{0.01^2} + \frac{\mu^2}{\sigma_y^2} - \frac{2\mu\mu_y}{\sigma_y^2} \right] \right\}
$$

$$
\propto \exp \left\{ -\frac{1}{2} \left[ \mu^2 \left( \frac{1}{0.01^2} + \frac{1}{\sigma_y^2} \right) - 2\mu \left( \frac{y}{0.01^2} + \frac{\mu_y}{\sigma_y^2} \right) \right] \right\}
$$

$$
\propto \exp \left\{ -\frac{1}{2} \cdot \frac{1}{B} \cdot \left[ \mu^2 - 2\mu A \right] \right\}
$$

donde

$$
A = \frac{y}{0.01^2} + \frac{\mu_y}{\sigma_y^2}, \quad B = \frac{1}{0.01^2} + \frac{1}{\sigma_y^2}
$$

En la última expresión de arriba, reconocemos la forma de una densidad normal, en este caso de media \(A/B\) y de varianza \(B^{-1}\). Entonces llegamos a la conclusión de que:

$$
p(\mu | y) = \text{normal} \left( \mu \bigg| \frac{A}{B}, \frac{1}{B} \right) = \text{normal} \left( \mu \bigg| \frac{\frac{y}{0.01^2} + \frac{\mu_y}{\sigma_y^2}}{\frac{1}{0.01^2} + \frac{1}{\sigma_y^2}}, \frac{1}{\frac{1}{0.01^2} + \frac{1}{\sigma_y^2}} \right)
$$

En la Figura\[1\] hemos representado la distribución _a priori_ y la distribución _a posteriori_ de $\mu$ para unos valores concretos de $\mu_y$, $\sigma_y$, y $y$.

La distribución _a posteriori_ contiene toda la información (_a priori_ y experimental) sobre el parámetro desconocido $\mu$. De momento basta empezar a estar familiarizado con la idea de que cualquier afirmación de tipo inferencial sobre $\mu$ pasará por resumir de forma adecuada la anterior distribución. Volviendo a la contextualización de este ejemplo en finanzas, podemos usar la distribución anterior para ver cómo han cambiado los datos (bueno, en este caso, el dato) sobre el rendimiento de este índice en la información _a priori_ sobre $\mu$. _A priori_, la media de $\mu$ era $\mu_y$, y _a posteriori_, la media de $\mu$ pasa a ser:

$$
E[\mu | y] = \frac{\frac{y}{0.01^2} + \frac{\mu_y}{\sigma_y^2}}{\frac{1}{0.01^2} + \frac{1}{\sigma_y^2}} = \frac{y \cdot \sigma_y^2 + \mu_y \cdot 0.01^2}{\sigma_y^2 + 0.01^2}.
$$


