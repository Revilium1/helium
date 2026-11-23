```math
\begin{aligned}
    [\text {Prog}] &\to [\text {Stat}]^* \\
    [\text {Stat}] &\to 
    \begin{cases}
        \text{exit}([\text {Expr}]); \\
        \text{let}\space\text {ident} = [\text {Expr}];
    \end{cases}\\
    [\text{expr}] &\to
    \begin{cases}
        \text{int\_lit} \\
        \text{ident} \\
        [\text{BinExpr}]
    \end{cases} \\
    [\text{BinExpr}] &\to
    \begin{cases}
        [\text{Expr}] * [\text{Expr}] & \text{prec} = 1 \\
        [\text{Expr}] + [\text{Expr}] & \text{prec} = 0 \\
    \end{cases}
\end{aligned}
```
