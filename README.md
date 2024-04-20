### Formulario

1. Teorema de Bayes
   1. [Versión clásica](00_Form/01_Bayes_theorem.md#11-versi%C3%B3n-cl%C3%A1sica)
   2. [Teorema de Bayes para variables aleatorias discretas](00_Form/01_Bayes_theorem.md#12-teorema-de-bayes-para-variables-aleatorias-discretas)
   3. [Teorema de Bayes para variables aleatorias continuas](00_Form/01_Bayes_theorem.md#13-teorema-de-bayes-para-variables-aleatorias-continuas)
   4. [Versión bayesiana del teorema de Bayes](00_Form/01_Bayes_theorem.md#14-versi%C3%B3n-bayesiana-del-teorema-de-bayes)

2. Distribuciones para variables aleatorias discretas
   1. [Variable aleatoria con distribución Bernoulli/Binomial](00_Form/01_Bayes_theorem.md#21-variable-aleatoria-con-distribuci%C3%B3n-bernoullibinomial)
   2. [Variable aleatoria con distribución de Poisson](00_Form/01_Bayes_theorem.md#22-variable-aleatoria-con-distribuci%C3%B3n-de-poisson)

3. Distribuciones para variables aleatorias continuas 
   1. [Variable aleatoria con distribución uniforme](00_Form/01_Bayes_theorem.md#31-variable-aleatoria-con-distribuci%C3%B3n-uniforme)
   2. [Variable aleatoria con distribución normal](00_Form/01_Bayes_theorem.md#32-variable-aleatoria-con-distribuci%C3%B3n-normal)
   3. [Variable aleatoria con distribución gamma](00_Form/01_Bayes_theorem.md#33-variable-aleatoria-con-distribuci%C3%B3n-gamma)
   4. [Variable aleatoria con distribución beta](00_Form/01_Bayes_theorem.md#34-variable-aleatoria-con-distribuci%C3%B3n-beta)
   5. [Variable aleatoria con distribución t-Student](00_Form/01_Bayes_theorem.md#35-variable-aleatoria-con-distribuci%C3%B3n-ji-cuadrada)
   6. [Variable aleatoria con distribución ji-cuadrada](00_Form/01_Bayes_theorem.md#36-variable-aleatoria-con-distribuci%C3%B3n-t-student)

---
## Bayesian statistical analysis


### Métodos y elementos de la inferencia bayesiana

**Sección 1**, se habla del uso propio de la probabilidad en el método bayesiano para formalizar todas las incertidumbres en un problema de inferencia.

1. [Probabilidad y elementos básicos del método bayesiano](01_/00_methods_and_elements/01_Probabilidad_y_elementos_basicos.md)  
   1.1. [Probabilidad condicional y regla de Bayes](01_/00_methods_and_elements/02_Probabilidad_condicional_y_regla_de_Bayes.md)  
   1.2. [Teorema de Bayes en variables aleatorias discretas](01_/00_Probability_and_basics_elements/03_Bayes_variables_aleatorias_discretas.md)  
   1.3. [Teorema de Bayes en variables aleatorias continuas](01_/00_Probability_and_basics_elements/04_Bayes_variables_continuas.md)  
   1.4 [Priori y posteriori](01_/00_Probability_and_basics_elements/05_priori_posteriori.md)  

**Sección 2**. El resto de las secciones son más generales y describen métodos que son útiles más allá del método bayesiano, pero que son cruciales para el desarrollo de este. Estamos hablando de la construcción de modelos en estadística (y por tanto de la definición de la función de verosimilitud) estudiada en la seccion 2.

2. [Modelización estadística y función de verosimilitud](01_/01_Statistical_modeling_likelihood_function/01_Statical_modeling_likehood_function.md)  
   2.1. [Independencia condicional y observaciones independientes e idénticamente distribuidas](01_/01_Statistical_modeling_likelihood_function/02_Conditional_Independence_and_Independent_Identically_Distributed_Observations.md)  
   2.2. [Observaciones independientes, pero no idénticamente distribuidas](01_/01_Statistical_modeling_likelihood_function/03_Independent_Observations_not_Identically_distributed.md)  
   2.3. [Observaciones no independientes](01_/01_Statistical_modeling_likelihood_function/04_Non_Independent_Observations.md)  

**Sección 3**, está dedicada a la simulación de variables aleatorias y en particular al método de Montecarlo. 

3. [Técnicas básicas de simulación de variables aleatorias](01_/02_random_variable_simulation_techniques/01_random_variable_simulation_techniques.md)  
   3.1. [La transformada integral de probabilidad](01_/02_random_variable_simulation_techniques/02_integral_probability_transform.md)  
   3.2. [Simulación y métodos Montecarlo como herramienta numérica para describir una distribución](01_/02_random_variable_simulation_techniques/03_simulation_and_monte_carlo_methods.md)  
   3.3. [Simulación en el contexto bayesiano](01_/02_random_variable_simulation_techniques/04_Simulation_in_the_Bayesian_context.md)  

**Sección 4**, estudiaremos las herramientas que R pone a nuestra disposición para simular variables aleatorias.

4. [Simulación en R](01_/03_Simulation_in_R/01_Simulation_in_R.md)  
   4.1. [Simulación de vectores aleatorios](01_/03_Simulation_in_R/02_Random_Vector_Simulation.md)  
*. [Extra sobre métodos Montecarlo](01_/04_Extra_on_Monte_Carlo_methods/04_Extra_on_Monte_Carlo_methods.md)  

### Primeros pasos en el proceso de aprendizaje bayesiano

Este apartado se subraya la importancia de la selección cuidadosa de la distribución a priori para facilitar el cálculo de la distribución a posteriori y cómo la elección de una distribución `conjugada previa` puede simplificar este proceso.

5. [Intro](02_/intro.md)


#### Previas conjugadas

Las previas conjugadas lo son con respecto a una verosimilitud concreta, lo que quiere decir que, al combinarse con esta, dan como resultado una distribución posterior de la misma familia aunque con parámetros actualizados.

Algunos procedimientos de aprendizaje conjugados:

6. [Verosimilitud binomial, distribución previa beta](02_/Verosimilitud_binomial_previa_beta.md)
7. [Verosimilitud de Poisson y previa gamma](02_/Verosimilitud_Poisson_previa_gamma.md)
8. [Verosimilitud exponencial distribución a priori gamma](02_/Verosimilitud_exponencial_priori_gamma.md)
9. [Verosimilitud normal](02_/Verosimilitud_normal.md)

* [Elección de los parámetros de la distribución previa](02_/Eleccion_parametros.md)
* [Mirando más allá](02_/Eleccion_parametros.md#mirando-más-allá)

#### Caso práctico : estimar número de mensajes WhatsApp que recibe un adolescente

10. [Caso práctico](02_/Practica_02_.pdf)
    1. [¿Porqué asumimos que nuestra variable de respuesta Y tiene distribución Poisson?](02_/prac1)
    2. [Función de verosimilitud](02_/prac2)