# Initial Project Ideas

## Reading notes

### What Computational Physics is Really About

#### The Nature of Science

* Science is all about making models and using them to predict events in real life.
* A **model** is anything that is used to represent real life. It can be many things, often mathematical.
* Making a model is theoretical physics and comparing a model to real life is experimental physics. 

#### The Computational Physicist

* Computers are very important in science, and computational science can be considered both experiment and theory, because we create the programs, but they produce data. 

#### A Computer Program is a Model

* Running a computer program is different from conducting a real experiment, because the process is entirely man made, even though we don't always know what the results are going to be. 
* The data given by a numerical model generally fits the expected analytical model.

#### Where Do We Put Computational Physics?

* Creating a computer program falls under the "build a model" category of physics. We have not tested it unless we compare it to real life. 
* Computer programs are now a very important part of every science field. 

### 12 Steps Toward Rock-Solid Scientific Python Code

1. Use version control
* This is useful because it allows you to save multiple versions of a code and easily switch between them or merge contributions.
2. Put your code in the cloud in the open
    * This allows you to share code and keep backup copies of your work.
3. Add a README and a license
    * It is important to have a README file with all the basic information needed to understand and use your code. A license allows other to use, redistribute, and modify your code. 
4. Write docstrings
5. Write tests
    * a doctest is a python module that takes all the examples in your docstrings, runs them, and checks whether the output in the docstring matches the actual output. These are useful for testing individual functions out on various cases. 
6. Keep track of issues
    * Raise an issue on GitHub to remind yourself and other people that there’s something wrong with your code, and have public discussions about it. 
7. Automate the tests
    * Nose is a test automation tool that automatically finds and runs all the tests in your code. 
8. Automate the build
9. Use continuous integration
10. Monitor test coverage
11. Write narrative documentation
12. Catch errors as you type them

* These steps can be done quickly and usually save you time and make your work more credible. 

## Project Ideas

One topic from the Giordano text that I am interested in is Earthquakes and Self-Organized Criticality. If I were to do this, I would probably follow the method that the article suggests and use the Euler or Runge-Kutta method to calculate the force at different positions, or blocks, at a certain time step.   
  
Another idea is to model the waves on a string of a musical instrument, and consider the frequency spectrum. For this project I might to a Fourier transform of the string vibration at various lengths.

## Project Outline 4/18/18

1. The general idea of my project is to simulate earthquakes using the model given in the Giordano text. I plan to change around the level of disorder and randomness in the initial conditions to search for a numerical model that is closer to what we see in nature. If I am feeling very ambitious, and I have the time, I might try to expand the model to two dimensions. 

2. Controlling equations:
* Force equations:
    * Force on block from neighboring blocks: $F_b = -k_c(x_i - x_{i+1}) - k_c(x_i - x_{i-1})$
    * Force of a leaf spring on block: $F_l = -k_p(x_i - v_0 t)$
    * Friction force due to bottom plate: $F_f = -\frac{F_0 sin(v_i)}{1 + |v_i / v_f|}$
* Overall equation of motion: $m_i \frac{d^2 x_i}{dt^2} = k_c(x_{i+1} + x_{i-1} - 2X_i) + k_p(v_0 t - x_i) + F_f$
    * If we break this up, we have: $\frac{dx_i}{dt} = v_i$ and $m_i \frac{d^2 v_i}{dt^2} = k_c(x_{i+1} + x_{i-1} - 2X_i) + k_p(v_0 t - x_i) + F_f$
    
3. The specific scenario I will simulate is a spring system with 25 blocks connected by springs a bottom plate, and a top plate connected to the blocks by leaf springs. I will probably start with the parameters that are given in the text, and then try the calculation again with an increased N value, and different initial conditions. 

4. I intend to use the Euler method on each block to determine its motion over time. I will also need to vary the time steps in order to get accurate and relatively speedy results. 

5. Boundary conditions: 
* The first block will start and x = 0, and $x_i$ will be greater than $x_{i - 1}$.
* The masses, spring constants, magnitudes of forces, and velocity of the top plate moving toward the right will all be nonnegative.
* Friction force should match the other forces until they exceed $F_0$ so that the blocks stay static.

6. The main result I will obtain is a plot of the motion of each individual block over time. They should move suddenly for a short period of time, and generally at the same time as each other. I should also be able to calculate a value of b from the Gutenberg-Richter law, and I will verify this by comparing it to the real life range of b values.

7. Outline:
* Thursday Apr. 19th: Write up the introduction, get started on working code
* Friday Apr. 20th: Run tests and debug if necessary
* Monday Apr. 23rd: Have Giordano’s version of the code done
* Wednesday Apr. 25th: Change parameters, and format plots into clear results
* Thursday Apr. 26th: Write up analysis and make necessary changes to project 1
* Friday Apr. 27th to Friday May 4th: Finalize writing and presentation of project, and revisit old labs
* Monday May 7th: Have draft of talk done
