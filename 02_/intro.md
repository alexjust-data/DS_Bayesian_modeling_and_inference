Este apartado se subraya la importancia de la selección cuidadosa de la distribución a priori para facilitar el cálculo de la distribución a posteriori y cómo la elección de una distribución `conjugada previa` puede simplificar este proceso.

Cuando se realiza una inferencia bayesiana con datos binarios, la distribución a priori y la verosimilitud trabajan juntas para proporcionar una distribución a posteriori. La belleza de usar la distribución beta como a priori para una verosimilitud Bernoulli es que ambas son matemáticamente "conjugadas", lo que significa que la forma funcional de la distribución posterior permanecerá en la misma familia (beta), simplificando la actualización de las creencias con nueva evidencia.

1. **Función de Verosimilitud `L(θ, y)`**: Esta función indica la probabilidad de los datos observados `y` dado un parámetro `θ`. Se determina por el modelo estadístico que se utiliza. Por ejemplo, para un modelo de lanzamiento de moneda, se emplearía una distribución de Bernoulli para la verosimilitud, donde `θ` sería la probabilidad de obtener cara.

2. **Distribución a Priori `p(θ)`**: Representa el conocimiento o creencias previas acerca del parámetro `θ` antes de ver los datos. La elección de esta distribución es más subjetiva y puede ser desafiante, ya que depende del conocimiento previo sobre el parámetro a inferir.

El desafío con la distribución a priori es seleccionar una que permita calcular de forma manejable una distribución a posteriori `p(θ | y)` que se combine con la verosimilitud proporcionada por los datos.

**Distribuciones Conjugadas Previas**

La solución a este desafío es el uso de `distribuciones conjugadas previas`. Al utilizar una distribución a priori que es conjugada de la verosimilitud del modelo, se asegura que la distribución a posteriori pertenezca a la misma familia de la distribución a priori, simplificando el cálculo.

Por ejemplo, si la verosimilitud es binomial, la distribución beta es una elección a priori conveniente, ya que es la conjugada de la binomial. Así, al combinar estas dos, la distribución a posteriori también será una beta, lo cual facilita la actualización de las creencias tras observar los datos.
