### distribución *a posteriori*, distribución *a priori*


En los dos ejemplos anteriores se han presentado los elementos básicos de la inferencia bayesiana. Por un lado tenemos los parámetros $\theta$ que representan las magnitudes desconocidas que son nuestro objeto de interés. En los ejemplos anteriores el parámetro de interés es unidimensional, pero en general será multidimensional. Además, veremos más adelante que también habrá parámetros en los que no estamos directamente interesados, pero cuya existencia tenemos que gestionar.


La información (mucha, poca o incluso ninguna) sobre estos parámetros antes de obtener información experimental está contenida en la función $p(\theta)$: la función de masa $p(\theta)$ en la [Tabla 1](03_Bayes_variables_aleatorias_discretas.md#tabla-1) del [ejemplo 2](00_methods_and_elements/03_Bayes_variables_aleatorias_discretas.md#ejemplo-2) y la función de densidad $p(\theta)$ en la [ecuación 3](00_methods_and_elements/04_Bayes_variables_continuas.md#3). A estas distribuciones se las conoce como distribuciones a priori, destacando que esta asignación inicial se corresponde con la información sobre los parámetros desconocidos disponible sin tener en cuenta la información muestral.


Además tenemos un experimento que nos proporcionará conocimiento sobre $\theta$ por medio de la observación de Y. El vínculo entre ambas cantidades Y y $\theta$ está contenido en la distribución de probabilidad de Y condicionada a que sabemos el valor de $\theta: p(y | \theta)$. Esta distribución se corresponde con el modelo asumido para Y (Poisson en el [ejemplo 2](00_methods_and_elements/03_Bayes_variables_aleatorias_discretas.md#ejemplo-2) y exponencial en el [ejemplo 3](04_Bayes_variables_continuas.md#ejemplo-3)). Si vemos esta función como una función de los parámetros, obtenemos un elemento crucial en el ámbito de la estadística: la función de verosimilitud o *likelihood function* en inglés. Es bastante frecuente simbolizar esta función como $L(\theta,y)$. Más adelante indicaremos cómo asignar modelos y por tanto veremos la forma de las funciones de verosimilitud en situaciones concretas.



