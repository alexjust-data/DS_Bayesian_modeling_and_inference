
### Formulario

La notación se ha adaptado, en parte, a la utilizada en la segunda edición del libro Doing Bayesian Analysis, de John K. Kruschke.

- Las variables aleatorias vendrán determinadas, en general, por letras en mayúscula, mientras que la minúscula se reserva para las observaciones o realizaciones de dicha variable.

- Dada una variable aleatoria, llamamos **rango** al conjunto de valores que esta puede tomar.

- La distribución de una variable aleatoria viene determinada por su función de probabilidad o de densidad, dependiendo de si esta es discreta o continua, respectivamente. Estas funciones las representamos por la letra $p$ minúscula y vendrán determinadas por parámetros que se indicarán haciendo uso del símbolo de condicionado: $p( \cdot | a,b)$.

- Si el contexto no es lo suficientemente claro, la letra $p$ irá acompañada del subíndice de la variable a la que hace referencia (por ejemplo, $p_x$), aunque, por simplicidad, este se eliminará siempre que sea posible.

- En ocasiones la letra $p$ se sustituye por la notación correspondiente a la distribución que representa (por ejemplo, $\text{gamma}( \cdot | a,b)$; $\text{normal}( \cdot | \mu,\sigma)$).

- $E(\cdot)$ hace referencia al valor esperado de una variable aleatoria, mientras que $\text{Var}(\cdot)$ representa la varianza.

- La letra $P$ mayúscula hará referencia a la probabilidad de un suceso en general (por ejemplo, $P(X > 0)$).

- La letra $\theta$ representará una cantidad desconocida de interés, siendo $\Theta$ el espacio de valores que podría tomar.

- El uso de la negrita en las fórmulas matemáticas quedará reservado, en general, para la representación de vectores, tanto de variables aleatorias como de parámetros o de observaciones.

- La función de verosimilitud para una cantidad o conjunto de cantidades desconocidas $\theta$ dado un vector de observaciones $y$ vendrá representada por la notación $L(\theta,y)$.


> Nota
>
>Siguiendo la notación anterior, dada una variable $X$ con función de densidad o probabilidad $p(\cdot)$, que depende de un vector de parámetros $\theta$, y un valor concreto de su rango $x$, podremos encontrarnos con las siguientes expresiones equivalentes:
>
>- $p_X(x) = P(X = x)$
>- $p_X( \{ x \} ) = p(x = x | \theta)$
>- $\text{distribución}(X = x | \theta) = \text{distribución}(x | \theta)$
>
>Además, si $X$ es una variable aleatoria discreta, estas expresiones coinciden con la probabilidad $P(X = x)$.

<br>

### 1. Teorema de Bayes

#### 1.1 Versión clásica

Pongamos que los posibles eventos son $A$ y $B$:

$$
P(A | B) = \frac{P(B | A)P(A)}{P(B)}.
$$

Cuando el espacio muestral asociado al evento $A$ se puede expresar como unión excluyente de $k$ sucesos, es decir, $A_1 \cup A_2 \cup \ldots \cup A_k$, entonces la regla de Bayes se puede expresar como:

$$
P(A_i | B) = \frac{P(B | A_i)P(A_i)}{\sum_{j=1}^{k}P(B | A_j)P(A_j)}.
$$

<br>

#### 1.2 Teorema de Bayes para variables aleatorias discretas

En variables aleatorias discretas, la función de probabilidad condicional $P(X = x | Y = y)$ es la probabilidad de que $X$ valga $x$ sabiendo que $Y = y$. La función que retorna, para cada valor de $x$ en su rango, la probabilidad $P(X = x | Y = y)$ se llama _distribución condicional de $X$ dado $Y = y$_.

El teorema de Bayes establece que la probabilidad condicional se puede calcular como un sencillo cociente

$$
P(X = x | Y = y) = \frac{P(X = x, Y = y)}{P(Y = y)} = \frac{P(Y = y | X = x)P(X = x)}{P(Y = y)}
$$

Si el rango de $X$ es el conjunto $R \subseteq \mathbb{R}$, entonces:

