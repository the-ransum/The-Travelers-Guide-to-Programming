# Development

## Meth Expressions

[Github - Getting Started with MathJax](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/writing-mathematical-expressions)

### Writing inline expressions
To include a math expression inline with your text, delimit the expression with a dollar symbol $.

This sentence uses `$` delimiters to show math inline:  $\sqrt{3x-1}+(1+x)^2$

### Writing expressions as blocks

To add a math expression as a block, start a new line and delimit the expression with two dollar symbols $$.

**The Cauchy-Schwarz Inequality**
$$
\left( \sum_{k=1}^n a_k b_k \right)^2 \leq \left( \sum_{k=1}^n a_k^2 \right) \left( \sum_{k=1}^n b_k^2 \right)
$$

Alternatively, you can use the ```math code block syntax to display a math expression as a block. With this syntax, you don't need to use $$ delimiters.

**Here is some math!**

```math
\sqrt{3}
```

### Writing dollar signs in line with and within mathematical expressions

To display a dollar sign as a character in the same line as a mathematical expression, you need to escape the non-delimiter $ to ensure the line renders correctly.

Within a math expression, add a \ symbol before the explicit $.

This expression uses `\$` to display a dollar sign: $\sqrt{\$4}$

Outside a math expression, but on the same line, use span tags around the explicit $.

To split <span>$</span>100 in half, we calculate $100/2$


## Random Resources

- [This Week’s Finds in Mathematical Physics - Weeks 1 - 50](https://math.ucr.edu/home/baez/twf_latex/TWF_1-50.pdf)
- [This Week’s Finds in Mathematical Physics - Weeks 51 - 100](https://math.ucr.edu/home/baez/twf_latex/TWF_51-100.pdf)
- [This Week’s Finds in Mathematical Physics - Weeks 101 - 150](https://math.ucr.edu/home/baez/twf_latex/TWF_101-150.pdf)
- [This Week’s Finds in Mathematical Physics - Weeks 151 - 200](https://math.ucr.edu/home/baez/twf_latex/TWF_151-200.pdf)
- [This Week’s Finds in Mathematical Physics - Weeks 251 - 300](https://math.ucr.edu/home/baez/twf_latex/TWF_251-300.pdf)
- [This Week’s Finds in Mathematical Physics - Weeks 201 - 250](https://math.ucr.edu/home/baez/twf_latex/TWF_201-250.pdf)


