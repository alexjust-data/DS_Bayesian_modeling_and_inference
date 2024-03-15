### 1.1 Probabilidad condicional y regla de Bayes

**Pregunta : ¿Cómo se modifica la probabilidad de un evento A si sabemos de la ocurrencia de otro suceso B relacionado?**

En teoría de probabilidad sobre sucesos, la regla de Bayes establece cómo se modifica la probabilidad de un evento A si sabemos de la ocurrencia de otro suceso B relacionado. Esta probabilidad *condicional* se denota $P(A | B)$ y se lee “probabilidad condicional de A dado B”. La regla de Bayes establece que:

$$
P(A | B) = \frac{P(A \cap B)}{P(B)} = \frac{P(B | A)P(A)}{P(B)}
$$

Cuando el espacio muestral asociado al evento A se puede expresar como unión excluyente de *k* sucesos, es decir $A_1 \cup A_2 \cup \ldots \cup A_k$, entonces la regla de Bayes se puede expresar como:

$$
P(A_i | B) = \frac{P(B | A_i)P(A_i)}{\sum_{j=1}^{k} P(B | A_j)P(A_j)}
$$

> **Espacio muestral** : Asociado a un experimento aleatorio, es el conjunto de resultados o sucesos simples que podemos observar.

<br>

**Ejemplo 1**

Imagina que eres deportista de élite, de pronto, en un control antidopaje que asegura una detección correcta en el `95%` de los casos, das positivo (+).  El teorema de Bayes nos sirve para demostrar que un positivo en la prueba no es tan concluyente como parece. 

Las especificaciones de la prueba de detección se pueden escribir como: $P(\text{Test+} |  \text{dopaje}) = P(\text{Test-} | \text{no dopaje}) = 0.95 $

Ambas probabilidades son del 95%, lo que indica que la prueba tiene una alta precisión tanto para detectar correctamente a los dopados (verdaderos positivos) como para no dar falsos positivos en los no dopados (verdaderos negativos).

Entonces, en virtud de la regla de Bayes, la probabilidad de que te hayas dopado es en realidad:

$$
P(\text{dopaje} | \text{Test+}) =\frac{P(\text{Test+} | \text{dopaje})P(\text{dopaje})}{P(\text{Test+} | \text{dopaje})P(\text{dopaje}) + P(\text{Test+} | \text{no dopaje})P(\text{no dopaje})}
$$


El único dato que nos falta es `P(dopaje)`, que representa la probabilidad de que un deportista escogido al azar haya consumido sustancias dopantes o no. Esta probabilidad es bastante baja. En las últimas olimpiadas de atletismo de Pekín, solo un `1% de los atletas había consumido este tipo de sustancias`. Entonces a partir de este dato:


$$
P(\text{dopaje} | \text{Test+}) =\frac{0.95x0,01}{0,5x0,01 + 0,05x0,99} \approx 0,16
$$


De mayor interés para el desarrollo de un curso de inferencia bayesiana es la aplicación del teorema de Bayes en variables aleatorias.


