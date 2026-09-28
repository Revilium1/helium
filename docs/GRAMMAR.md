$$
\begin{align}
    [\text {prog}] &\to [\text {stat}]^* \\
    [\text {stat}] &\to 
    \begin{cases}
        \text{exit}([\text {expr}]); \\
        \text{let}\space\text {ident} = [\text {expr}];
    \end{cases}\\
    [\text{expr}] &\to
    \begin{cases}
        \text{int\_lit} \\
        \text{ident}
    \end{cases}
\end{align}
$$