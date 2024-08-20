# Arithmetic in Pure CSS #

[Demo](http://MERNCraft.github.io/calc)

CSS can do arithmetic and trigonometry. This page shows just its arithmetical skills.

Custom CSS properties can hold precise values. CSS counters can display the nearest integer value stored in a custom property. To show figures after the decimal point requires a little trickery.

This CSS-only page uses up to 5 counters and custom properties to perform these calculations. It shows calculations performed with single digit numbers and shows the results to up to two decimal places, but this is a development choice. This is just a demonstration of the possibilities of CSS, not a demonstration of its limits.

 The calculation performed depends on which of 4 radio buttons with the name `"operator"`. The operands are stored by `--a` and `--b` custom properties. They are chosen depending on which of 10 radio buttons in a group with the name `"a"` or `"b"` is selected. They are performed using the `calc()` CSS method.
 
 For division, the `a` number is first scaled up by 100 before division is performed, to obtain an intermediate result. This is stored as `--c`. The `mod()` method is used to determine what `--c % 100` is. This number is stored as `--d`; it represents the decimal part in one-hundredths. It will always be between `0` and `99`. The integer part (`--i`) of the result is calculated by `(--c - --d) / 100`. This will always be a integer value. The final result is shown as `--i . --d`, where `--d` may simply be `0`, or any number up to `99`. This makes the display _look_ like it is showing a number with decimal places, ever though the counters used will round the numbers to the nearest integer. 
 
 The [-] and [+] buttons beneath the numbers are spans inside the same label as a digit radio button. By default, all these spans are set to `{ display: none; }`. A selector like...
 ```css
 html:has(#a1:checked) {
  --a: 1;
  .a0 span.m { display: block }
  .a2 span.p { display: block }
}
```
... displays the spans for the radio button for the next smaller and the next bigger number. The "bigger" number after `9` is `0`. The "smaller" number after `0` is `9`, so these buttons allow you to cycle through the numbers. 