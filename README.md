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

1. [Probabilidad y elementos básicos del método bayesiano](01_section_1/00_methods_and_elements/01_Probabilidad_y_elementos_basicos.md)  
   1.1. [Probabilidad condicional y regla de Bayes](01_section_1/00_methods_and_elements/02_Probabilidad_condicional_y_regla_de_Bayes.md)  
   1.2. [Teorema de Bayes en variables aleatorias discretas](01_section_1/00_Probability_and_basics_elements/03_Bayes_variables_aleatorias_discretas.md)  
   1.3. [Teorema de Bayes en variables aleatorias continuas](01_section_1/00_Probability_and_basics_elements/04_Bayes_variables_continuas.md)  
   1.4 [Priori y posteriori](01_section_1/00_Probability_and_basics_elements/05_priori_posteriori.md)  

**Sección 2**. El resto de las secciones son más generales y describen métodos que son útiles más allá del método bayesiano, pero que son cruciales para el desarrollo de este. Estamos hablando de la construcción de modelos en estadística (y por tanto de la definición de la función de verosimilitud) estudiada en la seccion 2.

2. [Modelización estadística y función de verosimilitud](01_section_1/01_Statistical_modeling_likelihood_function/01_Statical_modeling_likehood_function.md)  
   2.1. [Independencia condicional y observaciones independientes e idénticamente distribuidas](01_section_1/01_Statistical_modeling_likelihood_function/02_Conditional_Independence_and_Independent_Identically_Distributed_Observations.md)  
   2.2. [Observaciones independientes, pero no idénticamente distribuidas](01_section_1/01_Statistical_modeling_likelihood_function/03_Independent_Observations_not_Identically_distributed.md)  
   2.3. [Observaciones no independientes](01_section_1/01_Statistical_modeling_likelihood_function/04_Non_Independent_Observations.md)  

**Sección 3**, está dedicada a la simulación de variables aleatorias y en particular al método de Montecarlo. 

3. [Técnicas básicas de simulación de variables aleatorias](01_section_1/02_random_variable_simulation_techniques/01_random_variable_simulation_techniques.md)  
   3.1. [La transformada integral de probabilidad](01_section_1/02_random_variable_simulation_techniques/02_integral_probability_transform.md)  
   3.2. [Simulación y métodos Montecarlo como herramienta numérica para describir una distribución](01_section_1/02_random_variable_simulation_techniques/03_simulation_and_monte_carlo_methods.md)  
   3.3. [Simulación en el contexto bayesiano](01_section_1/02_random_variable_simulation_techniques/04_Simulation_in_the_Bayesian_context.md)  

**Sección 4**, estudiaremos las herramientas que R pone a nuestra disposición para simular variables aleatorias.

4. [Simulación en R](01_section_1/03_Simulation_in_R/01_Simulation_in_R.md)  
   4.1. [Simulación de vectores aleatorios](01_section_1/03_Simulation_in_R/02_Random_Vector_Simulation.md)  
*. [Extra sobre métodos Montecarlo](01_section_1/04_Extra_on_Monte_Carlo_methods/04_Extra_on_Monte_Carlo_methods.md)  

### Primeros pasos en el proceso de aprendizaje bayesiano

Este apartado se subraya la importancia de la selección cuidadosa de la distribución a priori para facilitar el cálculo de la distribución a posteriori y cómo la elección de una distribución `conjugada previa` puede simplificar este proceso.

5. [Intro](02_/intro.md)


#### Previas conjugadas

Las previas conjugadas lo son con respecto a una verosimilitud concreta, lo que quiere decir que, al combinarse con esta, dan como resultado una distribución posterior de la misma familia aunque con parámetros actualizados.

Algunos procedimientos de aprendizaje conjugados:

6. [Verosimilitud binomial, distribución previa beta]()

7. [Verosimilitud de Poisson y previa gamma]()

8. [Verosimilitud exponencial distribución a priori gamma]()

9. [Verosimilitud normal]()

* [Elección de los parámetros de la distribución previa]()
* [Mirando más allá]()

 * ####  Elección de los parámetros de la distribución previa

Si bien es cierto que el uso de distribuciones previas conjugadas puede simplificar mucho el proceso de aprendizaje bayesiano y los cálculos que se deben realizar, dando lugar a distribuciones a posteriori fácilmente identificables y con constante de normalización conocida, no debemos perder de vista que todavía hay un escollo que debe solventarse: la elección del valor de los parámetros a priori.

Todas las previas conjugadas que hemos visto en el apartado anterior tienen parámetros cuya interpretación no siempre es directa. Por ejemplo, cuando usamos una distribución previa normal, todos tenemos claro que los parámetros que tenemos que determinar son la media y la desviación estándar. Sin embargo, cuando estamos trabajando con una distribución a priori beta o con una gamma, la relación de los parámetros con la media y la varianza no es tan directa, por lo que es necesario replantearse cómo pueden reflejar esos parámetros la información disponible.

* #### Mirando más allá


En todos los procesos estudiados en este documento se dan dos circunstancias muy particulares. Por una parte, la cantidad o parámetro de interés que se estudia está bastante clara y relacionada directamente con los parámetros involucrados en la verosimilitud de forma individual. Por otra parte, estamos suponiendo que tiene sentido utilizar una forma concreta para la distribución previa de ese parámetro. Sin embargo, la situación no siempre es tan favorable.

En la modelización de situaciones reales es habitual encontrarse con situaciones donde la cantidad de interés no son los parámetros de la verosimilitud per se, sino, por ejemplo, alguna combinación, posiblemente no lineal, de estos. Además, es posible que no tengamos conocimiento previo sobre su valor, o lo tengamos, puede ser que no se adapte a la forma determinada por la previa conjugada.

En el primer caso, es posible que utilizar una previa conjugada sobre los parámetros originales no sea la estrategia óptima en cuanto a la transmisión de la información que tenemos sobre dicha cantidad de interés. Por poner un ejemplo, imaginad que en el proceso de crecimiento de una planta estamos midiendo su altura a cabo de un mes, y suponemos que sobre esta variable puedo considerarse una distribución normal(\( \mu,\sigma \)), con ambos parámetros desconocidos. Sin embargo, el parámetro sobre el que realmente tenemos información es el coeficiente de variación. Es decir, no tenemos conocimiento sobre \( \mu \) sobre o, sino sobre \( CV = \frac{\sigma}{\mu} \). Una situación similar se da en el caso de los modelos de regresión lineal, donde las cantidades de interés son los diferentes coeficientes del predictor lineal.

Por otra parte, en el caso de no tener información sobre la cantidad de interés o, por algún motivo, no querer incorporarla al estudio, es posible que debamos recurrir a lo que se conoce como distribuciones previas objetivas o mínimamente informativas. Este tipo de distribuciones suelen obtenerse mediante un estudio exhaustivo del proceso matemático de incorporación de información en el escenario estudiado y, en la mayoría de los casos, no serán previas conjug

En todos estos casos la obtención directa de la distribución marginal no está garantizada, lo que supone no conocer por completo la distribución a poste- riori. En estos casos será necesario recurrir a los métodos de simulación de los que ya os comenzamos a hablar en el reto anterior.