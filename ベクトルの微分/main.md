# ベクトル，行列，スカラー微分

## 定義

$$\begin{equation}
    \boldsymbol{x}=
    \begin{bmatrix}
        x_1\\
        \vdots \\
        x_n
    \end{bmatrix}
\end{equation}$$

$$X=\begin{bmatrix}
x_{11} & \cdots & x_{1n} \\
\vdots & x_{ij} & \vdots \\
x_{m1} & \cdots & x_{mn}
\end{bmatrix}$$

$$\begin{equation}
    f(\boldsymbol{x})=f(x_1,\cdots,x_n)
\end{equation}$$

$$\begin{equation}
    \boldsymbol{f}(x)=
    \begin{bmatrix}
        f_1(x) \\
        \vdots \\
        f_n(x)
    \end{bmatrix}
\end{equation}$$

$$\begin{equation}
    \boldsymbol{f}(\boldsymbol{x})=
    \begin{bmatrix}
        f_1(x_1,\cdots,x_n)\\
        \vdots\\
        f_m(x_1, \cdots ,x_n)
    \end{bmatrix}
\end{equation}$$

$$\begin{equation}
    \boldsymbol{F}(x)=
    \begin{bmatrix}
        F_{11}(x) & \cdots &F_{1n}(x)\\
        \vdots & F_{ij}(x) &\vdots \\
        F_{m1}(x)&\cdots &F_{mm}(x)
    \end{bmatrix}
\end{equation}$$

 
## ベクトルをベクトルで微分


### 定義

$$\begin{equation}
    \begin{aligned}
        \boldsymbol{y} \in \R^m\\
        \boldsymbol{x} \in \R^n \\
    \end{aligned}
\end{equation}$$

のとき，
$$\begin{equation}
    \frac{\partial \boldsymbol{y}}{\partial \boldsymbol{x}}=
    \begin{pmatrix}
        \frac{\partial y_1}{\partial x_1} & \cdots & \frac{\partial y_j}{\partial x_1} & \cdots & \frac{\partial y_m}{\partial x_1} \\
        \vdots & \ddots &  &  & \vdots \\
        \frac{\partial y_1}{\partial x_1} & \cdots & \frac{\partial y_j}{\partial x_i} & \cdots & \frac{\partial y_m}{\partial x_i}\\
        \vdots & & &\ddots & \vdots\\
        \frac{\partial y_1}{\partial x_n} &\cdots &\frac{\partial y_j}{\partial x_n}&\cdots &\frac{\partial y_m}{\partial x_n}
    \end{pmatrix}
    \in R^{n×m}
\end{equation}$$

となる.つまり，結果は(n×m)の行列となる．

### 公式
$$\begin{equation}
    \frac{\partial}{\partial \boldsymbol{x}}\boldsymbol{x}=I \in R^{n\times n}
\end{equation}$$

$$\begin{equation}
    \frac{\partial}{\partial \boldsymbol{x}}A\boldsymbol{x}=A^{T}\space A \in R^{n\times n}
\end{equation}$$
$$\begin{equation}
    
\end{equation}$$
> https://qiita.com/paopao_stat/items/c7020001ebb0414cddaa

## スカラーをベクトルで微分するときの定義

多変数関数$f(x_1,x_2,x_3,\cdots,x_n)$に対して，各変数による偏微分をならべたベクトルを勾配ベクトルという．

> https://mathwords.net/bekutorubibun
