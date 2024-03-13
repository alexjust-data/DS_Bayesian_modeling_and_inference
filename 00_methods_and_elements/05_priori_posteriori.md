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

Ya hemos visto que en el manejo de las distribuciones sobre los parámetros es bastante habitual encontrarnos con constantes de proporcionalidad. Las constantes de proporcionalidad están definidas por la obligación de la correspondiente distribución de probabilidad de integrar uno y por tanto su valor está implícitamente determinado por los factores que dependen de $\theta$. Esta observación permite avanzar en los cálculos sin especificar explícitamente su valor haciendo por tanto las matemáticas menos engorrosas. Esto se consigue
