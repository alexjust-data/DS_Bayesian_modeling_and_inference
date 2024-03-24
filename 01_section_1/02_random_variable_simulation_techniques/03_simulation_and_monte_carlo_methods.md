### Simulación y métodos Montecarlo como herramienta numérica para describir una distribución

Cuando hablamos de métodos Montecarlo simplemente nos estamos refiriendo al hecho de usar números aleatorios para aproximar alguna cantidad desconocida. Estos números aleatorios pueden haberse obtenido mediante observación (de una muestra obtenida al azar) o mediante la utilización de números (pseudo)aleatorios obtenidos, por ejemplo, con la `transformada integral de probabilidad`.

En concreto, entre las cantidades desconocidas que se pueden aproximar se encuentran aquellas que nos permiten describir una distribución de probabilidad. Ya sabemos que existen medidas resumen de las distribuciones de probabilidad que nos permiten conocer aspectos básicos de las variables aleatorias que siguen estas distribuciones. Estamos pensando en la esperanza o media de $Y$, la varianza, la mediana, el primer cuartil, o probabilidades de eventos de interés.

Todas las medidas resumen de una distribución se obtienen aplicando distintas operaciones sobre la distribución de probabilidad de $Y$. Si por ejemplo $Y$ es una variable continua (que pueden asumir cualquier valor en un rango, incluyendo fracciones y números decimales.), la esperanza de $Y$ es la integral:

$$
E(Y) = \int_{-\infty}^{\infty} y p(y) dy.
$$

En general, la esperanza de cualquier función $g(Y)$ se obtiene resolviendo la integral:

$$
E(g(Y)) = \int_{-\infty}^{\infty} g(y) p(y) dy.
$$

Otro ejemplo es la mediana, $q_{0.5}$, que es la solución a la ecuación:

$$
\int_{-\infty}^{q_{0.5}} p(y) dy = 0.5,
$$


y así con cualquier otra medida descriptiva de $p(y)$ (lo que a veces se llama medidas poblacionales, entendiendo por “población” el modelo probabilístico $p(y)$). En resumen, para determinar estas características, hay que realizar operaciones matemáticas que a veces pueden ser complejas. Es en este punto en el que la simulación puede sernos de mucha utilidad como un método numérico sencillo de aproximar estas operaciones. El principio en el que está basada esta aproximación es básico en estadística: 

>cualquier magnitud poblacional puede aproximarse utilizando una muestra suficientemente grande de la población. 

Entonces, para aproximar la $E(Y)$ a partir de una simulación

$Y_1,Y_2,\ldots,Y_N$,

utilizamos la lógica:

$$
E(Y) \approx \frac{Y_1 + Y_2 + \ldots + Y_N}{N},
$$

y la aproximación es tanto más precisa cuanto mayor es $N$. Otros ejemplos de aproximaciones serían:

$$
E(g(Y)) \approx \frac{g(Y_1) + g(Y_2) + \ldots + g(Y_N)}{N}.
$$

o

$$
q_{0.5} \approx \text{mediana de} \{Y_1,Y_2,\ldots,Y_N\},
$$

o

$$
P(Y > y) \approx \frac{\text{Número de } Y_i \text{ mayores que } y}{N}
$$