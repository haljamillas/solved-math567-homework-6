Download Link: https://assignmentchef.com/product/solved-math567-homework-6
<br>
<ol>

 <li><strong>Derivation of linear multistep (LMS) methods </strong>Consider the following third-order accurate LMS method</li>

</ol>

<em> .</em>

<ul>

 <li>Derive this method using any technique you desire</li>

</ul>

<u>Hint: </u>The most straightforward approach is to consider the appropriate approximation to the formal solution Z <em><sup>t</sup></em><em>n</em>+3

<em>u</em>(<em>t<sub>n</sub></em><sub>+3</sub>) = <em>u</em>(<em>t<sub>n</sub></em><sub>+1</sub>) +                       <em>f</em>(<em>t,u</em>(<em>t</em>))<em>dt</em>

<em>t</em><em>n</em>+1

of the general IVP <em>u</em><sup>0</sup>(<em>t</em>) = <em>f</em>(<em>t,u</em>).

<ul>

 <li>Draw the stencil for this method</li>

 <li>Determine if this method is zero-stable</li>

 <li>Determine if this method is consistent</li>

 <li>Determine if this method converges</li>

 <li>Determine the order of accuracy of this method</li>

 <li>Plot the stability domain for this method and include on your plot the stability domain for the third order Adams-Bashforth method (AB3). Compare and contrast the two stability domains in terms of the problems they might be good for solving. Would you ever want to use this method?</li>

</ul>

<h1>2. Heat equation: Crank-Nicolson</h1>

(a) Implement a function for numerically solving the solving the 1-D heat equation

<em> .</em>

using the Crank-Nicolson scheme (i.e. second order finite difference for the spatial derivative and trapezoidal rule for the time derivative). Your function should take as input: functions representing the initial condition and boundary conditions, the number of points for the uniform spatial discretization (<em>m </em>+ 1), the time span to solve the problem over, and the number of time steps (<em>N</em>). It should return the approximate solution at each time step (a matrix), a vector containing all the time steps, and a vector containing the spatial discretization. If using Matlab, then a possible function declaration is

[u,t,x] = cnhteq(f,g0,g1,tspan,alp,N,m)

The function should use a sparse matrix library or the fast discrete sine transform (DST) to solve the linear system that results from the implicit discretization. Hand-in a copy of your function and e-mail it to me.

If possible, reuse your code from homework 3 for the differentiation matrix of <em>u<sub>xx</sub></em>.

(b) Test your function on 1-D heat equation

<em> ,</em>

which has the exact solution

Use a waterfall plot to plot the Crank-Nicolson solution of the problem over the interval 0 ≤ <em>t </em>≤ 1 for <em>k </em>= 1<em>/</em>16 and <em>h </em>= 1<em>/</em>16. Illustrate the second order accuracy of the method by computing the relative errors in the solution at <em>t </em>= 1 for <em>h </em>= <em>k </em>= 2<sup>−<em>n</em></sup>, <em>n </em>= 4<em>,</em>5<em>,</em>6<em>,</em>7<em>,</em>8. Produce a table or plot clearly showing the second order accuracy.

<ol start="3">

 <li><strong>Heat equation: BDF2 </strong>Repeat problem 3, but use BDF2 for the time-integrator instead of trapezoidal rule. To bootstrap this method use one initial step with Crank-Nicolson. You do not need to produce a waterfall plot, but you do need to illustrate the second order accuracy. Which method is more accurate?</li>

 <li><strong>Linear stability analysis </strong>To numerically solve the equation</li>

</ol>

<em>u<sub>t </sub></em>+ <em>u<sub>xxx </sub></em>= 0<em>,                </em>0 ≤ <em>x </em>≤ 1<em>,           t </em>≥ 0<em>,</em>

IC: <em>u</em>(<em>x,</em>0) = <em>g</em>(<em>x</em>)<em>,       </em>BC: periodic

with periodic boundary conditions, a <em>naive </em>numerical analyst proposes to use the simple scheme of forward Euler in time and centered, second-order differences in space:

<em> .</em>

<ul>

 <li>Using some general principles about numerical stability of IVP solvers, explain to the numerical analyst that this scheme is unconditionally unstable, and thus should never be used.</li>

 <li>Propose an alternative scheme that can be used to successfully approximate this PDE (i.e. give a scheme that is conditionally or unconditionally stable).</li>

</ul>

<h1>5. Wave equation</h1>

<ul>

 <li>Show that the two-way wave equation</li>

</ul>

<em>u<sub>tt </sub></em>= <em>c</em><sup>2</sup><em>u<sub>xx</sub>, </em>0 ≤ <em>x &lt; </em>2<em>π, t &gt; </em>0<em>, u</em>(<em>x,</em>0) = <em>f</em>(<em>x</em>)<em>, u<sub>t</sub></em>(<em>x,</em>0) = <em>g</em>(<em>x</em>)<em>,                        </em>(1)

can be transformed into the equivalent first order system of two equations, given by

<em>u<sub>t </sub></em>+ <em>v<sub>x </sub></em>=       0

(2)

<em>v<sub>t </sub></em>+ <em>c</em><sup>2</sup><em>u<sub>x </sub></em>=       0

subject to <em>u</em>(<em>x,</em>0) = <em>f</em>(<em>x</em>), <em>v</em>(<em>x,</em>0) = <em>G</em>(<em>x</em>) = −<sup>R </sup><em>g</em>(<em>x</em>)<em>dx </em>for functions <em>u</em>(<em>x,t</em>) and <em>v</em>(<em>x,t</em>). This is a linear, constant coefficient hyperbolic system of the form

<em>q<sub>t </sub></em>+ <em>Aq<sub>x </sub></em>= 0                                                             (3)

where <em>A </em>is a 2 × 2 matrix and <em>q</em>(<em>x,t</em>) = (<em>u</em>(<em>x,t</em>)<em>,v</em>(<em>x,t</em>)).

<ul>

 <li>Write a function for numerically solving (2) using fourth-order centered finite differences in space and the standard fourth order Runge-Kutta (RK4) method in time. For reference, the fourth-order accurate centered finite difference formula is</li>

</ul>

<em>.</em>

As in the previous problem, compute the solution on the equispaced grid <em>x<sub>j </sub></em>= <em>jh</em>, <em>j </em>= 0<em>,…,m</em>, where <em>h </em>= 2<em>π/</em>(<em>m </em>+ 1).

2

<ul>

 <li>Use your function to solve the wave equation with <em>m </em>= 200, wave speed <em>c </em>= 1, and the initial conditions<a href="#_ftn1" name="_ftnref1"><sup>[1]</sup></a></li>

</ul>

<em>.</em>

Solve the problem for 0 ≤ <em>t </em>≤ 2<em>π </em>using a time-step of <em>k </em>= 2<em>π/</em>400. Produce a waterfall plot of the solution. Also plot the error in the solution at <em>t </em>= 2<em>π</em>. You can do this by simply computing the difference between the numerical solution at <em>t </em>= 2<em>π </em>and the initial condition.

<ul>

 <li>Extra credit: Since the domain is periodic, we can greatly increase the accuracy of the spatial derivative approximation without much worry about stability. For this extra credit problem, replace the fourth-order finite difference approximation with a Fourier spectral method approximation of <em>u</em><sup>0</sup>(<em>x</em>) and repeat part (b).</li>

</ul>

<a href="#_ftnref1" name="_ftn1">[1]</a> The initial condition <em>f</em>(<em>x</em>) is not technically periodic, but it looks periodic to machine precision.