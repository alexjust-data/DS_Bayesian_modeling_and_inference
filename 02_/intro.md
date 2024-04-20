Este apartado se subraya la importancia de la selección cuidadosa de la distribución a priori para facilitar el cálculo de la distribución a posteriori y cómo la elección de una distribución `conjugada previa` puede simplificar este proceso.

Cuando se realiza una inferencia bayesiana con datos binarios, la distribución a priori y la verosimilitud trabajan juntas para proporcionar una distribución a posteriori. La belleza de usar la distribución beta como a priori para una verosimilitud Bernoulli es que ambas son matemáticamente "conjugadas", lo que significa que la forma funcional de la distribución posterior permanecerá en la misma familia (beta), simplificando la actualización de las creencias con nueva evidencia.

1. **Función de Verosimilitud `L(θ, y)`**: Esta función indica la probabilidad de los datos observados `y` dado un parámetro `θ`. Se determina por el modelo estadístico que se utiliza. Por ejemplo, para un modelo de lanzamiento de moneda, se emplearía una distribución de Bernoulli para la verosimilitud, donde `θ` sería la probabilidad de obtener cara.

2. **Distribución a Priori `p(θ)`**: Representa el conocimiento o creencias previas acerca del parámetro `θ` antes de ver los datos. La elección de esta distribución es más subjetiva y puede ser desafiante, ya que depende del conocimiento previo sobre el parámetro a inferir.

El desafío con la distribución a priori es seleccionar una que permita calcular de forma manejable una distribución a posteriori `p(θ | y)` que se combine con la verosimilitud proporcionada por los datos.

### Distribuciones Conjugadas Previas

La solución a este desafío es el uso de `distribuciones conjugadas previas`. Al utilizar una distribución a priori que es conjugada de la verosimilitud del modelo, se asegura que la distribución a posteriori pertenezca a la misma familia de la distribución a priori, simplificando el cálculo.

Por ejemplo, 

- Cuando la **verosimilitud es Binomial**, una opción natural para la distribución a priori es la **distribución Beta**. La razón es que la Beta es conjugada de la verosimilitud Binomial, lo que significa que la **distribución a posteriori** resultante también será una distribución Beta. Esto es beneficioso porque:

  - **Simplifica los Cálculos**: No hay necesidad de resolver integrales complejas para encontrar la distribución a posteriori.
  - **Facilita la Actualización**: Cuando obtenemos nuevos datos, podemos actualizar nuestra distribución a posteriori simplemente ajustando los parámetros de la Beta, sin tener que recalcular toda la distribución desde cero.

Por ejemplo, si empezamos con una distribución a priori `Beta(α, β)` y observamos `z` éxitos en `N` ensayos, la distribución a posteriori será `Beta(α + z, β + N - z)`. Esto permite una actualización directa y sencilla de nuestras creencias después de considerar los nuevos datos.


### Procedimientos de Aprendizaje Conjugados

Los procedimientos de aprendizaje conjugados en estadística bayesiana involucran pares de distribuciones previas y verosimilitudes donde la distribución a priori es la "conjugada" de una verosimilitud específica. Esto resulta en que la distribución a posteriori pertenece a la misma familia que la previa. A continuación, algunos pares conjugados comunes:

1. **Bernoulli / Binomial y Beta**:
   - **Verosimilitud:** Bernoulli o Binomial (para ensayos independientes con dos resultados posibles).
   - **Priori Conjugada:** Beta.
   - **Resultado:** La distribución a posteriori es Beta con parámetros actualizados según los éxitos y fracasos observados.

2. **Normal con varianza conocida y Normal**:
   - **Verosimilitud:** Normal con varianza conocida.
   - **Priori Conjugada:** Normal.
   - **Resultado:** La distribución a posteriori es Normal con una media actualizada.

3. **Normal con media conocida y Gamma**:
   - **Verosimilitud:** Normal con media conocida.
   - **Priori Conjugada:** Gamma (para la precisión, el inverso de la varianza).
   - **Resultado:** La distribución a posteriori es Gamma, reflejando una precisión actualizada.

4. **Poisson y Gamma**:
   - **Verosimilitud:** Poisson (para contar eventos en un espacio o intervalo continuo).
   - **Priori Conjugada:** Gamma (para la tasa de eventos).
   - **Resultado:** La distribución a posteriori es Gamma con parámetros basados en el número de eventos observados.

5. **Exponencial y Gamma**:
   - **Verosimilitud:** Exponencial (para modelar el tiempo hasta un evento).
   - **Priori Conjugada:** Gamma (para la tasa del evento).
   - **Resultado:** La distribución a posteriori es Gamma con parámetros actualizados por los tiempos observados hasta los eventos.

6. **Multinomial y Dirichlet**:
   - **Verosimilitud:** Multinomial (para datos categóricos con múltiples categorías).
   - **Priori Conjugada:** Dirichlet (para las probabilidades de las categorías).
   - **Resultado:** La distribución a posteriori es Dirichlet con parámetros actualizados por los recuentos de observaciones por categoría.

Estos pares permiten actualizaciones analíticas y directas de la distribución previa con la incorporación de nuevos datos.
