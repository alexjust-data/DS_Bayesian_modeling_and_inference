### Simulación de vectores aleatorios

No existe una generalización del método de Montecarlo para simular un vector aleatorio $Y = (Y_1, Y_2, \ldots, Y_k)$ con distribución conjunta $p(y)$ y cuyos componentes no sean independientes (si son independientes basta aplicar el método a cada uno de los componentes por separado). Si conocemos la distribución marginal $p(y_1)$ y las condicionales:

$$
p(y_2 | y_1), p(y_3 | y_1, y_2), \ldots, p(y_k | y_1, y_2, \ldots, y_{k-1}),
$$

y sabemos simular de ellas, entonces por un proceso iterativo podemos conseguir una simulación de $Y$.

En concreto, repetimos para $i = 1,2, \ldots, N$ el proceso:

- **Paso 1** Simula $Y_1$ de $p(y_1)$ (obteniendo $y_1$);
- **Paso 2** dado el valor simulado anterior, simula $Y_2$ de $p(y_2 | y_1)$ (obteniendo $y_2$);
- **Paso 3** dado los valores simulados anteriores, simula $Y_3$ de $p(y_3 | y_1, y_2)$ (obteniendo $y_3$);
- **Paso ...**
- **Paso $k$** dados los valores simulados anteriores, simula $Y_k$ de $p(y_k | y_1, y_2, \ldots, y_{k-1})$ (obteniendo $y_k$)



```r
> y.sim<- rep(0, 40)
> mu<- -12; sigma<- 2; rho<- 0.7
> y.sim[1]<- mu
> for (i in 2:40){
+ y.sim[i]<- mu+rho*y.sim[i-1]+rnorm(1, sd=sigma) +}
```



En la Figura 6 hemos representado N = 9 simulaciones (por tanto 9 ejecuciones del código anterior) utilizando la instrucción $plot(y.sim, type="l"$).

El _i-ésimo_ valor simulado del vector $Y$ es $y_i = (y_1, y_2, \ldots, y_k)$.

En ocasiones, la función conjunta viene especificada con las condicionales anteriores, simplificando el proceso de simulación de un vector aleatorio. Veamos esta situación simulando del modelo de la ecuación 6 propuesto para las temperaturas en el ártico, $Y$, en el ejemplo 8. La lógica que seguimos para construir esta simulación es que dadas las temperaturas, $y_1, y_2, \ldots, y_{i-1}$ hasta el día $i$, la temperatura en el siguiente día es

$$
Y_i = \mu + \epsilon_i,
$$

donde $\epsilon_i$ ~ normal(0, $\sigma$). Con el siguiente bucle, en el que practicamos los pasos descritos anteriormente, obtenemos una simulación de $Y$ de $n = 40$ días seguidos de temperaturas que coleccionamos en el vector $y.sim$. Hemos supuesto que la temperatura el primer día era de –12 grados y para la simulación hemos supuesto $\mu = –12$, $\sigma = 2$ y $\rho = 0.7$ con:


> ##### Figura 6. 
> Representación de 9 simulaciones del vector de temperaturas en 40 días consecutivos siguiendo el modelo autorregresivo de orden 1

![](/img/8.png)

```r
> plot(y.sim, type="l")
```
