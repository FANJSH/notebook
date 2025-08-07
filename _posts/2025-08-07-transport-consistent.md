---
layout: default
title:  "Summary of transport approximation and Consistent P approximation"
date:   2025-08-07 00:00:00
categories: [Reactor Physics]
---

# Summary of transport approximation and Consistent P approximation
## Review of transport $P_N$ approximation
In 1-D single-group $S_N$ problem, the transport equation can be expressed as 

$$
     \mu \frac{d}{dx}\psi(x,\mu) + \Sigma_t(x)\psi(x,\mu) = 
     \sum^{\infty}_{l=0}{\frac{2l+1}{4\pi}\Sigma_s^l(x)\phi^l(x)} + S(x,\mu). 
$$

To eliminate the **pure-forward** scattering which is regarded as does not react with neutron, the scattering source term (RHS first term) should be manipulated. 
Writing the scattering cross-section into pure-forward and others terms, two parts,

$$
    \Sigma_s(x,\mu) = \hat{\Sigma}_s(x)\delta(\mu-1) - \hat{\Sigma}_s(x)\delta(\mu-1) + \sum^{\infty}_{l=0}{\frac{2l+1}{2}\Sigma_s^l(x) P_l(\mu)}. 
$$

Combing the second term of Eq.(2) RHS with the third term,

$$
    \Sigma_s(x,\mu) = \hat{\Sigma}_s(x)\delta(\mu-1) + \sum^{\infty}_{l=0}{\frac{2l+1}{2}P_l(\mu)[\Sigma_s^l(x) - \hat{\Sigma}_s(x)]}. 
$$

As we know that the pure-forward term should be removed from cross-section, the actual scattering cross-section is 

$$
    \tilde{\Sigma}_s(x, \mu) = \sum^{\infty}_{l=0}{\frac{2l+1}{2}P_l(\mu)[\Sigma_s^l(x) - \hat{\Sigma}_s(x)]}. 
$$

Assuming 
- $\hat{\Sigma}_s(x) = \Sigma_s^{N+1}(x)$;
- $\Sigma_s^l(x) = \Sigma_s^{N+1}(x)$, for each $l > N+1$, 
and then, the actual scattering cross-section (Eq. (4)) can be written as

$$
    \tilde{\Sigma}_s(x,\mu) = 
    \sum^{N}_{l=0}{\frac{2l+1}{2}P_l(\mu)[\Sigma_s^l(x) - \Sigma^{N+1}_s(x)]} + 
    \sum^{\infty}_{l=N+1}{\frac{2l+1}{2}P_l(\mu)[\Sigma_s^{N+1}(x) - \Sigma_s^{N+1}(x)]}. 
$$

The second term of RHS of Eq. (5) is zero so we can delete it. 

$$
    \tilde{\Sigma}_s(x,\mu) = 
    \sum^{N}_{l=0}{\frac{2l+1}{2}P_l(\mu)[\Sigma_s^l(x) - \Sigma^{N+1}_s(x)]}.
$$

Meanwhile, the total cross-section is changed into

$$
    \tilde{\Sigma}_t(x) = \Sigma_t(x) - \Sigma^{N+1}_s(x). 
$$

When $N$ is chosen as 0, 

$$
    \tilde{\Sigma}_s(x,\mu) = 
    \frac{1}{2}[\Sigma_s^0(x) - \Sigma^{1}_s(x)].
$$

This Eq. (7) is very important since an anisotropy scattering problem is changed into an isotropy scattering problem, but the $1$-th moment of scattering cross-section Legendre Polynomial expansion is taken account implicitly. It is the well-known **transport P$_0$ approximation** as well as **transport correction**. The treatment (or method) introduced above is the transport P$_N$ approximation. The essence of this method is removing the pure-forward scattering from cross-section, detailed implementation way is modifying each order of moment of scattering cross-section Legendre Polynomial expansion. 

## Consistent P approximation

At present, I have finished the group-collapse by using scalar neutron flux $\phi^0$ as weight. 
This method is quite primitive and straight-forward. This treatment does not take the anisotropy scattering into account. 

To consider the anisotropy scattering effect during group-collapse, **Consistent P approximation** can be used. 

Few group structure 1-D S$_N$ transport equation can be written as

