# Matematická úloha

Z náhledu rozdělení

<p align="left">
  <img src="https://github.com/user-attachments/assets/51695bfb-3267-42b7-8636-7a5a0bb19461" alt="Chart" width="300"/>
</p>

lze důvodně předpokládat, že se bude jednat o Poissonovo.

## Vzorce k použití

$$P(R)=\sum P(R|B_i)P(B_i)$$

$$P(B_j|R)=\frac{P(R|B_j)P(B_j)}{\sum P(R|B_i)P(B_i)}$$

$$P(B \geq 1 \vee R \geq 1)=1-P(B=0 \wedge R=0)$$

$$P(B=0 \wedge R=0)=P(B=0)+P(R=0)-P(B=0\vee R=0)$$


## Výpočet
$$0,25=P(B=R)=\sum_{i=0}^{\max k}\left(e^{-\lambda_1}\frac{\lambda_1^i}{i!}\right)\left(e^{-\lambda_2}\frac{\lambda_2^i}{i!}\right)$$

$$0,4=P(B>R)=\sum_{i=0}^{\max k \,(=10)}\sum_{j=0}^{i-1}\left(e^{-\lambda_1}\frac{\lambda_1^i}{i!}\right)\left(e^{-\lambda_2}\frac{\lambda_2^j}{j!}\right)$$

$$0,5=P(B+R\leq 2)=\sum_{i=0}^{2}\left(e^{-(\lambda_1 +\lambda_2)}\frac{(\lambda_1+\lambda_2)^k}{k!}\right)$$

Minimalizujeme chybu.

$$error=\left[ (P(B>R)-0,4)^2+(P(B=R)-0,25)^2+(P(B+R\leq 2)-0,5)^2 \right]$$

Using grid search:
<!-- Add image using HTML -->
<p align="center">
  <img src="https://github.com/user-attachments/assets/e000f56d-79a1-4221-9fbe-2396ccfbcd45" alt="Grid Search" width="400"/>
</p>

$$(\lambda_1;\lambda_2)=(1,4;1,28)$$

$$P(B=0 \wedge R=0)=P(B=0)+P(R=0)-P(B=0\wedge R=0)=e^{-1,4}+e^{-1,28}-e^{-(1,4+1,28)}\approx 0,247+0,278-0.069$$

$$P(B\geq 1 \vee R\geq 1)\approx 1-0,247-0,278+0,069=0,544$$
