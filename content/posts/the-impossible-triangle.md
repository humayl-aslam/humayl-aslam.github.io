---
title: "The Impossible Triangle and the Geometric Mean"
date: 2024-03-20
draft: false
tags: ["mathematics", "geometry", "puzzles"]
math: true
---

I came across a trap question recently:

> *A right-angled triangle has a hypotenuse of $10$, and an altitude to that hypotenuse of $6$ Find its area.*

Simple, right?

$$
\text{Area} = \frac{1}{2} \times 10 \times 6 = 30
$$

Aha, but that's the trap. We are assuming apriori that the triangle is even mathematically possible. 

As it turns out, it isn't.

---

### The Algebra

Instead of getting bogged down in vertex notation like $AB$ and $BC$, let's keep it intuitive: drop an altitude $h$ to the hypotenuse, splitting it into two base segments, $x$ and $y$.

<svg width="100%" viewBox="0 0 500 210" xmlns="http://www.w3.org/2000/svg" style="max-width: 440px; height: auto; display: block; margin: 1.5rem auto;">
  <polygon points="50,160 160,50 450,160" fill="currentColor" fill-opacity="0.03" />
  <line x1="50" y1="160" x2="450" y2="160" stroke="currentColor" stroke-width="2" />
  <line x1="50" y1="160" x2="160" y2="50" stroke="currentColor" stroke-width="1.8" />
  <line x1="160" y1="50" x2="450" y2="160" stroke="currentColor" stroke-width="1.8" />
  <line x1="160" y1="50" x2="160" y2="160" stroke="currentColor" stroke-width="2" stroke-dasharray="5,4" />
  <polyline points="160,146 174,146 174,160" fill="none" stroke="currentColor" stroke-width="1.5" opacity="0.6" />
  <polygon points="152,60 161,67 168,58 159,50" fill="none" stroke="currentColor" stroke-width="1.5" opacity="0.6" />
  <circle cx="50" cy="160" r="3.5" fill="currentColor" />
  <circle cx="450" cy="160" r="3.5" fill="currentColor" />
  <circle cx="160" cy="50" r="3.5" fill="currentColor" />
  <circle cx="160" cy="160" r="3" fill="currentColor" />
  <text x="35" y="165" font-family="serif" font-size="16" font-style="italic" fill="currentColor" text-anchor="middle">A</text>
  <text x="465" y="165" font-family="serif" font-size="16" font-style="italic" fill="currentColor" text-anchor="middle">B</text>
  <text x="160" y="35" font-family="serif" font-size="16" font-style="italic" fill="currentColor" text-anchor="middle">C</text>
  <text x="160" y="185" font-family="serif" font-size="14" font-style="italic" fill="currentColor" text-anchor="middle">D</text>
  <text x="105" y="185" font-family="serif" font-size="16" font-style="italic" fill="currentColor" text-anchor="middle">x</text>
  <text x="305" y="185" font-family="serif" font-size="16" font-style="italic" fill="currentColor" text-anchor="middle">y</text>
  <text x="175" y="110" font-family="serif" font-size="16" font-style="italic" fill="currentColor" text-anchor="start">h</text>
</svg>

By similar triangles ($\triangle ADC \sim \triangle CDB$), the ratios of the matching sides must be equal:

$$
\frac{h}{x} = \frac{y}{h} \implies h^2 = xy \implies h = \sqrt{xy}
$$

The altitude dropped to the hypotenuse is simply the **geometric mean** of the two base segments it creates.

Now, feed the problem's numbers into that relation:
* The hypotenuse is $x + y = 10 \implies y = 10 - x$
* The altitude is $h = 6 \implies h^2 = 36$

Substitute $y$:

$$
x(10 - x) = 36 \implies x^2 - 10x + 36 = 0
$$

Test the discriminant:

$$
\Delta = b^2 - 4ac = (-10)^2 - 4(1)(36) = 100 - 144 = -44 < 0
$$

The roots are purely imaginary: $x = 5 \pm i\sqrt{11}$. 

You cannot have a triangle with physical sides made of complex numbers. The geometry breaks down immediately.

---

### The Geometry: Semicircles and AM-GM

Why does this fail so cleanly? A circle makes it obvious.

By Thales’s Theorem, any right-angled triangle can be inscribed in a semicircle where the hypotenuse serves as the diameter.

<svg width="100%" viewBox="0 0 500 220" xmlns="http://www.w3.org/2000/svg" style="max-width: 440px; height: auto; display: block; margin: 1.5rem auto;">
  <path d="M 60,170 A 180,180 0 0,1 420,170" fill="currentColor" fill-opacity="0.03" stroke="currentColor" stroke-width="1.8" />
  <line x1="60" y1="170" x2="420" y2="170" stroke="currentColor" stroke-width="2" />
  <line x1="60" y1="170" x2="160" y2="36" stroke="currentColor" stroke-width="1.2" stroke-dasharray="3,3" opacity="0.5" />
  <line x1="160" y1="36" x2="420" y2="170" stroke="currentColor" stroke-width="1.2" stroke-dasharray="3,3" opacity="0.5" />
  <line x1="240" y1="170" x2="240" y2="-10" stroke="currentColor" stroke-width="2" />
  <circle cx="240" cy="-10" r="3.5" fill="currentColor" />
  <text x="252" y="85" font-family="serif" font-size="15" fill="currentColor" text-anchor="start"><tspan font-style="italic">r</tspan> = AM</text>
  <line x1="160" y1="170" x2="160" y2="36" stroke="currentColor" stroke-width="2" stroke-dasharray="5,4" />
  <circle cx="160" cy="36" r="3.5" fill="currentColor" />
  <text x="148" y="105" font-family="serif" font-size="15" fill="currentColor" text-anchor="end"><tspan font-style="italic">h</tspan> = GM</text>
  <circle cx="240" cy="170" r="3" fill="currentColor" />
  <text x="240" y="195" font-family="serif" font-size="13" font-style="italic" fill="currentColor" text-anchor="middle">O</text>
  <text x="110" y="195" font-family="serif" font-size="15" font-style="italic" fill="currentColor" text-anchor="middle">x</text>
  <text x="330" y="195" font-family="serif" font-size="15" font-style="italic" fill="currentColor" text-anchor="middle">y</text>
</svg>

Look at what those two lines actually represent:
* The radius of the semicircle is the **Arithmetic Mean (AM)** of the two base segments:

$$
r = \frac{x + y}{2}
$$

* The altitude $h$ dropped from the apex to the diameter is the **Geometric Mean (GM)**:

$$
h = \sqrt{xy}
$$

Can a vertical line standing inside a semicircle ever be taller than the radius? 

No. The highest point anywhere on that arc sits directly over the center $O$, where the height equals the radius. Everywhere else, it is strictly shorter.

Which means:

$$
h \le r \iff \sqrt{xy} \le \frac{x + y}{2}
$$

That is the **AM-GM Inequality**, proven by nothing more than the physical boundary of a circle.

---

### The Punchline

For a hypotenuse of $10$, the radius of the circle is:

$$
r = \frac{10}{2} = 5
$$

The tallest legal altitude this triangle can ever have is $5$, which only happens when the apex sits dead center ($x = y = 5$, an isosceles right triangle).

An altitude of $6$ pokes outside the circle entirely. The area is not $30$; the triangle cannot exist.