
### 1. Probabilidad y elementos básicos del método bayesiano

Desde un punto de vista bayesiano, la probabilidad tiene dos usos diferenciados.

**Cuantificar la certeza de que un suceso asociado a un experimento de naturaleza aleatoria ocurra.**

* `Suceso` : asignar la probabilidaad de que un meteorito impacte en la tierra en los próximos 100 años.
* `Variable aleatoria` : `X` como tiempo trascurrido (años) hasta que el impacto ocurre; estaríamos interesados en valorar la probabilidad del suceso : $P(X \in [0, 100])$
* `rango de X`: $\mathbb{R}^+ = (0,\infty)$

**Cuantificar y expresar valoraciones sobre magnitudes que tienen un valor determinado que desconocemos.**

* `experimento` : dos personas acuerdan que una de ellas lanza un dado y mantiene oculto el resultado para la otra.
* `valores posibles` : $\theta={1,2,3,4,5,6}$
* `No es una variable aleatoria` : $P(\theta=i) = 1/6$
---
* `experimento` :  cuantificar la reducción media de la masa tumoral de enfermos de un tipo de cáncer sometidos a un tratamiento experimental oncológico $\theta$
* `Es un valor desconocido` : el valor concreto de $\theta$ puede considerrse deconocido.
* `conclusión de las expertas` : $P(\theta > 0.05) = 0.1$ ; indicando que es poco probable que el tratamiento experimental reduzca en más de un 5% la masa tumoral.

La asignación de probabilidades en este sentido no es tarea fácil y además, es necesario que la probabilidad definida sea respetuosa con la axiomática de Kolmogorov que son condiciones indispensables para que el cálculo de probabilidades sea consistente. Habitualmente, esta cuantificación se aborda asumiendo que estas magnitudes, θ, son variables aleatorias por lo que la asignación de probabilidades utilizando modelos probabilísticos (Binomial, Normal, Poisson, etc) se convierte en una herramienta muy útil.

> [!NOTE]
> Usaremos la letra mayúscula `P` para hablar de la cuantificación de la probabilidad. Mas adelante usaremos la letra minúscula `p` para hablar de la distribución de probabilidad o función de densidad de una variable aleatoria.

 En el ejemplo de la reducción de masa tumoral, como $\theta$ toma valores en el intervalo **[0,1]** parece razonable asumir que $\theta ∼ beta(a,b)$, lo que también escribimos como  
 
 
 $$p(\theta | a,b) = \text{beta}(\theta | a,b) = \frac{\theta^{a-1}(1-\theta)^{b-1}}{B(a,b)}$$

donde B(a,b) es la función matemática Beta de Euler.

$$
B(a,b) = \int_{0}^{1} x^{a-1} (1-x)^{b-1} \, dx.
$$

`a, b` : para determinar a y b supongamos que el grupo de expertas coincide en que un valor razonable para $\theta$ es 0.07  (es decir una reducción en la masa tumoral del 7\%) e insisten en $P(\theta > 0.05) = 0.1$ . Esto nos llevaría a la definición implícita de a y b como solución del sistema:

$$E(\theta) = \frac{a}{a + b} = 0.07, \quad \int_{0.05}^{1} \text{beta}(\theta | a,b) d\theta = 0.1,$$

Esta integral se corresponde con la `función de distribución (acumulada)` en `0.05` de la variable aleatoria beta correspondiente. 

```{r}
f <- function(b) {
  # Asegúrate de que los parámetros shape1 y shape2 sean positivos
  shape1 <- b * 0.07 / 0.93
  shape2 <- b - 0.9
  if (shape1 <= 0 || shape2 <= 0) {
    return(NA)
  } else {
    return(pbeta(q=0.05, shape1=shape1, shape2=shape2))
  }
}
print(f(0.1))
print(f(1))

# Si todo está bien, ejecuta uniroot
solution <- try(uniroot(f=f, lower=0.1, upper=1), silent=TRUE)

# Verifica si uniroot encontró una solución
if(inherits(solution, "try-error")) {
  print("uniroot encontró un error.")
} else {
  b <- solution$root
  a <- b * 0.07 / 0.93
  print(b)
  print(a)
}
```

En este código hemos usado el comando pbeta(q, shape1, shape2), que proporciona la función de distribución de una variable aleatoria distribuida Beta de parámetros shape1 y shape2. En nuestra expresión de la distribución Beta shape1 es a y shape2 es b. 
