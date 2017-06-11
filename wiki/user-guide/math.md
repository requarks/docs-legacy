<!-- TITLE: MathML & TeX math equations  -->
<!-- SUBTITLE: How to include math equations in your page -->
# Usage
You can easily display math equations. Both the TeX and MathML formats are supported.

## TeX

### Block

TeX expressions must enclosed by `$$`, e.g.:

```
$$\sqrt{\frac{1}{N-1} \sum_{i=1}^N (x_i - \overline{x})^2}$$
```

will result in:

$$\sqrt{\frac{1}{N-1} \sum_{i=1}^N (x_i - \overline{x})^2}$$

### Inline

You can also put inline expressions by using enclosing them in `$`, e.g.:

```
The answer is: $M = 2n + 5$
```

will render as:

The answer is: $M = 2n + 5$

## MathML

MathML code can be inserted directly, e.g.:

```html
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mfrac>
    <mn>1</mn>
    <mrow>
      <mo>(</mo>
      <mrow>
        <mn>1</mn>
        <mo>+</mo>
        <mrow>
          <mo>(</mo>
          <mfrac>
            <mn>1</mn>
            <mrow>
              <mn>1</mn>
              <mo>+</mo>
              <mrow>
                <mo>(</mo>
                <mfrac>
                  <mn>1</mn>
                  <mrow>
                    <mn>1</mn>
                    <mo>+</mo>
                    <mn>2</mn>
                    <mi>x</mi>
                  </mrow>
                </mfrac>
                <mo>)</mo>
              </mrow>
            </mrow>
          </mfrac>
          <mo>)</mo>
        </mrow>
      </mrow>
      <mo>)</mo>
    </mrow>
  </mfrac>
</math>
```

will result in:

<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
  <mfrac>
    <mn>1</mn>
    <mrow>
      <mo>(</mo>
      <mrow>
        <mn>1</mn>
        <mo>+</mo>
        <mrow>
          <mo>(</mo>
          <mfrac>
            <mn>1</mn>
            <mrow>
              <mn>1</mn>
              <mo>+</mo>
              <mrow>
                <mo>(</mo>
                <mfrac>
                  <mn>1</mn>
                  <mrow>
                    <mn>1</mn>
                    <mo>+</mo>
                    <mn>2</mn>
                    <mi>x</mi>
                  </mrow>
                </mfrac>
                <mo>)</mo>
              </mrow>
            </mrow>
          </mfrac>
          <mo>)</mo>
        </mrow>
      </mrow>
      <mo>)</mo>
    </mrow>
  </mfrac>
</math>