$$
P(X = x | Y = y) = \frac{P(Y = y | X = x)P(X = x)}{\sum_{x'}P(Y = y | X = x')P(X = x')}.
$$

<br>

#### 1.3 Teorema de Bayes para variables aleatorias continuas

El teorema de Bayes en su versión continua establece una fórmula para la distribución condicional:

$$
p(x | Y = y) = \frac{p(X = x, Y = y)}{p(Y = y)} = \frac{p(Y = y | X = x)p(X = x)}{p(Y = y)}
$$

Si el rango de la variable aleatoria $X$ es el intervalo $R \subset \mathbb{R}$, entonces la fórmula anterior se puede escribir como:

$$
p(x | Y = y) = \frac{p(Y = y | X = x)p(X = x)}{\int_{R} p(Y = y | X = x')p(X = x')dx'}
$$

<br>

#### 1.4 Versión bayesiana del teorema de Bayes

El aspecto particular del método bayesiano es actualizar la información sobre una cantidad desconocida o una vez conocidos los datos. En particular, dado un vector de observaciones $y$, y el objeto matemático que contiene la actualización de la información es la distribución condicional $p(\theta | y)$, conocida como distribución _a posteriori_ y que se obtiene en virtud del teorema de Bayes como:

$$
p(\theta | y) = \frac{L(\theta, y)p(\theta)}{p(y)}
$$

Donde $L(\theta, y)$ es la función de verosimilitud para $\theta$ y $y$ se obtiene a partir de la distribución conjunta para el vector de observaciones $p(y | \theta)$. El valor que aparece en el denominador $p(y)$ es la distribución conjunta marginal de $Y$, que dado un vector de observaciones $y$, es una constante. Por este motivo es habitual encontrar el teorema de Bayes escrito en su forma proporcional:

$$
p(\theta | y) \propto L(\theta, y)p(\theta).
$$

<br>

### 2. Distribuciones para variables aleatorias discretas


#### 2.1 Variable aleatoria con distribución Bernoulli/Binomial

**Definición**: una variable aleatoria $X$ sigue una distribución de Bernoulli con parámetro $\pi$ ( $0 \leq \pi \leq 1$ ) y se denota $X \sim \text{bern}(\pi)$ si $X$ solo puede tomar los valores 0 o 1 con probabilidades $P(X = 1) = \pi$ y $P(X = 0) = 1 - \pi$.

Su función de probabilidad se puede escribir de forma compacta como:

$$
p(x|\pi) = \pi^x(1 - \pi)^{(1-x)}.
$$

Sus momentos son:

- $E(X) = 1 \times \pi + 0 \times (1 - \pi) = \pi$
- $\text{Var}(X) = E(X^2) - [E(X)]^2 = \pi - \pi^2 = \pi(1 - \pi)$

La suma de variables Bernoulli independientes sigue una distribución binomial.

**Definición**: una variable $X$ tiene una distribución binomial de parámetros $N$ y $\pi$ y se denota $X | N,\pi \sim \text{binomial}(N,\pi)$ cuando su función de probabilidad tiene la siguiente forma:

$$
p(x | N,\pi) = \binom{N}{x} \pi^x(1 - \pi)^{(N-x)} \quad \text{para } x = 0,1,\ldots,N.
$$

Sus momentos son:

- $E(X) = N\pi$
- $\text{Var}(X) = N\pi(1 - \pi)$

<br>

#### 2.2 Variable aleatoria con distribución de Poisson

**Definición**: una variable aleatoria $X$ sigue una distribución de Poisson de parámetro $\lambda$ y se denota $X | \lambda \sim \text{Poisson}(\lambda)$ cuando la probabilidad de $x$ se puede expresar como:

$$
p(x | \lambda) = \frac{e^{-\lambda}\lambda^x}{x!} \quad \text{para } x = 0,1,2,\ldots
$$

Sus momentos son:

- $E(X) = \lambda$
- $\text{Var}(X) = \lambda$

<br>

### 3. Distribuciones para variables aleatorias continuas

#### 3.1 Variable aleatoria con distribución uniforme

**Definición**: una variable aleatoria $X$ tiene una distribución uniforme en el intervalo $(a,b)$ y se denota $X | (a,b) \sim \text{unif}(a,b)$ si su función de densidad es

$$
p(x | a,b) = \frac{1}{b-a} \quad \text{para } a < x < b.
$$

Sus momentos son:

- $E(X) = \frac{a+b}{2}$
- $\text{Var}(X) = \frac{(b-a)^2}{12}$

<br>

##### 3.2 Variable aleatoria con distribución normal

**Definición**: decimos que una variable aleatoria $X$ tiene una distribución normal de parámetros $\mu$ y $\sigma$ y se denota $X | \mu,\sigma \sim \text{normal}(\mu,\sigma)$ para $-\infty < \mu < \infty$, $\sigma > 0$ si su función de densidad puede expresarse como:

$$
p(x | \mu, \sigma) = \frac{1}{\sigma\sqrt{2\pi}} \exp \left[ -\frac{1}{2} \left( \frac{x-\mu}{\sigma} \right)^2 \right].
$$

Sus momentos son:

- $E(X) = \mu$
- $\text{Var}(X) = \sigma^2$

<br>

#### 3.3 Variable aleatoria con distribución gamma

**Definición**: decimos que una variable $X$ sigue una distribución gamma de parámetros $a > 0$, $b > 0$ y denotamos $X | (a,b) \sim \text{Gamma}(a,b)$ si su función de densidad es

$$
p(x | a,b) = \frac{b^a}{\Gamma(a)}x^{(a-1)}e^{-bx} \quad \text{para } x > 0,
$$

donde $\Gamma(a)$ es la función gamma:

$$
\Gamma(a) = \int_{0}^{\infty} x^{(a-1)}e^{-x}dx
$$

Sus momentos son:

- $E(X) = \frac{a}{a+b}$
- $\text{Var}(X) = \frac{ab}{(a+b)^2(a+b+1)}$

<br>

#### 3.4 Variable aleatoria con distribución beta

**Definición**: una variable aleatoria $X$ tiene una distribución beta con parámetros $a > 0$ y $b > 0$ y se denota $X | (a,b) \sim \text{beta}(a,b)$ si su función de densidad es:

$$
f(x | a,b) = \frac{\Gamma(a+b)}{\Gamma(a)\Gamma(b)} x^{(a-1)}(1-x)^{(b-1)} \quad \text{para } 0 < x < 1.
$$

Sus momentos son:

- $E(X) = \frac{a}{a+b}$
- $\text{Var}(X) = \frac{ab}{(a+b)^2(a+b+1)}$

<br>

#### 3.5 Variable aleatoria con distribución ji-cuadrada

**Definición**: una variable aleatoria $X$ sigue una distribución ji-cuadrada con $\nu > 0$ grados de libertad y denotamos $X | \nu \sim \chi^2(\nu)$ si su función de densidad se puede expresar como:

$$
p(X | \nu) = \frac{2^{-\nu/2}}{\Gamma(\nu/2)} X^{\nu/2-1}e^{-X/2}, \quad X > 0.
$$

Sus momentos son:

- $E(X) = \nu$
- $\text{Var}(X) = 2\nu$

<br>

#### 3.6 Variable aleatoria con distribución t-Student

**Definición**: en una variable $T = \frac{Z}{\sqrt{V/\nu}}$, donde $Z \sim \text{normal}(0,1)$ y $V \sim \chi^2(\nu)$, decimos que $T$ sigue una distribución t de Student con $\nu$ grados de libertad y lo denotamos por $T \sim t\text{-Student}(\nu)$. La densidad de esta distribución viene dada por:

$$
p(t | \nu) = \frac{\Gamma \left( \frac{\nu+1}{2} \right)}{\sqrt{\nu\pi} \Gamma \left( \frac{\nu}{2} \right)} \left( 1+\frac{t^2}{\nu} \right)^{-\frac{\nu+1}{2}}.
$$


Sus momentos son:

- $E(T) = 0$ si $\nu > 1$ y no existe en otro caso.
- $\text{Var}(T) = \frac{\nu}{\nu-2}$ si $\nu > 2$ y no existen en otro caso.

> **Nota**
> La distribución de Cauchy es un caso particular de la distribución t-Student con un grado de libertad ($\nu = 1$).
