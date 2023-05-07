Download Link: https://assignmentchef.com/product/solved-mm621-tma937-lab2-constrained-optimization-penalty-methods
<br>
Study the theory of penalty methods in the textbook. In Part II of the exercise, there are some exercises which we recommend that you prepare by formulating the KKT conditions in advance. If you feel a slight anxiety in the proximity of computers, you may want to take a look at MATLAB’s optdemo in advance.

Part I: Constrained optimization: penalty methods

Consider the problem to

minimize <em>f</em>(<em>x</em>)<em>, </em>subject to <em>g</em>(<em>x</em>) ≤ 0<em><sup>m</sup>,</em>

where <em>f </em>and <em>g </em>are continuously differentiable functions. Penalty methods are generally of one of two different kinds: <em>exterior </em>and <em>interior </em>penalty methods, depending on if the methods generally give an infeasible of strictly feasible sequence of iteration points. We have implemented one method of each kind in MATLAB.

To start, download the zip-file from the course homepage and follow the directions given. Move to the directory LAB2 and start MATLAB by simply typing matlab. In order to run the programs, you should move from the directory LAB2 to the directories LAB2/epa (exterior penalty algorithm) or LAB2/lipa (interior penalty, or interior point, algorithm for linear programming). Both algorithms are started by typing go in Matlab’s command window.

Note that the problems are given with the constraints on “≤”-form, while Nash–Sofer describes the methods using the “≥”-form.

The <em>exterior </em>penalty method (sometimes called just the “penalty method”) works with the relaxation

minimize <em>f</em>(<em>x</em>) + <em>ρ<sub>k</sub>ψ</em>(<em>x</em>)<em>,</em>

<em>x</em>∈&lt;<em><sup>n</sup></em>

where <em>ρ<sub>k </sub>&gt; </em>0 and <em>ρ<sub>k </sub></em>→ +∞ when <em>k </em>→ +∞, and the penalty function is the quadratic function

<em>m </em><em>ψ</em>(<em>x</em>) := <sup>X</sup>(max{0<em>,g<sub>i</sub></em>(<em>x</em>)})<sup>2 </sup><em>.</em>

<em>i</em>=1

The <em>interior </em>penalty method (sometimes called the “barrier method”) works with the relaxation

minimize <em>f</em>(<em>x</em>) + <em>µ<sub>k</sub>φ</em>(<em>x</em>)<em>,</em>

<em>x</em>∈&lt;<em><sup>n</sup></em>

where <em>µ<sub>k </sub>&gt; </em>0 and <em>µ<sub>k </sub></em>→ 0 when <em>k </em>→ +∞, and where the penalty function is the function

<em>m</em>

<em>φ</em>(<em>x</em>) := −<sup>X</sup>log(−<em>g<sub>i</sub></em>(<em>x</em>))<em>.</em>

<em>i</em>=1

In order to avoid numerical problems one usually lets the sequences <em>ρ<sub>k </sub></em>and <em>µ<sub>k </sub></em>converge slowly.

<h2>Description of the interface</h2>

After choosing the example from the drop-down list in the lower-left part of the window, press the “Load” button. In the left window you will see the level sets of the objective function (you can think of them as a topographic map), the directions the <em>negative </em>gradient, as well as the curves constraining the feasible set. The coordinates of the current iteration point can be read below the left window.

After adjusting the desired penalty value, press the “Optimize” button. The right window will show the level sets of the penalised function, exactly as the algorithm would “see” it, were it not near-sighted. The current iteration point is plotted in the right window (pink “x” cross); the left window will contain the optimization “path”, showing the progress of the algorithm (pink curve).

<em>Note! </em>In our implementation of EPA we solve the penalised problem using a gradient algorithm to obtain a globally optimal solution. Instead, one can perform only a few iterations of the gradient algorithm.

In IPA, we perform <em>only one </em>iteration of the modified Newton method (with an Armijo line search). We show the global minimum point in the right window using a red “o” circle; its evolution as the penalty parameter changes (so-called “central path”) is shown in the left window as a red line.

