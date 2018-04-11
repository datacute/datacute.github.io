---
layout: post
title: Mathematics of Boxy Numbers
date: 2008-06-22 15:48
author: spdenne
comments: true
---

I've found some interesting mathematical concepts through researching my ideas presented in my previous blog posts on a
scheme for representing numbers using [Basic Primes](/2008/04/16/basic-primes-in-scala/), and drawing that
representation as [Boxy Numbers](/2008/04/16/boxy-numbers/).

<!--more-->

There is a function named [pi](http://en.wikipedia.org/wiki/Prime-counting_function), (written as the greek symbol),
but pi isn't used in reference to circles' diameters and circumferences, but is instead (as far as I can tell) P. I.
standing for prime index. pi(x) is equal to the number of primes equal to or less than x.

By altering my representation slightly so that the number one is represented as a single box:

<table border="1" cellspacing="0"><tbody>
<tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr>
</tbody></table>

So that two is the first prime, so two is a box with the representation of one inside it (which is how I previously
drew three).

Then the representation of any number *n* is drawn by producing *n*'s prime factors,
*f*<sub>0</sub> to *f*<sub>k</sub> and each factor *f*<sub>i</sub> is drawn as a box with the
representation of pi(*f*<sub>i</sub>) inside it.

To make the representation slightly more aesthetic, you can fill in all the gaps with the representation of one. This
is because everything is multiplied, and you can of course multiply by one as many times as you like without altering
the product. Multiplication is also commutative, so the boxes may be rearranged to give a pleasant looking number, so
long as the number of boxes within any box stays the same.

Multiplication is simply a case of drawing both sets of boxes for the numbers being multiplied.

Division and rational numbers are probably best drawn with a numerator over a divisor separated by a line. Common
factors are easily identified and removed.

By contrast, addition and subtraction are intensely difficult.

Here's a walk-through of representing your birthday as a bunch of boxes:

You could draw the number for the day, month and year individually, but you'll probably end up with more a more
interesting drawing if you start with one large number n = YYYYMMDD. So for my birthday, 8th September 1972, n=19720908

The first step is to produce the prime factors. There are lots of ways of doing this. The easiest way if you are
reading this online is to use an online tool. 
The one from [Maths Is Fun](http://www.mathsisfun.com/prime-factorization-tool.php) says my prime factors are 
6763 x 3 x 3 x 3 x 3 x 3 x 3 x 2 x 2.

So I need nine boxes, containing the representation of pi of each factor.

Though boxes can be arranged in any way you like, in order to demonstrate the technique I'll stay consistent, showing
these vertically, as otherwise by the end of the post I'll be running out of room. Web pages have a fixed width, but can
be infinitely long:

<table><tbody>
<tr><td><table border="1" cellspacing="0"><tbody><tr><td>pi(6763)</td></tr></tbody></table></td></tr>
<tr><td><table border="1" cellspacing="0"><tbody><tr><td>pi(3)</td></tr></tbody></table></td></tr>
<tr><td><table border="1" cellspacing="0"><tbody><tr><td>pi(3)</td></tr></tbody></table></td></tr>
<tr><td><table border="1" cellspacing="0"><tbody><tr><td>pi(3)</td></tr></tbody></table></td></tr>
<tr><td><table border="1" cellspacing="0"><tbody><tr><td>pi(3)</td></tr></tbody></table></td></tr>
<tr><td><table border="1" cellspacing="0"><tbody><tr><td>pi(3)</td></tr></tbody></table></td></tr>
<tr><td><table border="1" cellspacing="0"><tbody><tr><td>pi(3)</td></tr></tbody></table></td></tr>
<tr><td><table border="1" cellspacing="0"><tbody><tr><td>pi(2)</td></tr></tbody></table></td></tr>
<tr><td><table border="1" cellspacing="0"><tbody><tr><td>pi(2)</td></tr></tbody></table></td></tr>
</tbody></table>

There's an online calculator of pi(n) too [here](http://primes.utm.edu/nthprime/).

It reports that there are:

871 primes less than or equal to 6763

2 primes less than or equal to 3

1 prime less than or equal to 2

So our boxes need to be:

<table><tbody>
<tr><td><table border="1" cellspacing="0"><tbody><tr><td>871</td></tr></tbody></table></td></tr>
<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;2&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;2&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;2&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;2&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;2&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;2&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;1&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;1&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
</tbody></table>

We repeat the process for each of these numbers, drawing a box for each prime factor, and writing pi(factor) in each
box.

The prime factors of 871 are 67 x 13, so we need two boxes.

2 is prime, so each of the 2s need a single box.

1 has been defined as a box with nothing in it.

<table><tbody>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 6763 = 871st prime -->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>pi(67)</td></tr></tbody></table></td></tr>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>pi(13)</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 3 = 2nd prime -->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>pi(2)</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 3 = 2nd prime -->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>pi(2)</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 3 = 2nd prime -->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>pi(2)</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 3 = 2nd prime -->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>pi(2)</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 3 = 2nd prime -->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>pi(2)</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 3 = 2nd prime -->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>pi(2)</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 2 = 1st prime-->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 2 = 1st prime-->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
</tbody></table>

pi(67) = 19

pi(13) = 6

pi(2) we've previously seen  = 1

So our boxes need to be:

<table><tbody>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 6763 = 871st prime -->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;19&nbsp;</td></tr></tbody></table></td></tr>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;6&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 3 = 2nd prime -->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;1&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 3 = 2nd prime -->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;1&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 3 = 2nd prime -->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;1&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 3 = 2nd prime -->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;1&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 3 = 2nd prime -->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;1&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 3 = 2nd prime -->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;1&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 2 = 1st prime-->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 2 = 1st prime-->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
</tbody></table>

Producing prime factors again, 19 is prime, so a single box is needed. 6s prime factors are 3 x 2, so two boxes needed

We'll replace 1s as before.

So we've got:

<table><tbody>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 6763 = 871st prime -->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
				<!-- 67 = 19th prime -->
				<table><tbody>
					<tr><td><table border="1" cellspacing="0"><tbody><tr><td>pi(19)</td></tr></tbody></table></td></tr>
				</tbody></table>
			</td></tr></tbody></table></td></tr>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
				<!-- 13 = 6th prime -->
				<table><tbody>
					<tr><td><table border="1" cellspacing="0"><tbody><tr><td>pi(3)</td></tr></tbody></table></td></tr>
					<tr><td><table border="1" cellspacing="0"><tbody><tr><td>pi(2)</td></tr></tbody></table></td></tr>
				</tbody></table>
			</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 3 = 2nd prime -->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
				<!-- 2 = 1st prime-->
				<table><tbody>
					<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
				</tbody></table>
			</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 3 = 2nd prime -->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
				<!-- 2 = 1st prime-->
				<table><tbody>
					<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
				</tbody></table>
			</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 3 = 2nd prime -->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
				<!-- 2 = 1st prime-->
				<table><tbody>
					<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
				</tbody></table>
			</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 3 = 2nd prime -->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
				<!-- 2 = 1st prime-->
				<table><tbody>
					<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
				</tbody></table>
			</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 3 = 2nd prime -->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
				<!-- 2 = 1st prime-->
				<table><tbody>
					<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
				</tbody></table>
			</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 3 = 2nd prime -->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
				<!-- 2 = 1st prime-->
				<table><tbody>
					<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
				</tbody></table>
			</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 2 = 1st prime-->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 2 = 1st prime-->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
</tbody></table>

Evaluating the pi functions gives:

<table><tbody>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 6763 = 871st prime -->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
				<!-- 67 = 19th prime -->
				<table><tbody>
					<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;8&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
				</tbody></table>
			</td></tr></tbody></table></td></tr>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
				<!-- 13 = 6th prime -->
				<table><tbody>
					<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;2&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
					<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;1&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
				</tbody></table>
			</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 3 = 2nd prime -->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
				<!-- 2 = 1st prime-->
				<table><tbody>
					<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
				</tbody></table>
			</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 3 = 2nd prime -->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
				<!-- 2 = 1st prime-->
				<table><tbody>
					<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
				</tbody></table>
			</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 3 = 2nd prime -->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
				<!-- 2 = 1st prime-->
				<table><tbody>
					<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
				</tbody></table>
			</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 3 = 2nd prime -->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
				<!-- 2 = 1st prime-->
				<table><tbody>
					<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
				</tbody></table>
			</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 3 = 2nd prime -->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
				<!-- 2 = 1st prime-->
				<table><tbody>
					<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
				</tbody></table>
			</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 3 = 2nd prime -->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
				<!-- 2 = 1st prime-->
				<table><tbody>
					<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
				</tbody></table>
			</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 2 = 1st prime-->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 2 = 1st prime-->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
</tbody></table>

Factorising gives:

<table><tbody>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 6763 = 871st prime -->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
				<!-- 67 = 19th prime -->
				<table><tbody>
					<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
						<!-- 19 = 8th prime -->
						<table><tbody>
							<tr><td><table border="1" cellspacing="0"><tbody><tr><td>pi(2)</td></tr></tbody></table></td></tr>
							<tr><td><table border="1" cellspacing="0"><tbody><tr><td>pi(2)</td></tr></tbody></table></td></tr>
							<tr><td><table border="1" cellspacing="0"><tbody><tr><td>pi(2)</td></tr></tbody></table></td></tr>
						</tbody></table>
					</td></tr></tbody></table></td></tr>
				</tbody></table>
			</td></tr></tbody></table></td></tr>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
				<!-- 13 = 6th prime -->
				<table><tbody>
					<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
						<!-- 3 = 2nd prime -->
						<table><tbody>
							<tr><td><table border="1" cellspacing="0"><tbody><tr><td>pi(2)</td></tr></tbody></table></td></tr>
						</tbody></table>
					</td></tr></tbody></table></td></tr>
					<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
						<!-- 2 = 1st prime-->
						<table><tbody>
							<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
						</tbody></table>
					</td></tr></tbody></table></td></tr>
				</tbody></table>
			</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 3 = 2nd prime -->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
				<!-- 2 = 1st prime-->
				<table><tbody>
					<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
				</tbody></table>
			</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 3 = 2nd prime -->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
				<!-- 2 = 1st prime-->
				<table><tbody>
					<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
				</tbody></table>
			</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 3 = 2nd prime -->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
				<!-- 2 = 1st prime-->
				<table><tbody>
					<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
				</tbody></table>
			</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 3 = 2nd prime -->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
				<!-- 2 = 1st prime-->
				<table><tbody>
					<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
				</tbody></table>
			</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 3 = 2nd prime -->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
				<!-- 2 = 1st prime-->
				<table><tbody>
					<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
				</tbody></table>
			</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 3 = 2nd prime -->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
				<!-- 2 = 1st prime-->
				<table><tbody>
					<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
				</tbody></table>
			</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 2 = 1st prime-->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 2 = 1st prime-->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
</tbody></table>

Evaluating the pi functions gives:

<table><tbody>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 6763 = 871st prime -->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
				<!-- 67 = 19th prime -->
				<table><tbody>
					<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
						<!-- 19 = 8th prime -->
						<table><tbody>
							<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;1&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
							<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;1&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
							<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;1&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
						</tbody></table>
					</td></tr></tbody></table></td></tr>
				</tbody></table>
			</td></tr></tbody></table></td></tr>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
				<!-- 13 = 6th prime -->
				<table><tbody>
					<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
						<!-- 3 = 2nd prime -->
						<table><tbody>
							<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;1&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
						</tbody></table>
					</td></tr></tbody></table></td></tr>
					<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
						<!-- 2 = 1st prime-->
						<table><tbody>
							<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
						</tbody></table>
					</td></tr></tbody></table></td></tr>
				</tbody></table>
			</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 3 = 2nd prime -->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
				<!-- 2 = 1st prime-->
				<table><tbody>
					<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
				</tbody></table>
			</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 3 = 2nd prime -->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
				<!-- 2 = 1st prime-->
				<table><tbody>
					<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
				</tbody></table>
			</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 3 = 2nd prime -->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
				<!-- 2 = 1st prime-->
				<table><tbody>
					<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
				</tbody></table>
			</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 3 = 2nd prime -->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
				<!-- 2 = 1st prime-->
				<table><tbody>
					<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
				</tbody></table>
			</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 3 = 2nd prime -->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
				<!-- 2 = 1st prime-->
				<table><tbody>
					<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
				</tbody></table>
			</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 3 = 2nd prime -->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
				<!-- 2 = 1st prime-->
				<table><tbody>
					<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
				</tbody></table>
			</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 2 = 1st prime-->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 2 = 1st prime-->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
</tbody></table>

Replacing the last 1s with their representation of an empty box gives the final representation:

<table><tbody>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 6763 = 871st prime -->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
				<!-- 67 = 19th prime -->
				<table><tbody>
					<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
						<!-- 19 = 8th prime -->
						<table><tbody>
							<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
								<!-- 2 = 1st prime-->
								<table><tbody>
									<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
								</tbody></table>
							</td></tr></tbody></table></td></tr>
							<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
								<!-- 2 = 1st prime-->
								<table><tbody>
									<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
								</tbody></table>
							</td></tr></tbody></table></td></tr>
							<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
								<!-- 2 = 1st prime-->
								<table><tbody>
									<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
								</tbody></table>
							</td></tr></tbody></table></td></tr>
						</tbody></table>
					</td></tr></tbody></table></td></tr>
				</tbody></table>
			</td></tr></tbody></table></td></tr>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
				<!-- 13 = 6th prime -->
				<table><tbody>
					<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
						<!-- 3 = 2nd prime -->
						<table><tbody>
							<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
								<!-- 2 = 1st prime-->
								<table><tbody>
									<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
								</tbody></table>
							</td></tr></tbody></table></td></tr>
						</tbody></table>
					</td></tr></tbody></table></td></tr>
					<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
						<!-- 2 = 1st prime-->
						<table><tbody>
							<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
						</tbody></table>
					</td></tr></tbody></table></td></tr>
				</tbody></table>
			</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 3 = 2nd prime -->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
				<!-- 2 = 1st prime-->
				<table><tbody>
					<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
				</tbody></table>
			</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 3 = 2nd prime -->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
				<!-- 2 = 1st prime-->
				<table><tbody>
					<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
				</tbody></table>
			</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 3 = 2nd prime -->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
				<!-- 2 = 1st prime-->
				<table><tbody>
					<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
				</tbody></table>
			</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 3 = 2nd prime -->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
				<!-- 2 = 1st prime-->
				<table><tbody>
					<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
				</tbody></table>
			</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 3 = 2nd prime -->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
				<!-- 2 = 1st prime-->
				<table><tbody>
					<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
				</tbody></table>
			</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 3 = 2nd prime -->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
				<!-- 2 = 1st prime-->
				<table><tbody>
					<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
				</tbody></table>
			</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 2 = 1st prime-->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
	<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
		<!-- 2 = 1st prime-->
		<table><tbody>
			<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
		</tbody></table>
	</td></tr></tbody></table></td></tr>
</tbody></table>

Rearranging this into a pleasing arrangement gives

<table><tbody>
	<tr>
		<td><table border="1" cellspacing="0"><tbody><tr><td>
			<!-- 6763 = 871st prime -->
			<table><tbody>
				<tr>
					<td><table border="1" cellspacing="0"><tbody><tr><td>
						<!-- 67 = 19th prime -->
						<table><tbody>
							<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
								<!-- 19 = 8th prime -->
								<table><tbody>
									<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
										<!-- 2 = 1st prime-->
										<table><tbody>
											<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
										</tbody></table>
									</td></tr></tbody></table></td></tr>
									<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
										<!-- 2 = 1st prime-->
										<table><tbody>
											<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
										</tbody></table>
									</td></tr></tbody></table></td></tr>
									<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
										<!-- 2 = 1st prime-->
										<table><tbody>
											<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
										</tbody></table>
									</td></tr></tbody></table></td></tr>
								</tbody></table>
							</td></tr></tbody></table></td></tr>
						</tbody></table>
					</td></tr></tbody></table></td>
					<td><table border="1" cellspacing="0"><tbody><tr><td align="center">
						<!-- 13 = 6th prime -->
						<table><tbody>
							<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
								<!-- 3 = 2nd prime -->
								<table><tbody>
									<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
										<!-- 2 = 1st prime-->
										<table><tbody>
											<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
										</tbody></table>
									</td></tr></tbody></table></td></tr>
								</tbody></table>
							</td></tr></tbody></table></td></tr>
							<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
								<!-- 2 = 1st prime-->
								<table><tbody>
									<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
								</tbody></table>
							</td></tr></tbody></table></td></tr>
							<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
						</tbody></table>
					</td></tr></tbody></table></td>
				</tr>
			</tbody></table>
		</td></tr></tbody></table></td>
		<td>
			<table><tbody>
				<tr>
					<td><table border="1" cellspacing="0"><tbody><tr><td>
						<!-- 3 = 2nd prime -->
						<table><tbody>
							<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
								<!-- 2 = 1st prime-->
								<table><tbody>
									<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
								</tbody></table>
							</td></tr></tbody></table></td></tr>
						</tbody></table>
					</td></tr></tbody></table></td>
					<td><table border="1" cellspacing="0"><tbody><tr><td>
						<!-- 3 = 2nd prime -->
						<table><tbody>
							<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
								<!-- 2 = 1st prime-->
								<table><tbody>
									<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
								</tbody></table>
							</td></tr></tbody></table></td></tr>
						</tbody></table>
					</td></tr></tbody></table></td>
				</tr>
				<tr>
					<td><table border="1" cellspacing="0"><tbody><tr><td>
						<!-- 3 = 2nd prime -->
						<table><tbody>
							<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
								<!-- 2 = 1st prime-->
								<table><tbody>
									<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
								</tbody></table>
							</td></tr></tbody></table></td></tr>
						</tbody></table>
					</td></tr></tbody></table></td>
					<td><table border="1" cellspacing="0"><tbody><tr><td>
						<!-- 3 = 2nd prime -->
						<table><tbody>
							<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
								<!-- 2 = 1st prime-->
								<table><tbody>
									<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
								</tbody></table>
							</td></tr></tbody></table></td></tr>
						</tbody></table>
					</td></tr></tbody></table></td>
				</tr>
				<tr>
					<td><table border="1" cellspacing="0"><tbody><tr><td>
						<!-- 3 = 2nd prime -->
						<table><tbody>
							<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
								<!-- 2 = 1st prime-->
								<table><tbody>
									<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
								</tbody></table>
							</td></tr></tbody></table></td></tr>
						</tbody></table>
					</td></tr></tbody></table></td>
					<td><table border="1" cellspacing="0"><tbody><tr><td>
						<!-- 3 = 2nd prime -->
						<table><tbody>
							<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
								<!-- 2 = 1st prime-->
								<table><tbody>
									<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
								</tbody></table>
							</td></tr></tbody></table></td></tr>
						</tbody></table>
					</td></tr></tbody></table></td>
				</tr>
			</tbody></table>
		</td>
		<td>
			<table><tbody>
				<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
				<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
					<!-- 2 = 1st prime-->
					<table><tbody>
						<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
					</tbody></table>
				</td></tr></tbody></table></td></tr>
				<tr><td><table border="1" cellspacing="0"><tbody><tr><td>
					<!-- 2 = 1st prime-->
					<table><tbody>
						<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
					</tbody></table>
				</td></tr></tbody></table></td></tr>
				<tr><td><table border="1" cellspacing="0"><tbody><tr><td>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</td></tr></tbody></table></td></tr>
			</tbody></table>
		</td>
	</tr>
</tbody></table>
