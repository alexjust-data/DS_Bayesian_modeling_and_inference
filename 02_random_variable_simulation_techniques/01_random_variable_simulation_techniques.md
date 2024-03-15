### Técnicas básicas de simulación de variables aleatorias

Simular una variable aleatoria Y con una distribución de probabilidad conocida p(y) es obtener realizaciones $y_1,y_2,y_3,\dots$ de Y independientes.

En casos muy concretos, podemos confeccionar sencillos experimentos que nos permitan simular variables aleatorias. Un ejemplo es el de simular una variable aleatoria distribuida $Y \sim bern(0.8)$. Basta llenar una bolsa con 10 bolas idénticas excepto por el color: 8 son blancas y 2 son negras, y extraer bolas al azar devolviéndolas después a la bolsa. Para cada una de las extracciones anotamos $y_i = 1$ si es blanca y $y_i = 0$ si es negra. En este caso, una posible simulación de tamaño $N = 100$ quedaría:

$y_1 = 1$, $y_2 = 0$, $y_3 = 0$, $y_4 = 1$, $y_5 = 1$, $y_6 = 1$, $y_7 = 0$, ..., $y_{100} = 1$.

Otro ejemplo es el de simular una variable aleatoria uniforme en el intervalo (0,1), es decir, $Y \sim \text{unif}(0,1)$. En este tipo de variables, cualesquiera dos subintervalos de (0,1) con el mismo tamaño tiene asignada la misma probabilidad. Para simular $Y$ (digamos con una precisión de 4 decimales) tenemos que conseguir un dado de 10 caras numeradas del 0 al 9 que lanzamos 4 veces, anotando la puntuación 0622. El valor simulado de Y sería $y = 0.0622$. Si repetimos este experimento 30 veces conseguimos una muestra simulada de $Y$:

0.0622, 0.0317, 0.8779, 0.2765, 0.4290, 0.9858, 0.9532, 0.2770, 0.3342, 0.7574,  
0.8273, 0.9320, 0.8235, 0.8320, 0.2318, 0.6779, 0.8191, 0.9497, 0.0532, 0.8470,  
0.0058, 0.5690, 0.3934, 0.8873, 0.1560, 0.9020, 0.0822, 0.9692, 0.4686, 0.7893  

Estos son ejemplos sencillos y no son prácticos y lo que queremos es simular muchas veces, para lo cual es mejor tener un algoritmo que simule muchas realizaciones de una a la vez y esto lo pueden hacer computadoras usando algoritmos de generación de números aleatorios. En este último caso, partiendo de una variable aleatoria básica que se puede simular fácilmente, como la uniforme $U(0,1)$, es muy importante entender que existían tablas enormes de números aleatorios de este tipo, pero la actualidad estas simulaciones se obtienen utilizando algoritmos numéricos de generación de números aleatorios.


```r
> runif(10)
[1] 0.5519491 0.8165452 0.6338048 0.8875669 0.6292759 0.9251157 
[7] 0.2955939 0.4290943 0.7909494 0.2677865
```

Si has ejecutado el anterior código en tu ordenador, es muy probable que no obtengas los mismos números, pero esto se debe a que estamos simulando variables aleatorias (como si te digo que lances un dado y yo lanzo otro). Hay una forma de que dos usuarios obtengan las mismas simulaciones, y consiste en fijar la semilla (número a partir del cual actúan los algoritmos de secuencias de números aleatorios):

```r
> set.seed(16091956)
> runif(10)
[1] 0.7907290 0.3920964 0.9039974 0.2294803 0.5028575 0.9018944
[7] 0.3123450 0.7317088 0.3127938 0.7121062
```