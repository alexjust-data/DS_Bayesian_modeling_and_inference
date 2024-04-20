## Modelización estadística y función de verosimilitud


Entendemos por modelo estadístico la distribución asumida (función de masa conjunta en el caso de variables aleatorias discretas o función de densidad si son continuas) para el vector aleatorio $Y = (Y_1,Y_2,\ldots,Y_n)$.

Los modelos estadísticos los “construyen” los estadísticos y deben reflejar lo más fielmente posible la forma real de la distribución de frecuencias de $Y$ que podemos esperar antes de realizar el experimento. Una reflexión que se atribuye al estadístico George Box y que hay que tener siempre muy presente es que “todos los modelos son erróneos, pero alguno es útil”. Con esta idea en mente, una definición operativa de modelo es:

>###### Definición 1 (Modelo)
>Modelo es un conjunto de hipótesis, basadas en supuestos racionales, de utilidad y simplicidad, sobre las observaciones $Y_i$ que conforman una muestra y que definen, a excepción de parámetros desconocidos $\theta$, la distribución de probabilidad conjunta de la muestra $p(y_1,\ldots,y_n | \theta)$. Los parámetros desconocidos $\theta$ definen aspectos importantes de la población y/o dan flexibilidad al proceso con el que las observaciones ocurren. El conjunto de valores posibles de $\theta$ se llama espacio paramétrico y se denota $\Theta \subseteq \mathbb{R}^k$ (suponiendo que hay $k$ de estos parámetros).

Para empezar la construcción del modelo, obviamente debemos tener en cuenta la naturaleza y el rango de las variables aleatorias $Y_i$. Aunque ya sabemos que la situación de una sola observación no es la habitual, vamos a recordar los ejemplos de la sección anterior como punto de partida. En la situación del ejemplo [2](03_Bayes_variables_aleatorias_discretas.md#ejemplo-2) la variable aleatoria $Y$ es discreta (número de desperfectos por $10 m^2$ de chapa) con rango en $\{0,1,2,\ldots\}$, lo que parece aconsejar el modelo Poisson como una opción razonable. Por el contrario, en el ejemplo [3](04_Bayes_variables_continuas.md#ejemplo-3) la variable aleatoria $Y$ (tiempo hasta) es continua con rango en $[0,\infty)$ apuntando al modelo exponencial como una posibilidad simple para $Y$ (otras posibilidades habrían sido un modelo Gamma, Weibull o logNormal que ofrecen mayor flexibilidad, al coste de incluir un mayor número de parámetros).

Un supuesto muy usado como estrategia para construir modelos es el de observaciones independientes idénticamente distribuidas (iid).
