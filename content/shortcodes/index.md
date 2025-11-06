+++
title = "Short Codes"
date = 2025-11-03
updated = 2025-11-03
description = ""
tags = []
+++

Zokipedia supports several shortcodes to enhance your content.

## Math

Use the math shortcode to render mathematical expressions.

{% math() %}
\sum_{i=0}^{n} r^i = \frac{r^{n+1} - 1}{r - 1} \quad \text{for } r \neq 1
{% end %}

```jinja2
{%/* math() */%}
\sum_{i=0}^{n} r^i = \frac{r^{n+1} - 1}{r - 1} \quad \text{for } r \neq 1
{%/* end */%}
```

## Mermaid

Use the mermaid shortcode to create diagrams.

{% mermaid() %}
quadrantChart
    title Reach and engagement of campaigns
    x-axis Low Reach --> High Reach
    y-axis Low Engagement --> High Engagement
    quadrant-1 We should expand
    quadrant-2 Need to promote
    quadrant-3 Re-evaluate
    quadrant-4 May be improved
    Campaign A: [0.3, 0.6]
    Campaign B: [0.45, 0.23]
    Campaign C: [0.57, 0.69]
    Campaign D: [0.78, 0.34]
    Campaign E: [0.40, 0.34]
    Campaign F: [0.35, 0.78]
{% end %}

```jinja2
{%/* mermaid() */%}
quadrantChart
    title Reach and engagement of campaigns
    x-axis Low Reach --> High Reach
    y-axis Low Engagement --> High Engagement
    quadrant-1 We should expand
    quadrant-2 Need to promote
    quadrant-3 Re-evaluate
    quadrant-4 May be improved
    Campaign A: [0.3, 0.6]
    Campaign B: [0.45, 0.23]
    Campaign C: [0.57, 0.69]
    Campaign D: [0.78, 0.34]
    Campaign E: [0.40, 0.34]
    Campaign F: [0.35, 0.78]
{%/* end */%}
```
