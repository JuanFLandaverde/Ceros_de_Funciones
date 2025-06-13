# Fundamentos Teóricos de Métodos Numéricos

Este archivo contiene una descripción breve y teórica de los métodos numéricos implementados en este repositorio, enfocados en la solución de ecuaciones no lineales de la forma:

$$
f(x) = 0
$$

## 📐 1. Método de Bisección

Es un método **cerrado** que requiere que la función $$f(x)$$ sea continua en el intervalo $$[a, b]$$ y que se cumpla $$f(a) \cdot f(b) < 0$$ (cambio de signo).

**Idea**: En cada iteración se divide el intervalo a la mitad y se selecciona el subintervalo donde persiste el cambio de signo.

- Convergencia: **lineal**  
- Ventajas: siempre converge si se cumplen las condiciones  
- Desventajas: lento en comparación con otros métodos

---

## 📉 2. Método de Newton-Raphson

Es un método **abierto** que usa la derivada de la función para aproximar la raíz:

$$
x_{n+1} = x_n - \frac{f(x_n)}{f'(x_n)}
$$

**Requiere** una estimación inicial $$x_0$$ y que $$f'(x) \neq 0$$ cerca de la raíz.

- Convergencia: **cuadrática** (cuando converge)  
- Ventajas: muy rápido si se tiene buena aproximación inicial  
- Desventajas: puede divergir si $$f'(x)$$ se anula o es muy pequeña

---

## 📈 3. Método de la Secante

Similar a Newton-Raphson, pero no requiere la derivada. Usa una aproximación con diferencias finitas:

$$
x_{n+1} = x_n - f(x_n) \cdot \frac{x_n - x_{n-1}}{f(x_n) - f(x_{n-1})}
$$

- Convergencia: **superlineal** ($$\approx 1.618$$)  
- Ventajas: no necesita derivada  
- Desventajas: requiere dos estimaciones iniciales

---

## ⚖️ 4. Método de Regula-Falsi (Falsa Posición)

Es un método **cerrado** como la bisección, pero en lugar de usar el punto medio del intervalo, calcula el punto donde la línea secante entre $$f(a)$$ y $$f(b)$$ corta el eje $$x$$.

La fórmula para encontrar la siguiente aproximación $$x_r$$ es:

$$
x_r = b - \frac{f(b)(a - b)}{f(a) - f(b)}
$$

Luego se evalúa el signo de $$f(x_r) \cdot f(a)$$ para decidir el nuevo intervalo, igual que en la bisección.

- Convergencia: **lineal** (más rápida que bisección en muchos casos)  
- Ventajas: más eficiente que la bisección  
- Desventajas: puede estancarse si uno de los extremos no se actualiza (problema de "anclaje")

---

## 🔁 5. Método de Punto Fijo

Reescribe la ecuación original como $$x = g(x)$$, y se itera:

$$
x_{n+1} = g(x_n)
$$

Para que el método converja, la función $$g(x)$$ debe cumplir:

- Ser continua  
- $$|g'(x)| < 1$$ en el intervalo

- Convergencia: **lineal**  
- Ventajas: simple de implementar  
- Desventajas: depende fuertemente de la elección de $$g(x)$$


---
## ⚡ 6. Aceleración de Aitken (Δ²)

Mejora la convergencia de métodos iterativos lineales como el de punto fijo, aplicando la fórmula:

$$
x^* \approx x_n - \frac{(x_{n+1} - x_n)^2}{x_{n+2} - 2x_{n+1} + x_n}
$$

- Convergencia: más rápida  
- Requiere tres iteraciones sucesivas

---

## ⚙️ 7. Método de Steffensen

Evita el uso de derivadas como Newton, aplicando una técnica similar a Aitken pero internamente:

$$
x_{n+1} = x_n - \frac{[g(x_n) - x_n]^2}{g(g(x_n)) - 2g(x_n) + x_n}
$$

- No necesita derivadas  
- Convergencia: **cuadrática**

---

## 🧮 8. Método de Horner

Optimiza la evaluación de polinomios y su derivada:

Dado un polinomio:

$$
P(x) = a_nx^n + a_{n-1}x^{n-1} + \dots + a_0
$$

Horner lo reescribe como:

$$
P(x) = (\dots((a_nx + a_{n-1})x + a_{n-2})x + \dots ) + a_0
$$

- Menor complejidad computacional  
- Utilizado en combinación con Newton para raíces de polinomios

---

## 🔎 9. Método de Müller

Extiende la secante usando una parábola para interpolar tres puntos $$x_{n}, x_{n-1}, x_{n-2}$$. Resuelve la ecuación cuadrática que pasa por ellos para estimar la raíz.

- Puede encontrar raíces **complejas**
- Convergencia: **superlineal**
- No requiere derivadas

---

## 📊 6. Análisis de Convergencia

Durante la ejecución de algunos métodos (como Newton y Secante), se guarda el error relativo en cada iteración:

$$
e_n = |x_n - x^*|
$$

La **orden de convergencia** $$p$$ se estima empíricamente usando regresión lineal log-log sobre la relación:

$$
\log(e_{n+1}) = \log(C) + p \log(e_n)
$$

donde $$C$$ es la constante de convergencia.

---


