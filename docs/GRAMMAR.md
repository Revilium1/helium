$$
\begin{align}
    [\text {prog}] &\to [\text {stat}]^* \\
    [\text {stat}] &\to 
    \begin{cases}
        exit([\text {expr}]); \\
        let\space\text {ident} = [\text {expr}];
    \end{cases}\\
    [\text{expr}] &\to \text{int\_lit}
\end{align}
$$