<em>Hint! </em>You can change the starting point for the algorithm by modifying the variables x1_start and x2_start in the .m-file, corresponding to the example you solve. Even more, you can add your own problems by providing a corresponding example*.m file!

<h2>Exercises</h2>

There are four nonlinear problems, two convex (example_nl{01,02}.m), and two non-convex (example_nl{03,04}.m), as well as three linear problems (example_lin[01–03].m); you can find the problem formulations in the Appendix.

<ol>

 <li>Using the interior point method, solve the LPs 01–03. Do we alwaysfind an optimal extreme point (problem 03)? Notice how the algorithm follows closely the central path and goes “directly” to the global minimum point (i.e., it skips visiting the extreme points), if you change the penalty parameter smoothly. Compare with the Simplex method.</li>

 <li>Change the directory to LAB2/kkt and type go at the Matlab prompt.</li>

</ol>

Find the KKT points of the nonlinear problems (example_nl[01–04].m). Are the KKT conditions sufficient for the global optimality (problem 03)? Are they necessary (problem 04)?

<em>Hint: </em>There is a built-in tolerance in the graphical interface that sometimes fools you. Make sure to analytically verify the results. This hint is especially important for the problem 04.

<ol start="3">

 <li>Using the exterior penalty algorithm, solve the nonlinear and linearproblems. Can you get different “optimal” solutions by changing the penalty parameter in a different manner or by starting from different points (problem 03)? Tricky: Can you think of a reason for the slow convergence in problem 04 (hint: KKT)?</li>

</ol>

<h1>Part II: Constrained optimization; MATLAB:s Optimization Toolbox</h1>

In this part of the lab, you are to use MATLAB’s optimization routines to solve some nonlinear problems.

<em>Note! </em>This part of the lab should be prepared by formulating the KKT conditions for the exercise problems. We have created an example to show how Matlab’s constrained minimization, fmincon, works. In order to understand the command, it is helpful to read Matlab’s help about it (type help fmincon). If you also would like to know more about various options of the solver, type help optimset. Example:

s.t. <em>x</em><sub>1 </sub>≥ 0 <em>x</em>21 + <em>x</em>2 ≥ 2

The code for this example can be found in the file LAB2/fmincon1 and the example can be run by typing run fmincon1 in the MATLAB command window. Study the code that implements this example; to solve the other problems you need to create similar files.

<h2>Exercises</h2>

<ol>

 <li>Given is the problem</li>

</ol>

,

s.t.     <em>x</em><sup>2</sup><sub>1 </sub>− <em>x</em><sub>2 </sub>≤ 0<em>, </em>2<em>x</em><sub>1 </sub>− <em>x</em><sub>2 </sub>≥ 0<em>.</em>

<ul>

 <li>Solve the problem using fmincon.</li>

 <li>State the KKT conditions, examine the convexity of the problemand verify that the obtained solution is a <em>global maximum</em>.</li>

</ul>

<ol start="2">

 <li>Given is the problem</li>

</ol>

min <em>f</em>(<em>x</em>) := <em>x</em><sub>1                                                                            </sub>,

s.t.            (<em>x</em><sub>1</sub>− 1)<sup>2 </sup>+             (<em>x</em><sub>2 </sub>+ 2)<sup>2 </sup>≤ 16<em>, x</em>21                    +             <em>x</em>22               ≥ 13<em>.</em>

Solve the problem from at least five starting points. Describe what happens. Which point is the best one? Can you guarantee that this is a <em>global minimum</em>? Fun points to try are (1<em>,</em>1)<sup>T</sup><em>,</em>(0<em>,</em>0)<sup>T</sup><em>,</em>(3<em>.</em>7<em>,</em>0)<sup>T </sup>and (−1<em>,</em>−1)<sup>T</sup>.

<h1>Appendix</h1>

<h2>Linear problems</h2>

<h3>example_lin01.m</h3>

min<em>x</em><sub>1 </sub>+ 3<em>x</em><sub>2</sub><em>,</em>

<sup> </sup><em>x</em><sub>1 </sub>+ 2<em>x</em><sub>2 </sub>≥ 2<em>,</em>

 <em>x</em>1− 3<em>x</em>2 ≤ 2<em>,</em>

