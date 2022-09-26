@import "../local.less"
# Baseline correction using adaptive iteratively reweighted penalized least squares

## Theory
### Penalized least square algorithm

Assuming $\bold{x}$ is the vector of the analytical signals , and $\bold{z}$ is the fitted vector . The lengths of them are both $m$ The fidelity of $\bold{z}$ to $\bold{x}$ can be expressed as th sum square errors between them:
$$F=\sum_{i=1}^{m}\left(x_i-z_i\right)^2$$

The roughness of the fitted data $\bold{z}$ can be written as its squared and summed differences 
$$R=\sum^{m}_{i=2}(z_i-z_{i-1})^2=\sum^{m-1}_{i=1}(\Delta z_i)^2$$

The first differences penalty is adopted to simplify the presentation here. In most cases, the square of the second roughness . The airPLS Package offers a parameter for users to choose the orders of the differe ces.

 The balance of fidelity and smoothness can be then measured as the fidelity plus with penalties on the roughness, and it can be given by:

 $$\begin{equation}
    Q=F+\lambda R=\|\bold{x}-\bold{z}\|^2+\lambda\|\bold{D}\bold{z}\|^2
 \end{equation}$$

by solving Equation $\frac{\partial Q}{\partial \bold{z}}=0$, we get:

$$\begin{equation}
    (\bold{I}+\lambda\bold{D}^T\bold{D})\bold{z}=\bold{x}
\end{equation}$$

Eqn(2) is a smoothing method using the penalized least squares algorithm. In order to correct a baseline using the penalize. In order to correct a baseline using te penalized least squares algorithm, Cobas and Zhang introduced a weight vector of fidelity, and set zero to the at a position corresponding to peak segments of $\bold{x}$. Fidelity of $\bold{z}$ to $\bold{x}$ is changed to
$$\begin{equation}
    F=\sum^m_{i=1}w_i(x_i-z_i)^2=(\bold{x}-\bold{z})^T\bold{W}(\bold{x}-\bold{z})
\end{equation}$$

$\bold{W}$ is diagonal matrix with $w_i$ on its diagonal.
 The eqn(2) changes to
$$\left(\bold{W}+\lambda \bold{D}^T\bold{D}\right)\bold{z}=\bold{W}\bold{x}$$

Solving the above linear equation, the fitted vector can be obtained easily:

$$\begin{equation}
    \bold{z}=(\bold{W}+\lambda\bold{D}^T\bold{D})^{-1}\bold{W}\bold{x}
\end{equation}$$

The baseline correction methods of Cobas and Zhang both need peak detection before baseline correction,but the existence of a baseline will negatively affect peak detection/

 The adaptive iteratively reweighted procedure is propsed to replace peak detection and special treetment steps.

 ### Adaptively iteratively reweighted procedure

The adaptive iteratively reweighted procedure is similar to the weighted least squares and iteratively rewighted least squares,but using different ways to caluculate the weights and adding a penalty item to control the smoothness of the fitted baseline.Each step of the proposed adaptive iteratively reweighted procedure involves solving a wwighted penalized least squares problem of the following form:
$$\begin{equation}
    Q^t=\sum^m_{i=1}w^t|x_i-z_i^t|+\lambda\sum^m_{j=2}|z^t_j-z^t_{j-1}|
\end{equation}$$

 The weight vector $\bold{w}$ is obtained adaptively using an iterative method. One should give an initial value $\bold{w}^0=1$ at the starting step. After initialization, the $\bold{w}$ of each iterative step $t$ can be obtained using the following expressions:
 $$\begin{equation}
  f(x)=
  \begin{cases}
    0 & x_i>z_i^{t-1}\\
    \exp{\left(\frac{t(x_i-z^{t-1}_t)}{|\bold{d^t}|}\right)} & x_i<z_t^{t-1} \\
  \end{cases}
\end{equation}$$

Vector $\bold{d^t}$ consists of negative elements of the differences between $\bold{x}$ and $\bold{z}^{t-1}$ in the previous (t-1) iteration is a candidate of baseline. If the value of the ith point is greater than the candidate of baseline, it can be regarded as part of a peak. So its weight is set to zero to ignore it at the next iteration of fitting. In the airPLS algorithm , the iterative and reweight methods are used to automatically and gradually eliminate the points of peaks and preserve the baseline points in the weight veector $\bold{w}$.
Iteraton will stop eigher with the maximal iteration times or when the terminative criterion is reached. The termination criterion is defined by:

$$|\bold{d_t}|<0.001\times|\bold{x0}|$$