$$
     \mu \frac{d}{dx}\psi_q(x,\mu) + \Sigma_{t,q}(x)\psi_q(x,\mu) = 
     \sum^Q_{q'= 0}{\sum^{\infty}_{l=0}{\frac{2l+1}{4\pi}P_l(\mu)\Sigma_{s,q'\rightarrow q}^l(x)\phi_{q'}^l(x)}} + S_q(x,\mu).
$$

Expanding the collision term (2nd term of LHS) by Legendre Polynomial, just like the scattering source term. We will do this expansion for both fine-group and few-group structure both. 
At first, as the total cross-section in fine-group structure is independent to direction, so 

$$
    \Sigma_{t,g}(x)\psi_g(x,\mu) = \Sigma_{t,g}(x) \sum^{\infty}_{l=0}{\frac{2l+1}{4\pi}P_l(\mu)\phi^l_{g}(x)}.  
$$

Then, 

$$
    \Sigma_{t,q}(x,\mu)\psi_q(x,\mu) = \sum_{g\in q}{\Sigma_{t,g}(x) \sum^{\infty}_{l=0}{\frac{2l+1}{4\pi}P_l(\mu)\phi^l_{g}(x)}}.
$$

At the meantime, the following equation is hold theoretically. 

$$
    \Sigma_{t,q}(x,\mu)\psi_q(x,\mu) = \sum^{\infty}_{l=0}{\frac{2l+1}{4\pi}P_l(\mu)\Sigma^l_{t,q}(x)\phi^l_{q}(x)}. 
$$

Assuming the equivalent relationship of $l$-th order moment of flux still holds between fine-group and few-group structures, i.e., $\sum_{g\in q}\phi^l_g$ = $\phi^l_q$. The following equation can be obtained, 

$$
    \Sigma^l_{t,q}(x) = \frac{\sum_{g\in q}\Sigma_{t,g}(x)\phi^l_g(x)}{\sum_{g\in q}\phi^l_g(x)}. 
$$

Next, the multi-group 1-D S$_N$ transport equations for few-group structure is

$$
     \mu \frac{d}{dx}\psi_q(x,\mu) + \sum^{\infty}_{l=0}{\frac{2l+1}{4\pi}P_l(\mu)\phi^l_q(x)\Sigma^l_{t,q}(x)} = 
     \sum^Q_{q'= 0}{\sum^{\infty}_{l=0}{\frac{2l+1}{4\pi}P_l(\mu)\Sigma_{s,q'\rightarrow q}^l(x)\phi_{q'}^l(x)}} + S_q(x,\mu).
$$

Moving the collision term of LHS to RHS, 

$$
     \mu\frac{d}{dx}\psi_q(x,\mu) = 
     \sum^Q_{q'= 0}{\sum^{\infty}_{l=0}{\frac{2l+1}{4\pi}P_l(\mu)\phi_{q'}^l(x)\left[\Sigma_{s,q'\rightarrow q}^l(x) - \Sigma^l_{t,q}(x)\delta_{qq'}\right]}} + S_q(x,\mu).
$$

Next step, assuming an arbitrary value $\Sigma_q$ to make up a collision term $\Sigma_q(x)\psi_q(x,\mu)$ and put it into both side of Eq. (15). 

$$
     \mu\frac{d}{dx}\psi_q(x,\mu) + \Sigma_q(x)\psi_q(x,\mu) = 
     \sum^Q_{q'= 0}{\sum^{\infty}_{l=0}{\frac{2l+1}{4\pi}P_l(\mu)\phi_{q'}^l(x)\{\Sigma_{s,q'\rightarrow q}^l(x) + \left[\Sigma_q(x)- \Sigma^l_{t,q}(x)\right]\delta_{qq'}\}}} + S_q(x,\mu).
$$

Similar to the transport P$_N$ approximation, we assume that 
- $\Sigma_q(x) = \Sigma^{N+1}_{t,q}(x)$;
- $\Sigma^{l}_{t,q}(x) = \Sigma^{N+1}_{t,q}(x)$, for each $l>N+1$.

Then, the Eq.(16) becoems to 

$$
\begin{split}  
     \mu\frac{d}{dx}\psi_q(x,\mu) + \Sigma^{N+1}_{t,q}(x)\psi_q(x,\mu) &= \\
     &\sum^Q_{q'= 0}{\sum^{\infty}_{l=0}{\frac{2l+1}{4\pi}P_l(\mu)\phi_{q'}^l(x)\{\Sigma_{s,q'\rightarrow q}^l(x) + \left[\Sigma^{N+1}_{t,q}(x)- \Sigma^l_{t,q}(x)\right]\delta_{qq'}\}}} + S_q(x,\mu).
\end{split}
$$

Comparing to the initial equation, Eq.(9), the following changes happened,
- total cross-section $\Sigma_{t,q}(x,\mu) \rightarrow \Sigma^{N+1}_{t,q}(x)$;
- $l$-th moment of scattering cross-section $\Sigma_{s,q'\rightarrow q}^l(x) \rightarrow \{\Sigma_{s,q'\rightarrow q}^l(x) + \left[\Sigma^{N+1}_{t,q}(x)- \Sigma^l_{t,q}(x)\right]\delta_{qq'}\}$.

In the case of Consistent P0 Approximation, the total cross-section is substituted by $\Sigma_{t,q}^1(x)$, the 0-th moment of scattering cross-section is substituted by $\{ \Sigma_{s,q'\rightarrow q}^0(x) +\left[ \Sigma_{t,q}^{1}(x) - \Sigma_{t,q}^0(x) \right] \delta_{qq'}\}$. 

As introduced above, $$\phi^1_g(x)$$ is required to calculated $$\Sigma^1_{t,q}(x)$$. 
In my program, the scattering source is expressed in the way of including a coefficient $$\frac{1}{4\pi}$$ therefore the $$l$-th order moment of neutron flux is defined as 

$$
    \phi^l = 2\pi\int^1_{-1}P_l(\mu)\psi(\mu)\,d\mu \approx 2\pi\sum^N_{i=1}{\omega_i\psi(\mu_i)P_l(\mu_i)},
$$
in which $\omega_i$ is the weight corresponding to quadrature set.  
