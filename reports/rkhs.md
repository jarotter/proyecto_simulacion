#Apéndice C: Espacios de Hilbert con kernel reproductor 

#### Kernels positivos definidos

###### Definición.

Un *kernel positivo definido* en $\mathcal{X}​$ es una función simétrica $\mathrm{K}: \mathcal{X} \times \mathcal{X} \to \mathbb{R}​$ tal que para todo $n \in \mathbb{N}​$, $\{x_i,\dots,x_n\} \subseteq \mathcal{X}​$, y $\{c_i ... c_n \} \subseteq \mathbb{R}​$ se cumple
$$
\sum_{i,j=1}^n c_ic_i K(x_i,x_j) \geq 0
$$

###### Observación.

La definición 1 es equivalente a pedir que para cualquier conjunto $\{x_1, \cdots , x_n\}\subseteq\mathcal{X}$, la matriz $\mathbb{G}$ con $ (\mathbb{G})_{ij} = \mathrm{K}(x_i,x_j) $ sea (semi) positiva definida

Las siguientes proposiciones presentan formas en que se pueden construir kernels positivos definidosusando otros kernels y productos interiores.

###### Proposición.

Si $\mathrm{K}_1, \mathrm{K}_2 : \mathcal{X} \times \mathcal{X} \to \mathbb{R}$ son kernels positivos definidos, entonces los siguientes también lo son

- $a\mathrm{K}_1 + b\mathrm{K}_2$ con $ a,b \geq 0$
- $\mathrm{K}_1\mathrm{K}_2$
- $\lim\limits_{i\to\infty}  {K}_i$

###### Proposición.

Si $\mathrm{K}$ es un kernel positivo definido y $f:\mathcal{X} \to \mathbb{R}$ una función arbitraria, entonces $\tilde{K}(x,y)=f(x) \mathrm{K}(x,y)f(y)$ y  $K'(x,y)=f(x)f(y)$ son positivos definidos.

> *Demostración*
>
> Probemos que $\mathrm{K(x,y)} = f(x)f(y)$ es un kernel positivo definido. La simetría es inmediata, asimismo cumple $(1)$ pues
> $$
> \begin{align*}
> \sum_{i=1}^n\sum_{j=1}^n \mathrm{K}(x_i,x_j)c_ic_j &= \sum_{i=1}^n\sum_{j=1}^n f(x_i)f(x_j)c_ic_j \\ \\
> &= \left(\sum_{i=1}^nf(x_i)c_i \right)^2 \\
> &\geq 0 
> \end{align*}
> $$
> La prueba de $f(x) \mathrm{K}(x,y)f(y)$ queda como ejercicio al lector. $_\square$ 

###### Proposición.

Sea $(\mathrm{V} , \langle\cdot,\cdot\rangle)$ un espacio vectorial con producto interior. Para todo mapeo $\Phi : \mathcal{X} \to \mathrm{V}$, $\langle\Phi(x),\Phi(y)\rangle$ es un kernel definido positivo.

> *Demostración*
>
> Sean $\{x_i,\dots,x_n\} \subseteq \mathcal{X}$, y $\{c_i ... c_n \} \subseteq \mathbb{R}$
> $$
> \begin{align*}
> \sum_{i,j=1}^n c_ic_k\mathrm{K}(x_i,x_j) &= \left\langle\sum_{i=1}^nc_i\Phi(x_i),\sum_{i=1}^nc_k\Phi(x_j) \right\rangle \\
> &= \left\Vert \sum_{i=1}^n c_i\Phi(x_i)\right\Vert \\
> &\geq 0 \ _\square
> \end{align*}
> $$
>

###### Ejemplos.

$$
\begin{align*}
\text{Kernel lineal} && \mathrm{K}(x,y) &= x^Ty  \\
\text{Kernel Gaussiano} && \mathrm{K}(x,y) &= \exp\left(-\frac{1}{2\sigma^2}\Vert x-y \Vert^2\right)  \\
\text{Kernel Laplaciano} && \mathrm{K}(x,y) &= \exp\left(-\alpha \sum\limits_{i=1}^n|x_i-y_i|\right) \\
\end{align*}
$$

#### Espacios de Hilbert con Kernel reproductor

###### Definición.

Un *Espacio de hilbert con kernel reproductor* (RKHS por sus siglas en inglés) sobre $\mathcal{X}$ es un espacio de Hilbert $\mathcal{H}$ conformado por funciones en $\mathcal{X}$, tal que el funcional evaluacion
$$
\begin{align*}
e_x : \mathcal{H} \to \mathbb{K}, && e_x(f) = f(x)
\end{align*}
$$
es continuo para toda $x \in \mathcal{X}$.

###### Observación.

Por el teorema de representación de Riesz, $\forall x \in \mathcal{X}$, podemos escribir el funcional lineal $e_x$ como
$$
\begin{align}
e_x(f) := f(x) = \langle f, K_x\rangle && \forall f \in \mathcal{H}
\end{align}
$$
En particular, $K_x$ es una función en $\mathcal{H}$ de forma que si $y\in\mathcal{X}$, por el teorema de representación obtenemos
$$
K_x(y) = \langle K_x, K_y \rangle
$$
###### Definición.

A la propiedad $(2)$ le llamamos *reproducibilidad*. 

###### Definición.

El *kernel reproductor* de un RKHS es la función
$$
\begin{align*}
\mathrm{K}: \mathcal{X} \times \mathcal{X} \to \mathbb{R} && \mathrm{K}(x,y) := K_x(y)
\end{align*}
$$

Hemos visto como un RKHS define un *kernel reproductor* (el lector deberá convencerse de que es simétrico y positivo), pero cabe cuestionarse si el converso es cierto. La respuesta se debe a Moore.

###### Teorema (Moore–Aronszajn, 1950)

Sea $\mathrm{K}: \mathcal{X} \times \mathcal{X} \to \mathbb{R}$ un kernel positivo definido. Entonces, existe un único RKHS $\mathcal{H}_\mathrm{K}$ tal que:

- $\mathrm{K}(\cdot,x):=\mathrm{K}_x \in \mathcal{H}_\mathrm{K} \quad \forall x \in \mathcal{X}$
- $\mathrm{span}\{\mathrm{K}_x: x \in \mathcal{X}\}$ es denso en $\mathcal{H}_\mathrm{K}$
- $\mathrm{K}$ es un kernel reproductor de $\mathcal{H}_\mathrm{K}$

###### Demostración.

> Ver la prueba en [x] $_\square$
>
> http://members.cbio.mines-paristech.fr/~jvert/svn/kernelcourse/notes/aronszajn.pdf

###### Definición.

Sea  $F : \mathcal{H} \to \mathbb{K}$ un funcional. El *gradiente funcional* de $F$ denotado por $\nabla_f F(f)$ es una función en $\mathcal{H}$ tal que $F(f + \epsilon g(x)) = F(f) + \epsilon\langle \nabla_f F(f),g\rangle_{\mathcal{H}} + O(\epsilon^2)$ para cualquier $g \in \mathcal{H}$ y $\epsilon \in \mathbb{R}$

