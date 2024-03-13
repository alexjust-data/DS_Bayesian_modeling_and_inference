
**¿Porqué distribución de Poisson?**

La elección de una distribución de Poisson a priori se debe a las propiedades particulares de esta distribución, que la hacen adecuada para modelar el número de ocurrencias de eventos en un espacio fijo de tiempo o área, bajo ciertas condiciones. La distribución de Poisson se utiliza comúnmente cuando:

1. Los eventos son independientes entre sí.
2. La tasa promedio de ocurrencia es constante.
3. Dos eventos no pueden ocurrir al mismo tiempo (en un intervalo infinitesimalmente pequeño).

En el contexto de una fábrica, si estamos hablando de defectos o fallos que pueden aparecer en una chapa de material durante su fabricación, la distribución de Poisson puede aplicarse si:

* Los defectos ocurren de manera independiente entre sí.
* Hay una tasa media constante de defectos por unidad de área.
* Es raro que ocurran dos defectos exactamente en el mismo punto.
  
Si estas condiciones se cumplen, la distribución de Poisson es un modelo adecuado para estimar la probabilidad de encontrar un cierto número de defectos en un área dada.

Por lo tanto, si la fábrica tiene históricamente un número medio constante de defectos por 10m2 de chapa, y cada defecto ocurre independientemente de los demás, tendría sentido utilizar una distribución de Poisson para modelar la probabilidad de encontrar un cierto número de defectos en nuevas chapas de 10m2.

Esta modelación a priori está basada en la experiencia o en datos históricos, y es una forma de cuantificar la incertidumbre antes de observar los datos actuales. Una vez que se observa la evidencia (como el número de defectos en la inspección actual), se puede utilizar el teorema de Bayes para actualizar estas creencias a priori y obtener probabilidades a posteriori, que son ajustes de nuestras estimaciones iniciales en función de la nueva información.

---

La media de la distribución de Poisson \( \lambda = \frac{10}{\theta} \) está definida en términos de \( \theta \), el número de controles mensuales de calidad en el proceso de fabricación. La relación inversa entre \( \lambda \) y \( \theta \) implica que:

- **Cuando aumenta \( \theta \)**, es decir, hay más controles de calidad, **la media \( \lambda \) de defectos disminuye**. Esto refleja la idea de que un mayor control de calidad debería resultar en menos defectos en el producto final, ya que se corrigen más defectos durante el proceso de fabricación.

- **Cuando disminuye \( \theta \)**, o sea, hay menos controles de calidad, **la media \( \lambda \) de defectos aumenta**. Con menos controles, hay más oportunidades de que los defectos pasen desapercibidos, aumentando así la cantidad de defectos en el producto final.

La fórmula \( \lambda = \frac{10}{\theta} \) sugiere que si no se realiza ningún control (\( \theta = 0 \)), teóricamente esperaríamos una base de 10 defectos, y esta base se ajusta proporcionalmente al número de controles realizados. Este modelo presupone que cada inspección tiene la misma efectividad en detectar defectos.

Este es un modelo simplificado y debe ser corroborado con datos reales y una comprensión detallada del proceso de fabricación para asegurarse de que es una representación precisa.
