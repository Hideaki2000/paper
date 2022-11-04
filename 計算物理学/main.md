@import "../local.less"
# ヌメロフ法による2階常微分方程式の解法，数値計算

次の1次元シュレディンガー方程式を考える。
$$\begin{equation}
  \left(-\frac{h^2}{2m}\frac{d^2}{dx^2}+V(x)\right)\psi(x)=E\psi(x)
\end{equation}$$
となる。
ここで
$$\begin{equation}
  Q(x)=\frac{2m}{h^2}[E-V(x)]
\end{equation}$$
と定義すると。(1)の式は次のようになる
$$\begin{equation}
  \left(\frac{d^2}{dx^2}+Q(x)\right)\psi(x)=0
\end{equation}$$
問題設定は与えられた任意の$Q(x)$に対して(3)式を解き、固有値$E$と固有状態$\psi(x)$を得ることである。これに対する解法の一つが「繰り込みヌメロフ法」と呼ばれる。
## ヌメロフ法
離散化された関数を$\psi_n=\psi(x_n)$,$Q_n=Q(x_n)$とすると、$\psi_{n+1}$と$\psi_{n-1}$は$x=x_n$周りでテイラー展開して、
それぞれ
$$\begin{equation}
  \psi_{n+1}=\sum^{\infin}_{k=0}\frac{h^k}{k!}\psi_n^{(k)},\psi_{n-1}=\sum^{\infin}=\frac{(-h)^k}{k!}\psi_n^{(k)}
\end{equation}$$
と記述できる。これを用いると
$$\begin{equation}
  \frac{1}{2}\left(\psi_{n+1}+\psi_{n-1}\right)=\psi_n+\frac{1}{2}h^2\psi^{(2)}_n+\frac{1}{4!}h^4\psi^{(4)}_n+\frac{1}{6!}h^6\psi^6_n+\cdots
\end{equation}$$
また
$$\begin{equation}
  \frac{1}{2}\left(\psi_{n+1}^{(2)}+\psi_{n-1}^{(2)}\right)=\psi_n^{(2)}+\frac{1}{2}h^2\psi^{(4)}_n+\frac{1}{4!}h^4\psi^{(6)}_n+\cdots
\end{equation}$$
これらの式を用いることで、次のような式になる
$$\begin{equation}
  \frac{1}{2}(\psi_{n+1}+\psi_{n-1})-\frac{1}{2}\frac{h^2}{12}(-Q_{n+1}\psi_{n+1}-Q_{n-1}\psi_{n-1})=\psi_{n}-\frac{5}{12}h^2Q_n\psi_n-\frac{h^6}{480}\psi_n^{(6)}
\end{equation}$$
ここで波動関数を左辺に、6階以上の微分以降を０にして、
$$T_n=-\frac{h^2}{12}\psi_n^{6}$$
とすると
$$\begin{equation}
  (1-T_n)\psi_{n+1}-(2+10T_n)\psi_n+(1-T_{n-1})\psi_{n-1}=0
\end{equation}$$
この近似式を用いて境界条件を解くこれがヌメロフ法である。
[参考](https://qiita.com/sci_Haru/items/338a5bb68ce17189917b)

# 密度汎関数理論

密度汎関数理論では、電子軌道は、個々の電子軌道と言うよりはむしろ電子密度に依存しているシュレディンガー方程式の階である階である