s.t.

<sub></sub>−<em>x</em><sup>1 </sup>+ 3<em>x</em><sub>1</sub><em>,xx</em><sup>2</sup><sub>2 </sub>≤≥ 120<em>, ,</em>

<h3>example_lin02.m</h3>

min<em>x</em><sub>1 </sub>+ 3<em>x</em><sub>2</sub><em>,</em>



1<em>x</em>

11111<em>/////</em>65432<em>xxxxx</em><sub>111111</sub>+ 1+ 1+ 1+ 1+ 1+ 1<em>//////</em>1056789<em>xxxxxx</em><sub>222222 </sub>≥≥≥≥≥≥ 111111<em>,,,,,,</em>

s.t.

1<em>/</em>7<em>x</em>

111<em>///</em>9810<em>xx</em><sub>111</sub><em>x</em>+ 1+ 1+ 1<sub>1 </sub>+ 1<em>///</em>234<em>xxxxxx</em><sub>122222 </sub>≤≥≥≥≥≥ 2001111<em>.,,,, ,</em>

<h3>example_lin03.m</h3>

min<em>x</em><sub>2</sub><em>,</em>



<sup></sup>1<em>/</em>12<em>xx</em>1<sup>1</sup>+ 1+ 1<em>//</em>109<em>xx</em><sup>2</sup>2 ≥≥ 11<em>,,</em>



1<em>/</em>3<em>x</em><sup>1 </sup>+ 1<em>/</em>8<em>x</em><sup>2 </sup>≥ 1<em>,</em>

<sub></sub>11<em>//</em>54<em>xx</em><sub>11 </sub>+ 1+ 1<em>//</em>67<em>xx</em><sub>22 </sub>≥≥ 11<em>,,</em>

<sub></sub>1<em>/</em>6<em>x</em><sub>1 </sub>+ 1<em>/</em>5<em>x</em><sub>2 </sub>≥ 1<em>,</em>

s.t.

<sup></sup>11<em>//</em>87<em>xx</em><sup>1</sup>1 + 1+ 1<em>//</em>34<em>xx</em><sup>2</sup>2 ≥≥ 11<em>,,</em>

 <sub></sub>1<em>/</em>9<em>x</em><sub>1 </sub>+ 1<em>/</em>2<em>x</em><sub>2 </sub>≥ 1<em>,</em>

<sub></sub> 1<em>/</em>10<em>x</em><sub>1 </sub>+ 1<em>xxx</em><sub>212 </sub>≤≥≥ 2001<em>., ,</em>

<h2>Nonlinear problems</h2>

<h3>example_nl01.m</h3>

min<em>x</em>21 + <em>x</em>22<em>,</em>

<sup>                            </sup><em>x</em><sub>1 </sub>≥ 2<em>,</em>



s.t.                                  <em>x</em><sub>2 </sub>≥ 1<em>,</em>

<sup></sup>1<em>/</em>2<em>x</em><sub>1 </sub>+ 1<em>/</em>4<em>x</em><sub>2 </sub>≤ 2<em>.</em>

<h3>example_nl02.m</h3>

min<em>x</em><sup>2</sup><sub>1</sub><em>,</em>

                                         <em>,</em>

s.t.

<h3>example_nl03.m</h3>

min<em>x</em><sub>1 </sub>sin(<em>x</em><sub>1</sub>) + <em>x</em><sub>2 </sub>sin(<em>x</em><sub>2</sub>)<em>,</em>



<sup></sup><sub>                            </sub><em>xx</em><sub>2</sub>1 ≥≥ 31<em>//</em>43<em>,,</em>

s.t.

(<em>x</em>1− 1)2<em>x</em>+ (1−<em>x</em>sin(2−<em>x</em>1)22) ≤≥ 50<em>.,</em>

<h3>example_nl04.m</h3>

min(<em>x</em><sub>1 </sub>+ 1)<sup>2 </sup>+ 1<em>/</em>2<em>x</em><sup>2</sup><sub>2</sub><em>,</em>

<sup>    </sup><em>x</em><sub>1 </sub>≤ 3<em>, </em>s.t. <em>,</em>