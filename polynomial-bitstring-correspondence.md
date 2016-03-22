# Polynomial Bitstring Correspondence

I only just realized the relationship between polynomials mod 2 and
bitstrings. It's rather obvious after thinking about it, but I hadn't
realized until recently and found it rather interesting.

Specifically I refer to the ability to view bitstrings of length m as
polynomials mod 2 of degree n (where n < m). Each bit in the bitstring
corresponds to the equivalent coefficient of the polynomial.
> e.g. 1011 = 1*x<sup>3</sup> + 0*x<sup>2</sup> + 1*x<sup>1</sup> + 1*x<sup>0</sup> = x<sup>3</sup> + x + 1

This relationship between literals would be fairly uninteresting if
not for a correspondence between fundamental operations on both
structures. For example:

##### Addition

```
   x^3 + x + 1
+  x^3 + x^2 + x
----------------------
      x^2 + 1
```

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;⇔

```
   1011
⊕  1110
--------
   0101
```
##### Multiplication

```
        x^4 + x^2 + x
×             x^2 + 1
-----------------------
   x^6 + x^3 + x^2 + x
```

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;⇔

```
                                     1010
   0010110                          10100
×  0000101                    ⊕   1010000
-----------        =        ---------------
   1001110                        1001110
```


  Specifically the above procedure × (not to be confused with normal
  binary multiplication) xors/adds the second argument (i.e. 101)
  with itself once for every on bit in the first argument
  (i.e. 10110), where each copy of argument #2 is left shifted by
  the index of the corresponding on bit from argument #1.

  While the above procedure for 'multiplying' bitstrings is hardly a
  fundamental operation in itself, it is clearly the composition of
  more fundamental operations, concretely xor and leftshift<sup>[1]</sup>.


Besides just being generally cool, this correspondence (like most)
gives us the ability to solve problems in one domain with solutions
from the other. For example, to reverse the 'multiplication' procedure
on bitstrings described above, we can reuse the plethora of PTIME
algorithms for factoring polynomials over finite fields. Nifty!
<sub>(probably maybe?)</sub>

<br>
<sup>[1]</sup> This procedure also follows clearly from the premise that
multiplication by x corresponds to a single left shift. Unfortunately
addition and multiplication make for far more compelling elementary
operations than addition and multiplication by x, thus the examples above.

### References
 - http://www.doc.ic.ac.uk/~mrh/330tutor/ch04s04.html
 - https://en.wikipedia.org/wiki/Factorization_of_polynomials_over_finite_fields
