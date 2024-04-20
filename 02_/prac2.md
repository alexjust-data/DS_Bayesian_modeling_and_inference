**¿Qué es la función de verosimilitud?**

La **función de verosimilitud** es una función matemática usada en estadística para evaluar qué tan probable es obtener los datos observados, dado un conjunto específico de parámetros de un modelo estadístico. Mide la "verosimilitud" o plausibilidad de diferentes valores para los parámetros del modelo, basándose en los datos que tienes.

**¿De dónde sale la función de verosimilitud?**

La función de verosimilitud se deriva del modelo estadístico que elijas para describir tus datos. Se basa en la función de probabilidad asociada a ese modelo, considerando los datos como constantes y los parámetros como variables.

**¿Cómo se formula?**

Imaginemos que tienes un conjunto de datos y un modelo que depende de ciertos parámetros. La función de verosimilitud se construye tomando la función de probabilidad del modelo y aplicándola a tus datos observados, tratando los parámetros como variables. Por ejemplo, con una distribución de Poisson que es común para modelar conteos, la probabilidad de ver exactamente $k$ eventos es:

$$P(X = k) = e^{-\lambda} \frac{\lambda^k}{k!}$$

donde $\lambda$ es el parámetro de la tasa media de eventos, y $k$ son los eventos observados.

**¿Cómo se ejecuta?**

1. **Define el modelo**: Escoge un modelo basado en tu entendimiento del fenómeno que estudias.
2. **Recolecta datos**: Obtiene datos que se ajusten al modelo elegido.
3. **Formula la verosimilitud**: Calcula la verosimilitud multiplicando las probabilidades de cada dato observado, dado el parámetro.
4. **Maximiza la verosimilitud**: Busca el valor del parámetro que hace que la verosimilitud sea máxima, indicando el mejor ajuste del modelo a los datos.
