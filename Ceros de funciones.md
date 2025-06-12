# Métodos Numéricos Utilizados

Este código implementa una solución numérica para un sistema de ecuaciones diferenciales acopladas, típicas en cinética química, usando el **método de Runge-Kutta de cuarto orden (RK4)**. Este método permite obtener soluciones aproximadas de alta precisión para sistemas de la forma:

\[
\frac{d\mathbf{y}}{dt} = \mathbf{f}(t, \mathbf{y})
\]

donde \( \mathbf{y} \) es un vector de variables dependientes del tiempo, y \( \mathbf{f} \) representa la función vectorial que describe la dinámica del sistema.

---

## Método de Runge-Kutta de 4º Orden (RK4)

El método RK4 para un solo paso desde \( t_n \) hasta \( t_{n+1} = t_n + h \) se define como:

\[
\begin{aligned}
k_1 &= f(t_n, y_n) \\
k_2 &= f\left(t_n + \frac{h}{2}, y_n + \frac{h}{2}k_1\right) \\
k_3 &= f\left(t_n + \frac{h}{2}, y_n + \frac{h}{2}k_2\right) \\
k_4 &= f(t_n + h, y_n + hk_3) \\
y_{n+1} &= y_n + \frac{h}{6}(k_1 + 2k_2 + 2k_3 + k_4)
\end{aligned}
\]

Este proceso se repite para cada paso de tiempo.

---

## Aplicación al Sistema de Reacciones

Las ecuaciones modeladas corresponden a reacciones químicas entre diversas especies, cuya velocidad depende de constantes cinéticas \( k_i \) y de las concentraciones de reactivos. Por ejemplo:

\[
\frac{d[A]}{dt} = -k_1 [A][B] + k_2 [C]
\]

\[
\frac{d[B]}{dt} = -k_1 [A][B]
\]

\[
\frac{d[C]}{dt} = k_1 [A][B] - k_2 [C]
\]

Cada una de estas ecuaciones se resuelve de forma simultánea mediante el método RK4.

---

## Ventajas del Método RK4

- Alta precisión sin necesidad de derivadas de orden superior.
- Adecuado para sistemas acoplados y no lineales.
- Buen compromiso entre exactitud y complejidad computacional.

---

## Consideraciones

- El paso de tiempo \( h \) debe ser suficientemente pequeño para garantizar la estabilidad numérica.
- Las condiciones iniciales y constantes de reacción deben estar bien definidas para obtener soluciones físicas realistas.

---

Este enfoque permite modelar dinámicamente la evolución temporal de especies químicas en sistemas complejos como los involucrados en catálisis o degradación de contaminantes.

