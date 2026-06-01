# Sage routines for algebraic curves

This repository contains a SageMath routine} related to the study of algebraic curves, Riemann surfaces and Weierstrass points.

Current functionality includes:

- Computation of implicit derivatives in a polynomial equation
- Computation of Wronskians and Weierstrass weights.

These routines were developed for research purposes and are primarily
intended for experiments in algebraic geometry.

## Mathematical background

For a nodal plane curve

    F(x,y,z)=0

of degree d, the space of holomorphic differentials on the
normalization is obtained from adjoint curves of degree d−3.

Given a basis of differentials

    w₁,...,wg

the routines compute local expansions and Wronskians whose vanishing
orders determine Weierstrass weights.

## Requirements

- SageMath

Clone the repository and load the desired routines inside Sage.

## Files

wronskian.sage includes functions:

    implicit_derivatives
        inputs a point (x0,y0) on a plane curve F(x,y)=0 and outputs the truncated Taylor expansion y=y0+...+y_gt^g 

    Wronskian
        inputs a a point on a projective curve with nodes and outputs the (truncated) Wronskian around the point of a basis of 1-forms of the normalization of the curve

## References

Fulton, Algebraic Curves.

Miranda, Algebraic Curves and Riemann Surfaces.

Brieskorn and Knörrer, Plane Algebraic Curves.

Farkas and Kra, Riemann Surfaces.


## Example

### Computing the weight of the point [1:0:1] on the curve F(x,y,z)=x^4+y^4-z^4

R.<x,y,z>=PolynomialRing(QQ)

F = x^4 + y^4 - z^4

M=Wronskian(F,(1,0),[])

M.valuation()


### Computing the weight of the point $[2^{-1/n}:2^{-1/n}:1]$ on the Fermat curve of degree n=5
n=5
a=0
S.<x> = PolynomialRing(QQ)

f=x^n+2
K.<k> = S.quotient(f)

R.<x,y,z>=PolynomialRing(K)

F = x^n + y^n + z^n

M=Wronskian(F,(k^-1,k^-1),[])

M.valuation()

### Computing the weight of the point $[\sqrt{3}i:1:1]$ on the Wiman's sextic

S.<x> = PolynomialRing(QQ)

f = x^2+3

K.<k> = S.quotient(f)

R.<x,y,z>=PolynomialRing(K)

F = x^6+y^6+z^6+(x^2+y^2+z^2)*(x^4+y^4+z^4)-12*x^2*y^2*z^2

print(F(k,1,1))

M=Wronskian(F,(k,1),[(1,1,1),(-1,1,1),(1,-1,1),(1,1,-1)])

M.valuation()




